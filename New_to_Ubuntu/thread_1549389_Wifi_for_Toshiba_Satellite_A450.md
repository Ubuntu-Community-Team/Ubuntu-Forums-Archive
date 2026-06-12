---
title: "Wifi for Toshiba Satellite A450"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Tmicha8l on 2010-08-09
Hello

I've just now installed Ubuntu and I can't seem to get wifi working on my laptop.
I'm using a [Toshiba Satelite A450]("http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&BV_UseBVCookie=yes&PRODUCT_ID=1076061") and I'm not sure how to check the name of the network card -- I had a little go but it involved compiling so I had to stop there. Anyway, I've opened the terminal and I've typed ipconfig and that gives me a message saying, "the command dosen't exist" or something.

Any help at all would be appreciated.

Kind Regards

---

### Post by roger_1960 on 2010-08-09
Hi

Enter > lspci in terminal and look at the line which starts "network controller"

---

### Post by davidmohammed on 2010-08-09
you may wish to read the [following]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html").  If you have further problems please reply with the output copy-and-pasted into code tags

in a terminal session

sudo lshw -C network

iwconfig

---

