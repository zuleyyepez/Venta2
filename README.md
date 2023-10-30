# Venta2
<div>
    <form method="post">
        <div>
            <label>Cliente: </label>
            <select name="cboCliente">
                <option value="Antonio">JeanCarlos</option>
                <option value="Felix">Felix</option>
                <option value="John">John</option>
                <option value="Style">Style</option>
            </select>
        </div>

        <div>
            <label>Fecha: </label>
            <input type="date" name="txtFecha">
        </div>

        <div>
            <label>Producto: </label>
            <select name="cboProducto">
                <option value="Tee">Camisa</option>
                <option value="Skirt">Falda</option>s
                <option value="Jeans">Pantalones</option>
                <option value="Had">Gorra</option>
                <option value="Album">Album</option>
            </select>
        </div>

        <div>
            <label>Cantidad: </label>
            <input type="number" name="txtCantidad">
        </div>

        <div>
            <label>Precio: </label>
            <input type="text" name="txtPrecio">
        </div>

        <div>
            <button type="submit" name="btnCalcular">Calcular</button>
        </div>

    </form>
</div>

<h3>Resultados: </h3>
<?php
if (isset($_POST['btnCalcular'])) {
    $fecha = $_POST['txtFecha'];
    $cliente = $_POST['cboCliente'];
    $producto = $_POST['cboProducto'];
    $cantidad = $_POST['txtCantidad'];
    $precio = $_POST['txtPrecio'];
    $subTot = $cantidad * $precio;
    $Iva = $subTot * 0.12;
    $descuento = 0;

    if ($subTot < 50) {
        $descuento = $subTot * 0.05;
        $regalo = "No";
    } else {
        if ($subTot >= 50 && $subTot < 100) {
            $descuento = $subTot * 0.07;
            $regalo = "gorra";
        } else {
            if ($subTot >= 100 && $subTot < 200) {
                $descuento = $subTot * 0.1;
                $regalo = " Camisa";
            } else {
                $descuento = $subTot * 0.15;
                $regalo = "album";
            }
        }
    }
    $total = $subTot + $Iva - $descuento;
    ///resultados
    echo "Cliente: " . $cliente . "<br>";
    echo "Fecha: " . $fecha . "<br>";
    echo "Producto: " . $producto . "<br>";
    echo "Subtotal: " . $subTot . "<br>";
    echo "IVA: " . $Iva . "<br>";
    echo "Descuento: " . $descuento . "<br>";
    echo "Total: " . $total . "<br>";
    echo "Regalo: " . $regalo . "<br>";
}

?>
