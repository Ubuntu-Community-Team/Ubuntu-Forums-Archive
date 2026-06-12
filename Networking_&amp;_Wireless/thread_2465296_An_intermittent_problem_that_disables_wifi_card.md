---
title: "An intermittent problem that disables wifi card"
date: 2021-07-28
forum: Networking &amp; Wireless
---

### Post by williepabon on 2021-07-28
Hi:
This is a problem that has been occurring for some time now. For some inexplicable reason, the computer disconnects from my local wifi and  looses Internet connectivity. This behavior is erratic. Some times it occurs two or three times on the same day, But other times, two or three days may pass without experiencing the problem. I discounted the possibility of a defective wifi card because my machine works Ok when running on Mac OS. To restore the computer to normal operation, I have to do a restart. If I reset the wifi card instead, the computer freezes and need to do a cold boot. Following, is the information I've gathered from my system that I hope should help to find out what the problem is.

Information about my networking hardware:

```
williepabon@williepabon-Macmini:~$ sudo lshw -C network
[sudo] password for williepabon: 
  *-network                 
       description: Ethernet interface
       product: NetXtreme BCM57766 Gigabit Ethernet PCIe
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0f0
       version: 01
       serial: 10:dd:b1:99:74:4b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=57766a-v1.13 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:a0400000-a040ffff memory:a0410000-a041ffff
  *-network
       description: Wireless interface
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 02
       serial: 88:53:95:30:a8:bb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) ip=192.168.1.192 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:a0600000-a0603fff


```

When the machine is operating normally and connected to the Internet:

```
williepabon@williepabon-Macmini:~$ nmcli general
STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
connected  full          enabled  enabled  enabled  enabled 

williepabon@williepabon-Macmini:~$ nmcli dev status
DEVICE             TYPE      STATE         CONNECTION 
wlp2s0             wifi      connected     BeckyNet   
60:B7:6E:11:DA:72  bt        disconnected  --         
enp1s0f0           ethernet  unavailable   --         
lo                 loopback  unmanaged     --         
williepabon@williepabon-Macmini:~$ 

williepabon@williepabon-Macmini:~$ nmcli dev wifi list
IN-USE  BSSID              SSID                        MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
        32:C9:AB:96:E9:C8  DIRECT-MAHL-L2350DW_BRe9c8  Infra  6     65 Mbit/s   87      &#9602;&#9604;&#9606;&#9608;  WPA2     
*       76:69:42:8C:87:B0  BeckyNet                    Infra  44    540 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2     
        10:0C:6B:39:EF:7F  SarmientoFamily_2GEXT       Infra  1     270 Mbit/s  30      &#9602;___  WPA2     
        F0:72:EA:54:0D:E2  Sarmientofamily2            Infra  1     130 Mbit/s  29      &#9602;___  WPA2     
        B0:E4:D5:59:57:2F  Sarmientofamily2            Infra  11    130 Mbit/s  20      &#9602;___  WPA2     
        16:91:7F:89:C4:4A  SarmientoFamily             Infra  1     540 Mbit/s  17      &#9602;___  WPA2     

```

When wifi connectivity is lost:

```
williepabon@williepabon-Macmini:~$ nmcli general
STATE                  CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN    
connected (site only)  limited       enabled  enabled  enabled  enabled 

williepabon@williepabon-Macmini:~$ nmcli dev status
DEVICE             TYPE      STATE         CONNECTION 
wlp2s0             wifi      connected     BeckyNet   
60:B7:6E:11:DA:72  bt        disconnected  --         
enp1s0f0           ethernet  unavailable   --         
lo                 loopback  unmanaged     --         

williepabon@williepabon-Macmini:~$ nmcli dev wifi list
IN-USE  BSSID              SSID      MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
*       76:69:42:8C:87:B0  BeckyNet  Infra  44    540 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  WPA2     


```

Thank you in advance to any advice/suggestions that may help to solve this problem. If further information about my system is required, please, let me know. Thanks.

---

### Post by TheFu on 2021-07-31
Check the power-saving settings for the system and for the wifi adapter.
**iwconfig** is one command to control those settings. To disable power management, this command:
```
sudo iwconfig wlp2s0 power off
sudo iwconfig wlp2s0 commit
```
should work.

