---
title: "Help installing wireless drivers for DWL-G122 rev. C1"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by Yaholo on 2006-12-12
Please help me.  I have a DWL-G122 wireless usb adapter.  I bought it because of it's supposed compatibility with Linux.  I followed the instructions found at [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview)
very carefully.

I actually got it to work at one point with Ubuntu 6.10 but had to switch computers. Now I just can't seem to get it to work.  I am getting all the right messages and NO errors, the lights on the adapter just don't come on and it won't connect to anything.  Here is my output:

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
rausb0    RT73 WLAN  ESSID:""  
          Mode:Auto  Frequency=1 MHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


dmesg:

[17179585.716000] rtusb init ====>
[17179585.716000] idVendor = 0x07d1, idProduct = 0x3c03 
[17179585.716000] usbcore: registered new driver rt73
[17179585.740000] rt73 driver version - 1.0.3.6
[17179585.760000] ts: Compaq touchscreen protocol output
[17179586.288000] rausb0 (WE) : Driver using old /proc/net/wireless support, please fix driver !

[17179621.220000] rausb0: no IPv6 routers present


/etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

# rt73 wireless network device using DHCP
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid MyWifi
wireless-key AVERYLONGKEYIDONTWANTTOSHOW
auto rausb0



My only clue is that iwconfig shows the essid at "" when I clearly have it defined.

---

### Post by FrodoB on 2006-12-12
Your iwconfig output almost makes it look like there is no good access point nearby:

          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm

When the Signal level is below the Noise level there can be no connection.

---

### Post by Yaholo on 2006-12-12
thanks for your help.  I have an access point 2-feet away from the usb card.  The real concern I have is that the lights on the adapter are not coming on.  The link and activity lights let me know if it is properly installed.  When I did it before the light came on immediatly.  Since the lights are not on now, I know there is a problem with the installation.

---

### Post by FrodoB on 2006-12-12
Yes, that message is telling us what you are observing with the lights. 

Is  the device plugged into an unpowered USB hub perhaps? Mine does not like being used in an unpowered hub I know.

Also I had a problem on another computer at one point because I was using the built-in USB system and it acted strangely, but when I plugged it into my USB add-on card in that system everything worked correctly.

---

### Post by FrodoB on 2006-12-12
Also, did you remember to blacklist the contending drivers:

You need to blacklist the existing rt73 module which is not working: 
 user@ubuntu:~$ sudo gedit /etc/modprobe.d/blacklist 
add the following three lines to the end of the file:  
 # Added when rt73 module was installed
blacklist rt73usb
blacklist rt2570
Save the file. The blacklisted module will not be loaded from now on.

Now just do a reboot and see if the device does not start responding.

---

### Post by FrodoB on 2006-12-12
Don' forget to reboot after blacklisting as the contending drivers are loaded now, and that is the easy way to remove them for sure.

Also make sure that you can see the device in lsusb, if not try a different USB port, or just remove and replace if you only have the one.

---

### Post by Yaholo on 2006-12-12
I followed your instructions to the letter (well written by the way).  I blacklisted, restarted, etc.  My device IS recognized by lsusb, and it is plugged into a powered USB port.  I also have two of these usb devices, so I know that it is the installation and not a bad device.  Again, I got it working before...  

What about iwconfig not recognizing the essid I put in the etc/network/interfaces?  Does that mean anything?

---

### Post by FrodoB on 2006-12-12
I am still concerned with your signal. Here is mine, in the same room as the router:


 Link Quality=100/100  Signal level:-28 dBm  Noise level:-79 dBm

No signal, no connection.

---

### Post by FrodoB on 2006-12-12
Maybe try to kick start it with:

sudo ifconfig rausb0 up 

from the command line.

Also WEP keys can be an issue at this point, triple check them and the ESSID name in interfaces.

---

### Post by FrodoB on 2006-12-12
Also did you get your device ID entered correctly int rtmp_def.h this would cause a problem.

I suppose you have tried removing and replacing the device several times as well.

---

### Post by FrodoB on 2006-12-12
Also of interest I can simulate your iwconfig output:

rausb0    RT73 WLAN  ESSID:""  
          Mode:Auto  Frequency=1 MHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


My wireless router is turned off.

Here is yours:


rausb0    RT73 WLAN  ESSID:""  
          Mode:Auto  Frequency=1 MHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Are you sure that your router does not just turn off wireless between certain hours perhaps?


This is my output if the router is on, but I have no WEP set:

rausb0    RT73 WLAN  ESSID:""  
          Mode:Auto  Frequency=11 MHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Note the good signal.


And here it is connected:

rausb0    RT73 WLAN  ESSID:"MY_ESSID"  
          Mode:Managed  Frequency=11 MHz  Access Point: 00:70:3B:D7:53:19   
          Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-28 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by FrodoB on 2006-12-12
And perhaps more revealing, this is with the router on, but the wrong ESSID entered into interfaces, or with the right ESSID and no WEP key:

rausb0    RT73 WLAN  ESSID:""  
          Mode:Auto  Frequency=1 MHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


