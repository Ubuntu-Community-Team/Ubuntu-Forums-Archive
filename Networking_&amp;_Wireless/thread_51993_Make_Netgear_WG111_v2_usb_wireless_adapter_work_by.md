---
title: "Make Netgear WG111 v2 usb wireless adapter work by ndiswrapper"
date: 2005-07-26
forum: Networking &amp; Wireless
---

### Post by ychen on 2005-07-26
After a few day's pain on making NetGear WG111 v2 work on my laptop, I work out this problem today. Let's share the experience below:

# ndiswrapper -i netwg111.inf  /*install the windows xp driver*/
# ndiswrapper -l   /*check if it is installed*/

# modprobe ndiswrapper   /*if works, you can see the light on*/

# ndiswrapper -m  /*boot it as a module*/

# iwconfig wlan0   /*you can see some information about the setting*/
# iwlist wlan0 scan /*you can see some information about your AP*/

In my case, use 128 bits WEP

# iwconfig wlan0 essid ESSID key restricted XXXXXXXXXXXXXXXXXXXXXXXXXX

**There is a trick on finding the key -- find it in the windows xp's registry database.**
Anybody found "key restricted s:XXXXX" works?  I can't use string as the key.

# dhcpclient wlan0

After it is done, the network is up. Now you can use "network-admin" to write the /etc/network/interfaces.

Have fun!

---

### Post by mwaddoups on 2005-07-26
This trick also works for the WG121, which is notoriously hard to setup in linux. :)

---

### Post by mr_bean on 2005-07-26
I did that same thing, with the Netgear WG311v2 and it wouldn't work with 128 bit, but just for kicks I changed it to 64 bit and it connected.

---

### Post by blakeyrat on 2005-08-05
Uh, ok, I'm a brand new user with a WG111, and I don't know how to follow these instructions.  Do I type "ndiswrapper -i netwg111.inf" into a terminal?  I've tried that and I just get command not found.

I've also found that the Ubuntu Device Database program freezes when you run it with no network connection (apparently.  At least, it did for me.)

Thanks in advance for any help.

---

### Post by ychen on 2005-09-09
WG111 v2 can work on Ubuntu 5.04, but when I used WG511 v2, it came out error below:

> Sep  7 23:00:23 localhost kernel: ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
Sep  7 23:00:23 localhost kernel: ndiswrapper (import:235): Unknown symbol: ntoskrnl.exe:ObfDereferenceObject
Sep  7 23:00:23 localhost kernel: ndiswrapper (load_sys_files:335): unable to prepare driver 'wg511v2'
Sep  7 23:00:23 localhost kernel: ndiswrapper (wrapper_init:1494): loadndiswrapper failed (11); check system log for messages from 'loadndisdriver' 

It took me a while to solve this issue. Then I got the solution:

