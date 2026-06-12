---
title: "pear HTML_Template_IT"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by tharchin on 2011-01-11
I have the latest version of apache and php running and can't get these scripts to work.  When I load the test.php with errors on I get the following for each call to the $templates object.

Strict Standards: Non-static method PEAR::raiseError() should not be  called statically, assuming $this from incompatible context in  /usr/share/php/HTML/Template/IT.php on line 1075  Strict Standards: Non-static method PEAR::isError() should not be called  statically, assuming $this from incompatible context in  /usr/share/php/HTML/Template/IT.php on line 1178  

Below are my scripts.  thanks for any help.

TEST.PHP

<?php

ini_set('display_errors',1);
error_reporting(E_ALL|E_STRICT);

require_once "HTML/Template/IT.php";

$template = new HTML_Template_IT("./templates");

$template->loadTemplatefile("test.tpl", true, true );

$template->setCurrentBlock("CUSTOMER");

$template->setVariable("FIRSTNAME", "Matt" );
$template->setVariable("SURNAME", "Weiss" );
$template->setVariable("ADDRESS", "30 Walden Dr." );
$template->setVariable("CITY", "Natick" );
$template->setVariable("STATE", "MA" );
$template->setVariable("ZIPCODE", "01760" );

$template->parseCurrentBlock();

$template->show();

?>

TEST.TPL

<html>
<head>
    <title>Customer Details</title>
<body>
<table>
<tr><th>Name<th>Address<th>City<th>State<th>Zipcode

<!-- BEGIN CUSTOMER -- >
<tr><td>{FIRSTNAME} {SURNAME}<td>{ADDRESS}
     <td>{CITY}<td>{STATE}<td>{ZIPCODE}
<!-- END CUSTOMER -->

</table>
</body>
</html>

---

