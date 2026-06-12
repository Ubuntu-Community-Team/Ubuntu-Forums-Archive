---
title: "no wireless connection - only on home network"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by angelsneverdie on 2010-03-18
I just got a new Sony Vaio Y series and am dual booting windows 7 and ubuntu 9.1.

Yesterday I took it to class with me and it connected just fine with the school wifi - 

when I got it home however it won't connect with my wireless network.  Neither Ubuntu nor Windows will connect.

All the other devices on my network work fine (desktop - ubuntu 9.1, old laptop - ubuntu 9.1, PS3) which leads me to believe that I should be able to connect with my new laptop.

I have mac filtering turned on and I made sure I had entered the right mac address for the laptop, still nothing.  I turned mac filtering off and nothing.

In the list of wireless networks I see my network, i click on it, enter the encryption key, and it just pops up and says network disconected. (yes, i'm sure i'm entering the right key)

anyone have any ideas?  here is some info i pulled from it in case it helps:
> mitchell@mitchell-laptop:~$ sudo lspci | grep -i network 
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01) 

> mitchell@mitchell-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:24:be:5e:37:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:30 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6239 (6.2 KB)  TX bytes:6239 (6.2 KB) 

wlan0     Link encap:Ethernet  HWaddr 2c:81:58:fd:cc:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 2C-81-58-FD-CC-25-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 


mitchell@mitchell-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:24:be:5e:37:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:30 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6239 (6.2 KB)  TX bytes:6239 (6.2 KB) 

wlan0     Link encap:Ethernet  HWaddr 2c:81:58:fd:cc:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 2C-81-58-FD-CC-25-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 


---

### Post by Peter09 on 2010-03-18
As your machine works elsewhere it more likely to be a misconfiguration of your router. Have you DHCP enabled on your router? Are the other devices on your network hardwired/wireless?

---

### Post by angelsneverdie on 2010-03-18
I'm pretty sure DHCP is enabled (it should be, right?) and all of the devices i listed are wireless (except the desktop which is hardwired, but i unpluged it and the wireless card worked fine)

---

### Post by admiralspark on 2010-03-18
Yknow, I'm not sure this will help, but I've had to do it maybe twice a year (when I'm messing with my wireless cards):
**_[COLOR=Red]**WARNING** Proceed with Caution!![/COLOR]_**
Boot into the BIOS menu, and press whichever keys you need to to "Reset to Factory Defaults". This will fix any lower-problems with your wireless, assuming it's the wireless card and not the router. 

[COLOR=Red]_**/Caution**_[/COLOR]

The fact that your router connects fine with other computers makes me think it's your laptop. Would you kindly post the output of "iwconfig"? To see if the wireless card is operating at the right levels. 
Potential problems:
--Permissions problems
--misconfigured wlan0 connection
--driver problems?

---

### Post by admiralspark on 2010-03-18
[Your Wireless Card]("https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285")

---

### Post by angelsneverdie on 2010-03-18
> **admiralspark said:**
> Yknow, I'm not sure this will help, but I've had to do it maybe twice a year (when I'm messing with my wireless cards):
**_[COLOR=Red]**WARNING** Proceed with Caution!![/COLOR]_**
Boot into the BIOS menu, and press whichever keys you need to to "Reset to Factory Defaults". This will fix any lower-problems with your wireless, assuming it's the wireless card and not the router. 

[COLOR=Red]_**/Caution**_[/COLOR]

The fact that your router connects fine with other computers makes me think it's your laptop. Would you kindly post the output of "iwconfig"? To see if the wireless card is operating at the right levels. 
Potential problems:
--Permissions problems
--misconfigured wlan0 connection
--driver problems?

mitchell@mitchell-laptop:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11bgn  ESSID:""   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=20 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


i am doing this at work right now where there is no wifi . . . if that makes a difference

---

### Post by admiralspark on 2010-03-18
Yeah, that would make a difference, part of what I hoped to see was whether iwconfig read it as connecting to an AP.

You'd mentioned earlier that Windows won't connect now either, I'm thinking that might point to either the BIOS needing to be reset (to factory defaults, as mentioned above) or it might be a hardware problem. It shouldn't be an issue with hardware since the laptop is new, so I'm leaning towards BIOS or the driver being bad.

Here's a test: Boot windows and reinstall the driver.

---

### Post by angelsneverdie on 2010-03-18
> **admiralspark said:**
> Yeah, that would make a difference, part of what I hoped to see was whether iwconfig read it as connecting to an AP.

You'd mentioned earlier that Windows won't connect now either, I'm thinking that might point to either the BIOS needing to be reset (to factory defaults, as mentioned above) or it might be a hardware problem. It shouldn't be an issue with hardware since the laptop is new, so I'm leaning towards BIOS or the driver being bad.

Here's a test: Boot windows and reinstall the driver.

i don't know if this will help anything, but i just went to the pub down the block for lunch and again my laptop connected to their wifi no problem (with both ubuntu and windows)  here's what it gave me:
> mitchell@mitchell-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:"BritishBulldog"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:15:70:9F:26:A9   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 


---

### Post by cerealtx on 2010-03-18
this may sound stupid but on the mac filter list, are you sure u didn't filter your mac out instead of safelisting it?

---

### Post by angelsneverdie on 2010-03-18
> **cerealtx said:**
> this may sound stupid but on the mac filter list, are you sure u didn't filter your mac out instead of safelisting it?

that doesn't sound stupid because that is one of the first things I checked because it is something I would do.  but it was deffintly set up right.

do you think i should try just factory resetting the router?

---

### Post by cerealtx on 2010-03-18
are you the only comp in the house connecting to it?, do you have a eth cable you can connect to it with?

---

### Post by lisati on 2010-03-18
I don't use iwlist much, but might have expected it to at least show the wireless network at home, even if it wasn't connecting. Unless the SSID is "hidden"....

---

### Post by eronisko on 2010-03-18
Yeah, if it doesn't involve too much hassle, I would say resetting the router might be the quickest solution.
If nothing else, it will eliminate the misconfigured router option... 

But again, do it only if you don't have many devices relying on it.

And when you have decided to do it, don't forget to turn your WPA(2) protection back on. With that in place, and a strong password, MAC filtering isn't really necessary IMHO.

---

### Post by angelsneverdie on 2010-03-18
well i am typing this from the computer in question on my home network.   doing a hard reset of the router seems to have done the trick.  
the reason i had mac filtering on was because originally that was the only way i could get a reliable connection with my ps3, but i'll try it  without - maybe that issue was fixed.

now i just need to get sound working on ubuntu on this pc . . .

thanks for all your help guys!

---

### Post by admiralspark on 2010-03-18
Yeah, sometimes things just happen with the routers. 
As eronisko said, WPA is nearly impossible to break if done right. Using a totally random password guarantees the highest amount of security, since the only strong way I'm aware of for wirelessly cracking a WPA router is running a dictionary against it. If the password's not in the attacker's wordlist, nothing can break it.

Anyways, as for your sound, did you open another thread yet?

---

