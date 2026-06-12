---
title: "Connecting to my wireless network"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by tommyperkins on 2006-12-30
Hi,

I've just built my own PC and decided to install Ubuntu, but i'm having a problem connceting to my wireless network.

I'm using a Netgear DG834 wirless router, and trying to connect to it using WG111 v2 USB adaptor. 

The problem is i can't seem to get the USB driver cd to run, how would i go about doing this? and what other programs would i need in order to complete this process?

You've probably had this question a million times! I did look for some solutions but seem to be going round in circles. ](*,) 

Any help would be great!

Cheers.

---

### Post by scaryant on 2006-12-30
Try checking out the [Ubuntu WiFi Help documents]("https://help.ubuntu.com/community/WifiDocs"). The troubleshooting pages there are very well written in pretty much lay-mans terms.

It might interest you to know that the WG111 v2 doesn't appear in the list of Ubuntu [supported WiFi cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), however this doesn't necessarily mean it *wont* work.

I'm having my own problems with my 3Com USB card, so good luck!! :)

---

### Post by tommyperkins on 2006-12-30
> **scaryant said:**
> Try checking out the [Ubuntu WiFi Help documents]("https://help.ubuntu.com/community/WifiDocs"). The troubleshooting pages there are very well written in pretty much lay-mans terms.

It might interest you to know that the WG111 v2 doesn't appear in the list of Ubuntu [supported WiFi cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), however this doesn't necessarily mean it *wont* work.

I'm having my own problems with my 3Com USB card, so good luck!! :)


I've done a little digging and the card  is showing to be supported.
 802.11g 	 WG111 v. 2 	 man: 0846 dev: 6a00 	 USB 	 RealTek 	 rtl8180 	 green  	 "driver: [ftp://152.104.238.194/cn/wlan/linux26x-8187(110).zip](ftp://152.104.238.194/cn/wlan/linux26x-8187(110).zip) ; from realtek

Found the page i needed from the link you provided, thanks. Will give it a blast tomorrow.

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29")

---

### Post by tommyperkins on 2006-12-31
ok, 

so i downloaded and installed
ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb and ndiswrapper-common_1.18-1ubuntu2_all.deb

i then followed the instructions on
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29")
but when i run modprobe ndiswrapper i get the following error message:

tommy@Machine01:~$ sudo -s
root@Machine01:~# ndiswrapper -i /media/cdrom/netwg111.inf
netwg111 is already installed. Use -e to remove it
root@Machine01:~# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
root@Machine01:~# 

could someone please tell me where i'm going wrong?

thanks.

---

### Post by [L2G] Slapshot on 2006-12-31
Hi tommy

Ndiswrapper is actually saying that the driver is already in use. If the driver isn't what you have installed then use ndiswrapper -e to remove it then reinstall with your version of the driver.

Hope this helps
Jacko

---

### Post by tommyperkins on 2006-12-31
> **'[L2G] Slapshot said:**
> Hi tommy

Ndiswrapper is actually saying that the driver is already in use. If the driver isn't what you have installed then use ndiswrapper -e to remove it then reinstall with your version of the driver.

Hope this helps
Jacko

so i entered
ndiswrapper -e /media/cdrom/netwg111.inf
and it said 
Driver /media/cdrom/netwg111.inf is not installed. Use -l to list installed drivers. 
ao i'm assuming it uninstalled that one. 

Which driver do i need to use? the ones on the netgear cd are all in the Windows folder!

---

### Post by [L2G] Slapshot on 2006-12-31
Hi mate
Sorry but I'm a noob myself so bear with me. When you installed netwg111.inf from that location /media/cdrom/ linux puts it somewhere to use, so when you uninstall it just use 
ndiswrapper -e netwg111.inf 
or maybe just netwg111 I cant remember if you need the .inf, then if you use ndiswrapper -l it will show any drivers it's using. If it lists none then its removed ok. The drivers I used were my windows xp drivers and I copied all the files in the folder on the cdrom to my home directory to a folder I made to make it easier to find.

Keep at it you'll get there
Jacko

---

### Post by tommyperkins on 2006-12-31
so here's the process i should go thorugh:

