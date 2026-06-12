---
title: "Firefox &quot;Launch Application&quot; window"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by suomalainen on 2011-06-30
Ubunteros,

Would anyone happen to know how applications are removed from the "Launch application" window in Firefox?

Pic is attached as reference.

Thank you!

---

### Post by jerrrys on 2011-06-30
tools>addons>plugins

---

### Post by drpjkurian on 2011-06-30
Not sure
You can tr by right click the selection and see for delete or remove option

---

### Post by suomalainen on 2011-06-30
Thanks folks!

The right click idea was the most intuitive to try first but since that didn't work I asked the "how to question".

Regardless, the "tools>addons>plugins" may or may not work. I don't know?

I want to remove Sopcast from the launch application menu and haven't been able to determine how its done.

I DO NOT WANT TO UNINSTALL THE PROGRAM!

Thanks!

---

### Post by Elfy on 2011-06-30
This might help - [http://ubuntuforums.org/showthread.php?p=8783218](http://ubuntuforums.org/showthread.php?p=8783218)

---

### Post by suomalainen on 2011-06-30
Thanks forestpiskie. I gave it a go but no luck. Although the info is only a year old it seems things are out of place and not including the information in specifically referenced files.

---

### Post by Elfy on 2011-06-30
I'd suspect that lovinglinux has some firefox search going on and is likely to pitch in at some point. 

That said I appear to have the mimetype.rdf file in my .mozilla/firefox/stupidname.default folder

> .mozilla/firefox/gmhqg0qg.default/mimeTypes.rdf

---

### Post by suomalainen on 2011-06-30
Hi,

I attached a pic and as you can see none of the programs found in Launch Application are in the .rdf file I have.

Kinda strange.....

---

### Post by Elfy on 2011-06-30
OIC - thought you meant you didn't have the file.

I've no idea then - I just had a search as it intrigued me ...

---

### Post by lovinglinux on 2011-06-30
> **forestpiskie said:**
> I'd suspect that lovinglinux has some firefox search going on and is likely to pitch in at some point.

Indeed :-)

> **forestpiskie said:**
> That said I appear to have the mimetype.rdf file in my .mozilla/firefox/stupidname.default folder

The mimetype.rdf is indeed the file you need to delete. However you need to close Firefox first.

Close Firefox and try this:

```
rm -f ~/.mozilla/firefox/**/mimeTypes.rdf
```

BTW, your dialog looks very different than mine. Which version of Firefox you are using?

---

### Post by Elfy on 2011-06-30
I can unsubscribe now then :)

---

### Post by suomalainen on 2011-06-30
Thanks Lovinglinux! That did the trick.

Thanks to everyone for your support!!!!!

Have a Great summer 2011 !!!!!

---

### Post by lovinglinux on 2011-06-30
> **suomalainen said:**
> Thanks Lovinglinux! That did the trick.

Thanks to everyone for your support!!!!!

You are welcome.

> **suomalainen said:**
> Have a Great summer 2011 !!!!!

Thanks. Please enjoy the summer for us, because unfortunately we entered the winter here and it is freezing already :(

I live in a warm country, so the winter is not harsh, but anything between 0 and 5 degrees Celsius is very cold for us. A couple of nights ago the temperature drop below zero in some places.

---

