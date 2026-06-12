---
title: "can not connect to router"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by muggins on 2006-09-18
I have been tring for ages to get wireless connection to work. Using the iwconfig command I detect frequency, signal strength,link quality 100/100, bit rate 54 mbps however I get nothing for access point. I tried disabling WEP still nothing. Any suggestions? Router is TRENDnet 432BRP and wireless adapter is TEW424UB.

---

### Post by spd106 on 2006-09-18
I suggest that you ignore any output that is at full. Some drivers don't implement those features, particularly if you're using ndiswrapper.

Could you try posting some of the output you get, such as from **sudo iwlist wlan0 scan** and **iwconfig**. Also it would be useful to include details about your cards driver.

Have you tried [network manager]("https://wiki.ubuntu.com/WifiDocs/NetworkManager") or wifi-radar?

---

### Post by muggins on 2006-09-18
Thanks for reply spd106.
iwlist wlan0 scan

Address:00:40:F4:E4:2E:C2
ESSIS:TRENDnet
Protocol:IEEE 802.11g
Mode:managed
Frequency:2.412GHz
Quality:0/100
Signal Level:-52dBm
Noise Level:-256dBm
Encryption Key:on
Bit Rate:54mb/s
Extra:bcn_int=100
Extra:atim=0

iwconfig
IEEE 802.11FH
ESSID:off/any
Mode:managed
Frequency:2.412
Access Point:not associated
Bit Rate:54mb/s
Tx-Power:16dBm
Link Quality:100/100

wireless usb adapter is TEW424UB made by trendnet
driver is SIS 163
used NDISGTK to install.
Have not tried network manager or wifi-radar.
Thanks for your help.

---

### Post by muggins on 2006-09-19
Have installed wifi radar now and it sees my router. However I can not find any instructions/help on configuring wifi options for it. 
What to I enter for the following mode,channel-should I use auto or enter the channel number,also what do you put in for key, and for security.

---

### Post by spd106 on 2006-09-19
It should be enough to enter the essid and the encryption key. All of the other settings should be automatically detected when your card associates with the AP (router). If it doesn't like that then go with *managed*, *1*, *your WEP key* and *restricted* repectively.

---

### Post by muggins on 2006-09-19
Thanks again for reply spd106. I have tried both of your suggestions and when I select connect, it says connected to none ip (127.0.0.1). I tried to install network manager also but said application might not support system architecture.

---

### Post by joereid on 2007-01-09
i was having same problem as you.
here is a fix.
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
in the future, it would be worth checking if the latest ndiswrapper works, and if not, then grab ndiswrapper-1.23 and compile and install it. see install file in .tar.gz for install instructions.
do a depmod -a after installing. also remove the driver listed by ndiswrapper -l
probably sudo ndiswrapper -r sis163u or sudo ndiswrapper -e sis163u
make sure the module is unloaded, sudo rmmod ndiswrapper
then use it like normal. (i listed the steps above)
this ought to make some people happy.
after a little time passes from now, it will be worth checking if the problem has been fixed in latest ndiswrapper.
i'm using the tew424ub right now. i'm wireless !

---

### Post by joereid on 2007-01-09
sudo iwlist wlan0 scan 
will scan the network and if it finds anything out there, it will show the essid
hope that helps too

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

