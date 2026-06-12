---
title: "Apache/PHP Error"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Kchymet on 2009-12-16
I installed Apache and PHP using the instructions found here:
[http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/](http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/)
These instructions the PHP should be working since I got the output, but then now when I try a simple PHP entry:
```

<?php
echo &#8220;Hello World&#8221;;
?>
```I get the following error on Firefox:
> **Parse error**:  syntax error, unexpected T_STRING, expecting ',' or ';' in **/var/www/test.php** on line **2**What would the reason for this be, and how can I fix this?

---

### Post by jamieleshaw on 2009-12-16
> **Kchymet said:**
> I installed Apache and PHP using the instructions found here:
[http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/](http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/)
These instructions the PHP should be working since I got the output, but then now when I try a simple PHP entry:
```

<?php
echo &#8220;Hello World&#8221;;
?>
```
I get the following error on Firefox:
What would the reason for this be, and how can I fix this?
Replace &#8221; with " 
Here is a fixed version 
<code><?php
echo "Hello World";
?></code>

---

### Post by Kchymet on 2009-12-16
That worked. Thank you very much. I wish I had noticed that -.-... Seems like a stupid thing to miss

---

