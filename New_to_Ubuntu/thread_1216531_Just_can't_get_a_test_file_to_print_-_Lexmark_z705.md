---
title: "Just can't get a test file to print - Lexmark z705"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by clivewalker555 on 2009-07-18
I've just installed Ububtu 9.04 and can't get the printer going.

It is a shared printer which is attached to a neighbouring windows running PC.

I have downloaded the drivers and installed them. When I installed the printer (as a network printer using windows printer via SAMBA) everything seemed to go fine.

I now have the printer showing as the default one (the only one) in printer configuration - localhost but when I try and print a test page it shows as "failed".

It goes from:

Printer Status : Idle - usr/lib/cups/filter/rastertoz700

to:

Printer Status : Idle - usr/lib/cups/filter/rastertoz700 failed.

This also happens if I try to print a document. There is no authentication required from the other PC.

When the printer configuration offers to diagnose the problem, I get as far as being asked if I want to allow de-bugging. I say yes and then the dialogue box disappears never to be heard of from again (unless I repeat the process)

The response from the query: uname -a 

yields:

Linux Ubuntu 2.6.28-13 generic #45 - Ubuntu SMP Tue Jan 30 19:49:51 UTC 2009 i686 GNU/Linux.

Any assistance will be gratefully received.

---

### Post by TuxLand on 2009-09-04
Lexmark P700 Z700 serie works great in edgy feisty & jaunty .

These instructions assume your USB is working correctly and that you already have "alien" installed from the package manager. If this is not the case for you, search around because the instructions on how to take care of this is on the site.

go to a terminal and make a dir lexmark. I made it in my home folder so that it was accessible regardless of which kernel I booted to.

Code:

mkdir /home/*YOURUSERNAME*/lexmark

As said above, download these files (right click, save as, and save them to your newly created lexmark directory):

[http://users.cybercity.dk/~dko12479/z700llpddk-2.0-1.i386.rpm]("http://users.cybercity.dk/%7Edko12479/z700llpddk-2.0-1.i386.rpm")
&
[http://users.cybercity.dk/~dko12479/lexmark-z700-cups-driver-1.1.1-1.i586.rpm]("http://users.cybercity.dk/%7Edko12479/lexmark-z700-cups-driver-1.1.1-1.i586.rpm")


go back to the terminal and do the following commands:

Code:

cd /home/*YOURUSERNAME*/lexmark
sudo alien -t z700llpddk-2.0-1.i386.rpm
sudo alien -t lexmark-z700-cups-driver-1.1.1-1.i586.rpm
sudo tar xvzf  z700llpddk-2.0.tgz -C /
sudo tar xvzf lexmark-z700-cups-driver-1.1.1.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z700-lxz700cje-cups.ppd.gz
sudo /etc/init.d/cups restart

and just to check to make sure it being recognized properly:
Code:

cd /usr/lib/cups/backend
./z700

and it should show you this or something similar:
Code:

direct z700:/dev/usblp0 "Lexmark  Lexmark Z700-P700 Series" "Lexmark Printer"

(if required install trought synaptic libstdc++.so.5)

If all is good, you can close the terminal out.

Go to SYSTEM > ADMINISTRATION > PRINTING to set up the printer
Select "New Printer"
Fill out whatever you want for Printer Name, Description, & Location
click "Forward"

Under "Select Connection" you should see "Lexmark Printer" and select that.
Next to it at "Enter Device URI" you should see the USB port where it is connected to ( such as - "z700:/dev/usblp0")
click "Forward"

You then have the option to "Select Printer From Database" or to "Provide PPD File". Choose "Provide PPD File"
Select the location "/usr/share/cups/model/Lexmark-Z700-lxz700cje-cups.ppd"

When you're done and back at the main Printer Configuration page, you should see listed under Local Printers "Z700-v1.0-1". That's a sign of success You can select it and change the options you want like making it your default printer, printing a test page, and so on, but that should pretty much do it.

I had tried many other ways and this was the only way that worked correctly for me. I hope it can be of help to some of you other p700 z700 owners.

---

