---
title: "Connecting to Linksys WRT54G router"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by M3gabyte on 2007-02-01
ok first off im new to linux and ubuntu here's my problem im trying to connect to the wireless router via the router in the title i set up the connection through the networking menu but it doesnt seem to work so im wondering what else needs to be done to get this internet up and running any suggestion are welcome.

-M3gabyte

---

### Post by M3gabyte on 2007-02-02
can anyone help or do u guys need more info to help please i need feedback

---

### Post by TheWizzard on 2007-02-02
> **M3gabyte said:**
> can anyone help or do u guys need more info to help please i need feedback


more info is definitely needed. 
- did you use the router before? e.g. from windows partition.
- did you set up wireless security? 

if you did use the router before and secured the connection with wep, do the following: 

1. open a terminal/conole
2. type:
```
iwconfig
```
if your wireless card is working, you'll see a wireless device listed. probably called eth1
3. type:
```
sudo nano -B /etc/network/interfaces
``` en give your password if needed. 
4. look for an entry with eth1 (or something else if #3 listed an other wireless device)
5. make it look like this: 
```
auto eth1
iface eth1 inet dhcp
wireless-essid type_wireless_id_here
wireless-key type_wep_key_here
```
6. use ctrl+x to exit and save changes
7. reboot

stuff should be working now

---

### Post by M3gabyte on 2007-02-03
ok when i type iwconfig the only eth thing i see is eth0 when i try to edit the files below it never saves so when i reboot its the old stuff still there i have been able to connect on the windows partition as u can see i am posting from it and yes wireless securityhas been setup on the router

---

### Post by TheWizzard on 2007-02-03
> **M3gabyte said:**
> ok when i type iwconfig the only eth thing i see is eth0 when i try to edit the files below it never saves so when i reboot its the old stuff still there i have been able to connect on the windows partition as u can see i am posting from it and yes wireless securityhas been setup on the router

please post the exact output of iwconfig. 
what do you mean by "when i try to edit the files below it never saves"?

---

### Post by M3gabyte on 2007-02-03
ok heres the output 

```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"CKoester"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:-2 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

and what i mean by it not saving is when i boot back up and go back into the interface thing it doesnt have the changes i made to it
also i think the ra0 is from when i tried to set it up in the networking menu

---

### Post by TheWizzard on 2007-02-04
> **M3gabyte said:**
> ok heres the output 

```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"CKoester"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:-2 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```


this means your wifi card has a RT2500 chipset. search the forum for howto's. 
you problem doesn't have to do anything with your router. next time when you post, make sure the title of your post corresponds with your problem. this way you'll get more responses to your questions. 



> **M3gabyte said:**
> 
and what i mean by it not saving is when i boot back up and go back into the interface thing it doesnt have the changes i made to it


did you, after the changes, use ctrl+X to exit and answer "Yes" when it asked to save changes? 
one thing: when you open the GUI network tools with root previledges, they can overwrite your changes in /etc/network/interfaces. 

basically my advice to you is to go looking for rt2500 howto's.

---

### Post by M3gabyte on 2007-02-04
ok thanks for the point in the right direction

---

### Post by TheWizzard on 2007-02-05
> **M3gabyte said:**
> ok thanks for the point in the right direction

welcome. good luck!

---

### Post by Matt Yun on 2007-02-05
Fortunately for you, the RaLink wireless card is 100% Linux friendly, and does not even require wpa_supplicant for WPA compatibility.  I have one of these cards (CNET CWP-854) on my desktop machine at home, running Sidux, and it required no manual configuration apart from entering my wireless network's SSID and WPA key.

It would be much easier if you simply install the Gnome Network Manager.  It is a little Gnome system tray applet that helps you manage your wireless network, like in Windows XP, without having to muck about with ifconfig, iwlist, iwconfig or wpa_supplicant.

It works for me like a charm on a Dell Latitude D600 running Dapper.  It automatically detects proximate wireless networks, and handles WPA encryption easily.  

To install it, open a command terminal and type 'sudo su' to get a root prompt.  Then run 'apt-get update && apt-get install network-manager-gnome'

If you don't like using a console, then try the 'Add/Remove Applications' in your Applications menu, and search for network-manager-gnome.

See this thread for more info:  [http://www.ubuntuforums.org/showpost.php?p=703020&postcount=1](http://www.ubuntuforums.org/showpost.php?p=703020&postcount=1)

---

### Post by Skidpad on 2007-02-05
I also have an RT2500 wireless card (ASUS WL-107G) that worked in Ubuntu out-of-the-box.  I did update the driver to get it working correctly in XP, but no problems at all in Ubuntu.

Your iwconfig output does not show any link quality.  To make things easier, you may want to disable all router security/encryption and try again.  Once your wireless is running ok, re-introduce security on your network.

Here's my iwconfig output for reference...   

[B]ra0       RT2500 Wireless  ESSID:"******"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate:24 Mb/s   Tx-Power:1 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=66/100  Signal level=-66 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/B]

---

### Post by M3gabyte on 2007-02-06
ok ive made some changes and now im gettting a signal through iwconfig and everything seems to be right but it still wont work .... btw im using wep encryption and i havent found any posts that corespond to my problem i can post the output of the iwconfig if that will help

---

