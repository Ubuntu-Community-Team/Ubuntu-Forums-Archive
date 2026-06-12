---
title: "Share my usb printer with VirtualBox XP guest"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by aharown07 on 2009-08-22
Can't seem to find anywhere how to get my USB printer onto a network so the VirtualBox XP guest I've got running can connect to it.
Maybe somebody can link me to directions?

---

### Post by inobe on 2009-08-22
one question' do you wish to network the printer or allow the guest to be able to use it ?

in virtual box settings under usb you can add the device to the guest usb hardware list.

---

### Post by louieb on 2009-08-22
Which edition Open Source from the repositories. or the PUEL version from Sun?  

For USB support, believe you will need the PUEL licensed version from Sun. [http://www.virtualbox.org/wiki/Editions]("http://www.virtualbox.org/")

---

### Post by aharown07 on 2009-08-23
> **inobe said:**
> one question' do you wish to network the printer or allow the guest to be able to use it ?

in virtual box settings under usb you can add the device to the guest usb hardware list.
Really just want to print to it from the XP guest. But I'm not sure abut the USB option. I've got OSE but there is a USB menu item under Devices, though nothing shows there (maybe it's disabled but still appears in the OSE version?)
I think I'd qualify for the other version but how would one switch?

---

### Post by Marlonsm on 2009-08-23
Just go to Sun's site and download it, PUEL means Personal Use and Evaluation Licence (I think), so as long as you don't do business with the virtual machine, it's alright.

Just use the USB option to connect the printer and install the driver.
Just make sure your user is in the "vbox users" group, or else you can't use USB.

---

### Post by aharown07 on 2009-08-23
> **Marlonsm said:**
> Just go to Sun's site and download it, PUEL means Personal Use and Evaluation Licence (I think), so as long as you don't do business with the virtual machine, it's alright. 
If I download it, is there a way to switch without wiping out my current vbox setup? I guess I should do some reading over at vbox about that.

---

### Post by Marlonsm on 2009-08-24
I'm not really sure about it, but if you make a backup of your virtual harddrives, it'll be very easy to recover the virtual machines after reinstalling.
Maybe someone knows it for sure...

---

### Post by miwaypet on 2009-08-24
Just uninstall from synaptic without complete removal ( a simple uninstall). Then when you install the new virtualbox it will use the files already created including the virtual machine.

---

### Post by aharown07 on 2009-08-26
Reporting in...  Uninstalled VBox OSE from Aptitude and then installed the PUEL version. No problems there. It's a little bit different. It prompts you a couple of times and there's a wait while it does some kind of compile.
And the menu item is in a different place after install (a reboot may be necessary.... I couldn't find it in the menus until I rebooted but I may have simply not seen it there). New location is Applications > System Tools.
It migrates the old settings to the new install after a prompt.

So now I just have to figure out the USB stuff and shd be good to go.

---

