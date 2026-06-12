---
title: "Broadcom wireless initially worked, now balky"
date: 2020-01-29
forum: Networking &amp; Wireless
---

### Post by davepool on 2020-01-29
I became a new member of this forum just a few weeks ago when I downloaded Ubuntu Budgie and installed in on my Lenovo ThinkPad X131e. That installation went without a hitch and for quite some time afterwards, I was able to go online for lots of stuff, not limited to package updates, downloads, email, YouTube, etc.

But yesterday my wireless connection went all balky on me.  The icons still show I'm connected to the wifi in the house, but I'm rarely getting more than 6 Mbps download (there are occasionally "burps" of connectivity up to 70+ Mbps).  Every time I try to load a web page, it times out and I get the screen telling me either the site is too busy or it has moved (yeah, right).

I can assure you that the problem is not with the wifi in the house: our phones are making wi-fi calls and connecting to the internet, so, too, is another laptop running Linux Mint and we're Chromecasting streaming video from Hulu Life without a hiccup.

When I hover the cursor over the wifi icon in the panel, it confirms connected and it shows the brcmsmac driver that I have seen there since the install.

Here's some more info:

 
  *-network                 
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0b1
       version: 01
       serial: 2c:d0:5a:01:5d:aa
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=5.3.0-26-generic firmware=610.812 ip=192.168.0.31 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0a00000-f0a03fff

I understand that certain Broadcom wireless cards can be real nightmares.  I'm puzzled by why this one would've worked just fine and then go cranky on me.  Apparently it hasn't crapped out on me...it's still working (or Ubuntu thinks it is).  I'm already thinking that another card (maybe Intel) would be at least one answer. I'd just like to see if there are any others.

---

### Post by jeremy31 on 2020-01-29
See the wireless script link in my signature and post results

---

### Post by davepool on 2020-01-30
> **jeremy31 said:**
> See the wireless script link in my signature and post results

Fair enough, @jeremy31...however, I'm stumbling a bit.

I've run through all the steps, installed pastebin and also have both the .txt file and the tar.gz archive stored locally (and was advised that the .txt. file exceeded the size permitted in the forum).  I do not see, however, a link in the terminal (which is still open, btw) "permitting you to paste it to a forum thread."

I also clicked on the link for pastebinit but that seems to require a login/join, etc...apparently pastebinit is something that runs in the background because even though it's now installed I don't find it in the GUI menu.

So, I think I have the files you requested...but I'm not sure on what to do with them or how.

Also, in reading ahead in your tutorial, even though I don't know yet "if Broadcom appears in the output next to [0280], head over to the Broadcom guide"...I can almost assure you that it does....because @chili555 was good enough to assist me in an earlier challenge and he pointed me to that very same guide, in which we discovered that I needed to follow Special Case #1 which, IIRC, ultimately got the correct brcmsmac driver installed for me (which is still there).

---

### Post by chili555 on 2020-01-30
I suggest that you paste the .txt here and give us the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by davepool on 2020-01-30
> **chili555 said:**
> I suggest that you paste the .txt here and give us the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)


The attempt to send the .txt produced this message:


