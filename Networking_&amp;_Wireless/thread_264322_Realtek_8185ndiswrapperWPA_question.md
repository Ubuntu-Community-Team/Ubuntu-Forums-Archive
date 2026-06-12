---
title: "Realtek 8185/ndiswrapper/WPA question"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by ArgentSilver on 2006-09-24
My wireless card has the Realtek 8185 chipset which is now natively supported by Dapper. I can get it working OK, but only without WPA security. So my goal is to get WPA working. It looks to me like the 8185 driver in Dapper doesn't support WPA (correct me if that's wrong). So could I use ndiswrapper and wpa_supplicant? If so does that mean I should disable the wlan0 from System->Administration->Networking to remove the native 8185 driver or what? And then load up the Win driver into ndiswrapper and move on to wpa_supplicant?

I've tried to read up in the forums and elsewhere how to do this, but it appears that in the WPA area the documentation is contradictory and bleeding edge. Older stuff says one thing; newer stuff says something else. Some people are saying to just install network-manager-gnome; tried it-didn't work; seems to depend on which driver you're using. Does anyone have some definitive knowledge in this area? It's driving me crazy!

---

### Post by wieman01 on 2006-09-25
No, if you're using your native Windows driver then the tool that let's you deploy it is "ndiswrapper". "ndiswrapper" is just a container for Windows drivers, that's all. 

Yes, you need to install wpa_supplicant. If you want to try WPA, there are two useful links for you:

**_WPA1:_** [http://www.ubuntuforums.org/showthread.php?t=225290&page=11]("http://www.ubuntuforums.org/showthread.php?t=225290&page=11")

**_WPA2:_** [http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

Bear in mind: Your device's name is "wlan0". You'll need that later on. Let us know if you need more help.

---

### Post by jon_herr on 2007-05-20
I'm running feisty...

It's a celebration!  Using the latest ndiswrapper and network manager WPA is working!

Version 1.44 of ndiswrapper is required...
[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

Follow anyone's instructions that you can find for setting up ndiswrapper with rtl8185 to use a WinXP driver from realtek.

If you don't have them already you'll need the linux kernel headers in order for make to work.
For me this was but beware of your kernel version: 
sudo apt-get install linux-headers-2.6.20-15-generic

Basically...  download the tarball of ndiswrapper - extract it, change to the folder called 'driver' then type:
sudo make
sudo make install

now reboot
when you are up again do this:
sudo ndiswrapper -i net8185.inf
sudo ndiswrapper -m

and reboot.

Next time you use network manager to connect to your wireless network it will work.  (well did for me).

Thanks to the ubuntu, and ndiswrapper teams for getting this working!  Gotta love ubuntu!

Best of luck,
Jon

---

