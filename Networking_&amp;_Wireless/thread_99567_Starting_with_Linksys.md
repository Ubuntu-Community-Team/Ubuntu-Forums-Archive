---
title: "Starting with Linksys"
date: 2005-12-05
forum: Networking &amp; Wireless
---

### Post by slide4417 on 2005-12-05
Loaded ubuntu just a few minutes ago...I have no clue how to get the wifi working. I have a USB Linksys WUSB54GS.
I suspect this is going to be a fully manual process. Can someone clue me where to begin....Thanks!  
PS...the 'LIVE' version worked from the start with this laptop...wireless and all!!  But NG with the Compaq desktop.
....Dave

---

### Post by cyaconi on 2005-12-05
Personally, I do prefer scripts... 
Are your router configured has DHCP??
If not, here is the script I use to activate my wifi (just an extract, because I use ubuntu in my notebook and I have a few profiles)

```

WIFI="eth1"
GW="YOUR_ROUTER_FIXED_IP"
SSID="YOUR_SSID"
CHANNEL="YOUR_CHANNEL"
KEY="YOUR_WEP_KEY" # If you has security enabled in your router
IP="YOUR_NOTEBOOK_WIFI_IP"
sudo ifdown $WIFI
sudo ifup $WIFI
sudo iwconfig $WIFI essid $SSID
sudo iwconfig $WIFI channel $CHANNEL
sudo iwconfig $WIFI key restricted $KEY #Again, only if you need WEP
sudo ifconfig $WIFI $IP netmask 255.255.255.0
sudo route add default gw $GW $WIFI

```

I know this script could be better, but for me is enough...

---

### Post by slide4417 on 2005-12-05
Linksys' online chat told me the wifi adapter will not work in LINUX. I wonder if I should try anyway, or just try another brand...Netgear or whomever.....

---

### Post by jml on 2005-12-05
My personal experience has been very poor with USB based wireless adaptors in Linux.  I've tried Linksys, (two different versions,) and Belkin.  Neither worked.  Granted, I was looking for a solution that would recognize them out of the box, without any manual configuration, but my research also failed to give me even a complicated solution.  If your computer has a PC card slot, you are more likely to get that working in Ubuntu.  It supports a lot of cards "out of the box"  You may not need to load any drivers, just configure the card once Ubuntu boots up by going to System--->Administration--->Networking.

If portability is not a requirement, you can configure a wireless router/accesspoint like the Linksys WRT54G to function as a remote access point.  It just plugs into your ethernet port.  Instructions are included in the documentation that comes with the hardware.  Hope this helps.

Joe

---

### Post by slide4417 on 2005-12-05
Joe...Can you suggest a wireless card to get?  I'll get one tomorrow, and plug it in...I'll save the USB job for windows stuff. 
Thanks for the advice!
...Dave

---