The manpage section for iwconfig:
```
       power  Used to manipulate power management scheme parameters and mode.
              To set the period between wake ups, enter period  `value'.   To
              set  the  timeout  before  going  back  to sleep, enter timeout
              `value'.  To set the generic level of power saving, enter  sav&#8208;
              ing  `value'.   You  can also add the min and max modifiers. By
              default, those values are in seconds, append the suffix m or  u
              to  specify  values in milliseconds or microseconds. Sometimes,
              those values are  without  units  (number  of  beacon  periods,
              dwell, percentage or similar).
              off  and on disable and reenable power management. Finally, you
              may set the power management mode to all (receive all packets),
              unicast  (receive  unicast  packets only, discard multicast and
              broadcast) and multicast (receive multicast and broadcast only,
              discard unicast packets).
```

  May need to disable/re-enable the entire card after changing settings according to the manpage. Different cards work differently.

---

### Post by williepabon on 2021-07-31
[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685"):

Thanks for answering.  For your info, following is my current configuration. 
```
williepabon@williepabon-Macmini:~$ sudo iwconfig wlp2s0
wlp2s0    IEEE 802.11  ESSID:"BeckyNet"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: 76:69:42:8C:87:B0   
          Bit Rate=450 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I'm going to implement your recommendations and will let you know if they solve my problem. Thanks again.

---

### Post by williepabon on 2021-07-31
[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685"):

I ran the commands as per your suggestion and it worked ok as shown:
```
williepabon@williepabon-Macmini:~$ sudo iwconfig wlp2s0
wlp2s0    IEEE 802.11  ESSID:"BeckyNet"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: 76:69:42:8C:87:B0   
          Bit Rate=450 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

My problem now is that after I reboot the computer the Power management reverts back to on. How do I make the change permanent? Thanks.

---

### Post by TheFu on 2021-07-31
Until you leave this setup this way a few days and it actually is proven to fix the issue, I wouldn't.
I don't use wifi much. It is never to be trusted - both performance and security. That includes wifi-6, the newest standard has security issues that have been known over a year.

I would setup the netplan.yaml file with the settings, but it is unlikely that you are using that to manage connections. On pre-netplan systems, there was a pre-up option in the "interfaces" file.
Google found these answers: [https://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on](https://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on)

---

### Post by williepabon on 2021-07-31
[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685"):

Thanks for the advice. I will turn Power Manager setting  off with the iwconfig  command every morning for two or three days to see if the problem actually disappears. Then, I would do the changes on the /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf file to make it permanent. Thamks again.

---

### Post by williepabon on 2021-07-31
**TheFu:**

I started  this afternoon doing my test with Power Manager settings to Off, but unfortunately, the problem came up again. Some other thing is causing this fail. I wish there should be a way to monitor the machine in such a way to capture the instant of the failure. Maybe the logs could tell us what would be causing this issue. Any ways, I appreciate any other advice you may provide. Thanks.

---

### Post by ActionParsnip on 2021-08-01
Try rebooting your router as well.

---

### Post by wildmanne39 on 2021-08-01
Moved to Networking and Wireless.

---

### Post by williepabon on 2021-08-16
ActionParsnip:

Thanks for your suggestion, but no, that didn't solve my problem, either. On the other hand, none of the other machines in my network experiences the problem.

---

### Post by chili555 on 2021-08-16
I'm not quite sure that you have the correct driver. [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by williepabon on 2021-08-20
**chili555:**

Thanks for answering. First of all, I do not consider myself capable enough, yet, to do any driver modification. The driver software that is installed in my system is the one that was installed by the OS. But I know it is proprietary, as shown on the attachment. Running the code suggested:

```
williepabon@williepabon-Macmini:~$ lspci -nn -d 14e4:
01:00.0 Ethernet controller [0200]: Broadcom Inc. and subsidiaries NetXtreme BCM57766 Gigabit Ethernet PCIe [14e4:1686] (rev 01)
01:00.1 SD Host controller [0805]: Broadcom Inc. and subsidiaries BCM57765/57785 SDXC/MMC Card Reader [14e4:16bc] (rev 01)
02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)

