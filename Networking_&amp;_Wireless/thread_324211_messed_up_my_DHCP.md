---
title: "messed up my DHCP"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by ivanoats on 2006-12-23
oh boy... i installed KNetworkManager and lost my DCHP connection... then I did sudo remove KNetworkManager and still no connection.  So, I can't connect my ubuntu box to the internet. Where should I start and does anyone have suggestions on how to fix?

---

### Post by sharperguy on 2006-12-23
Are you using Ubuntu or Kubuntu?

In Ubuntu look in system > administration > networking, choose your connection, click properties and make sure its getting the ip automatically.

Then close the properties box and uncheck then check the box nexst to your connection and see if that helps

If its kubuntu i'm not sure what you would do although you could look at [https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/internet.html](https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/internet.html)

---

### Post by ivanoats on 2006-12-23
Thanks for the quick response! I am in ubuntu. I tried what you suggested, but I could not find a "refresh" or "renew" button - it appears to be set to DHCP, but I cannot ping anything.  I know the wifi works because my mac is connected.   Is there a command line tool I could use or some other method?

EDIT: it worked!!! Thanks for your help!

---

### Post by sharperguy on 2006-12-23
Great, I'm glad you got it working

---

