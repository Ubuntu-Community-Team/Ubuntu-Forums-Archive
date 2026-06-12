---
title: "Adobe flash install error message in 9.04"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by hocvol1 on 2009-04-23
I made a fresh install of 9.04 final, and in setting up, downloaded Adobe flash.  I keep getting error message, "Error dependency not satisfied Libcurl3" and flash will not install.  Tried deleting cache, sudo apt-get autoremove, autoclean and downloaded again but with same results.  Suggestions or is this a bug?

---

### Post by enervation on 2009-04-23
Try:
sudo apt-get install libcurl3

---

### Post by hocvol1 on 2009-04-23
> **enervation said:**
> Try:
sudo apt-get install libcurl3

That worked.  Thank you!

---

### Post by billgoldberg on 2009-04-23
Did you downloaded flash from the adobe website?

Because if you downloaded it from the Ubuntu repo, that shouldn't be happening.

---

### Post by hocvol1 on 2009-04-23
> **billgoldberg said:**
> Did you downloaded flash from the adobe website?

Because if you downloaded it from the Ubuntu repo, that shouldn't be happening.

Yes, I downloaded from Adobe's site.  Thanks for your input!

---

### Post by wewa on 2009-06-02
hi,

i did the sudo apt-get and i get the following error in terminal:

couldn't find package libcurl3

what am i doing wrong?

thanks.

---

### Post by cwrb on 2009-06-07
I am brand new to Ubuntu and I received the same error, just after installing Ubuntu and trying to install the plugin from Adobe site.
How do i do "sudo apt-get ..." and/or where is thre Ubuntu repo site?

---

### Post by MDNZ on 2009-06-07
> **cwrb said:**
> I am brand new to Ubuntu and I received the same error, just after installing Ubuntu and trying to install the plugin from Adobe site.
How do i do "sudo apt-get ..." and/or where is thre Ubuntu repo site?

You use your terminal to do just that. Click on Applications > Accessories > Terminal. After you're in the terminal, type sudo apt-get install libcurl3 . You'll be asked for a password when you do this.

If the package could not be found, try sudo apt-get update first.

---

### Post by kansasnoob on 2009-06-07
I'd just go to terminal and:

```
sudo apt-get install ubuntu-restricted-extras
```

Of course substitute kubuntu or xubuntu with ubuntu if that's what you're running.

Then you'll have to restart Firefox.

---

### Post by philinux on 2009-06-07
This is so easy, when you know how.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

From the drop down select the deb version.

Download to your desktop.

Then just double click the deb file to install.

Edit:- Or the above post will get you flash from the ubuntu repos too.
Click the restricted formats link below for info.

---

