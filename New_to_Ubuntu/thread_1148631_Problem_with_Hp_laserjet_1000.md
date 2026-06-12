---
title: "Problem with Hp laserjet 1000"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Lars Emil Gutt on 2009-05-04
I can't print with my Laserjet 1000 printer. I followed the instructions on the foo2jzs installation site but when i got to the part about going to localhost:631 cups site it just said: "No printers" under the printers part of the site.
It made it work on another computer, with Ubuntu 8.10. Right now i use 9.04

---

### Post by swoody on 2009-05-04
Hi Lars Emil Gutt, and Welcome to Ubuntu and The Forums! ):P

It has been known that the Laserjet 1000 doesn't work out-of-the-box in Ubuntu, and that the instructions over at foo2jzs need a bit of modification to work for your printer.

Here's a little How To for you to check out. It is a little older, but give it a try and see if it'll work for you :)
[http://ubuntuforums.org/showthread.php?t=200179](http://ubuntuforums.org/showthread.php?t=200179)

Do what the first post in that thread says, and see if it works out for you. Post back here and let us know how it goes :D

---

### Post by Lars Emil Gutt on 2009-05-05
The how to says:
As root, edit the file /etc/cups/printers.conf...
But i dont have a printers.conf file, and if i had i wouldent know how to edit it :(
Im pretty new on ubuntu...

---

### Post by swoody on 2009-05-05
Have you ever had any other printer connected to your computer before? If not, Ubuntu may just create the printers.conf file after it has a printer attached. Try going to the terminal "Applications">"Accessories">"Terminal" and enter (you can copy and paste these commands directly):
```
gksu gedit /etc/cups/printers.conf
```

It'll ask you for your password, so type it in and hit enter. That will not only create the file, but open it for you to edit. Paste this into the file that just opened:
```
DeviceURI file:///dev/usb/lp0
```

Then save the file, either by clicking the 'Save' icon, or going to File>Save. Back in the terminal again, enter this:
```
sudo /etc/init.d/cupsys restart
```

That will restart the CUPS system. Now try connecting your printer, and seeing if it's recognized under "System">'Administation'>'Printing' If you see your printer there, attempt to print a test page, and see if it works! Post back here, and let us know if that doesn't work out for you :)

---

### Post by Lars Emil Gutt on 2009-05-06
I did as the instructions said but still i don't see my printer :(
At cups localhost:631 it still said no printers...

---

### Post by drs305 on 2009-05-06
From the CUPS main menu, have you tried to add the printer? I'm using a LaserJet-1000. Add Printer, Enter a description, and on the Device page see if there is a listing for any USB printer or device. If you find it and click on "Continue" it should show the foomatic driver already selected. I am using foo2zjs. My device URI is: usb://HP/LaserJet%201000

---

### Post by Lars Emil Gutt on 2009-05-06
The cups main menu?

---

### Post by drs305 on 2009-05-06
> **Lars Emil Gutt said:**
> The cups main menu?

With CUPS installed, if you enter [http://localhost:631/](http://localhost:631/) in your browser's url window the CUPS menu should appear.

---

### Post by clive littlewood on 2009-05-06
Hi

HP have a toolbox facility in Ubuntu which can be loaded from synaptic.

Just enter HPLIP in the search box and tick for install.

Further down you will see a gui for the toolbox, so also tick that as well.

Hope this helps.

Clive

---

### Post by Lars Emil Gutt on 2009-05-06
Hmm... Now it shows the printer in the printing menu... But i cant print anything from it..

---

### Post by tundraquad on 2009-05-26
A very _**easy**_ & clean way **which worked** in Jaunty:
unplug usb > del any printer
> from Synaptic, remove any foo, foomatic, hp , hplip , hpoj
> reboot > install hplip-3.9.4b (just double-click the *.run)
> plug usb when rqrd > close all printer config windows >
> set hp-Laserjet-10002 as default printer > open HP Device Mgr > Actions > Install required plugin > select ...from HP authorized...    => printer should spool.
> reboot cpt (should spool during start) > perform a printing test > del printer hp-Laserjet-1000

---

### Post by michaelgilch on 2009-12-20
I tried tundraquad's steps but after removing foo* and hp*, i could not find hplip-3.9.4b.

I unplugged and replugged in the printer and it started working. I'm not sure exactly what I did to get it working because I have been editing config files and reinstalling packages all day, but it works now, even after a reboot. 

If anyone would like to see any of my configuration settings or files, just let me know which ones you want to see. I am using Karmic amd64.

---

### Post by swoody on 2009-12-20
That's good to hear, michaelgilch!

Edit: Sorry, I didn't realize you weren't the OP. Still, good to hear you got it working :)

---

