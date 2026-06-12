---
title: "Trendnet - TEW-424UB"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by msuemnig on 2006-12-03
New to linux here, apologies up front.

I have a Trendnet tew-424UB and it doesn't seem to be plug and play on Ubuntu 6.10.  I downloaded the newest zd1211 (v1.2 from sourceforge [http://sourceforge.net/projects/zd1211/](http://sourceforge.net/projects/zd1211/)) driver but I have no idea how to actually install it.  The readme doesn't allow for supreme ignorance.

Thanx for any help in advance!!

---

### Post by FrodoB on 2006-12-03
If you are sure that is it is a zd1211 device then follow this instruction:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

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
To find out which chipset you have run lsusb at a terminal prompt and get the US ID to find out which one you have.

If your ID is 0457:0163 you have the SiS chipset then ndiswrapper is your only course of action, if it is 0ace:1211 it is  Zydas a zd1211 or zd1211b proceed with the Belkin F5D7050 ver 4000 instruction:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

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
later

---

### Post by lddm00 on 2007-06-16
Hi...I`m new in ubuntu, I just installed Festy Fawn and I can´t get to work my Trendnet TEW-424UB. I recently was reading this topic but when I install the driver from the cd or the last driver from the SIS web page and I type ndiswrapper -l to check if my driver is correctly instaled and I get: sis163u.inf invalid driver.:(:( I would aprecciate any help. Sorry about my bad english but me native tongue is spanish.
Greets for all.
Lddm

---

### Post by brianyang on 2007-06-18
I installed the latest version of ndiswrapper 1.47. And I managed to install the required drive sis163u. But the network adaptor cannot be found. When I type
ndiswrapper -l
Only the installed driver is listed.
What might be the problem? Thanks!

---

### Post by riles01 on 2007-06-25
> **lddm00 said:**
> Hi...I`m new in ubuntu, I just installed Festy Fawn and I can´t get to work my Trendnet TEW-424UB. I recently was reading this topic but when I install the driver from the cd or the last driver from the SIS web page and I type ndiswrapper -l to check if my driver is correctly instaled and I get: sis163u.inf invalid driver.:(:( I would aprecciate any help. Sorry about my bad english but me native tongue is spanish.
Greets for all.
Lddm

I had the same problem. Which driver were you using? I tried both the XP and 2000 versions, but didn't try the 98 or ME versions.

---

### Post by Victor.Barna on 2007-07-27
run lsusb and check the chipset of your card, for example i had a realtek chipset and needed the net8187b drivers

---

### Post by oxygenfarm on 2007-09-05
I have the 'new' TEW-424ub (v3) and am completely confused by the technical aspects of installing a driver.

---

### Post by oxygenfarm on 2007-11-13
I just read the following: "October 10, 2007. 
Linux 2.6.23 was released today. On the wireless front, a variety of fixes and improvements were contributed all over the place. The biggest news items are the inclusion of the rtl8187 driver, which supports USB devices based on the RTL8187 chipset"
Does this mean that my TEW424UB will now work. (version 7.10)

---

### Post by dawonn on 2007-12-18
As of Dec 2007, unfortantly no. I just plugged my TEW-424UB V3 in and got nothing from 7.10.

I figured out my issue and made a [Wiki page]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-424UB_3.0R_(ndiswrapper)") for the newer 3.0R. Maybe it will be helpfull.

---

### Post by astir13 on 2008-07-12
Today is 2008-07-12 and I am on a ubuntu 8.04LTS.

The 'lsusb -v' for my version of the USB Wlan card shows that it is a Realtek card => use the net8187b.inf.

I installed ndiswrapper and ndisgtk tool (synaptic package manager, have all repositories enabled)
Then I called 'sudo ndiskgtk' from the commandline.
'Add driver' installes the Windows 98 Version of the driver net8187b.inf from the installation CDROM that comes with the TEW-424UB. 

Info: if I try with the WINXP driver, it doesn't work.

Now I get shown the available networks and can log onto network ;-)

---

### Post by astir13 on 2008-07-12
Using ubuntu 8.04
lsusb -v shows that I have a Realtek chipset for my TEW-424UB
=> I use the 8187b driver from the original installation CD

- install ndiswrapper and ndisgtk with Synaptic Packetmanager
- using ndiskgtk, install the windows 98 version of the 8187b driver (file name is n8187b.inf in my case)
- then the device is shown with ifconfig -a as wlan0 and can be used to scan for wlan, etc.

---

