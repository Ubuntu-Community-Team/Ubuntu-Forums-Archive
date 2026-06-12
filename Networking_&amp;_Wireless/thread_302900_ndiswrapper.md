---
title: "ndiswrapper"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by johnny9794 on 2006-11-19
ok i am using edgy , I had exactly the same problem with dapper 6.06.1 and it is really bugging the heck out of me.

I downloaded the windows driver for my D-Link DWL-G510 wireless card from
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D)
under 
Contents List of D
Card: D-Link DWL-G510
[ftp://ftp.dlink.com/Wireless/dwlg510/Drivers/dwlg510_driver_100.zip](ftp://ftp.dlink.com/Wireless/dwlg510/Drivers/dwlg510_driver_100.zip)

I installed ndiswrapper from the this guide
[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)

Then I installed the driver ```
sudo ndiswrapper -i /home/johnny/Driver/manual/Win98/mrv8k51.inf
```
i give the cmd ```
sudo ndiswrapper -l
``` and I get  a list of my driver saying invalid driver
```
Installed ndis drivers:
mrv8k51 invalid driver!
your_driver     invalid driver!
```

I have read and followed exactly what to do, this also happened on my dapper 6.06.1, I have tried all the os drivers "WinXP, Win2K, WinME and Win98."

How come I am getting invalid driver?

Do I need to configure a file or something, is there something I am missing?

Has anyone else ran into this problem?

---

### Post by spd106 on 2006-11-19
Which version of the card do you have? 

Is it the one with the Marvell or the Atheros chipset. Have a look at the output from **lspci** at a terminal and check the sticker on the back of the card for the revision number.

---

### Post by johnny9794 on 2006-11-19
> **spd106 said:**
> Which version of the card do you have? 

Is it the one with the Marvell or the Atheros chipset. Have a look at the output from **lspci** at a terminal and check the sticker on the back of the card for the revision number.

Output of lspci 
```
00:0c.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
```

I think its version ver.1.00

---

### Post by trubblemaker on 2006-11-19
you need to remove both the bad drivers, you might need to manually delete them deleting their folders from /etc/ndiswrapper.  spd106 is right you need to get the right driver for the job google 

but you might be running into a native driver /ndiswrapper issue

[https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1](https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1)

isn't the same version but it might help you find your way.  and this was at the bottom of that page.  

   > The card is often incorrectly recognized by Ubuntu. This causes the module orinoco_pci to be loaded (and subsequently time out) during the 'Starting hotplug system' part of the boot process. To prevent this module from loading add the line

      orinoco_pci

to the bottom of /etc/hotplug/blacklist

so you could try blacklisting the module, removing the "your_driver" from ndiswrapper, then reboot and see if your any closer.  If there is a native driver issue you'll need to remove ndiswrapper or the native driver from the kernel before trying to use it. (blacklisting would work.)  as they will fight eachother and you'll have no wireless

also Check here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/](http://ndiswrapper.sourceforge.net/mediawiki/index.php/) to see if your cards listed as compatible with ndiswrapper

---

### Post by johnny9794 on 2006-11-19
ok I took both out and rebooted then reinstalled the mrv8k51 driver and i got good results :)
```
johnny@Edgy:~$ sudo ndiswrapper -l
Installed ndis drivers:
mrv8k51 driver present, hardware present
```

But I do have a problem.
When i issue this cmd 
```
sudo modprobe ndiswrapper
```
I get bad results
```
johnny@Edgy:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```

How could i fix this problem? I went to go put orinoco_pci into /etc/hotplug/blacklist but Couldn't find "/etc/hotplug/blacklist". 
Do i need to create the directory and file of "/etc/hotplug/blacklist"?

Thank You for your quick reply.

---

### Post by trubblemaker on 2006-11-20
that could mean the /etc/modprobe.d/blacklist,(this is how you should remove the native driver) 

what's tail of the dmesg after trying "sudo modprobe ndiswrapper". 

How'd you remove both? try a reboot might help.

---

### Post by johnny9794 on 2006-11-20
> **trubblemaker said:**
> that could mean the /etc/modprobe.d/blacklist,(this is how you should remove the native driver) 

what's tail of the dmesg after trying "sudo modprobe ndiswrapper". 

How'd you remove both? try a reboot might help.


I don't understand 

> that could mean the /etc/modprobe.d/blacklist,(this is how you should remove the native driver) 

what's tail of the dmesg after trying "sudo modprobe ndiswrapper".

