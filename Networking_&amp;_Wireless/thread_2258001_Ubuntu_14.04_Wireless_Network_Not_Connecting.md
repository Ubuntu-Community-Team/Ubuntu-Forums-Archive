---
title: "Ubuntu 14.04 Wireless Network Not Connecting"
date: 2014-12-24
forum: Networking &amp; Wireless
---

### Post by m-veron622 on 2014-12-24
Hello, I am new to Ubuntu 14.04. I installed this version of Ubuntu using a micro-USB that was given to me by a friend. The problem I am having is when I try to connect to other wireless networks. I am using **Wicd Network Manager**, and its able to successfully scan using my internal NIC, but it is not able to connect to any of them except my own home address. It just stays on the "Obtaining IP address" function after attempting a connection, but it never successfully connects. I am not sure what to do from here, so if anyone can help me out I would greatly appreciate it! :KS

-Mark

---

### Post by e633 on 2014-12-24
"Before posting in networking & wireless"... [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by chili555 on 2014-12-24
Boy! We have a bunch of things going on here! Two devices, two drivers, conflicts, overlaps... I haven't had this much fun in weeks! Frankly, I'd love to start by troubleshooting the internal. Please detach the USB and open a terminal and run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by m-veron622 on 2014-12-27
Okay, I am trying the first reply. Sorry it has taken me so long to get back, holiday cheers! 
As for the second reply, I don't use the USB to run Linux. I have already installed it from that USB, so I just added that in case it made a difference. I will try running your script if I do not get any success with the first reply. 

I've ran the following code so far, and it says everything is now updated and some extraneous software/firmware is removed. Later this evening I will try and access a different wireless host, so that I can test whether or not I am still having the problem. 

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove

---

### Post by m-veron622 on 2014-12-29
I am still having partial difficulties accessing WIFI. It seems that at certain spots I am able to connect, and others I am not. For example at my gf's house I am able to, but not at Coffee shops...

---

### Post by chili555 on 2014-12-30
Our requests above were for you to provide the results of the commands for us to diagnose your problem. They were not intended to magically fix anything. We're really good, but not that good! Please provide the requested information.

---

### Post by m-veron622 on 2015-01-26
I understand the issue is not "magically fixed". I wrote that I am new with this system, and as a result I do not understand how the diagnostic system works on Ubuntu. Therefore I do not know how to provide the results of the commands, so I did in layman's terms. If you or anyone could please guide me on how I could provide this data, I would be more than happy to help.

---

### Post by chili555 on 2015-01-26
Please open a terminal Ctrl+Alt+t. Type in this code:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Press Enter. Several details about your internal wireless device will be returned. Here is an example from my computer:> chili@T410:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)Yours will probably be different. Please post what you get for our examination. We hope it will give us some clues as to how we can solve your problem, which is:> The problem I am having is when I try to connect to other wireless networks. I am using Wicd Network Manager, and its able to successfully scan using my internal NIC, but it is not able to connect to any of them except my own home address. It just stays on the "Obtaining IP address" function after attempting a connection, but it never successfully connects.

---

### Post by m-veron622 on 2015-01-27
This is what I am receiving:

08:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)

Oh and btw, Ctrl+Alt+T doesn't work on my PC for some reason?

---

