---
title: "Wifi problem on 13.10"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by Irasad_Ahamad on 2014-03-30
Hi there,

I have gone through many suggestions which have been provided in the forum but I am still unable to my connect wifi.

I have to restart my system multiples time and suddenly it get connected in a occurrence after trying many times.

Can you please help me out there to resolve this problem. It will be great help.
I have run your wireless script and attaching the result here.

[http://pastebin.com/GKaAzCCN](http://pastebin.com/GKaAzCCN)


Thanks & Regards,
Irasad Ahamad

---

### Post by chili555 on 2014-03-30
I notice that /etc/modules asks for b43 to be loaded automatically:```
##### modules #####
 
lp
rtc
lp
rtc
b43
```And blacklist asks that it *not* be loaded!> [/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
<snip>I'm not sure how significant it is, but let's correct it and see if it helps:```
gksudo gedit /etc/modules
```Please change the file to remove the last three lines so that it now reads:```
lp
rtc
```Proofread, save and close gedit.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)  Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
``` Of course, substitute your country code if not Iceland. Proofread carefully, save and close gedit. 

Now reboot and let us have your report.

---

### Post by Irasad_Ahamad on 2014-04-02
Hi There,

I tried your recommendation but sorry to say that it didnt help. Still I am facing the problem. 
Please find my latest output for wireless script : [http://pastebin.com/uCVcZ2Yq](http://pastebin.com/uCVcZ2Yq)

Thanks in advance :)

---

### Post by chili555 on 2014-04-02
First, I'd suggest you check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Second, I'd be interested in the same report after a reboot so that we have a clean slate and with the tethered phone disconnected. Run the script and then connect the phone to paste it.

Is this your network?> Cell 02 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"faizan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 00066661697A616E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030102
                    IE: Unknown: 0706494E49010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD050010910400

---

### Post by Irasad_Ahamad on 2014-04-04
Hi There,

I am still facing the problem. Please find the latest result for wireless script:
[http://pastebin.com/6GzLJEMu](http://pastebin.com/6GzLJEMu)

Please help me on this

---

### Post by chili555 on 2014-04-04
If this is your network:> Cell 02 - Address: <MAC address removed>
Channel:2
Frequency:2.417 GHz (Channel 2)
Quality=51/70 Signal level=-59 dBm
Encryption key:on
ESSID:"faizan"Then nothing has changed according to your latest wireless script. Is this a router over which you have administrative privileges? Can you please make the changes I suggested?

---

### Post by Irasad_Ahamad on 2014-04-06
Hi there,

Yes, my network ESSID is "faizan". I did your recommended router changes today. Sorry to say but still no luck.
Please find latest wireless script result and help me to come out from this problem.
[http://pastebin.com/mxr30Wfg](http://pastebin.com/mxr30Wfg)

Thanks & Regards
Irshad

---

### Post by chili555 on 2014-04-06
Maybe we can see why it isn't connecting as expected. Please reboot with any ethernet detached and then run:```
cat /var/log/syslog | grep -e etwork -e eth1 | tail -n25  >  wifi.txt
```Hook up the ethernet so you can post the details. Find the file wifi.txt in your user directory  and pastebin it.

---

### Post by praseodym on 2014-04-06
There are no nameservers listed in the /etc/resolv.conf:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by Irasad_Ahamad on 2014-04-23
Hi there,

Sorry for coming late, I have updated OS to 14.04 now. But still facing this problem now and then.
Please find the output of given command as an attachment.
[HTML]cat /var/log/syslog | grep -e etwork -e eth1 | tail -n25  >  wifi.txt[/HTML]

And latest file "wireless-info.txt"

I have other ubuntu laptop(lenovo) which connect to same wifi without any problem always. 
Please help me to get rid of this problem.

Thanks in advance !

---

### Post by praseodym on 2014-04-23
Please run these commands:
```

sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
sudo service udev restart
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```
Check:
```

iwconfig
lsmod #completely!
sudo iwlist scan
iwlist chan
route -n
ifconfig -a
```

---

### Post by Irasad_Ahamad on 2014-04-24
Hi There,

I ran the above commands but situation didnt change.
Please the command result in an attachment. I am non technical person so couldnt understand them.

Thanks & Regards

---

### Post by praseodym on 2014-04-24
The interface name is still wlan0. Please run

```
sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
```
again, reboot and show the outputs again.

---