1. Download and install - 
ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb and ndiswrapper-common_1.18-1ubuntu2_all.deb

2.  Place the XP drivers in my home directory (e.g. tommy/netgear drivers)

3. Install these with ndiswrapper - 
ndiswrapper -i /tommy/netgear drivers/winxp/net111v2.inf

:confused:

---

### Post by Pxncture on 2006-12-31
Hey,
 I'm having a similar, if not the same problem. I'm working on connecting a Linksys WUSB11 v2.6. I have gathered the drivers from the CD but when I try to install it returns that it cannot insert the INF file into line 140--I think, around that basis anyways. When I attempt to uninstall it, nothing is returned but when I list installed drivers it remains there as an invalid driver! 2.6 is not on the ndiswrapper supported list, which may be the main problem here. Then again, it may not have even been tested in the past. In addition this does not supply any modified drivers that I can download, unless I've missed something on the list. I'm sorry if this should be placed in a new thread, but a little help is needed.

Edit : Answer to one of my problems, Wasn't uninstalling as root but when i try to install it says couldnt copy NETUSB.inf at /usr/sbin/ndiswrapper line 144

---

### Post by tommyperkins on 2006-12-31
I think i was getting that 'cannot insert at line...' error message as well. I think once i get my network connection sorted then i should grasp Linux/Ubuntu a bit more, but i seem to be going round in circles trying to do this. I'm not sure if it's just me but i never thought setting up a wirless connection could be so difficult! :confused:

---

### Post by linuxonbute on 2006-12-31
I am having problems with wifi on ubuntu but I have installed ndiswrapper on Mandriva so I hope these pointers will help. :neutral: 
to view installed drivers do
ndiswrapper -l   ( that lower case L not number one )
mine reports :

installed drivers:
bcmwl5a         driver installed, hardware (14E4:4324) present 

to remove a driver do :
ndiswrapper -e driver name ( as reported in above command - no path or anything else just exactly as the command shows it. )

when you install a windows driver using ndiswrapper get the .inf and .sys file from the windows driver disc.
you could either mount the disc then cd to the WinXp directory on it and run ndiswrapper from there.
in my example the .inf file would be bcmw5a.inf so you would type :
ndiswrapper -i bcmwl5.inf
or you could copy the files to some place on your system and cd to that directory to run ndiswrapper.

hth
Norm

---

### Post by Pxncture on 2006-12-31
Thanks for your input but I think we've already established that by following the INSTALL guide within ndiswrapper. I am wondering whether ndisgtk has anything to do with it? The problem with this is that it compiles fine, however I am running A KDE based Kubuntu. Meaning I cant run it as I dont have Gnome installed. Furthermore, when I run lsusb nothing is returned which brings forth another issue that maybe my adapter isn't even being detected. ](*,)  ](*,)  Can someone give us a hand here?

---

### Post by bikeboy on 2006-12-31
> **tommyperkins said:**
> so here's the process i should go thorugh:

1. Download and install - 
ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb and ndiswrapper-common_1.18-1ubuntu2_all.deb

2.  Place the XP drivers in my home directory (e.g. tommy/netgear drivers)

3. Install these with ndiswrapper - 
ndiswrapper -i /tommy/netgear drivers/winxp/net111v2.inf


Firstly, it seems from your posts that to install software you're downloading .debs manually and installing them. Or is that just my wrong assumption? The easiest way to make sure ndiswrapper is installed properly is via System > Admin > Synaptic.

Also, although ndisgtk isn't required for ndis to function, it's perfectly ok to install gtk based apps on a kde desktop system, again Synaptic will handle the dependencies. It will simply install the minimum packages required for a gnome/gtk app to run, and after that most gnome apps will install without the need for many additional dependencies. I run kde programs like k3b on my gnome desktop.

It's a while since I've used ndiswrapper but from memory the above poster's steps are all I needed. At some stage during the install it asked whether I wanted automatically add the appropriate entry to /etc/modules and I said yes, worked fine ever since. But I'm using a cheap Ralink Rt2500 based card now as it has open source drivers.

---

