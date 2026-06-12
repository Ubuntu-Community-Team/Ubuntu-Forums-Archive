---
title: "Trouble with Wif/Fi Adapter Alfa AWUS036H chipset Rtl8187"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by arce on 2009-05-11
After searching this forum for information regarding the Rtl8187 I have been directed to the same links.

[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

[http://aircrack-ng.org/doku.php?id=r8187](http://aircrack-ng.org/doku.php?id=r8187)

[http://aircrack-ng.org/doku.php?id=install_drivers&DokuWiki=016c553e7fd0cd09b1fa7808527dee87#mac80211_versus_ieee80211_stacks](http://aircrack-ng.org/doku.php?id=install_drivers&DokuWiki=016c553e7fd0cd09b1fa7808527dee87#mac80211_versus_ieee80211_stacks)

[http://aircrack-ng.org/doku.php?id=rtl8187](http://aircrack-ng.org/doku.php?id=rtl8187)

After being confused with these links and my skills from 1-10 with terminal and Ubuntu being a 2 I have no idea where to go from here. 

My friend tried to compile the driver 2 times and it didn't work. I really don't want to bother him any more with my issue. 

I see Ubuntu has a paid tech service that I'm not sure would even cover my issue. I see other Distros have paid support but found only 2 for Unbuntu.

Are there any members that do freelance work that can provide help for me? I'm not looking for a free service. I would be paying.

---

### Post by mprince on 2009-05-12
I don't think you need to do any driver compiling if you are using a kernel version 2.6.27 (or greater).

You can check that out by opening a terminal and typing this:

```
uname -r
```

---

### Post by arce on 2009-05-12
I downloaded the driver from the makers website. How would you install it unless it was compiled? Also after reading those sites it was said I must blacklist my old driver? 

Basically the issue with me is the steps that need to be done and in what order they need to be done in. Add to that my lack of command,terminal knowledge makes me even hate windows more:)


I know the driver that Ubuntu supplies is not working correctly because I can connect to the internet but then it disconnects. 

Also Signal strength is beyond weak. In Vista I have full bars on signal strength on my router in the same room and 4 additional AP's are present in my network monitor.

---

### Post by Didius Falco on 2009-05-12
Hi,

What version of Ubuntu are you using? Did you run the command mprince suggested to get your kernel version? If so, what did it say?

Plenty of folks here will try and help you for free, but it's a lot harder without the relevant information.

Regards,

Didius

---

### Post by caravel on 2009-05-12
You might have better luck with ndiswrapper.  I've been having the same problems with the rtl8185 and though it now works with ndiswrapper it's not perfect and every now and then it disconnects and then takes several attempts to reconnect.

-Edit: I have no experience with the aircrack driver because there isn't one for the rtl8185 AFAIK.  But the first driver you linked to at sourceforge is the driver you're currently using if you're running a newish version of Ubuntu (such as 8.xx/9.xx).  If not then I suggest you save yourself the headache and reinstall (or upgrade at your own risk) to a newer version of Ubuntu.

Also the other two posters are correct.  You should have followed mprince's advice and posted back with the relevant info.  This is because you probably don't need a driver, as it's already installed.

---

### Post by arce on 2009-05-12
Sorry guys I was at work.. So I couldn't try it.

Ok heres the response

2.6.28-11

---

### Post by caravel on 2009-05-12
The rtl8187 driver is in that kernel.  It's just a case of clicking the network manager applet in the panel and you should see the SSID of your wireless network.  Just click that and it will start to connect.  Enter the key and encryption type and you should be good to go.

-Edit: what is the output of these:

```
lsmod | grep rtl8187
dmesg | grep rtl8187
iwconfig
```

---

### Post by arce on 2009-05-12
ok first line

xtror@xtror-laptop:~$ lsmod | grep rtl8187
rtl8187                53376  0 
mac80211              217208  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               38032  2 rtl8187,mac80211

second line

xtror@xtror-laptop:~$ dmesg | grep rtl8187
[  275.599276] usbcore: registered new interface driver rtl8187
xtror@xtror-laptop:~$ 


3rd


xtror@xtror-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by caravel on 2009-05-13
The above that your wireless (wlan1) is installed and working.  You just need to click on the network connections icon at the top right of your desktop (near to the date, time and audio icons) and click on the SSID name ("linksys" in your case) of your wireless network.  You will then see a prompt for a network key and encryption type.  Enter the details and you should be in.

---

### Post by arce on 2009-05-13
But what about my connectivity issues? I can't seem to stay connected to any open AP's in my school. Also my Lack of APs in my area? I see much more in vista and signal strength in the same room of my laptop is only 4 bars verse Vista full bars.

---

### Post by caravel on 2009-05-13
> **arce said:**
> But what about my connectivity issues? I can't seem to stay connected to any open AP's in my school. Also my Lack of APs in my area? I see much more in vista and signal strength in the same room of my laptop is only 4 bars verse Vista full bars.
In your original post you did not ask about connectivity issues.  In fact you made no indication that you'd ever gotten the wireless adaptor to work at all and inquired about installing a driver.  The connection have now may be as good as it gets, the alternative is ndiswrapper or the aircrack drivers which I have no experience with.

What encryption are you using?

---

### Post by 3rdalbum on 2009-05-13
Unlike the other posters to this thread, I have an RTL8187-based card. The low signal strength is a known problem since Intrepid. If you don't mind switching your network to WEP instead of WPA, there is an excellent driver from the makers of Aircrack.

This page explains it well:

[http://zenzike.blogspot.com/2008/11/wireless-woes.html]("http://zenzike.blogspot.com/2008/11/wireless-woes.html")

You will need to recompile the driver each time you update your kernel, but this is just "sudo make clean", "sudo make", and "sudo make install".

You will get high signal strength, excellent range, great reliability, and pretty good speed. You lose WPA capability, but overall the Aircrack driver is a million times better than the stock Jaunty driver, and a hundred times better than the stock Hardy driver.

If you have any problems following this, please give me an instant message as I'm currently using one of those cards with this driver, and I can give much more accurate help than someone who doesn't.

---

### Post by caravel on 2009-05-13
> **3rdalbum said:**
> If you don't mind switching your network to WEP instead of WPA...
Sounds like a *great* trade off... good luck with that.

A lot of people have better results using ndiswrapper.  And at least with that you should be able to get at least WPA/TKIP working - which is a million times better than WEP.

---

### Post by arce on 2009-05-13
I might not have explained all of my issues correctly . I mentioned the connectivity issue in my 3rd post.

 Also everything you have said Caravel is helpful. I'm very knew to this OS and those commands you gave me I never knew before. You have also taken your time to help diagnose the problem.

Also vendor that sold me the card said it would be an issue to get it to work properly in Ubuntu. He suggested Backtrack 3 or Backtrack 4.. So I loaded Backtrack this week and my wireless worked perfect just like in Vista. 

At the moment this is my Second Wi/Fi adapter I bought that was highly recommended for Linux OS's. The first card I gave up on and put it on my wifes XP machine since the Signal strength was just aweful so I didn't want to invest time in it knowing that.

Yes, WEP for security is a very big issue and trade off. But this is my laptop that I connect on to Wifi at school so I'm not concerned. Also there is only one part of school that wifi works in and I know all of the people. 

 I actually am still amazed I installed Backtrack 4 on a USB drive and made it bootable. 



3rdalbum

You have a PM. I will be taking you up on your offer for help.

---

### Post by vze57gc8 on 2009-06-12
patch the driver using the aircrack version

wget [http://dl.aircrack-ng.org/drivers/rt...ux_26.1010.zip](http://dl.aircrack-ng.org/drivers/rt...ux_26.1010.zip)
unzip rtl8187_linux_26.1010.zip
cd rtl8187_linux_26.1010.0622.2006/

wget [http://patches.aircrack-ng.org/rtl8187_2.6.27.patch](http://patches.aircrack-ng.org/rtl8187_2.6.27.patch)

tar xzf drv.tar.gz
tar xzf stack.tar.gz

sudo gedit ./beta-8187/r8187.h
and find the line:

#include <asm/semaphore.h>

and change it to:

#include <linux/semaphore.h>

sudo patch -Np1 -i rtl8187_2.6.27.patch

remove old drivers
rm -rf /lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl818x/rtl8187.ko
rm -rf /lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl_ieee80211/ieee80211-rtl.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko

Then I put rtl8187 to the blacklist:

sudo gedit /etc/modprobe.d/blacklist and add &#65533;blacklist rtl8187&#65533; as a new line.
Then remove the present driver:

sudo ifconfig wlan0 down
sudo rmmod rtl8187

make
sudo make install

reboot & enjoy

---