The ndiswrapper with Ubuntu 5.04 is out-of-date! So I go to [http://ndiswrapper.sf.net](http://ndiswrapper.sf.net) to get the newest tarball; then compile it, ```
make deb
``` get two deb packages.

```
sudo ndiswrapper -e wg511v2
sudo dpkg -r ndiswrapper-utils
sudo dpkg -i ndiswrapper-utils_1.2-1_i386.deb
sudo dpkg -i --force-overwrite ndiswrapper-modules-2.6.10-5-386_1.3rc1-1_i386.deb
``` 

Then follow the top thread, make wg111 v2 pcmcia card work.

Suggest Ubuntu update this driver. :smile:

---

### Post by oimon on 2006-02-27
this is Good info - thanks

However I also understand that the WG121 uses the prism chipset

I have problems using Ubuntu 5.10 with ndiswrapper and my SMP kernel 2.6.12-10 SMP - the system freezes upon boot (works OK without SMP)

Can anyone confirm first-hand if the Prism54.org drivers work with the WG121?

thanks

---

### Post by Eyebolt on 2006-02-27
Is this using the wg111 v1 drivers??? my drivers that of course came with my wg111v2 are wg111v2.inf not wg111.inf.

I'm not having any luck with the one that came on my disk. The drivers get loaded fine...I can configure my device, but it just blinks every few seconds in an attempt to get a connection.

---

### Post by Mahones on 2006-04-30
When I do the ndiswrapper -l, things look right, but when i do the modprobe, the blue light flashes once, then goes out, and my keyboard becomes disabled.  If i then unplug the wireless adapter from the USB cable, they keyboard works again.  

Does anyone have any idea why this might be occuring?

Thanks

Mahones

---

### Post by Yurij on 2006-09-25
> **Eyebolt said:**
> Is this using the wg111 v1 drivers??? my drivers that of course came with my wg111v2 are wg111v2.inf not wg111.inf.



It works perfectly fine with Wg111 v2.

---

### Post by MiD-AwE on 2007-01-20
When I follow these instructions, I see the netgear wg111 in the usb section but it does not show as a network device. Is there a command I can use to get ubuntu to recognize wg111 as a network device or some way I can start over without doing a full ubuntu reinstall? I should mention I am using 6.06. I'm willing to do a complete edgy install if necessary. ](*,)

UPDATE: I read in another post that Netgear WG111v2 is not compatible with the 64bit Ubuntu. Maybe this is my answer. I imagine that I'll have to install 32bit Edgy. (rhetorical: When will Ubuntu 64bit finally come of age?)

Thanks

---

### Post by Rotarychainsaw on 2007-01-29
Now why did this let me connect, but the nm-applet (network manager) doesn't> 64 WEP shouldn't be a problem.

edit I should clarify. I have had ndiswrapper working for a while and could connect to unencrypted ponits, but she just wouldnt do wep.

---

### Post by boudders on 2007-02-04
This is great guide, though I am in a pickle.

I can scan using:
iwlist wlan0 scan

And I can see the access points but I cant mange wireless in the Network Manager Applet, so how do I connect?

I also get this when I type in ndiswrapper -m

module configuration contains directive install pci:v000014E4d00004301sv00001737sd00004301bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004301sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004320sv000014E4sd00000417bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004320sv00001737sd00004320bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004320sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install usb:v0846p4220d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install usb:v0846p4240d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete thatmodprobe config already contains alias directive

---

### Post by steve_hill4 on 2007-06-25
Hi all, I'm a newbie who's been trying to get around to Linux for years now. Finally got to install Ubuntu 6.10 and all seems to be going well, well except my wireless adapter.

I have established by Netgear's website that my WG111 is a v1, even though Ubuntu reports it as a V2. Either way, I have copied the netwg111.inf file from the CD that came with it, set up ndiswrapper and gone to install it that way. When I -i it, it tells me it is a invalid file or folder, (the folder within etc/ndiswrapper is created at this point but empty), I then -l it and it tells me it's indeed installed but an invalid version. I can only assume here it is seeing the folder, reporting it installed but not finding the correct contents inside.

Windows obviously works fine with the adapter, (just fairly crap at everything else). I am primarily a Mac user, (where I am now), and the installation disc has been tested under Parallels Desktop for Mac and picked up my built-in Airport card without hassle.

Any pointers?? :-k

---

### Post by Ayuthia on 2007-06-25
You might want to verify the ID by using lsusb at the terminal to see which adapter you have.  The ndiswrapper site has a few driver options for this adapter:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)

---

### Post by neilbmehta on 2007-08-10
Thanks for the info

---

### Post by futileissue on 2007-10-25
I just wanted to post that ndis-wrapper is no longer necessary for this chipset,
Netgear111 series should work in Gutsy Gibbon with plug and play support.

---

### Post by sgtbug on 2007-11-19
shudnt do this but *bump*.. not working on my gutsy 64-bit..

---

### Post by sgtbug on 2007-11-20
it sees my router but just doesnt connect..

it is however working on my xp without any problems.. i tried the ndiswrapper method, but it does NOT work..

it just wont connect to the network.. dunno why..

---

### Post by haifisch27 on 2007-12-29
Sorry, my question is probably very basic, but I am completely new to Linux. I'm using Ubuntu 7.10 and Netgear WG111v2. As mentioned before, I typed 

ndiswrapper -i netwg111.inf

and it replied 

couldn't create /etc/ndiswrapper/netwg111: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152:confused:

What could be the problem? 

Thanks,
Michael

---

### Post by coolbrook on 2007-12-30
> **haifisch27 said:**
> 
ndiswrapper -i netwg111.inf

and it replied 

couldn't create /etc/ndiswrapper/netwg111: Permission denied at /usr/sbin/ndiswrapper-1.9 line 152:confused:


```
sudo ndiswrapper -i netwg111.inf
```

and I suggest it be the same version 1.3 (Windows 98 driver) as the link in my sig.  GL.

---

### Post by txrj on 2008-01-03
Hello all
I have tried the same wireless wg111 device and when I used the command

# modprobe ndiswrapper /*if works, you can see the light on*/

it came back with the error

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko): Operation not permitted

any ideas how I can permit this? Sorry but I am new to Linux.

Thanks

---

### Post by oimon on 2008-01-04
have you confirmed that the directory exists? on mine:
ls -l /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/
total 224
-rw-r--r-- 1 root root 222792 2007-10-13 06:43 ndiswrapper.ko

obviously you must do it as root

---

### Post by carrera594 on 2008-03-24
My adapter works right out of the box on Ubuntu 7.10, the probably is that the signal is horrible and something the signal drops for no reason. Also the network manager just hangs on me, does anyone know how to fix this?

---

### Post by staubio on 2008-06-12
It fired up right out of the box in Hardy for me, too, but it has the same problems with dropped connections. It is using a realtek driver that seems to just give up from time to time. I usually can keep a connection for about an hour.

I think we'll need to blacklist the realtek driver (as it uses it regardless) and use the ndiswrapper method described.

Edit:

Blacklist by adding the line "blacklist drivername" to /etc/modprobe.d/blacklist
Also, remove the old driver (modprobe -r drivername) before modprobing nidswrapper

I'm not sitting on that machine but I believe the offending driver is rtl8187 or something.

---