```

I read the post you suggested and will welcome any advice to implement it. Thanks again.
wp

---

### Post by chili555 on 2021-08-20
> welcome any advice to implement it.Please open a terminal and do:```
sudo apt update
sudo apt install firmware-b43-installer
sudo apt purge bcmwl-kernel-source
```Reboot and let us hear your result. Is the performance improved?

There are several examples where the Additional Drivers window suggests the wrong driver; I believe this is one of them.

---

### Post by williepabon on 2021-08-21
[COLOR=#ff0000][B]chili555:
[/B][/COLOR]
Thanks for the instruction. I'm going to try it today and will let you know what happens. Thanks.
wp

---

### Post by williepabon on 2021-08-21
chili555:

Bad news! After changing the driver, now the card only recognizes the 2.4 Gig band. It doesn't connect to the 5.2 Gig wifi. My wifi speed went down from 200 Mbps to about 20 Mbps. See below.

```
williepabon@williepabon-Macmini:~$ nmcli dev wifi list
IN-USE  BSSID              SSID                        MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
        32:C9:AB:96:E9:C8  DIRECT-MAHL-L2350DW_BRe9c8  Infra  6     65 Mbit/s   84      &#9602;&#9604;&#9606;&#9608;  WPA2     
*       76:69:42:8C:87:AF  BeckyNet                    Infra  6     540 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2     
        F0:72:EA:54:0D:E2  Sarmientofamily2            Infra  1     130 Mbit/s  35      &#9602;&#9604;__  WPA2     
        16:91:7F:89:C4:4A  SarmientoFamily             Infra  11    540 Mbit/s  27      &#9602;___  WPA2     
        10:0C:6B:39:EF:7F  SarmientoFamily_2GEXT       Infra  11    130 Mbit/s  25      &#9602;___  WPA2     

```

If this is something that can't be solved, I would like your instructions to revert back to the previous driver. Thanks.

---

### Post by chili555 on 2021-08-21
> I would like your instructions to revert back to the previous driver.
Please do:

```
sudo apt update
sudo apt install bcmwl-kernel-source
```Reboot.

You might also look into the settings in the router.  WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Fixed channel is recommended, not auto channel select. Typically, channels 34-50 are not DFS (preferred) as well as channels 149 and higher. To avoid channel switching due to DFS, prefer those channels.

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like BeckyNet2.4 and BeckyNet5.

After making these changes, reboot the router.

---

### Post by williepabon on 2021-08-21
chili 555:

Thanks for helping in reverting back. Maybe your explanation of having the two frequency bands of the router with the same SSID could be the cause of my problem. Unfortunately, my isp (Spectrum) set it up that way, and such setting was made inaccessible to the user. The settings page in the router re-directs you to install a phone app that defines what settings can be changed by the user. Anyways, thanks for the help and the education given.
wp

---

### Post by chili555 on 2021-08-21
The two bands typically have differing MAC addresses. Please try binding to the 5 gHz band like this: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

### Post by williepabon on 2021-08-25
**chili555:**

I just did the binding of my wifi card to the 5 GHz band as you suggested on your last post. I will be checking the behavior of the system to see if that solves my problem. As far as today goes, it seems to be working. I'll keep you posted. Thanks.
wp

---

### Post by williepabon on 2021-08-28
chili555:

I was very hopeful that your suggestion of binding my wifi card to the 5Ghz band of the router would solve the problem of intermittent disconnection but... it didn't. What else should I try? Hope you haven't run out of ideas. Thanks again for all your help.
wp

---

### Post by chili555 on 2021-08-30
Let's see if the log has any clues:

```
sudo dmesg | grep -ie brcm -e wl
```I am running a bit low on ideas, for sure.

---

### Post by williepabon on 2021-08-31
chili555:

It took me some time to answer your last post, because something happened in the last few days that forced me to double check the validity of my problem. And yes, my  problem still exists. Following is what happened that didn't make sense to me. Probably, you may have better understanding of this.

The wifi router in my house is installed in the second floor, 'cause most of the stuff my family use that require strong wifi signal (and bandwidth) is there. A couple of days ago, I installed a range extender (tp-link RE450) to cover for the low signal areas on the first floor. My computer is no farther than 25 feet from the router, but maybe out of frustration with my problem or curiosity, I connected to the internet through the range extender which is located like 60 feet downstairs. I got dumbfounded!. I had a nice, consistent signal (lower speed, though) that did not get disconnected from the Internet no matter what I did. That didn't make sense to me. When I connect directly the the router (that is closer) I have intermittent connection, but when I connect through the range extender I get a solid connection. Following, I show my present network configuration, for you to analyze.

```
williepabon@williepabon-Macmini:~$ nmcli dev wifi list
IN-USE  BSSID              SSID                        MODE   CHAN  RATE        SIGNAL  BARS  SECURITY 
        76:69:42:8C:87:AF  BeckyNet                    Infra  6     540 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2     
        32:C9:AB:96:E9:C8  DIRECT-MAHL-L2350DW_BRe9c8  Infra  6     65 Mbit/s   84      &#9602;&#9604;&#9606;&#9608;  WPA2     
