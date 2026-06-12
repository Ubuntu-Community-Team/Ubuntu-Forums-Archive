---
title: "PHP shows no errors"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by callmeabin on 2010-11-16
Hello,

I installed the LAMP package using

sudo tasksel install lamp-server

I created a simple php file with contents as follow and placed it in the
 /var/www/ folder



<?php
include("wrongFile.php");
echo "Hello World!";
?>


and there is no file called wrongFile.php in the folder. I believe an error
has to be shown but i simply get the output as

"Hello World"

I do not get any such error messages even with the require().

Am new to Ubuntu, so please guide me in englishiest way.

Regards,
Abin

---

### Post by Wtower on 2010-11-16
Perhaps something to do with the reporting level (error_reporting) setting of the php.ini file. I am not familiar with LAMP but I guess there should be a php.ini file in a relevant subdirectory of /etc/php5.

Regards

---

### Post by wojox on 2010-11-16
It's been a while since I php'ed Shouldn't it be

```
include('wrongFile.php');
```

For errors check your Apache error log.

---

### Post by mcduck on 2010-11-16
> **Wtower said:**
> Perhaps something to do with the reporting level (error_reporting) setting of the php.ini file. I am not familiar with LAMP but I guess there should be a php.ini file in a relevant subdirectory of /etc/php5.

Regards

You might have a point there. Include only gives a warning, not error, for missing file. 

Using require instead of include should give an actual error.

---

### Post by Wtower on 2010-11-16
> **wojox said:**
> It's been a while since I php'ed Shouldn't it be

```
include('wrongFile.php');
```


For php5 '' or "" should be fine, not sure for older versions though. More info on [php.net]("http://php.net/manual/en/language.types.string.php").

Regards

---

### Post by SeijiSensei on 2010-11-16
For security reasons, PHP errors do not appear on the displayed page.  They only appear in /var/log/apache2/error.log.  You can change the settings for error reporting in /etc/php.ini, but remember to set them back if you publish on the Internet.

Like Unix shells, PHP treats single and double quotes somewhat differently.  If you include a variable in a double-quoted string, the result will include the variable's value.  If you use single quotes, the string will be interpreted literally:

```

$foo='bar';

echo "This is a $foo problem";
echo 'This is a $foo problem';


```

The first version returns "This is a bar problem"; the second version returns "This is a $foo problem".  For any strings that don't include variables I generally use single quotes because they are faster to type.

---

