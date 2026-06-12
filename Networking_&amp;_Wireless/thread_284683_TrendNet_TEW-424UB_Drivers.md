---
title: "TrendNet TEW-424UB Drivers"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by stevenma188 on 2006-10-26
OK I have a TrendNet TEW-424UB wireless USB adapter. I found linux drivers here: [http://www.qbik.ch/usb/devices/showdev.php?id=3285](http://www.qbik.ch/usb/devices/showdev.php?id=3285)

The instructions say to copy the files to /lib/firmware/zd1211 but when i try to do that it says i do not have premission to do so.
First of all, will this driver work with ubuntu
Second, is my method of installation correct
Third, How do i do it

Thanks for all your help

This is my first linux experience, so thanks for your patience

---

### Post by joereid on 2006-12-11
i've gotten this driver to work in ubuntu 6.10 edgy eft.
i am sorry that i do not remember every exact step to do it, but hopefully this will get ya'll headed in the right direction.
i can confirm that it will work in ubuntu. i have done it. it worked.
the zd1211 or other drivers that i see people talking about isn't made for the particular chipset in the tew-424ub usb wireless thingy.
the zd1211 or whatever driver is made for the older model. the A series. we have the b series/model. mine is blue with a flippy cover for the usb thing.
here is how i did it.
i went to ndiswrapper home page, [http://ndiswrapper.sf.net](http://ndiswrapper.sf.net) and got their latest release. this might not be entirely neccessary.
then i got all the build tools for ubuntu from synaptic. gcc g++ etc.
look for a howto if you need help with that part. i always refer to howtos.
next, i built and installed ndiswrapper.
now you may not need the latest version. it may be possible to skip those steps, and just install the ndiswrapper that is in synaptic.
after installing ndiswrapper, make sure you have the wireless tools, iwconfig and iwpriv and iwlist. its all in a wireless tools package or something in synaptic.
next, get your windows driver or the new driver for it off the [www.sis.com](www.sis.com) website. i used both, so either will work.
then give the command, ndiswrapper -i /path/to/driver.inf which is the windows driver. i think it is named 163u.inf or something.
that installed the driver.
next, run the command, depmod -a (this should only have to be run the first time, or only once.)
next run the command, modprobe ndiswrapper
you should have wlan0 now. its like eth0.
iwconfig will allow you to set essid and stuff.
and dhclient is already running on it.
your hardware is working now, all you have to do is configure it.
so to sum up, install ndiswrapper, get windows driver, run ndiswrapper -i driver.inf, the first time you use ndiswrapper after installing it you have to run depmod -a, then run modprobe ndiswrapper.
next, commands like iwconfig wlan0 essid s0me_id, iwlist scan, and man iwpriv should be helpful for setting it up. if i remember correctly, i just had to set essid, and used ifconfig to set the ip (no base station or dhcp here, i used ad-hoc mode and talked between two of them)
sorry this post is so sloppy, and fast.
i just wanted to give yall the info i know about this quickly and wanted to share. i hope it helps you. and if you get it working, please post instructions here and anywhere else you can find. like better directions than these. also, i expect that i would have had a lot easier time setting it up the first time if i had had dhcp and a base station.
you won't need the ifconfig command if you have dhcp.
after i got it set up here, i broke it somehow and then finals came in college and i'm waiting to finish before delving into it.
you can check back in a week or two from this post and i'll probably put up a much better howto. again, sorry its not exactly step by step.
this should get you headed into the right direction, and let you know its possible. i surfed from the couch for the first time in my life. it worked, for sure. hope this helps.

---

### Post by FrodoB on 2006-12-11
If you really have the zd1211 version and not the SiS version you can test the driver that is build into Edgy Eft. To copy the firmware you need to use sudo with  your command to have permissions:

sudo cp filename /lib/firmware/zd1211

If the built in driver does not work then see:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29")

When you make the driver use "sudo make both" and you will install new drivers for the zd1211 and zd1211b and one of them should work for you unless you have the SiS chipset that joereid has, then you will need to go the ndiswrapper route.

To find out which chipset you have run lsusb at a terminal prompt and get the US ID to find out which one you have.

If your ID is 0457:0163 you have the SiS chipset then ndiswrapper is your only course of action, if it is  0ace:1211 it is  Zydas a zd1211 or zd1211b proceed with the Belkin F5D7050 ver 4000 instruction in the link above.

---

### Post by erizo on 2006-12-24
WOW!
now I finally get connected with this TEW242UB.....
well here is the solution:
follow all the ndiswrapper instructions related to this issue.
but.....
USE WINDOWS 2000 DRIVERS!!!!!!

I have been trying with the WINBLOWS XP ones for one week....until today I decided to try with the 2000 drivers.... little detail...
VOILA!!
any comment...let me know!!

---

### Post by joereid on 2007-01-09
todays date is jan. 8 2007.
i figured out the problem i was having with this card, the tew424ub from trendnet.
ndiswrapper versions larger than 1.23 don't work with them.
i downloaded ndiswraper-1.23.tar.gz and compiled it, installed it, ran depmod -a, and then ran the commands:
sudo ndiswrapper -i /path/to/sis163u.inf
sudo modprobe ndiswrapper
sudo iwconfig wlan0 essid MyEssid
sudo dhclient wlan0
then my wireless worked.
as of today, the latest ndiswrapper is 1.34
it doesn't work with the tew424ub. i submitted a bug report and chatted with a developer on #ndiswrapper
he is aware of the problem and it will probably be fixed soon.
in the future, it would be worth checking if the latest ndiswrapper works, and if not, the grap ndiswrapper-1.23 and compile and install it. see install file in .tar.gz for install instructions.
do a depmod -a after installing. also remove the driver listed by ndiswrapper -l
probably sudo ndiswrapper -r sis163u or sudo ndiswrapper -e sis163u
make sure the module is unloaded, sudo rmmod ndiswrapper
then use it like normal. (i listed the steps above)
this ought to make some people happy.
after a little time passes from now, it will be worth checking if the problem has been fixed in latest ndiswrapper.
i'm using the tew424ub right now. i'm wireless ! 
i am using xp drivers.

---

### Post by joereid on 2007-01-29
it works now.  it has been fixed. i tested it too.  it works. :)
the date is 1-28-2007 
currently, its in the svn revision 2186.
the current stable version is 1.35  but it doesn't work in this version.
it will in the next version, 1.36 or later
to get the svn version, run this command.
svn co [https://svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper](https://svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper) 
now you will have a folder called ndiswrapper.  
to install it, run these commands.  doesn't matter if the first two give errors or not.

sudo rmmod ndiswrapper
sudo ndiswrapper -e sis163u
cd ndiswrapper
sudo make uninstall     # might try running that twice
make
sudo make install

you have it installed now.  next plug in your trendnet thingy if it isn't already, and set it up. for example:
sudo ndiswrapper -i /path/to/sis163u.inf
sudo modprobe ndiswrapper

hardware is up and working now.
iwlist wlan0 scan  should give you results. get your essid and type:
sudo iwconfig wlan0 essid YourEssid
sudo dhclient3 wlan0  #to do dhcp   else, use ifconfig wlan0.
you should be set.  

with svn you can use svn up -r XXXX  to go back or forward through revision numbers. shouldn't need that.
2186 is the latest and the first to work with this card in ubuntu.
after ndiswrapper 1.36 comes out, it and every one after should work.  :)
i'll follow [https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html)  and make a package for it, but i don't know if it will make it to any repositories.   
enjoy !  and i'm using the card now. it works.
i'm using the [http://downloads.trendnet.com/TEW-424UB_v2%5CDriver_Utility%5CUtility_Driver_TEW-424UB(v2.x).zip](http://downloads.trendnet.com/TEW-424UB_v2%5CDriver_Utility%5CUtility_Driver_TEW-424UB(v2.x).zip)
driver for windows.  found it of the [www.trendnet.com](www.trendnet.com) site.  easy to find.

---

### Post by darkwalt on 2008-05-03
Ok, just installed hardy, but this makes no sense to me.  Can someone explain it to me in a bit more layman terms?

---

### Post by joereid on 2008-05-03
do you have net access on the ubuntu box already, so you can install from the net while running ubuntu ?
do you have the windows drivers too ?
is your usb wireless card the TEW-424-ub ?

---

### Post by darkwalt on 2008-05-04
do you have net access on the ubuntu box already, so you can install from the net while running ubuntu ?
do you have the windows drivers too ?
is your usb wireless card the TEW-424-ub ?

I don't currently have the box connected to the network, but I can run a long cable if necessary.  I do have the windows drivers saved on my thumb drive, and the usb dongle is the correct model number.

---

### Post by joereid on 2008-05-04
that's great.  it will be simpler to have net on it.
install ndiswraper: sudo apt-get install ndiswrapper-common
then run the command: sudo depmod -a
then load the ndiswrapper kernel module: sudo modprobe ndiswrapper
now your ubuntu is set up for it.  next set up ndiswrapper with the windows driver.
sudo ndiswrapper -i /media/thumb_drive/driver.inf
that should do it.  you should be ready to go, and have wlan0 now.
in gnome, you should be able to set up the networking in the corner by the clock/time.  i use: sudo wifi-radar because i don't use gnome, but fluxbox.
either of those should offer the essid and run dhclient3 on it, after which you are ready to surf.  good luck, and let me know if you have any problems.  i'll be happy to help.  may 4th 2008

---

### Post by darkwalt on 2008-05-04
> **joereid said:**
> that's great.  it will be simpler to have net on it.
install ndiswraper: sudo apt-get install ndiswrapper-common

After running that command, I get this error,
"Couldn't find package ndiswrapper-common"  

What does that mean?

---

### Post by joereid on 2008-05-04
that is very odd.  it is a package that should be in the ubuntu repositories.  maybe you have to enable the universe repos, but i don't know.  its odd that you don't have it and that i do....   you can typing: sudo apt-get install ndis<and hit tab twice and see the choices it gives you>  
one of those choices should be ndiswrapper.  you might want to use synaptic and look for ndiswrapper.  also check your repositories, and see if you can enable more repositories and disable the cd if it is listed in there as a source.  (cd is good for no net, or for installing only) 
my suggestion to you is try to install ndiswrapper.  either from my earlier posts or from the following posts i did a quick search for.  
you may try sudo apt-get update  and try sudo apt-get install ndiswrapper-common 
i have hardy and had gutsy and both installed ndiswrapper this way.
anyways, here are my quick searches: 
[http://ubuntuforums.org/showthread.php?t=768161&highlight=ndiswrapper+hardy+heron](http://ubuntuforums.org/showthread.php?t=768161&highlight=ndiswrapper+hardy+heron)
[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)
those are not your card, but do have instructions for installing ndiswrapper.
also [http://ndiswrapper.sf.net](http://ndiswrapper.sf.net) has the newest ndiswrapper source to build and install.
its not as hard as it seems.  you seem like a newbie, so i'll let you in on a secret, really, the command line is the easiest way for newbies to do stuff, especially with step by step instructions. (for real)  it doesn't take very long for someone to get really good at cutting and pasting commands from a howto into a terminal, so don't let complicated commands that don't seem to make sense scare you.
if you want, follow my instructions from my earlier posts using the newest release from [http://ndiswrapper.sf.net](http://ndiswrapper.sf.net) and that should get you ndiswrapper installed.
unless you already have a ndiswrapper command (type it and check) installed.
if so, go right on to the modprobe and then the ndiswrapper -i /path/to/driver.inf
and ndiswrapper -l   (thats an L)  will list hardware and loaded drivers to double check.  after that you should be ready to go. i'll probably be gone tomorrow, so i'll be sure to check here more frequently tonight if you have any more questions.
so you're trying to install ndiswrapper.  should be a good/easy howto for installing ndiswrapper somewhere.  then all you have left is: sudo depmod -a ; sudo ndiswrapper -i /wherever/your/driver.inf  ; sudo ndiswrapper -l 
and then your set.  it was hard for me at first to, having never used wireless before ever, even knowing linux very well.   i'll help more if i can, let me know.

---

### Post by darkwalt on 2008-05-04
do you have an an aim name?  I seem to be retarded and not able to get this to work.

---

### Post by joereid on 2008-05-04
yes i do.  gimme your yahoo or aim name and i'll im you.  
it sucks that these wireless cards are the new winmodems.  
at least the ndiswrapper developer is doing something about it.
yeah, gimme aim or yahoo name and tell me which it is and i'll im you.

---

### Post by haran_hockey on 2008-05-10
EDIT: What do you do after you install ndiswrapper. (I've isntalled my driver but I don't know what to do)

---

### Post by jedi22 on 2008-07-04
I followed these steps exactly and it worked! After hours and hours of head aches finally! The only thing about the steps that didn't work were the drivers used. I downloaded drivers from 

[http://trendnet.com/downloads/list_subcategory.asp?TYPE_ID=24&SUBTYPE_ID=700](http://trendnet.com/downloads/list_subcategory.asp?TYPE_ID=24&SUBTYPE_ID=700)

and it work right after using those XP drivers!  Thanx so much for this tutorial!

---

### Post by halitech on 2008-07-12
An easier way to do this is usinf synaptic, install ndiswrapper-common, ndiswrapper-util and ndisgtk. Then use Windows wireless driver (should be found under System - Administration - Windows wireless drivers). you can also configure the network from there after the driver is installed. I'm currently surfing wirelessly on Xubuntu 7.10 on an old Compaq Armada with no cd rom :)

---

