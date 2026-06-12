---
title: "Printing to Windows 2000 machine"
date: 2005-09-11
forum: Networking &amp; Wireless
---

### Post by TwiceOver on 2005-09-11
First off you'll have to pardon me for being a complete newbie when it comes to Linux and Ubuntu.  I have installed and attempted to run a wide veriety of Linux flavors but this is the first one I actually feel comfortable with and am willing to learn.

I am trying to print to a Dell 1100 Laser printer connected to a Windows 2000 machine.  I have shared the windows printer under the name 'laser'.  When adding a printer and choosing SMB printer I get the error:

"Printing: Unable to connect to SAMBA host, will retry in 60 seconds...foomatic-rip version $Revision: 3.43.2.6 $ running..."

So I set up printing via the Unix print services as also recommended in one of the how-to forum threads.  When I do that I get the error:

"Printing: Network host '192.168.1.11' is busy, down, or unreachable; will retry in 30 seconds..."

I have tried disabling bidirectional printing support and some of the other things listed in the how-to thread.  I am still unable to print.  Sorry for being new at this, hopefully someone can help.

EDIT: Some info.  
Windows 2000 Box is named: Server2
IP address: 192.168.1.11 (I can ping this from Ubuntu)
Printer share name: laser
Can access shares on this computer.

I have been using the Samsung ML-1000 driver as a couple of searches have shown this driver to work with the Dell 1100.

---

### Post by s_p_a_r_k_y on 2005-09-11
can you have do smb://windowsBox 
from nautilus or 
smbclient -L windowsBox -U windowsUser
from the command line?

---

### Post by TwiceOver on 2005-09-11
[QUOTE=s_p_a_r_k_y]can you have do smb://windowsBox 
from nautilus or 
smbclient -L windowsBox -U windowsUser
from the command line?[/QUOTE]

I am not sure what Nautilus is, but I can do the SMBClient command.

Kinda suprised that the SMBClient step even shows my hidden shares.

---

### Post by s_p_a_r_k_y on 2005-09-11
nautilus is your file manager that your used to. Go to places->network servers and look for windows networks

---

### Post by TwiceOver on 2005-09-11
[QUOTE=s_p_a_r_k_y]nautilus is your file manager that your used to. Go to places->network servers and look for windows networks[/QUOTE]

Yup.  That works fine.  

Tried some other things that I found around the forum which included editing the printers.conf file but to no avail so far.

---

### Post by TwiceOver on 2005-09-12
Well, I don't know what was going on but I got it to work.  I am not sure what exactly fixed it as I did a couple things all at once.

I ended up uninstalling and reinstalling the printer on the Windows machine and then setting up the share again.  I also set up a user account called print without a password and without any rights except to print to the printer.

Went back to the Ubuntu machine added the printer through the SMB Windows Printer option using the username "print" and leaving the password blank and voila it worked.  

The test page is kinda messed up as it scrolls off the bottom of the page.  Probably something minor I can fix or maybe a small difference in the driver since it is not the exact driver for the Dell 1100.

Anyway, this hurdle is over and it feels good.

---

### Post by s_p_a_r_k_y on 2005-09-12
check out linuxprinting.org with your model number to see if anyone there has any tips

---