But I uninstalled the two by issuing
```
sudo ndiswrapper -e your_driver
sudo ndiswrapper -e mrv8k51
```

---

### Post by trubblemaker on 2006-11-20
right so you removed the drivers from ndiswrapper I understand.  I think that your underlying problem is that there is a native driver for you nic.  that means the kernel is loading a driver at boot *and* you installed ndiswrapper.  so both are trying to driver at the same time.  what do you get if you run the command:
```

rmmod ndiswrapper
iwlist scan

```

---

### Post by johnny9794 on 2006-11-20
> **trubblemaker said:**
> right so you removed the drivers from ndiswrapper I understand.  I think that your underlying problem is that there is a native driver for you nic.  that means the kernel is loading a driver at boot *and* you installed ndiswrapper.  so both are trying to driver at the same time.  what do you get if you run the command:
```

rmmod ndiswrapper
iwlist scan

```

for rmmod ndiswrapper

```

johnny@Edgy:~$ rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
```

and then for iwlist scan

```
johnny@Edgy:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.
```

---

### Post by trubblemaker on 2006-11-20
well it was worth a try, ok so I suggest adding "blacklist orinoco_pci" to /etc/modprobe.d/blacklist
 
something like 
```
 sudo echo "blacklist orinoco_pci" >>/etc/modprobe.d/blacklist 
``` should do the trick then reboot and see if you can load ndiswrapper, if it isn't already present.  If you can't get ndiswrapper up and running post the last 20~ish lines of "dmesg" for me.

---

### Post by johnny9794 on 2006-11-20
Ok I added "blacklist orinoco_pci" to /etc/modprobe.d/blacklist and rebooted.

Then i issued ```
sudo modprobe ndiswrapper
``` and got the same error 

```
johnny@Edgy:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```

Then you mentioned, see if I can load up ndiswrapper, did you mean just load it like as in typing "ndiswrapper" in the terminal without the quotes?
if so I got

```
johnny@Edgy:~$ ndiswrapper
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
```

Then for dmesg

---

### Post by trubblemaker on 2006-11-20
I'm done for tonight my girls wants loving will post more tomorrow.

---

### Post by johnny9794 on 2006-11-20
kk Thanx :).

---

### Post by trubblemaker on 2006-11-20
Hey I just checked your dmesg, you need to reinstall ndiswrapper.  us the "ndis from source" in my signature below

---

### Post by johnny9794 on 2006-11-20
good mornin, ok i installed from the source and everything went well up to the part of
 
```

johnny@Edgy:~/ndiswrapper-1.28$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
couldn't add module alias:  at /usr/sbin/ndiswrapper line 717.
```

[edit]
ok i just rebooted and put
```
sudo ndiswrapper -m
```
and got
```
modprobe config already contains alias directive
```
so i guess that is good?

---

### Post by johnny9794 on 2006-11-20
here is my new dmsg if you want it

---

### Post by trubblemaker on 2006-11-20
did you blacklist that driver?  I found [another post talking about it:]("http://ubuntuforums.org/showpost.php?p=222955&postcount=127")..  It's a total 180 on what we're doing but it is your driver.  and basically underlines that the driver(kernel module not ndis:driver) must be used or it must be blacklisted.

---

### Post by FrodoB on 2006-11-20
johnny;

I would just ask if you have seen this:

[http://www.megalinux.net/archives/467.html](http://www.megalinux.net/archives/467.html)

This gentleman gives some instructions that would indicate that you have to be careful which cab file you get the driver from. Could this be part of your issue?

---

### Post by trubblemaker on 2006-11-20
FrodoB like the idea, good call

---

### Post by johnny9794 on 2006-11-20
k I will try the link that FrodoB posted.
hope it works prolly won't but uhwell.
Thank You so much Trubblemaker for your time and help.
Thanx for the link FrodoB.

---

### Post by FrodoB on 2006-11-20
The key to getting ndiswrapper to work is finding the exact right NDIS files to work with. Not all of them work and a lot just somewhat work which causes a lot of frustration.

---

### Post by johnny9794 on 2006-11-20
> **FrodoB said:**
> The key to getting ndiswrapper to work is finding the exact right NDIS files to work with. Not all of them work and a lot just somewhat work which causes a lot of frustration.

Yeah sounds like a needle in a hay stack

---

### Post by trubblemaker on 2006-11-20
if you are still on dual boot with windows, you can make it tell you what files it's using, yuo have to dig, look at drivers but it's totally possible.

---

