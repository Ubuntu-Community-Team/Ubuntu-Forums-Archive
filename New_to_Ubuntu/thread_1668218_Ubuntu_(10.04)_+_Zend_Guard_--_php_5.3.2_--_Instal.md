---
title: "Ubuntu (10.04) + Zend Guard -- php 5.3.2 -- Install Problem"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Masked Crusader on 2011-01-16
I cannot seem to find any assistance with this matter and I cannot post on the Zend forums for some reason.  Their new registration process for their forums is broken.

Anyways, I am hoping someone can point me to some kind of guide/tutorial for figuring this out.

I am trying to run PHP Pro Bid on my server and it requires Zend Optimizer (Zend Guard Loader in my case because I am running PHP 5.3.2). 

I have placed the ZendGuardLoader.so file in my /usr/local/lib/Zend folder and then put the following in my php.ini file:

```
zend_extension = /usr/local/lib/Zend/ZendGuardLoader.so
; Enables loading encoded scripts. The default value is On
zend_loader.enable=1
```I put this at the very top of my php.ini file right after the [PHP] tags.

Here is the site I am running the PHP Pro Bid script at: [http://www.maskedcrusader.com/](http://www.maskedcrusader.com/)

Any help would be greatly appreciated.

---

### Post by memento_as on 2011-06-15
yes the same problem :( how to solve it ?

---

