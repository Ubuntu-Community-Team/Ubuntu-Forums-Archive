---
title: "I can't exit Firefox"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by sanderella on 2009-02-13
The exit button which should be at top right of the screen is not there, just a little wheel which is stuck. I can't exit or minimise, and have to use my on/off button to exit Ubuntu. This has been happening since yesterday.

---

### Post by mike555 on 2009-02-13
Instead you could just log out with   Ctl + Alt +Del   ....... or maybe just rt. click on Firefox top bar if you can see it and click exit .
    turning off Compiz might help .....

---

### Post by redseventyseven on 2009-02-13
Perhaps Firefox has been accidentally set to full-screen mode?

Try pressing F11 and see if that brings your close button back.

Alternatively, you can always exit Firefox through the menu system: File > Exit.

If neither of those approaches works, then (as an absolute last resort) you can open a terminal window and type:
```
killall firefox
```

---

### Post by sanderella on 2009-02-13
Thank you very much, guys. Great help.:KS

---

### Post by sanderella on 2009-02-17
I have to press F11 twice to get it to appear on the screen properly, and I have to do it every time I use Firefox. Is this a Firefox problem? It isn't really a great inconvenience, but slightly annoying, and I'd like to get it rights. Thanks.

---

### Post by shabs on 2009-02-17
Well when you restart firefox and click on View, do you already see a check mark on 'Full Screen'?

---

### Post by perpetualcacophany on 2009-02-17
It seems like everyone has this problem eventually. The problem may be with Compiz. Get CCSM if you don' have it already.

```
sudo apt-get install compizconfig-settings-manager
```

After it's installed open it in System > Preferences > CompizConfig Settings Manager

Find the section called Workarounds. Uncheck Legacy Fullscreen Support.

That should fix the problem for good.

---

### Post by sanderella on 2009-02-18
Thank you perpetualcacophany, this worked.:p

---

### Post by nothingspecial on 2009-02-18
Just so you know Alt + F9 will minimize the current window including firefox.  Alt + F4 will close it.

---

