---
title: "WPA problem or PCMCIA?"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by aztektum on 2006-10-12
I have this problem where it takes me multiple boot ups of my laptop before wpa_supplicant finds and connects to my wifi network. Once it finally does (usually after attempt 3 or 4), it works great, better than this card works in Windows. It's a annoying issue I would like to fix if possible.

The thing is I don't know if the problem is wpa or with my adapter card and ndiswrapper.

wpa_cli status always says scanning and the interactive prompt doesn't show anything, no attempts or nothin'.

I'm wondering if it has to do with my card and driver, but it's just a thought. I have no idea how to test.

Anyone have any ideas?

---

### Post by wieman01 on 2006-10-12
What wireless adapter have you got? WPA(1) with TKIP? Is the ESSID hidden?

Once you have booted and logged on to your system, please try this command & _**let us know if your card connects**_:
> sudo /etc/init.d/networking restart
If it does, then I know a remedy as I am facing the same problem on both of my computers (Linksys WUSB54G and Intel IPW2200, wpa_supplicant running). The solution is two create a boot-script that restarts the networking automatically so that you won't notice anything & don't have to restart manually. But we'll get to that later.

---

### Post by aztektum on 2006-10-25
actually i think it has something to do with the fact that i was hiding my SSID. once i enabled the SSID broadcast it connects no problem.

---

### Post by wieman01 on 2006-10-25
If you show us your WPA_SUPPLICANT configuration file, I could help you. You need to tell wpa_supplicant that your ESSID is hidden.

---

### Post by aztektum on 2006-10-25
Mine pretty much looks like this, but with my specific network variables

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="your_ssid"
       bssid=MA:CA:AD:DR:ES:S
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=longstringofgibberish
}

From how I understood it, if I had a hidden ssid I needed to use BSSID to specify the physical address. Didn't seem to work.

---

### Post by wieman01 on 2006-10-25
No, you need to uncomment this line:
> ap_scan=2
"ap_scan" defines the scanning logic & as far as I remember "2" stands for hidden ESSID, "1" for broadcast. But try both ways.

---

### Post by aztektum on 2006-10-25
just out of curiosity wouldn't doing

> sudo ifdown/up wlan0

do the same as 

> sudo /etc/init.d/networking restart

but obviously only for the wlan0 interface? or is restarting the entire network service provide a more thorough method?

oh and the ap_scan seemed to have little effect. wpa_cli says it tries to auth and even connects for a few seconds, long enough for DHCP to accept an IP, but terminates. 

it does that with a hidden SSID or visible. when it's visible no amount of restarting the interface or the network restart helps. only a reboot.

---

### Post by wieman01 on 2006-10-25
Yes, it does the job as well. :-)
> sudo ifdown/up wlan0
Any success with "ap_scan"?

---

### Post by aztektum on 2006-10-25
no it doesn't seem to make any difference.

sudo wpa_cli says it tries to auth with the ssid, but times out.

---

### Post by wieman01 on 2006-10-26
You could try to add this to "interfaces" file:
> auto wlan0
iface wlan0 inet dhcp
**[COLOR="Red"]wpa-ap-scan 2[/COLOR]**
_**EDIT:**_
Or change this line in the wpa_supplicant config file:
> scan_ssid=**[COLOR="Red"]2[/COLOR]**

---