### Post by chili555 on 2015-01-27
Let's try a driver parameter. In the terminal:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
reboot
```> Oh and btw, Ctrl+Alt+T doesn't work on my PC for some reason?I haven't any idea; sorry.

---

### Post by m-veron622 on 2015-02-03
Okay, I typed all of that and rebooted. I haven't tried to connect to any other AP's except my home thus far. In the meantime, is there any other indicator I should be looking for following the command that you instructed?

---

### Post by chili555 on 2015-02-03
Just tell us if you are able to connect satisfactorily. We'll have other suggestions depending on the symptoms.

---

### Post by m-veron622 on 2015-02-07
I successfully logged into my school's NW today. I'm not sure about other locations, but will post more info soon. Thank you.

---

### Post by m-veron622 on 2015-02-07
[IMG]Photo.jpg[/IMG]

This also started showing up after I used your code. Not sure exactly what Avahi is?

---

### Post by chili555 on 2015-02-07
Please see: [http://askubuntu.com/questions/339702/network-service-discovery-disabled-what-does-this-mean-for-me](http://askubuntu.com/questions/339702/network-service-discovery-disabled-what-does-this-mean-for-me)

---

### Post by m-veron622 on 2015-02-08
Thanks for that last post. I recently tried to connect to a NW through a coffee shop, but it failed. I am still using Wicd network manager and through that application is what I usually try and connect to other NWs. I am not sure if this next bit of info helps, but I also added the stock ubuntu Network Monitor on my top panel and it says the interface is down. I find this strange since I am able to connect via WICD.

---

### Post by chili555 on 2015-02-08
> **m-veron622 said:**
> Thanks for that last post. I recently tried to connect to a NW through a coffee shop, but it failed. I am still using Wicd network manager and through that application is what I usually try and connect to other NWs. I am not sure if this next bit of info helps, but I also added the stock ubuntu Network Monitor on my top panel and it says the interface is down. I find this strange since I am able to connect via WICD.I am not sure, but I suspect that Network Manager is stepping back to allow Wicd to work.

---

### Post by m-veron622 on 2015-02-08
Should I try uninstalling WICD in order to see if my Network Manager will work in other locations besides my school or home?

---

### Post by m-veron622 on 2015-02-08
I uninstalled WICD, but my Network Manager panel still says the interface is down. The strange thing is I am still able to connect to the internet. (This was all done at my local university.) Might be that this is related to my inability to connect to other WAP's?

---

### Post by chili555 on 2015-02-08
I would. If you are unable to connect using NM, installing another method, usually Wicd, almost never helps. It simply masks the underlying problem. Let's treat the disease, not the symptoms.

---

### Post by chili555 on 2015-02-08
> **m-veron622 said:**
> I uninstalled WICD, but my Network Manager panel still says the interface is down. The strange thing is I am still able to connect to the internet. (This was all done at my local university.) Might be that this is related to my inability to connect to other WAP's?Are there still other methods trying to control networking? May we see:```
cat  /etc/network/interfaces
```

---

### Post by m-veron622 on 2015-02-09
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


^^Response

---

### Post by m-veron622 on 2015-02-14
Any idea on what to try next?

---

### Post by chili555 on 2015-02-15
May I assume this is still the case?> it says the interface is down. I find this strange since I am able to connect via WICD. That is, you are able to connect although Network Manager says the network is down, is that correct?

May I see:```
nm-tool
```

---

### Post by m-veron622 on 2015-02-15
Yes that is correct, I am able to connect even though my Network Manager says the NW is down. 

NetworkManager Tool


State: connected (global)


- Device: wlan0  [eaglenet] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        68:17:29:2D:42:9F


  Capabilities:
    Speed:           104 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    eduroam:         Infra, 18:64:72:EB:58:62, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA2 Enterprise
    eaglenet:        Infra, 18:64:72:EB:58:60, Freq 2437 MHz, Rate 54 Mb/s, Strength 87
    HP-Print-58-Officejet 7110: Infra, 2C:59:E5:D0:91:58, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2
    UNT:             Infra, 18:64:72:EB:88:41, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    eduroam:         Infra, 18:64:72:EB:88:42, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    eduroam:         Infra, 18:64:72:EB:92:82, Freq 2412 MHz, Rate 54 Mb/s, Strength 79 WPA2 Enterprise
    tlittle&#8217;s iPhone: Infra, 7E:FA:DF:93:D2:8A, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2
    eduroam:         Infra, 18:64:72:EB:8B:C2, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    eaglenet:        Infra, 18:64:72:EB:88:40, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    *eaglenet:       Infra, 18:64:72:EB:92:80, Freq 2412 MHz, Rate 54 Mb/s, Strength 56
    UNT:             Infra, 18:64:72:EB:58:61, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA2 Enterprise
    eduroam:         Infra, 18:64:72:EB:92:22, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    UNT:             Infra, 18:64:72:EB:90:A1, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA2 Enterprise
    UNT:             Infra, 18:64:72:EB:92:21, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    hpsetup:         Ad-Hoc, 32:C1:DE:0D:0B:33, Freq 2437 MHz, Rate 11 Mb/s, Strength 27
    eaglenet:        Infra, 18:64:72:EB:92:20, Freq 2412 MHz, Rate 54 Mb/s, Strength 64
    UNT:             Infra, 18:64:72:EB:79:E1, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    eduroam:         Infra, 18:64:72:EB:79:E2, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    UNT:             Infra, 18:64:72:EB:8B:C1, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2 Enterprise
    eduroam:         Infra, 18:64:72:EB:9A:42, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2 Enterprise
    eaglenet:        Infra, 18:64:72:EB:79:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 34
    eaglenet:        Infra, 18:64:72:EB:8B:C0, Freq 2412 MHz, Rate 54 Mb/s, Strength 27
    UNT:             Infra, 18:64:72:EB:8E:41, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2 Enterprise


  IPv4 Settings:
    Address:         10.124.76.17
    Prefix:          24 (255.255.255.0)
    Gateway:         10.124.76.250


    DNS:             129.120.210.235




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        00:8C:FA:4A:CF:2A


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off

(This was taken while I was at my university).

---

### Post by m-veron622 on 2015-02-24
Next possible step?

---

### Post by m-veron622 on 2015-03-04
???

---