This would lead one to investigate the WEP keying and the router's on/off times if any. Something appears to not be matching.

---

### Post by Yaholo on 2006-12-12
Ok going on the theory that no lights simply means a bad connection, I have turned off WEP on my router.  I still can't get it to connect. Do I need to worry about channel?  What about the rt73sta.dat files?

---

### Post by FrodoB on 2006-12-12
You do not need to change rt73sta.dat.

---

### Post by FrodoB on 2006-12-12
Have you tried:
 
sudo iwlist rausb0 scanning
 
That should show if the machine can see the router at all.

---

### Post by Yaholo on 2006-12-12
"No scan results" - I need to mention that I have tried this with 2 different routers now.  I did notice that when I tried "sudo iwlist rausb0 channel" that I didn't have 6 available.  So I changed my router to channel 5.. but it didn't help

---

### Post by FrodoB on 2006-12-12
Run demsg and take a look and see if the firmware is being loaded.

---

### Post by FrodoB on 2006-12-12
Try doing it manually, one line at a time:
 
sudo ifconfig rausb0 up
 
sudo iwconfig rausb0 mode "Managed"
 
sudo iwconfig rausb0 key "XXXXXXXXXXXXXXXXXXXXXXX"
 
or if using ASCII:
sudo iwconfig rausb0 key "s:XXXXXXXXXXXXX"
 
sudo iwconfig rausb0 essid "My_Access_Point"
 
sudo iwconfig rausb0 commit
 
sudo dhclient rausb0

---

### Post by dissident_0 on 2007-01-04
Install driver of Win with ndiswrapper, assign the device when driver and it gives back to me “driver installed, hardware present”.

I have downloaded the SWScanner package, sometimes find ones me or more networks but with himself not to connect, give back to me that the device has problems or are busy. With Win it connected to me directly, is not signal problem.

	
That I can do?

---

### Post by Khaled Khalil on 2007-01-16
i had the same problem that leds are closed, but it was sufficient to try "sudo ifup wlan0",
then it runs again

now my problem (as i used to make trouble) is that it doesn't receive packets from access point

---

### Post by tapia on 2007-01-16
Hi! I'm very new in Linux, but trying to configure my DWL-G122 adapter has helped me a lot to lern how Linux works. xD

 I've done everything I've read here and in this page : [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview) but still have one little problem... 

I was able to connect with my router manually by doing the following: 
> **FrodoB said:**
> Try doing it manually, one line at a time:
 
sudo ifconfig rausb0 up
 
sudo iwconfig rausb0 mode "Managed"
 
sudo iwconfig rausb0 key "XXXXXXXXXXXXXXXXXXXXXXX"
 
or if using ASCII:
sudo iwconfig rausb0 key "s:XXXXXXXXXXXXX"
 
sudo iwconfig rausb0 essid "My_Access_Point"
 
sudo iwconfig rausb0 commit
 
sudo dhclient rausb0
... It gives me an IP and the signal level is 93/100... that means good... but I still can't surf in the internet... the link light is on and the activity light flashes on time to time.

What can this be??:confused: 

Sorry if my english sucks, but it is clearly not my motherlanguage... xD

Thanks!

---

### Post by tapia on 2007-01-16
Forget what I said!!!... It works great now!!!!!!
Thanks a lot!!!!!;) :D :-D

---

### Post by Floppyjoe on 2007-01-16
I just installed the drivers for DWL-G122 ver A1 on one of my computers. I also have the DWL-G122 ver C1. I got the first one working with Ndiswrapper and WPA with the drivers downloaded from D-link for the A1 Version. I then turned off my computer removed the version A1 dongle and plugged in the Version C1 dongle rebooted and wouldn't you know it worked with the other drivers for A1. When i do iwconfig I get a wierd interface name present with the C1 dongle called wmaster0 plus the wlan0 interface. When I scan or do iwconfig I don't get as much info as with the A1 version. This post is via the A1 version ndiswrapper driver with the C1 hardware with WPA encryption. Also when i do ndiswrapper -l  it says:
> Installed drivers:
prisma02                driver installed 
 But no hardware present. What do you think of that?

---

### Post by oasism on 2007-01-24
d link dwl g122 rev c1 ver: 3.00 driver is not found or not work but I give 


[http://rapidshare.com/files/13047974/dwlg122c1_driver_300.part1.rar](http://rapidshare.com/files/13047974/dwlg122c1_driver_300.part1.rar)
[http://rapidshare.com/files/13051306/dwlg122c1_driver_300.part2.rar](http://rapidshare.com/files/13051306/dwlg122c1_driver_300.part2.rar)
[http://rapidshare.com/files/13059188/dwlg122c1_driver_300.part3.rar](http://rapidshare.com/files/13059188/dwlg122c1_driver_300.part3.rar)
[http://rapidshare.com/files/13068432/dwlg122c1_driver_300.part4.rar](http://rapidshare.com/files/13068432/dwlg122c1_driver_300.part4.rar)

---

