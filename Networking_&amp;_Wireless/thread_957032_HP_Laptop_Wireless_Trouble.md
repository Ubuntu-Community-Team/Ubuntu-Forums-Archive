---
title: "HP Laptop Wireless Trouble"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by PrinceArithon on 2008-10-23
OK so I searched around the net and can't seem to find my solution...well I'll admit.  Not the solution that I want...so I figure I'll ask to see if there is something I can do.

I recently had to buy a new laptop.  Since I've had so much hardware trouble with Dell I figured I'd try HP.  Since I have no choice thanks to classes I need to dual boot Vista....and Ubuntu.

My first problem with wireless....so let me give you the run down on what I got.

I have an HP Pavilion dv5t 1000.  As far as from what I can tell I have a "Wireless-G Card" (I'm not great with hardware really).  Anyway, I can't seem to get this thing to work.

So right now I'm on my Windows partition hoping to find some kind of help.

I don't have a really easy wired connection to get onto the internet...so I was kinda hoping there were things I could download onto my windows partition, and then transfer them over to my Ubuntu partition and then set things up from there....

---

### Post by PrinceArithon on 2008-10-23
Never mind guys I got it to work.

I was lucky enough to be able to steal the internet to myself for about 30 mins while I simply went in, upgraded my source list.  Then after it upgraded I downloaded all the updates, I also updated all my restricted drivers, and then sure enough the restricted drivers showed me that I could now enable the Broadcom wireless.

So for all you HP people Broadcom does HP's generic wireless card for the laptop...

Anyway I loaded my nvidia driver and the wireless driver and restarted my system.  After that all I had to do was touch the wireless lite on my keyboard after Ubuntu reloaded and I now have wireless again.

So yeah fixed it now.

---

### Post by Ayuthia on 2008-10-24
Glad to see that you have it working.  The 4311, 4312, 4322, and 4328 series Broadcom cards now have a driver that will work with Hardy once you have the 2.6.24-21 kernel.  The Intrepid (8.10) version will have it on the live CD so those cards will now work on the live CD and if you install Intrepid, it will work once you activate the Broadcom STA driver through System->Administration->Hardware Drivers.

It is the proprietary driver that was made by Broadcom.  There is also an open source version that comes with the kernel (b43), but it requires some firmware to make it work.  This driver provides more functionality, but cannot work out of the box without some help.

---

