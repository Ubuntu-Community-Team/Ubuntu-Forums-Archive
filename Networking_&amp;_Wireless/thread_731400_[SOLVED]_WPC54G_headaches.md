---
title: "[SOLVED] WPC54G headaches"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by kewlfuzz on 2008-03-21
hi guys,

I'm a new user, and could really use some help here, i'll try to describe my issue fully.

I have a linksys Model No. WPC54G (no ver the linksys guy said ver 1)wireless adapter (fcc id: PKW-WPC54G-2), 

i have been using ndiswrapper to try and use a WPC54G ver 2 (DIFFERENT CARD) using this guide:

[http://blog.eksfiles.net/2007/12/30/using-the-linksys-wpc54g-v2-and-wpa-with-ubuntu-gutsy/](http://blog.eksfiles.net/2007/12/30/using-the-linksys-wpc54g-v2-and-wpa-with-ubuntu-gutsy/)

but then i realised that my ver 2 card (DIFFERENT CARD) never worked on windows either,

so try my ver 1 card and ubuntu said it was using a broadcom b43xx or bcm43xx chipset needed proprietary driver, would you like to install?  i said yes and did the restart and i could see the network!  i know the wep key i've checked it over and over but everytime i try to connect it keeps coming back and asking me for the wep key again and again never quite connecting, i get syslogs like this:

Mar 21 18:50:37 super-duper kernel: [  489.612000] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Mar 21 18:50:37 super-duper last message repeated 7 times
Mar 21 18:50:37 super-duper kernel: [  489.612000] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
Mar 21 18:50:37 super-duper last message repeated 3 times
Mar 21 18:50:37 super-duper kernel: [  489.616000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Mar 21 18:50:39 super-duper kernel: [  491.412000] pccard: card ejected from slot 0

is there a good easy way to fix this?  i've been trying to ndiswrapper the driver i downloaded from linksys(not sure if this is the right approach or not) but when i try
 sudo ndiswrapper -i <filename>
terminal returns:
driver lsbcmnds is already installed

do i just need to uninstall lsbcmnds, and try the files i have?  how would i do that?  or is there some other little tweak or command line i can use to fix these issues?  i mean it seems to work kind of, other than the whole asking for wepkey repeatedly and never actually connecting the the network

thanks a lot for showing ubuntu love,
kewlfuzz

---

### Post by kevdog on 2008-03-21
Ok,  you have two overall options here

#1 - bcm43xx
#2 - ndiswrapper with the bcmwl5.inf file and lscmnds physical driver file

Both bcm43xx and ndiswrapper are considered kernel modules

The bcmwl5.inf and lscmnds are a Window's driver

The Window's driver is loaded inside the ndiswrapper kernel module

Then either the ndiswrapper or bcm43xx kernel module need to be loaded into the kernel (with the modprobe statement)

The /etc/modprobe.d/blacklist and /etc/modules file control which modules will specifically be loaded during boot.  Drivers contained inside the linux kernel (such as bcm43xx -- this driver is in the vanilla kernel) automatically load during boot unless specifically put in the blacklist file to prevent this

Kernel modules such as ndiswrapper (a third party kernel module not contained by default in the linux vanilla kernel) need to be mentioned explicitly in the /etc/modprobe file in order to get them to load during boot.

I know this didn't probably specifically answer some of your questions, however what else do you need to know!?

---

### Post by kewlfuzz on 2008-03-21
like i said bcm43xx sees the network asks for wep repeatedly and never connects so i guess i need to use ndiswrapper? well once i put my card back in and rebooted i was able to remove bcm43xx using the restricted drivers manager, then reboot again, but when i try to use ndiswrapper

> ser@super-duper:~$ sudo ndiswrapper -i /home/user/linksys/Driver/NT/LSBCMNDS.inf
[sudo] password for user:
driver lsbcmnds is already installed
user@super-duper:~$ sudo depmod -a
user@super-duper:~$ sudo modprobe ndiswrapper
user@super-duper:~$ sudo modprobe -r acx
user@super-duper:~$ sudo gedit /etc/modprobe.d/blacklist
user@super-duper:~$ ndiswrapper -l
lsbcmnds : invalid driver!
user@super-duper:~$ 

so my question i guess is how do i uninstall lsbcmnds?  and once i do should i install the lscmnds i've dled from linksys?  if so should i use the one in the NT folder or the one in the 9X folder?  also i have no bcmwl5.inf only a bcmwl5.sys and a lsbcmnds.inf in the driver folder i got from linksys for WPC54G ver 1

thanks for helping a noob,
kewlfuzz

---

### Post by kevdog on 2008-03-21
You can remove the driver from inside ndiswrapper by 

sudo rm -rf /etc/ndiswrapper/*

You dont have a Windows XP driver available?  Have you checked on the linksys website?

Can you run this command in the terminal and post the output?
lspci -n | grep '14e4:43'

---

### Post by kewlfuzz on 2008-03-22
user@super-duper:~$ lspci -n | grep '14e4:43'
user@super-duper:~$ 

i get nothing right now

but lemme try to edit all the files uninstall ndiswrapper reinstall bcm43xx and reboot then i'll come back and try again

---

### Post by kewlfuzz on 2008-03-22
user@computer:~$ lspci -n | grep '14e4:43'
user@computer:~$ sudo rm -rf /etc/ndiswrapper/*
[sudo] password for user:
user@computer:~$ sudo gedit /etc/modprobe.d/blacklist
user@computer:~$ sudo gedit /etc/modules
user@computer:~$ 

so i ran those commands made sure my edits to modules and blacklist were commented out and used the package manager to remove ndiswrapper entirely

now i am going to try a reboot

---

### Post by kewlfuzz on 2008-03-22
so i reinstalled bcm43xx now i get:
user@computer:~$ lspci -n | grep '14e4:43'
02:00.0 0280: 14e4:4320 (rev 02)
user@computer:~$

---

### Post by kevdog on 2008-03-22
Lets get on the same page

You either use the bcm43xx driver or you use ndiswrapper.  If everything works with bcm43xx driver -- great.  If it doesnt then uninstall it (or put blacklist bcm43xx in the blacklist file) and move on to ndiswrapper.  You are kind trying to use both kernel modules at the same time.

You have a 4320 chipset and I dont even know if its supported by the bcm43xx driver since it doesnt exactly specify either way:

Supported:
    * bcm4303 (802.11b-only chips)
    * bcm4306
    * bcm4311 rev 1 / bcm4312
    * bcm4311 rev 2 / bcm4312 (needs patches for 2.6.24)
    * bcm4318 

unsupported

    * The 802.11a part of the 4309 and 4312 is not supported.
    * There is no support for any Draft 802.11n features. We are working on it.
    * BCM 4328/4329

---

### Post by kewlfuzz on 2008-03-22
i finally got it to work!  i am posting this from my wifi connection.

after uninstalling and blacklisting bcm43xx just to be sure then uninstalling reinstalling and running ndiswrapper with the lsbcmnds.inf i found in the folder downloaded from linksys i got it to work

i'm not sure if you're in charge of it or not but you may want to add this card to the list, of cards that work as stated earlier it is a linksys Model No. WPC54G (no ver the linksys guy said ver 1)wireless adapter (fcc id: PKW-WPC54G-2)

thanks kevdog
kewlfuzz

---

### Post by kevdog on 2008-03-22
Can you post lspci -nn again and the drivers you ended up using?  I want to add this to a master list of broadcom chipsets.

---

### Post by kewlfuzz on 2008-03-22
lspcr-nn
returns:
02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

lspci -n | grep '14e4:43'
returns:
02:00.0 0280: 14e4:4320 (rev 02)

it worked after i got the driver from here:
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&packedargs=sku%3D1130276681921&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230081921B03&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&packedargs=sku%3D1130276681921&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230081921B03&displaypage=download#versiondetail)

and ran (or installed?) ndiswrapper using the lsbcmnds.inf i found in the nt folder which was in the drivers folder
sudo ndiswrapper -i <path and filename>

blacklisted:
blacklist bcm43xx
blacklist acx
blacklist ssb
blacklist b43

which was probably overkill but who knows just wanted to be safe

made module
sudo depmod -a
sudo modprobe ndiswrapper

also:
sudo modprobe -r acx

and:
sudo gedit /etc/modules
and added
# doing this to make my wireless card work properly
# Set ndiswrapper to load automatically. Edit the /etc/modules file
ndiswrapper

thats what i REMEMBER doing i guess i should have copy pasted everything before the restart to make sure nothing got lost, i was expecting another failure i must admit, shame on me.

but i hope that gives you the info you were asking for
and thanks again
kewlfuzz

---