### Post by linuxonbute on 2006-12-31
> **Pxncture said:**
> Thanks for your input but I think we've already established that by following the INSTALL guide within ndiswrapper. I am wondering whether ndisgtk has anything to do with it? The problem with this is that it compiles fine, however I am running A KDE based Kubuntu. Meaning I cant run it as I dont have Gnome installed. Furthermore, when I run lsusb nothing is returned which brings forth another issue that maybe my adapter isn't even being detected. ](*,)  ](*,)  Can someone give us a hand here?

Yes,  but as I saw this :
> 
so i entered
ndiswrapper -e /media/cdrom/netwg111.inf
and it said
Driver /media/cdrom/netwg111.inf is not installed. Use -l to list installed drivers.
ao i'm assuming it uninstalled that one.

Which driver do i need to use? the ones on the netgear cd are all in the Windows folder!

and it seemed that he was confused about the syntax and I know I need it spelling out very simply:( 
Norm

---

### Post by Pxncture on 2006-12-31
After Every attempted install It returns

NETUSB.inf installing...
Couldn't copy netusb.inf into line 144 of [some particular directory here]

Also, It doesn't seem that Synaptic was preinstalled, I'll have to look into it.
What task does ndisgtk perform anyways? Just wondering. 

:Last thing, whenever I run lsusb it doesn't return anything. Meaning the USB adapter is undetected?

Two completely unrelated problems I would suppose. 

Any help is appreciated, 
Pxncture

---

### Post by bikeboy on 2006-12-31
Yes after running my own lsusb and checking the output I'm starting to believe that's where the problem actually lies. Do you have any other USB devices to test it with? A mouse would suffice, as long as it's plugged into the same controller (not necessarily same port that the wireless has been in.

For example, my laptop has just 2 USB ports, obviously on the controller built into the motherboard and I get this output indicating one mouse and one empty port.

```
matt@ubuntu:~$ lsusb
Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000
```

---

### Post by tommyperkins on 2007-01-03
Could someone please help me because i'm still having problems?! 

This is from the terminal:

tommy@machinebuild01:~$ sudo -s
Password:
root@machinebuild01:~# ndiswrapper -i /media/cdrom/driver/winxp/net111v2.inf
net111v2 is already installed. Use -e to remove it
root@machinebuild01:~# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
root@machinebuild01:~# 

Could someone tell me what i'm doing wrong? I seem to be following instructions exactly but it still doesn't want to work!

---

### Post by [L2G] Slapshot on 2007-01-03
Hi

The machine is saying its installed and if you want to remove it type ndiswrapper -e net111v2 to remove it then type the command to install yours from your location. When you have installed it put the usb adapter in wait 15 seconds and then type ndiswrapper -l ( lowercase L ) and it should list something like mine does. if it does carry on with the howto you showed the link to before. Here is my code

jacko@jacko-desktop:~$ ndiswrapper -l
Installed drivers:
rt73            driver installed, hardware present
jacko@jacko-desktop:~$

If you get that then do the rest of the howto but don't forget the depmod -a bit.

Jacko

---

### Post by tommyperkins on 2007-01-03
This is what i'm getting:

ndiswrapper -l
Installed drivers:
net111v2     invalid driver!

---

### Post by [L2G] Slapshot on 2007-01-04
Hi mate first ( well take it slowly ) you need to get rid of the invalid driver by using       

ndiswrapper -e net111v2

then againlist the drivers ndiswrapper is using by typing

ndiswrapper -l

do this action till it says no drivers present or just does nothing when you do the command. If it cant get rid of the driver try taking out the usb device and the re try the command. You cant go any further until you get no drivers listed with ndiswrapper -l.

When you get no drivers listed, create a folder in your home directory called netdriver   or something. Then copy EVERYTHING in the driver folder on the cd to your new netdriver folder on your home directory ( ndiswrapper needs more than just the .inf file ). Then try the commands again from that directory in your home folder netdriver or whatever you called it. This will get around any file permission errors you may get by trying to acces mounted cds etc ( the commands being ndiswrapper -i net111v2 and so on ) 

Hope this helps but bear with me I'm new to this also. I can't respond as quick as I'd like as I have to work long hours and then have to check a little about how to answer any questions you may have, so check back but it takes a little while.

Jacko

---

