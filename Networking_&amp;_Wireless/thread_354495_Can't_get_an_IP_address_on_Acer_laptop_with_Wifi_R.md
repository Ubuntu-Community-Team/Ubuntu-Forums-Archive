---
title: "Can't get an IP address on Acer laptop with Wifi Radar"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by sugar_chihuahua on 2007-02-06
Hey everyone....

Have recently installed 6.10 on a Acer TravelMate 521TXV. I have a Lucent Orinoco Silver wifi card and have yet been able to get it to work.

Firstly went to networking- the card itself is recognised, but when I went into properties my home network wasnt in the dropdown menu- so entered the network name (panther) and WEP key and doesnt seem to connect...

I download Wifi Radar thats got me a bit closer- it shows my network and signal strength, but when I press connect, it says 'could not get IP address'. it also displays at the bottom of Wifi radar: 'Connected to panther ip(None)'. 

Suggests that it recognises the network but can't get an IP... anyone had this problem before?

(Also- I have entered a WEP key as listed on my other computer which is a Mac- is that format the same for Ubuntu?)

---

### Post by ESPOiG on 2007-02-06
yes i had this problem, you have to set up your options via Wifi Radar, ip channel etc etc

but defiantly set ur ip manually in wifi radar

---

### Post by sugar_chihuahua on 2007-02-06
Hey- thanks for the suggestion- had a linux friend come around and set up everything manually for the IP but still no joy...

---

### Post by HilliBilly on 2007-02-08
have the same problem (with pheenet wifi usb stick). can't explain why but this works for me: (re)boot without the usb stick, open wifi-radar, put in the stick, click on 'connect', if get an IP, it's fine, if not, unplug the usb stick, stop/restart wifi-radar, put in the usb stick again, click again on connect and get the IP. 

that's not comfortable but it works. if anyone could explain to me what's wrong with my setup would be great!

forgot: put all options in the wifi-radar's profile-configuration on 'auto'.

---

### Post by sugar_chihuahua on 2007-02-09
thanks for the post hillibilly - however my wifi card is a PCMCIA card, not a usb based wifi card so im not sure if that will work for me- cheers!

---

### Post by sugar_chihuahua on 2007-02-09
> **ESPOiG said:**
> yes i had this problem, you have to set up your options via Wifi Radar, ip channel etc etc

but defiantly set ur ip manually in wifi radar

Hey ESPOiG... had a friend help me set up everything manually... she's a bit of a linux lady but still couldnt get it working... this is what I'm getting from the card now when I try to connect:

eth1      Link encap:Ethernet  HWaddr 00:02:2D:1E:CF:21  
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5482 (5.3 KiB)
          Interrupt:3 Base address:0x100 

any suggestions? is there any other info i can post about whats happening? says that its connecting in wifi radar with the manually set IP but doesnt seem to get any data from the web..

---

### Post by gradedcheese on 2007-02-09
you can check on the status of the WiFi like this:

iwconfig eth1

This should show you if it's associated, what SSID its using, etc.  If it's not associated, you can tell it to associate like this:

sudo iwconfig eth1 essid your_ssid_here

You can manually assign an IP address like this:

sudo ifconfig eth1 ip_address_here

Make sure that the IP address if valid and isn't in the DHCP range for your router (if there is such a range on your LAN).  If, instead, you want to manually ask for a DHCP address:

sudo dhclient eth1

If you want to do a scan at the terminal to see what access points the card really sees:

sudo iwlist eth1 scanning

Make sure it sees the access point that you're trying to use.

---

### Post by sugar_chihuahua on 2007-02-09
Thanks for the msg gradedcheese- i think that eth1 is associated with a SSID and from running the first command you suggested

[QUOTE=gradedcheese;2127854]you can check on the status of the WiFi like this:

iwconfig eth1

This should show you if it's associated, what SSID its using, 

eth1      IEEE 802.11b  ESSID:"panther"  Nickname:"panther"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:8A:CC:8B   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/92  Signal level=-37 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:111  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

has this got an IP address

---

### Post by tonab on 2007-02-09
You could try disabling your ethernet card in network manager, I have orionoco gold and its connected as at0 not et0 , havnt used wifi radar to any extent.

---

### Post by sugar_chihuahua on 2007-02-09
Hi Tonab- have tried disabling the ethernet card in network manager but still no joy....

---

### Post by tonab on 2007-02-11
ok i dont know how much you know about network manager setup,when i connected i activated my orinoco and chose ath01 ,im very new to linux i use ubuntu 5.10,by looking at your log its saying eth01 which on my system is the eternet card which im not using ,as i said just a beginner but hope its of some help.

---

### Post by sugar_chihuahua on 2007-02-11
Thanks for the post- how did you select ath01? in Network manager somehow? I have been connecting the laptop via ethernet cable to the net as the wifi card isnt working... however the ethernet card is eth0 and the wifi identifier has been eth1 when ive been plugging it in. I have tried turning off the ethernet card in Network Manager, but it hasnt made a difference

---

### Post by tonab on 2007-02-13
when u open network manager at the bottom of the manager window there is  a default gateway device with a arrow and a small menu to change at0 or eth0

---

### Post by bart82 on 2007-10-04
Thanks! - gradedcheese.
doing a "sudo dhclient eth1" -- assigns an IP Address and I am able to connect to the Internet.  

Thanks again so much!

---