[COLOR=#000000]Your submission could not be processed because a security token was missing.

If this occurred unexpectedly, please [inform the administrator]("https://ubuntuforums.org/sendmessage.php") and describe the action you performed before you received this error. If possible, please include the error page URL plus the date and time the error occured.

Tip : Please shorten long posts by using [https://paste.ubuntu.com/](https://paste.ubuntu.com/) for terminal and log output and link to it in your posts.
[/COLOR]
[COLOR=#000000]Ubuntu Forums[/COLOR]

---

### Post by davepool on 2020-01-30
> **chili555 said:**
> I suggest that you paste the .txt here and give us the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)


Here's the last screen of info from the process the forum requires:

Connecting to github.com (github.com)|140.82.114.3|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: **[https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)** [following]
--2020-01-30 08:31:35--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.196.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.196.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17452 (17K) [text/plain]
Saving to: ‘wireless-info’


wireless-info              100%[=====================================>]  17.04K  --.-KB/s    in 0.002s  


Last-modified header missing -- time-stamps turned off.
2020-01-30 08:31:36 (7.51 MB/s) - ‘wireless-info’ saved [17452/17452]




Results saved in "/home/dave/wireless-info.txt".


Results also archived in "/home/dave/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

*************************

Is the link I have put in boldface the link that's to be pasted to pastebinit?

---

### Post by chili555 on 2020-01-30
> **davepool said:**
> The attempt to send the .txt produced this message:


[COLOR=#000000]Your submission could not be processed because a security token was missing.

If this occurred unexpectedly, please [inform the administrator]("https://ubuntuforums.org/sendmessage.php") and describe the action you performed before you received this error. If possible, please include the error page URL plus the date and time the error occured.

Tip : Please shorten long posts by using [https://paste.ubuntu.com/](https://paste.ubuntu.com/) for terminal and log output and link to it in your posts.
[/COLOR]
[COLOR=#000000]Ubuntu Forums[/COLOR]Please check here: [https://paste.ubuntu.com/p/SsDQFPzyx6/](https://paste.ubuntu.com/p/SsDQFPzyx6/)

---

### Post by chili555 on 2020-01-30
> Results saved in "/home/dave/**wireless-info.txt**".Paste that and give us the link, please: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by davepool on 2020-01-30
> **chili555 said:**
> I suggest that you paste the .txt here and give us the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)


Very sorry, @chili555...I took you literally.  When you said "paste the .txt here" I thought that meant **here** in a message in this thread.  I did not understand it to be instructions to paste BOTH .txt and the link in pastebinit.

With any luck, I have now provided what you need....but LMK either way, please, because I really want to get the necessary info in your hands.

---

### Post by chili555 on 2020-01-30
> 
I really want to get the necessary info in your hands.
Likewise. May we please have the link?

---

### Post by davepool on 2020-01-30
> **chili555 said:**
> Likewise. May we please have the link?


Scroll up a few messages and see the one where I pasted the last screen of info from my terminal when I ran the whole process this morning. I've highlighted a link and asked if that's the one y'all are talking about. There was info in the instructions about how the script would be "...[LEFT][COLOR=#000000][FONT=Ubuntubeta]creating at the same time a link to it in your terminal..."

[LEFT][COLOR=#222222][FONT=Verdana]Well, that's what I see as a link in my terminal.  And I've pasted it and sent it.  But if that's not the right link, let me know what link I should be looking for (terminal is still open from this morning).[/FONT][/COLOR][/LEFT][B][I][U][SUB][SUP]
[/SUP][/SUB][/U][/I][/B][/FONT][/COLOR][/LEFT]

---

### Post by chili555 on 2020-01-30
> 
[https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)

That is the not so simple shell script that gathers the required information from your system when you actually run it. We need the results. Please open a terminal and do:```
pastebinit wireless-info.txt
```It will produce a link, aka URL like this: [https://paste.ubuntu.com/p/kcGdQR43qr/](https://paste.ubuntu.com/p/kcGdQR43qr/)

Please tell us what it s.

---

### Post by davepool on 2020-01-30
Just ran that command, got the link and pasted it to paste.ubunto.com

---

### Post by chili555 on 2020-01-30
> **davepool said:**
> Just ran that command, got the link and pasted it to paste.ubunto.comWe want the link right here in your reply, just like this:


[https://paste.ubuntu.com/p/kcGdQR43qr/](https://paste.ubuntu.com/p/kcGdQR43qr/)

---

### Post by davepool on 2020-01-30
> **chili555 said:**
> We want the link right here in your reply




[https://paste.ubuntu.com/p/x6sQ6XWNMH/](https://paste.ubuntu.com/p/x6sQ6XWNMH/)

---

### Post by chili555 on 2020-01-30
Let's try a few things. Please open a terminal and do:

```
sudo -i
modprobe -r ssb
modprobe -r b43
echo "blacklist ssb"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist b43"  >>  /etc/modprobe.d/blacklist.conf
exit
```Is your router set to a fixed channel 1 or is it set to auto channel select? Please be sure it is fixed.

I notice that you have both wireless and ethernet connected. Please detach the ethernet and tell us if there is any iimprovement.

---

### Post by davepool on 2020-01-31
Let me work backwards through your questions:

I have both ethernet and wireless attached because Jeremy31's instructions said at the very outset that everything that needed to be done there required a hardwire connection. The problems I've been having and reported in the first message were all without ethernet connected.  It has now been disconnected.

I have no idea if my router is set to a fixed channel or auto...but I suspect it's fixed because on the 1-2 occasions when I've had to use a utility on it, there was a list of channels and it showed which one.  In any case, nothing about that router has changed in the 2+ years we've lived in this house and there's been no previous problem with wifi until this particular device and even then only very recently.

I ran what you suggested...no change.  Web pages time out. "The site can't be reached" [LEFT][COLOR=#222222][FONT=Verdana]Though the network connection panel shows Signal Strength: Excellent and Link speed: 14Mb/s[/FONT][/COLOR][/LEFT]

I even re-booted. No change.

Then, in case your commands needed to be re-run after the re-start, I did them again.  No change. All pages time out.  Speed shown now as 72 Mb/s

---

### Post by chili555 on 2020-01-31
> I have both ethernet and wireless attached because Jeremy31's instructions said at the very outset that everything that needed to be done there required a hardwire connection. The problems I've been having and reported in the first message were all without ethernet connected. It has now been disconnected.

Excellent.

> I have no idea if my router is set to a fixed channel or auto...but I suspect it's fixed because on the 1-2 occasions when I've had to use a utility on it, there was a list of channels and it showed which one. In any case, nothing about that router has changed in the 2+ years we've lived in this house and there's been no previous problem with wifi until this particular device and even then only very recently.

Something obviously has changed. Perhaps not in the router, perhaps in the Ubuntu kernel, perhaps in the driver code, I simply don't know. All I am getting at here is to give your wireless the best possible environment in which to work correctly. 

Please go into the router's administrative pages and check the settings. While you are in there, here are some tips that have been extremely helpful in several other cases, including my own setup.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Also, please set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

> Then, in case your commands needed to be re-run after the re-start, I did them again. No change. All pages time out. Speed shown now as 72 Mb/s.

The commands need not be repeated. The changes are permanent unless we affirmatively reverse them.

Please run these commands and let us see the results:

```
ping -c3 www.google.com
dmesg | grep -e brcm -e wlp
```

---

### Post by davepool on 2020-01-31
Okay, here's the report:

WPA2-PSK [AES] is where it's set. That seemed close to what you said...I left it alone.

It *was* set to Auto (this is for the 2.4GHz channel) with it being, at this time, on 1.  But I changed it from Auto to 1

I saw 2.4GHz b/g/n which tells me it's not set for n speed only (correct?)

The reg domain was, as you suspected, set to 00.  It has now been permanently set to the correct country.


And here's the results of your two commands:

dave@ThinkPad-X131e:~$ ping -c3 [www.google.com](www.google.com)
ping: [www.google.com:](www.google.com:) Temporary failure in name resolution
 
dave@ThinkPad-X131e:~$ dmesg | grep -e brcm -e wlp
[   10.647046] brcmsmac bcma0:1: mfg 4bf core 812 rev 24 class 0 irq 17
[   10.649520] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 499
[   10.863698] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21f4.hcd failed with error -2
[   10.863713] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-21f4.hcd not found
[   11.559537] brcmsmac bcma0:1 wlp2s0b1: renamed from wlan0
[   22.817326] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   22.817353] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[   24.500949] wlp2s0b1: authenticate with 14:59:c0:84:e3:b3
[   24.501356] wlp2s0b1: send auth to 14:59:c0:84:e3:b3 (try 1/3)
[   24.503507] wlp2s0b1: authenticated
[   24.505746] wlp2s0b1: associate with 14:59:c0:84:e3:b3 (try 1/3)
[   24.521017] wlp2s0b1: RX AssocResp from 14:59:c0:84:e3:b3 (capab=0x1411 status=0 aid=6)
[   24.521495] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[   24.521511] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   24.521542] wlp2s0b1: associated
[   24.530118] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 159/256 dur 1778/1504
[   24.564475] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 137/256 dur 1602/1504
[   24.638604] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0b1: link becomes ready
[   27.518501] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[   52.468286] [UFW BLOCK] IN=wlp2s0b1 OUT= MAC= SRC=fe80:0000:0000:0000:6129:96a1:f772:1674 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=617079 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[   52.468405] [UFW BLOCK] IN=wlp2s0b1 OUT= MAC= SRC=fe80:0000:0000:0000:6129:96a1:f772:1674 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=919105 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[   52.478933] [UFW BLOCK] IN=wlp2s0b1 OUT= MAC= SRC=fe80:0000:0000:0000:6129:96a1:f772:1674 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=617079 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[   52.479042] [UFW BLOCK] IN=wlp2s0b1 OUT= MAC= SRC=fe80:0000:0000:0000:6129:96a1:f772:1674 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=919105 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[   76.529526] [UFW BLOCK] IN=wlp2s0b1 OUT= MAC=2c:d0:5a:01:5d:aa:c8:1f:66:0c:0d:e5:08:00 SRC=192.168.0.19 DST=192.168.0.31 LEN=44 TOS=0x00 PREC=0x00 TTL=128 ID=5575 PROTO=UDP SPT=50135 DPT=8612 LEN=24

---

### Post by chili555 on 2020-01-31
Everything looks perfect until:> 
dave@ThinkPad-X131e:~$ ping -c3 [www.google.com](www.google.com)
ping: [www.google.com:](www.google.com:) *Temporary failure in name resolution*
Let's try to see where it fails.Please run and post the result of:```

ping -c3 192.168.0.1
ping -c3 8.8.8.8
ping4 -c3 www.google.com

```I hope we see a clue in there!

---

### Post by davepool on 2020-01-31
> **chili555 said:**
> Everything looks perfect until:Let's try to see where it fails.Please run and post the result of:```

ping -c3 192.168.0.1
ping -c3 8.8.8.8
ping4 -c3 www.google.com

```I hope we see a clue in there!


[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]dave@ThinkPad-X131e:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2033ms[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]dave@ThinkPad-X131e:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.0.31 icmp_seq=1 Destination Host Unreachable
From 192.168.0.31 icmp_seq=2 Destination Host Unreachable
From 192.168.0.31 icmp_seq=3 Destination Host Unreachable[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2051ms
pipe 3
dave@ThinkPad-X131e:~$ ping4 -c3 [www.google.com](www.google.com)
ping4: [www.google.com:](www.google.com:) Temporary failure in name resolution[/FONT]

---

### Post by chili555 on 2020-01-31
> **davepool said:**
> [FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]dave@ThinkPad-X131e:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2033ms[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]dave@ThinkPad-X131e:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.0.31 icmp_seq=1 Destination Host Unreachable
From 192.168.0.31 icmp_seq=2 Destination Host Unreachable
From 192.168.0.31 icmp_seq=3 Destination Host Unreachable[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2051ms
pipe 3
dave@ThinkPad-X131e:~$ ping4 -c3 [www.google.com](www.google.com)
ping4: [www.google.com:](www.google.com:) Temporary failure in name resolution[/FONT]If you can't even ping the gateway (router) at 192.168.0.1, that suggests that you aren't actually connected. What does this report? ```
iwconfig
ip addr show wlp2s0b1

```

---

### Post by davepool on 2020-01-31
> **chili555 said:**
> If you can't even ping the gateway (router) at 192.168.0.1, that suggests that you aren't actually connected. What does this report? ```
iwconfig
ip addr show wlp2s0b1

```

And yet, every time I start up or re-start, the pop-up notification and then the icon in the tray all report that I'm connected. In fact, right now it shows active when I hover the cursor over it and then opening Connection information it's got all the info, including 65 Mb/s as the speed.

[FONT=Verdana]dave@ThinkPad-X131e:~$ iwconfig
enp3s0    no wireless extensions.[/FONT]
[FONT=Verdana]wlp2s0b1  IEEE 802.11  ESSID:"NETGEAR55"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 14:59:C0:84:E3:B3   
          Bit Rate=65 Mb/s   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:197  Invalid misc:9   Missed beacon:0[/FONT]
[FONT=Verdana]lo        no wireless extensions.[/FONT]
[FONT=Verdana]dave@ThinkPad-X131e:~$ ip addr show wlp2s0b1
3: wlp2s0b1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 2c:d0:5a:01:5d:aa brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.31/24 brd 192.168.0.255 scope global dynamic noprefixroute wlp2s0b1
       valid_lft 86231sec preferred_lft 86231sec
    inet6 fe80::6129:96a1:f772:1674/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
[/FONT]

---

### Post by chili555 on 2020-01-31
> [ 76.529526] [UFW BLOCK] IN=wlp2s0b1 OUT= MAC=2c:d0:5a:01:5d:aa:c8:1f:66:0c:0d:e5:08:00 SRC=192.168.0.19 DST=192.168.0.31 LEN=44 TOS=0x00 PREC=0x00 TTL=128 ID=5575 PROTO=UDP SPT=50135 DPT=8612 LEN=24

I notice a lot of messages in the log having to do with blocking by your firewall. Please try:```
sudo ufw disable
ping -c3 192.168.0.1
sudo ufw enable
```Any change/improvement/miracles?

> 
Tx excessive retries:*[COLOR="#FF0000"]197[/COLOR]* 
Studying...

---

### Post by davepool on 2020-01-31
> **chili555 said:**
> I notice a lot of messages in the log having to do with blocking by your firewall. Please try:```
sudo ufw disable
ping -c3 192.168.0.1
sudo ufw enable
```Any change/improvement/miracles?

Studying...


[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]dave@ThinkPad-X131e:~$ sudo ufw disable
[sudo] password for dave: 
Firewall stopped and disabled on system startup
dave@ThinkPad-X131e:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2055ms[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]dave@ThinkPad-X131e:~$ sudo ufw enable
Firewall is active and enabled on system startup[/FONT]

---

### Post by davepool on 2020-01-31
Separate thought: I'm reading that as many millions of laptops as there are around the world with Broadcom cards, some of them (not sure if it's specific models or just random production errors) are just beasts. The web is full of "as soon as I got rid of the Broadcom card it came with...." messages.  Hard to miss 'em.  I'm also seeing that an Intel card for this specific ThinkPad can be bought for $20 (and a buddy has told me he replaced a card once with a rather "generic" card that he got for $10...but I think he was lucky that it was compatible because I'm also told that some manufacturers have a very tight "whitelist" of wireless cards).

All to say that I'm already prepared to find this is the only way out.

---

### Post by chili555 on 2020-02-01
> **davepool said:**
> Separate thought: I'm reading that as many millions of laptops as there are around the world with Broadcom cards, some of them (not sure if it's specific models or just random production errors) are just beasts. The web is full of "as soon as I got rid of the Broadcom card it came with...." messages.  Hard to miss 'em.  I'm also seeing that an Intel card for this specific ThinkPad can be bought for $20 (and a buddy has told me he replaced a card once with a rather "generic" card that he got for $10...but I think he was lucky that it was compatible because I'm also told that some manufacturers have a very tight "whitelist" of wireless cards).

All to say that I'm already prepared to find this is the only way out.I am not at all convinced that the wireless card itself is the fault here. You have the curious circumstance of appearing, by all accounts, to be connected and yet you cannot ping any site including the gateway (router) that you are apparently connected to.

Will you please click the Network Manager icon and turn on Airplane Mode so as to disable, temporarily, the wireless. Then connect the ethernet and try again:```
ping -c3 192.168.0.1
ping -c3 8.8.8.8
ping4 -c3 www.google.com
```

---

### Post by davepool on 2020-02-01
> **chili555 said:**
> I am not at all convinced that the wireless card itself is the fault here. You have the curious circumstance of appearing, by all accounts, to be connected and yet you cannot ping any site including the gateway (router) that you are apparently connected to.

Will you please click the Network Manager icon and turn on Airplane Mode so as to disable, temporarily, the wireless. Then connect the ethernet and try again:```
ping -c3 192.168.0.1
ping -c3 8.8.8.8
ping4 -c3 www.google.com
```

For whatever reason, the ethernet connection keeps cycling from Connecting 1000 Mb/s to Disconnected.  When I try to use the terminal with Airplane Mode engaged, I get what you see in the first lines below. When I turned Airplane Mode off (which I know is not what you asked...but I wanted to get you *something* in the way of results), everything after those first two lines is what came back:

[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]dave@ThinkPad-X131e:~$ ping -c3 192.168.0.1
ping: connect: Network is unreachable

[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]dave@ThinkPad-X131e:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=680 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=5.94 ms[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]--- 192.168.0.1 ping statistics ---
3 packets transmitted, 2 received, 33.3333% packet loss, time 2028ms
rtt min/avg/max/mdev = 5.944/343.212/680.480/337.268 ms
dave@ThinkPad-X131e:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=56 time=120 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=56 time=65.8 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=56 time=35.9 ms[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 35.900/74.029/120.423/34.997 ms
dave@ThinkPad-X131e:~$ ping4 -c3 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (172.217.11.164) 56(84) bytes of data.
64 bytes from lax28s15-in-f4.1e100.net (172.217.11.164): icmp_seq=3 ttl=56 time=162 ms[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]--- [www.google.com](www.google.com) ping statistics ---
3 packets transmitted, 1 received, 66.6667% packet loss, time 2016ms
rtt min/avg/max/mdev = 161.959/161.959/161.959/0.000 ms
[/FONT]

---

### Post by davepool on 2020-02-01
> **chili555 said:**
> I am not at all convinced that the wireless card itself is the fault here. You have the curious circumstance of appearing, by all accounts, to be connected and yet you cannot ping any site including the gateway (router) that you are apparently connected to.

Will you please click the Network Manager icon and turn on Airplane Mode so as to disable, temporarily, the wireless. Then connect the ethernet and try again:```
ping -c3 192.168.0.1
ping -c3 8.8.8.8
ping4 -c3 www.google.com
```

Wait! Success! I got the ethernet to work.  So, with the wifi off because it was in Airplane Mode, here are the results from the same commands:

[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]dave@ThinkPad-X131e:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=2.58 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.18 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=1.18 ms[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 1.176/1.646/2.583/0.662 ms
dave@ThinkPad-X131e:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=56 time=31.9 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=56 time=28.6 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=56 time=28.8 ms[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 28.597/29.750/31.894/1.517 ms
dave@ThinkPad-X131e:~$ ping4 -c3 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (172.217.14.100) 56(84) bytes of data.
64 bytes from lax31s01-in-f4.1e100.net (172.217.14.100): icmp_seq=1 ttl=56 time=27.9 ms
64 bytes from lax31s01-in-f4.1e100.net (172.217.14.100): icmp_seq=2 ttl=56 time=30.1 ms
64 bytes from lax31s01-in-f4.1e100.net (172.217.14.100): icmp_seq=3 ttl=56 time=28.7 ms[/FONT]
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]--- [www.google.com](www.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 27.934/28.923/30.132/0.910 ms[/FONT]

---

### Post by chili555 on 2020-02-02
> For whatever reason, the ethernet connection keeps cycling from Connecting 1000 Mb/s to Disconnected.

> 3 packets transmitted, 2 received, **33.3333% packet loss,** time 2028ms

> 3 packets transmitted, 1 received, **66.6667% packet loss,** time 2016ms

> Wait! Success! I got the ethernet to work. 

Isn't it at all suspicious that, at times, BOTH the wireless AND the ethernet are, as you say, balky?? Are any other devices connected to the same network "balky" at tiimes? Could this be an issue at the router? 

The fact that the ethernet correctly pings the router and [www.google.com](www.google.com) seems to rule out any DNS configuration issue in your Ubuntu computer.

---

### Post by davepool on 2020-02-02
> **chili555 said:**
> Isn't it at all suspicious that, at times, BOTH the wireless AND the ethernet are, as you say, balky?? Are any other devices connected to the same network "balky" at tiimes? Could this be an issue at the router? 

The fact that the ethernet correctly pings the router and [www.google.com]("http://www.google.com") seems to rule out any DNS configuration issue in your Ubuntu computer.

The ethernet "problem" was solved by simply plugging the router end of the cable into another one of the ports available there. This was the cable I needed to temporarily connect to the ThinkPad...and not the cable that's always in place for my PC.

Otherwise, I'll just say again that 3 other laptops, two tablets, two phones and one smart TV have (and have had....for years) no problem with connecting to this router or getting enough signal for full operation. My desktop PC has forever been connected to this same router via what was (until a few days ago when I needed to hardwire connect the ThinkPad per Jeremy31's tutorial instructions) the only hardwire connection to it. 

It has only been *this* laptop and, even then, only in the past 10 days or so.  So....yeah....it's a stumper.

---

### Post by chili555 on 2020-02-03
Please interrupt the boot process and get to the GRUB menu. Boot into an earlier kernel version and tell us if the problem persists.

[https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time](https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time)

If the problem remains, I have no further ideas and then you might try an Intel. I use and recommend the 7260 B/G/N/AC.

---

### Post by davepool on 2020-02-03
From the looks of that thread, it appears to be a real trail-and-error process. But I'll give it a go! Does Ubuntu not offer the handy tools to switch kernels that some other distros have?

If I go the card-replacement route, from what I've found on ebay, the Intel card for my ThinkPad X131e is the Centrino N-6205

---

### Post by davepool on 2020-02-03
> **chili555 said:**
> Please interrupt the boot process and get to the GRUB menu. Boot into an earlier kernel version and tell us if the problem persists.

[https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time](https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time)

If the problem remains, I have no further ideas and then you might try an Intel. I use and recommend the 7260 B/G/N/AC.

Okay, here's what happened: I booted into a version with 5.3.0-18.generic (there were others but that seemed "right") and I confirmed that was the one installed via uname -r

No change.

Then, as an extra step, I decided to plug in the USB I have for 18.04.3 LTS (which goes farther back than the 19.10 that's hard installed) and run Ubuntu live from it.  Same thing as always, actually...the wireless icon says I'm connected, says I'm using the brcmsmac driver....but shows only 6 Mb/s and every URL times out.

Sooo....is that even more evidence, then, that it's the card?

---

### Post by CelticWarrior on 2020-02-03
> **davepool said:**
> Sooo....is that even more evidence, then, that it's the card?

Yes, it feels like an hardware issue, IMO.

At this pint I would be checking the antennae connections and/or re-seating the card itself but you may not be comfortable doing it.

---

### Post by davepool on 2020-02-03
> **CelticWarrior said:**
> Yes, it feels like an hardware issue, IMO.

At this pint I would be checking the antennae connections and/or re-seating the card itself but you may not be comfortable doing it.


One day last week I did pop the back off and have a look-see. The two connections were on but I did not pull the card and re-seat it. If I'm considering a new one, I guess I'm gonna be pulling it sooner or later so, why not now, huh?

---

### Post by chili555 on 2020-02-04
> From the looks of that thread, it appears to be a real trail-and-error process. We who frequently answer threads here have but a few tools at our disposal; past experience, reviewing logs (primarily dmesg), and trial and error. None of us are developers or kernel hackers.

I'm sorry if this whole process appears a bit amateurish, but that's really who we are here: amateurs.

---

### Post by davepool on 2020-02-07
> **chili555 said:**
> We who frequently answer threads here have but a few tools at our disposal; past experience, reviewing logs (primarily dmesg), and trial and error. None of us are developers or kernel hackers.

I'm sorry if this whole process appears a bit amateurish, but that's really who we are here: amateurs.

[SIZE=3][FONT=arial]Sorry, I didn't see this earlier...omigosh, no, that certainly wasn't what I was suggesting and I apologize if that was the impression I gave you.  I very much appreciate all of the assistance from everyone. I was just reacting to what was being conveyed...and my assumption was that this process is exactly what you guys go through, too...which I think you've confirmed! :KS  Kinda like the test pilots in "The Right Stuff" (the book): "I tried A, I tried B...."

Anyway, @chili555 and @CelticWarrior, I wonder if we can revisit this.  There might be some signs that the wireless card is not the problem here (or at least it might not be faulty enough to warrant replacing it...but what do I know?).  Why do I say that?

[/FONT][/SIZE][COLOR=#121112][FONT=&quot][SIZE=3][FONT=arial]Last night, I decided to see what other evidence I might have -- either way -- that this device actually works and that something else is getting in the way.[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#121112][FONT=&quot][SIZE=3][FONT=arial]I happen to have a USB that contains a live iso snapshot of my running MX Linux system that I have on my Acer Aspire (courtesy of the simple MX Snapshot tool which all distros should emulate, IMHO)

[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#121112][FONT=&quot][SIZE=3][FONT=arial]I plugged it into the ThinkPad, booted from it...and guess what? My ThinkPad connected happily to my home wifi, loaded up [nbcnews.com]("http://nbcnews.com/") with the latest news and played a video on YouTube smoothly without breakup or buffering.


Anticipating the first questions you might have: 

[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#121112][FONT=&quot][SIZE=3][FONT=arial]kernel release is 4.19.0-6-amd64
kernel version is #1 SMP Debian 4.19.67-2+deb10u2 (2019-11-11)

[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#121112][FONT=&quot][SIZE=3][FONT=arial]What follows is way too much information, I know....sorry, it's the command I knew to use:[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#121112][FONT=&quot]
dave@acer:~
```
$ sudo lshw
acer
description: Notebook
product: AO722 (123456789)
vendor: Acer
version: V1.06
serial: LUSFT021711431E0421601
width: 64 bits
capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
configuration: boot=normal chassis=notebook family=Type1Family sku=123456789 uuid=2CAC470C-F3BC-11E0-B7C0-DC0EA108D1FB
*-core
description: Motherboard
product: JE10-BZ
vendor: Acer
physical id: 0
version: Base Board Version
serial: Base Board Serial Number
slot: Base Board Chassis Location
*-firmware
description: BIOS
vendor: Acer
physical id: 0
version: V1.06
date: 09/19/2011
size: 1MiB
capacity: 2MiB
capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
*-memory
description: System Memory
physical id: 24
slot: System board or motherboard
size: 2GiB
capacity: 2GiB
*-bank:0
description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
product: NT2GC64B88B0NS-CG
vendor: Nanya Technology
physical id: 0
serial: EE022924
slot: DIMM0
size: 2GiB
width: 8 bits
clock: 1066MHz (0.9ns)
*-bank:1
description: SODIMM Synchronous [empty]
physical id: 1
slot: DIMM1
width: 8 bits
*-cpu
description: CPU
product: AMD C-60 APU with Radeon(tm) HD Graphics
vendor: Advanced Micro Devices [AMD]
physical id: 2c
bus info: cpu@0
version: AMD C-60 APU with Radeon(tm) HD Graphics
serial: NotSupport
slot: Socket FT1
size: 907MHz
capacity: 1GHz
width: 64 bits
clock: 100MHz
capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt cpb hw_pstate vmmcall arat npt lbrv svm_lock nrip_save pausefilter cpufreq
configuration: cores=2 enabledcores=2 threads=2
*-cache:0
description: L1 cache
physical id: 2d
slot: L1 Cache
size: 128KiB
capacity: 128KiB
capabilities: pipeline-burst internal write-back unified
configuration: level=1
*-cache:1
description: L2 cache
physical id: 2e
slot: L2 Cache
size: 1MiB
capacity: 1MiB
capabilities: pipeline-burst internal write-back unified
configuration: level=2
*-pci:0
description: Host bridge
product: Family 14h Processor Root Complex
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 100
bus info: pci@0000:00:00.0
version: 00
width: 32 bits
clock: 66MHz
*-display
description: VGA compatible controller
product: Wrestler [Radeon HD 6290]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 1
bus info: pci@0000:00:01.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=radeon latency=0
resources: irq:24 memory:80000000-8fffffff ioport:4000(size=256) memory:90400000-9043ffff memory:c0000-dffff
*-multimedia:0
description: Audio device
product: Wrestler HDMI Audio
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 1.1
bus info: pci@0000:00:01.1
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm pciexpress msi bus_master cap_list
configuration: driver=snd_hda_intel latency=0
resources: irq:25 memory:90444000-90447fff
*-sata
description: SATA controller
product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 11
bus info: pci@0000:00:11.0
logical name: scsi0
version: 00
width: 32 bits
clock: 66MHz
capabilities: sata ahci_1.0 bus_master cap_list emulated
configuration: driver=ahci latency=64
resources: irq:19 ioport:4118(size=8) ioport:4124(size=4) ioport:4110(size=8) ioport:4120(size=4) ioport:4100(size=16) memory:9044c000-9044c3ff
*-disk
description: ATA Disk
product: WDC WD3200BPVT-2
vendor: Western Digital
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: 1A01
serial: WD-WXQ1E61CLVZY
size: 298GiB (320GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=0a08e77d
*-volume:0
description: EXT4 volume
vendor: Linux
physical id: 1
bus info: scsi@0:0.0.0,1
logical name: /dev/sda1
logical name: /
version: 1.0
serial: 17bec310-1d1c-4eeb-8e2b-451589b64a33
size: 296GiB
capacity: 296GiB
capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
configuration: created=2019-10-27 09:58:10 filesystem=ext4 label=rootMX19 lastmountpoint=/ modified=2020-02-06 21:55:08 mount.fstype=ext4 mount.options=rw,relatime mounted=2020-02-06 21:55:22 state=mounted
*-volume:1
description: Linux swap volume
physical id: 2
bus info: scsi@0:0.0.0,2
logical name: /dev/sda2
version: 1
serial: f4c94cbc-c0ac-48fc-b676-68e67926316b
size: 2GiB
capacity: 2GiB
capabilities: primary swap initialized
configuration: filesystem=swap label=swapMX pagesize=4096
*-usb:0
description: USB controller
product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 12
bus info: pci@0000:00:12.0
version: 00
width: 32 bits
clock: 66MHz
capabilities: ohci bus_master
configuration: driver=ohci-pci latency=64
resources: irq:18 memory:9044b000-9044bfff
*-usb:1
description: USB controller
product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 12.2
bus info: pci@0000:00:12.2
version: 00
width: 32 bits
clock: 66MHz
capabilities: pm debug ehci cap_list
configuration: driver=ehci-pci latency=64
resources: irq:17 memory:9044a000-9044a0ff
*-usb:2
description: USB controller
product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 13
bus info: pci@0000:00:13.0
version: 00
width: 32 bits
clock: 66MHz
capabilities: ohci bus_master
configuration: driver=ohci-pci latency=64
resources: irq:18 memory:90449000-90449fff
*-usb:3
description: USB controller
product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 13.2
bus info: pci@0000:00:13.2
version: 00
width: 32 bits
clock: 66MHz
capabilities: pm debug ehci cap_list
configuration: driver=ehci-pci latency=64
resources: irq:17 memory:90448000-904480ff
*-serial
description: SMBus
product: SBx00 SMBus Controller
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 14
bus info: pci@0000:00:14.0
version: 42
width: 32 bits
clock: 66MHz
configuration: driver=piix4_smbus latency=0
resources: irq:0
*-multimedia:1
description: Audio device
product: SBx00 Azalia (Intel HDA)
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 14.2
bus info: pci@0000:00:14.2
version: 40
width: 64 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=snd_hda_intel latency=64
resources: irq:16 memory:90440000-90443fff
*-isa
description: ISA bridge
product: SB7x0/SB8x0/SB9x0 LPC host controller
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 14.3
bus info: pci@0000:00:14.3
version: 40
width: 32 bits
clock: 66MHz
capabilities: isa bus_master
configuration: latency=0
*-pci:0
description: PCI bridge
product: SBx00 PCI to PCI Bridge
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 14.4
bus info: pci@0000:00:14.4
version: 40
width: 32 bits
clock: 66MHz
capabilities: pci subtractive_decode bus_master
*-pci:1
description: PCI bridge
product: SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 15
bus info: pci@0000:00:15.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:16 ioport:3000(size=4096) memory:90300000-903fffff ioport:90000000(size=1048576)
*-pci:2
description: PCI bridge
product: SB900 PCI to PCI bridge (PCIE port 2)
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 15.2
bus info: pci@0000:00:15.2
version: 00
width: 32 bits
clock: 33MHz
capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:16 ioport:2000(size=4096) memory:90200000-902fffff
*-network
description: Ethernet interface
product: AR8152 v2.0 Fast Ethernet
vendor: Qualcomm Atheros
physical id: 0
bus info: pci@0000:06:00.0
logical name: eth0
version: c1
serial: dc:0e:a1:08:d1:fb
capacity: 100Mbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
resources: irq:26 memory:90200000-9023ffff ioport:2000(size=128)
*-pci:3
description: PCI bridge
product: SB900 PCI to PCI bridge (PCIE port 3)
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 15.3
bus info: pci@0000:00:15.3
version: 00
width: 32 bits
clock: 33MHz
capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:16 memory:90100000-901fffff
*-network
description: Wireless interface
product: BCM4313 802.11bgn Wireless Network Adapter
vendor: Broadcom Limited
physical id: 0
bus info: pci@0000:07:00.0
logical name: wlan0
version: 01
serial: 60:d8:19:7f:d3:fc
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) ip=192.168.0.22 latency=0 multicast=yes wireless=IEEE 802.11
resources: irq:19 memory:90100000-90103fff
*-pci:1
description: Host bridge
product: Family 12h/14h Processor Function 0
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 101
bus info: pci@0000:00:18.0
version: 43
width: 32 bits
clock: 33MHz
*-pci:2
description: Host bridge
product: Family 12h/14h Processor Function 1
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 102
bus info: pci@0000:00:18.1
version: 00
width: 32 bits
clock: 33MHz
*-pci:3
description: Host bridge
product: Family 12h/14h Processor Function 2
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 103
bus info: pci@0000:00:18.2
version: 00
width: 32 bits
clock: 33MHz
*-pci:4
description: Host bridge
product: Family 12h/14h Processor Function 3
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 104
bus info: pci@0000:00:18.3
version: 00
width: 32 bits
clock: 33MHz
configuration: driver=k10temp
resources: irq:0
*-pci:5
description: Host bridge
product: Family 12h/14h Processor Function 4
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 105
bus info: pci@0000:00:18.4
version: 00
width: 32 bits
clock: 33MHz
*-pci:6
description: Host bridge
product: Family 12h/14h Processor Function 6
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 106
bus info: pci@0000:00:18.5
version: 00
width: 32 bits
clock: 33MHz
*-pci:7
description: Host bridge
product: Family 12h/14h Processor Function 5
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 107
bus info: pci@0000:00:18.6
version: 00
width: 32 bits
clock: 33MHz
*-pci:8
description: Host bridge
product: Family 12h/14h Processor Function 7
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 108
bus info: pci@0000:00:18.7
version: 00
width: 32 bits
clock: 33MHz
*-pnp00:00
product: PnP device PNP0c02
physical id: 1
capabilities: pnp
configuration: driver=system
*-pnp00:01
product: PnP device PNP0b00
physical id: 2
capabilities: pnp
configuration: driver=rtc_cmos
*-pnp00:02
product: PnP device PNP0303
physical id: 3
capabilities: pnp
configuration: driver=i8042 kbd
*-pnp00:03
product: PnP device ETD0500
physical id: 4
capabilities: pnp
configuration: driver=i8042 aux
*-pnp00:04
product: PnP device PNP0c02
physical id: 5
capabilities: pnp
configuration: driver=system
*-pnp00:05
product: PnP device PNP0c01
physical id: 6
capabilities: pnp
configuration: driver=system
```

[/FONT][/COLOR]
[COLOR=#121112][FONT=&quot][SIZE=3][FONT=arial]If I've missed anything, just let me know how to fetch it and I will.[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by tea for one on 2020-02-07
I'm pretty sure that MX Linux have an agreement with Broadcom which allows the inclusion of Broadcom packages/drivers in the MX Linux kernel.

Possibly, MX Linux also have some special Broadcom assistance that is not available to Ubuntu. 

Unfortunately, I can't find the exact internet page where I saw this.

Therefore an MX Linux snapshot would include the Broadcom additions automatically.

The MX snapshot utility from a running system is a fun tool to explore. 

I have an early 2016 HP Stream 11 which uses a Broadcom wireless chip and I have installed MX Linux 19 snapshot specifically to enable the Broadcom wireless (No ethernet port on my HP Stream 11}

However, there can be a slowish connection if you stray too far from the router.

---

### Post by davepool on 2020-02-08
If that's true about MX Linux and Broadcom, it would sure explain it. For sure, this BCM-4313 creates a lot of grief for a lot of people (but, in truth, that's a reflection of the comments and the help I received from the Manjaro community [the other half of this dual-boot] and may be true, too, for Ubuntu). I'm not opposed to popping for another wireless card...and I was gonna get an Intel card that's ID'd as correct for the ThinkPad X131e...but I'm told that Intel cards are also prone to problems and that swapping Broadcom for Intel may not cure my headaches.

If your info is correct...I wonder if the expedient thing for this particular $40 laptop find isn't to install MX Linux and just be done with it...leaving it with a distro install that's about as good as things can get with the BCM-4313.

And, yeah, that MX Linux Snapshot tool is brilliant!

---

### Post by davepool on 2020-02-09
tea for one, I went to the MX Linux Forum (since, as I reported, I run that distro on an Acer Aspire One) and conveyed my improved experience on the ThinkPad X131e (compared to when I booted from my MX Linux Snapshot USB compared to what I'd been getting with Ubuntu and the wireless drivers it installs. I heard directly from two of their developers and, while I don't know about any agreement or special assistance, they *do* ship with proprietary Broadcom drivers that they said specifically work with the BCM-4313.

I made the decision to juggle around some of my distros and install my MX snapshot on the ThinkPad....and voila! Instant wireless connectivity and massively improved download and upload speeds compared to what I was getting when Ubuntu was on it (that is, when there was even enough signal to load a web page and not get time outs!  So I really appreciate your "heads up" on this!

In the Manjaro forum (the other distro in the dual-boot that was facing the same problem with the BCM-4313) I was even getting strong suggestion that I needed to flash the BIOS.  Yikes! To the credit of the Ubuntu forum, I don't recall anyone suggesting going quite that far (which was waaaaay out of my comfort zone and, as it turned out, was like the old expression "driving a nail with a sledgehammer!). But your info (leading to my decision to put MX Linux on the ThinkPad) cured the problem without flashing the BIOS or even replacing the wireless card...so thanks very much!  I'll see if I can put Ubuntu Budgie on another device.

---

### Post by tea for one on 2020-02-09
I had a look at your thread on the MX Linux forum and your desire to find a practical solution is admirable.

The answer supplied on the MX Linux forum stated > we ship with both the free-but-proprietary broadcom-sta drivers and the opensource b43* drivers. On first boot of the live system, we make a decision about which driver to enable based on known broadcom parts. usually, but not always, the broadcom-sta drivers are selected to be used. Yet they also stated that Ubuntu will install the same driver after installation.

I have found that my HP Stream (Broadcom 43142) suffers fewer connection interruptions with MX Linux than Ubuntu/Xubuntu although the **same** driver is used. I really do **not** understand this outcome but, like you, I use MX Linux on this HP Netbook purely for improved wireless connectivity.

Anyway, it is interesting that you have reached the same conclusion as I did and I am pleased that I was able to provide some sort of pointer.

Best wishes

---

### Post by jeremy31 on 2020-02-09
In Ubuntu Network Manager has the ability to enable wifi power management and this can cause issues, to disable run these 2 commands in terminal
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

[https://forum.mxlinux.org/viewtopic.php?f=107&t=56062&p=558474&hilit=broadcom#p558458](https://forum.mxlinux.org/viewtopic.php?f=107&t=56062&p=558474&hilit=broadcom#p558458)

The statement about the open source drivers not working with the BCM4313 is false in some cases as mine worked fine with bcma and brcmsmac modules from the kernel

---

