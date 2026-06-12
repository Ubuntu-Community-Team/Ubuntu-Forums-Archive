---
title: "Ipod Mounting Problems"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by BelgianKiwi on 2010-12-19
**Re: Gtkpod errors & Ipod will not mount** 			
 			 			 		   		 		 		Hi Guys, I am  having a similar issue with Xubuntu 10.04. I have installed both gtkpod  & amorok but to use either the Ipod must be mouted as an external  device. I have tried the mount command in the terminal as advised in the  help tab in Gtkpod but it advises me to use root but looking at the DEV  and UDEV folders in the root menus I cannot find the device listed as  Sda1 or Sda2.

Is there any workaround terminal command or software I can download to  mount my (Invisible) Ipod Nano from the USB port it is plugged into so  that either Gtkpod or Amorak can recognise it and update it?

---

### Post by Wobblybob on 2010-12-20
can you say which generation iPod you have [[COLOR="Blue"]http://support.apple.com/kb/ht1353[/COLOR]]("http://support.apple.com/kb/ht1353") and run the following command in a Terminal after you have connected your iPod;

lsusb

and post the result.

If the iPod has mounted, it should show in /media folder

---

### Post by BelgianKiwi on 2010-12-21
Hi Wobblybob, I have a 1st Generation Ipod Shuffle 512M. I have issued the terminal response lsusb and get the following message in terminal;

lsusb
Bus 001 Device 002: ID 05ac:1300 Apple, Inc. iPod Shuffle
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I have looked in the /media folder and it only shows CD & Floppy drives, but curiously there is a text document - and no USB input. 

Should I try and download the GNOME Device Manager? Will this help? Do I need to change any settings?

Please let me know if you have any ideas.

Thanks BelgianKiwi

---

### Post by Wobblybob on 2010-12-22
ok so your system is finding it, have you jailebroken the iPod?if not see my post here

[[COLOR="Blue"]http://ubuntuforums.org/showpost.php?p=10261658&postcount=2[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10261658&postcount=2")

---

### Post by BelgianKiwi on 2010-12-22
Hi Wobblybob, still not able to mount

Tried the first terminal command on your jailbreaking post see below;

[B]sudo apt-get install libgpod4 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgpod4 is already the newest version.
The following packages were automatically installed and are no longer required:
  sdparm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/B]

to mount and no sign of anything new in /Media folder.

The second command produced this message;

[B]~$ sudo lsusb -v | grep -i Serial
[sudo] password for domandpaul: 
can't get device qualifier: Connection timed out
can't get debug descriptor: Connection timed out
cannot read device status, Connection timed out (110)
  iSerial                 3 
  iSerial                 1 0000:00:02.0
domandpaul@domandpaul-laptop:~$ [/B]

Rather odd, I will try Ifuse or Gnome devise Manager.

I am open to any ideas.

thanks for your help

---

### Post by Wobblybob on 2010-12-23
I'm using a week old version of Xubuntu 10.10 and my iPod classic video mounts in thunar automatically without gnome-device-manager I'm just not sure what I did or added to make that work :p I did right click the thunar package in synaptic and install all the recommended and suggested packages if that helps

---

### Post by BelgianKiwi on 2010-12-26
Hi Guys, 

Thanks for your help and support. I think after all of I have tried that perhaps I will not be able to mount my 2006 1st generaton 512M Ipod to my Xubuntu 10.04 desktop on my 2003 HP Pavilion Computer. 

I have tried Thunar File Manager, Gnome Device Manager, iFuse, and manual mounting through the root menu, Jailbreaking scripts, and after all of this I am only left with small text file in the /media folder that shows the Ipod type. 

Pity, nevermind.

If anyone out there has exactly the same sort of issue where they have the Gtkpod or Amarok software installed on Xubuntu has has solved this particular problem please let me know.

Cheers

---

### Post by BelgianKiwi on 2011-02-27
Hello all - this gets stranger and stanger. . .

I had given up on Ipod mounting with my system as above than something odd happened. I plugged my 1st gen Ipod Shuffle into my Laptop (Turned off) running Xubuntu 10.04. I turned my lap top on and low and behold it was automounted on my desktop as and IPOD Icon! 

It gets stranger. When I turned my lap top off and when to plug into my network and turn it back on the Ipod would not mount - auto or otherwise:-( I have installed Gkpod and a CD ripper in the meantime but try as I may startting or re-starting, searching devices, USB ports my Xubuntu system will not duplicate what it did once (Automounting) again. It does not seem to recognise the IPOD as a storage device.

Does anyone have any ideas on what is happening ? Any advice?

Cheers Belgiankiwi

---

