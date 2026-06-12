---
title: "installing windows drivers"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by muggins on 2006-09-06
How does one go about installing a windows driver into ubuntu?This is for a wireless usb adapter "trendnet TEW424UB". I have gone to SIS homepage and downloaded the recommended driver onto a blank CD. But when I try to install it in ubuntu "dapper drake" I get the following couldn't display "/media/cdromO/R105-Logo/Setup.exe".From what I have read in the guide a need a driver installed before I use the ndiswrapper application. Any help would be appreciated,thanks

---

### Post by meng on 2006-09-06
What you need is to find the .inf file that contains the Windows driver information. I have been fortunate enough not to require ndiswrapper, but there is a guide here that tells you what to do with the .inf file.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Taskr36 on 2006-09-08
After scouring the web like mad I found what I think are the right drivers for my wireless usb adapter. The model isan ABS NW-200-USB and it is 802.11b/g. My device manager sees it but has no idea what it is and has no driver listed for it. I used the terminal to get the chipset number which is 07b8:6001. 

I searched high and low with that number and eventually came to the zd1211 wireless driver module. I then installed the kernel package, module assistant, and then double clicked and seemingly installed the zd1211 driver. I rebooted the computer and nothing seems to have changed. Did I miss a step somewhere? Does anyone have any advice on how to get this thing to work?

Just to be clear, the wireless adapter does not show up in the connections window and I did have it plugged in when I originally installed Ubuntu.

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
i'll check this forum again soon, so if you have problems, post about it and i will try to help you out.

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

