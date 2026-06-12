---
title: "D-Link DWA-552 (please help)"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by arutch on 2007-08-31
So i just installed Ubuntu for my first time ever on my desktop and the first thing I was advised to do was get my internet working on it, unfortunately that's about as far as i didn't get.  Is anyone willing to help me figure out why this card won't work?

---

### Post by peebly on 2007-09-01
Hello

I have had a lot of luck installing dlink cards using the windows wireless driver application in ubuntu.

You did not give much info on your set-up but I take it your connecting to a router using the wireless card.

You would have to have an internet connection to try this, is it possible you can connect your computer to the router using a network cable as a temporary measure.

How to.

Download the driver for your card.

[http://www.dlink.com/products/support.asp?pid=531&sec=0#drivers](http://www.dlink.com/products/support.asp?pid=531&sec=0#drivers)

Download the 1.11 drivers to your desktop, then right click and select extract here.

Now in ubuntu go to add/remove which is under Applications on the menu bar. you will find the app under system tools its called **windows wireless drivers** install it, it will show up in system - administration.

Run the app and then click install new driver, navigate to the drivers you downloaded from dlink, you want the file **net5416.inf** and install it.

You may have to reboot your computer to see if it has worked.

I don't have one of these cards so have never tried it so it might not work, but theres nowt like trying.

---