*       90:9A:4A:4A:5E:BE  BeckyNet_Ex24               Infra  6     195 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2     
        76:69:42:8C:87:B0  BeckyNet                    Infra  44    540 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2     
        90:9A:4A:4A:5E:BF  BeckyNet_Ex52               Infra  44    405 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2     
        DE:54:D7:67:64:E1  --                          Infra  44    130 Mbit/s  49      &#9602;&#9604;__  WPA2     
        F0:72:EA:54:0D:E2  Sarmientofamily2            Infra  1     130 Mbit/s  34      &#9602;&#9604;__  WPA2     
        B0:E4:D5:59:57:2F  Sarmientofamily2            Infra  1     130 Mbit/s  19      &#9602;___  WPA2     
williepabon@williepabon-Macmini:~$ 

```

The BeckyNet and subsidiaries represent my internal home network. The_Ex24 and _Ex52 are the signals from the range extender. I hope that this information will help to better understand (or confuse?) the problem that I experience. Thanks again for all your help.
wp

---

### Post by chili555 on 2021-08-31
The answer is, to me, fairly evident. Above, I suggested:

> Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like BeckyNet2.4 and BeckyNet5.You are not able to do this because the router is supplied by your ISP with limited options to make any changes. Afterwards, as suspected, your connection hops between the 2.4 and 5 gHz bands despite, evidently, binding to the 5 gHz band via its MAC address.

However, your extender is provided by you and offers the ability to rename the segments as you’ve wisely done.

```
*       90:9A:4A:4A:5E:BE  BeckyNet_Ex24               Infra  6     195 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2     
        90:9A:4A:4A:5E:BF  BeckyNet_Ex52               Infra  44    405 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2 
```Without a forensic examination of the logs in your computer AND the original BeckyNet router to prove otherwise, I can only conclude that  your Ubuntu computer is connected to the 2.4 gHz segment of your extender and will remain until otherwise instructed by you.

I might have tried my own router, which I could configure as needed, rather than the extender. That’s what I do and it works beautifully. The wireless in my ISP-provided device is turned off.   

Internet--->AT&T Uverse box--->Chili's TP-Link router )))))) wireless to laptops, pads, phones, etc.

---

### Post by williepabon on 2021-08-31
[SIZE=4]**[COLOR=#ff0000]chili555:[/COLOR]**[/SIZE]

Thanks for your answer. The mystery is solved. Now, as you suggest, I need to do the forensic examination of my logs (which I don't know how to find and reproduce), and with the findings I obtain with the logs, I will request Spectrum to reconfigure my router according to my findings. Thanks again.
wp

---

### Post by chili555 on 2021-08-31
>  I need to do the forensic examination of my logs (which I don't know how to find and reproduce),As to your router, I haven't any clue. As to your computer, I suggest looking at:

```
sudo dmesg | grep wl

```
...where 'wl' will get both the interface wlp2s0 and the driver wl.

I'd also see what Network Manager is doing:

```
sudo cat /var/log/syslog | grep Network
```They may be lengthy and a bit tedious to decipher, but I think you will see the interface hopping between segments at BeckyNet.

---

