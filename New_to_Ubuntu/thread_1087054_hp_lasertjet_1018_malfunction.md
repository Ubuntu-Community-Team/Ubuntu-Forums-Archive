---
title: "hp lasertjet 1018 malfunction"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Blåbär on 2009-03-04
Hi again.

I don't know if this is suitable in this area, but here goes:

My printer is automatically detected, receive printing jobs and the computer confirm and execute. Ubuntu see them as executed (nothing qeued up) - but nothing's getting printed. Yes, there's "ink" in it and it's loaded with paper(!).

The printer works fine under windows.

Any idea what could be wrong? I don't even get any error messages...

/Al.

---

### Post by lykwydchykyn on 2009-03-04
Can you post the contents of /var/log/cups/error_log
Is it network or USB?

---

### Post by kansasnoob on 2009-03-04
You didn't mention what version of Ubuntu you're using, but I've had trouble with HPLIP in 8.10. I always have to install the newest hplip here:

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1018.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1018.html)

You can see that your printer is supported.

What I've always had to do in Ubuntu 8.10 is go to Synaptic and remove "all" hplip, then download the newest hplip from the website.

Just use the automatic installer:

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

I have occassionally run into dependency problems, so if you run into trouble please use the "quote" feature on the forums and post the output from the installer.

I should also add that I've always had to add the following packages to get the HPLIP gui (toolbox) to work:

```
sudo apt-get install &#65279;libqt4-assistant libqt4-help libqt4-svg libqt4-test libqt4-webkit libqt4-xmlpatterns python-qt3 python-qt4 python-qt4-common python-reportlab python-sip4 ttf-dustin

```

And the gui will now show up in Accessories > HP Device Manager.

---

### Post by Blåbär on 2009-03-04
Kansasnoob - that did the trick!

Thanks.

[solved] - wherever I label the thread that. :)

/Al

---

