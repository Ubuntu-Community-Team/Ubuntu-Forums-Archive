---
title: "How do I install a 802.11N USB to WiFi dongle?"
date: 2017-11-28
forum: Networking &amp; Wireless
---

### Post by bierdo69 on 2017-11-28
I have a USB dongle that connects to WiFi for me.
(802.11N   USB 2.0 wireless) 
I can install it in Windows, but I cannot install it in Ubuntu 16.04
Please help me, I cannot get it to work in Ubuntu, but it works in Windows. :-(
HELP
(I connect to the internet with WiFi)

---

### Post by ajgreeny on 2017-11-28
With the dongle attached run lsusb in terminal and show us the output back here.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

It may also be worth running the Wireless-Info script in my signature below and posting the output from that back here also in code tags.

---

### Post by bierdo69 on 2017-11-29
Hi thanks, 
here is the output from lsusb which I ran with the dongle attached: 
"[B]Latitude-E6410:~$ lsusb
[/B]Bus 002 Device 006: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 005: ID 0bda:8178 **Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter**
Bus 002 Device 004: ID 0e8f:00a7 GreenAsia Inc. 
Bus 002 Device 003: etc.... "

Does this help ?

---

### Post by bierdo69 on 2017-11-30
I couldn't see any problems with the terminal output I posted, so I didn't worry about **code-tags**.
Should I post it with them again ?

I tried running the "Wireless-info" script in the Terminal with no luck.

Have I given enough information?
If not, how do I run the script ?

---

### Post by Hadaka on 2017-12-01
Hi, from a working wired connection with the usb wifi inserted
please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the wireless-info.txt
Thanks.

---

### Post by bierdo69 on 2017-12-01
Hi thanks for that, I connected the computer to the Internet via USB and also plugged in my USB WiFi Dongle.
I ran the command you sent me and it created "wireless-info.txt"
I have attached that file from my home directory.
(It is attached)
Thank you I hope this helps.

---

### Post by praseodym on 2017-12-02
Change the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
sudo git clone https://github.com/vincent-t/rt8192cu_dkms /usr/src/8192cu-4.0.2.9000.20130911
sudo dkms add -m 8192cu -v 4.0.2.9000.20130911
sudo dkms build -m 8192cu -v 4.0.2.9000.20130911
sudo dkms install -m 8192cu -v 4.0.2.9000.20130911 
echo -e "blacklist rtl8192cu\nblacklist rtl8xxxu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot

---

### Post by bierdo69 on 2017-12-02
On internet from Windows now.
I ran your code in the terminal (not connected to the net) and restarted Ubuntu, but no luck.
Do I need to be connected to the internet too ?

So I connected (wired) to the internet and ran your code (in Ubuntu, terminal), restarted the comp. and unplugged and plugged in my USB to WiFi dongle and nothing happened. (no WiFi)
Is there something else I am supposed to do ?

Help ...

---

### Post by Hadaka on 2017-12-02
Hi,please open a terminal then copy and paste one line at a time.

```
sudo iw reg set AU
sudo sed -i 's/=.*/=AU/' /etc/default/crda
```
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
```
rm -rf b43
rm -rf brcmsmac
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
#rfkill list is showing the wifi hard blocked
#please press the fn/f2 keys one time and then enter the commands..
```
rfkill unblock all
rfkill list all
```
#to see if the hard block clears
# *If it clears then do...
```
sudo modprobe -v rtl8192cu
```
#Finally..with the ubuntu os, connect to the internet with a wired connection
and enter the code praseodym gave you in post #7
Insert wireless usb ,boot and test wireless
Thanks.

---

### Post by praseodym on 2017-12-02
Yes, run those commands under Linux while connected wired

---

### Post by bierdo69 on 2017-12-02
Hi, I did all that you said in #9 and after hitting Fn/F2 and running the two lines below: 
"~$ rfkill unblock all
~$ rfkill list all"
I got:
"0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no"
I thought this meant it had been cleared so I ran: 
"~$ sudo modprobe -v rtl8192cu"
And then I ran #7 from praseodym
Then I rebooted and plugged in my USB-WiFi dongle ... nothing happened, no connection.
(The reason i am using this dongle is I can't get WiFi to work on this laptop, in Windows the dongle does work well, but I want the dongle to work in Ubuntu as I mostly use this OS, I really like Ubuntu, I really want WiFi to work with Ubuntu ... HELP ...)

---

### Post by Hadaka on 2017-12-02
We are trying to help, to begin, until you are able to clear the wifi hard block
there is no way any internal or external wifi unit is going to work. Please post 
a new wireless info report so we can see what has and hasn't transpired.

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
Thanks.

---

### Post by bierdo69 on 2017-12-03
Here it is.

---

### Post by bierdo69 on 2017-12-03
Do you need me to give you more information ?

---

### Post by Hadaka on 2017-12-03
Hi, you still have the hardblock on wifi... did you disable secure boot ??
did you make any changes in bios ??
also..please do again..by copy and paste while attached to the internet with ubuntu..
Copy and paste one line at a time.
```
sudo iw reg set AU
sudo sed -i 's/=.*/=AU/' /etc/default/crda
```
Then do..
```
rm -rf bcma
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and do and post the output of..
```
rfkill unblock all
rfkill list all
```
we need to clear the hard block before any drivers can be loaded.
thanks.

---

### Post by bierdo69 on 2017-12-04
I don't know how to clear the hard block, do I need to disable the secure boot? If so how do I do this?
I ran your code in the Terminal.
Here is the output:
"0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes"

PS: The USB-WiFi dongle, works well in Windows 7 but I can't get it to work in Ubuntu ... why ??? ...

---

### Post by bierdo69 on 2017-12-05
Need some more information ?

---

### Post by Hadaka on 2017-12-05
Hi, to begin Ubuntu/Linux..is not or anything like windows. The dongle
manufactuer supports and provides drivers for windows, but not Ubuntu.
There is a linux driver for it, but the hard block needs to be cleared first.
please check again by pressing the FN and F2 keys together one time
at the same time and then do the rfkill command to see if it cleared.
if it does not..do a search on "How to enter bios on a dell computer".
once you are in bios ,choose the "legacy" boot.
Thanks

---

### Post by bierdo69 on 2017-12-05
Cheers I will do. 
I'll let you know how I go.

---

### Post by chili555 on 2017-12-06
I hate to step on the toes of my esteemed colleagues Hadaka and praseodym but I hope I can clear some things up.

First:

   >  I don't know how to clear the hard block

Someplace on that Dell is a wireless switch or key combination that turns on and off the wireless. It may be called Airplane Mode. Find it and press it. Confirm that the hard block is resolved with:

    ```
rfkill list all
```

Now does the USB dongle work?

I am fairly confident that you got the USB because the internal device didn’t work. Once the hard block is fixed, you may be able to set aside the USB and we’ll address the internal device if needed.

---

### Post by bierdo69 on 2017-12-08
In Ubuntu I went into the network settings and confirmed "Airplane Mode" is turned off for Wireless, Wired and Network Proxy.
I'll check with rfkill list all 

It still seems to be blocked :-(' here's the output.

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

(This is with the USB-WiFi to dongle plugged in, otherwise Wireless wouldn't show up, as presently I am using a wired connection to the internet)

---

### Post by chili555 on 2017-12-08
> **bierdo69 said:**
> In Ubuntu I went into the network settings and confirmed "Airplane Mode" is turned off for Wireless, Wired and Network Proxy.
I'll check with rfkill list all 

It still seems to be blocked :-(' here's the output.

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: noDid you find and press the switch on the computer itself? What is the exact model of your Dell?

---

### Post by bierdo69 on 2017-12-08
In Ubuntu in Network Settings. I made sure "Airplane Mode" was turned off, in Wireless, Wired and in Proxy Settings.

I then run _rfkill list all_ : here's the output:

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no

So it still seems blocked in Dell, but not in the USB-WiFi dongle. (I have the dongle plugged in for this)
If I take it out I get:

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

(As I said before : The USB-WiFi dongle works fine in Windows, but I can't figure out how to get it going in Ubuntu ....)

---

### Post by chili555 on 2017-12-08
Did you find and press the switch on the computer itself? What is the exact model of your Dell?

---

### Post by bierdo69 on 2017-12-08
I just found one on the side, it looked like a wireless switch, one way is red the other the red dissapears, It is definitely switched to hide the red now.
My Computer is a Dell Latitude E6410 laptop

That seems to have helped: I ran _rfkill list all_:
and I get now:

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by bierdo69 on 2017-12-08
It now says its not Hard blocked.(YAY)
But I think wireless is no good on this computer, hence why I have the dongle.
Wireless in Settings isn't active until I plug in the dongle - the Wireless appears.

Is there some software I need to load now to run the USB-WiFi dongle?
Is there something else I should do as well ?

---

### Post by chili555 on 2017-12-08
Wonderful! Please plug in the USB and then tell us what these tests tell us:```
dmesg | grep -e rtl -e wlx
sudo iwlist scan
```The internal wireless is very probably just fine, however, it's driver is currently blacklisted in order to coax the USB to life.

---

### Post by bierdo69 on 2017-12-08
```
$ dmesg | grep -e rtl -e wlx
[   15.911813] rtl8192cu: Chip version 0x11
[   15.989807] rtl8192cu: MAC address: 80:3f:5d:11:16:f0
[   15.989812] rtl8192cu: Board Type 0
[   15.990052] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   15.990081] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   16.094853] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   16.095158] usbcore: registered new interface driver rtl8192cu
[   16.200875] usbcore: registered new interface driver rtl8xxxu
[   16.681050] rtl8192cu 2-1.3:1.0 wlx803f5d1116f0: renamed from wlan0
[   28.154655] IPv6: ADDRCONF(NETDEV_UP): wlx803f5d1116f0: link is not ready
[   28.156560] rtl8192cu: MAC auto ON okay!
[   28.190098] rtl8192cu: Tx queue select: 0x05
[   29.146303] IPv6: ADDRCONF(NETDEV_UP): wlx803f5d1116f0: link is not ready
[   30.566623] IPv6: ADDRCONF(NETDEV_UP): wlx803f5d1116f0: link is not ready
[   39.095989] rtl_usb: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3902a2a
[   39.095994] rtl_usb: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x2a2a2a2a
[   39.095997] rtl_usb: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x2a2a2a2a
[   39.096014] rtl_usb: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x2a2a2a27
[   75.472403] rtl8192cu: Chip version 0x11
[   75.561448] rtl8192cu: MAC address: 80:3f:5d:11:16:f0
[   75.561456] rtl8192cu: Board Type 0
[   75.561764] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   75.561814] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   75.562055] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[   76.583282] rtl8192cu 2-1.3:1.0 wlx803f5d1116f0: renamed from wlan0
[   76.608382] IPv6: ADDRCONF(NETDEV_UP): wlx803f5d1116f0: link is not ready
[   76.612397] rtl8192cu: MAC auto ON okay!
[   76.646317] rtl8192cu: Tx queue select: 0x05
[   77.094106] IPv6: ADDRCONF(NETDEV_UP): wlx803f5d1116f0: link is not ready
[   77.140259] IPv6: ADDRCONF(NETDEV_UP): wlx803f5d1116f0: link is not ready
[   78.209378] IPv6: ADDRCONF(NETDEV_CHANGE): wlx803f5d1116f0: link becomes ready
[  196.412071] rtl8192cu: MAC auto ON okay!
[  196.446865] rtl8192cu: Tx queue select: 0x05
[  196.953910] IPv6: ADDRCONF(NETDEV_UP): wlx803f5d1116f0: link is not ready
[  198.036003] IPv6: ADDRCONF(NETDEV_CHANGE): wlx803f5d1116f0: link becomes ready
[  230.596658] rtl8192cu: Chip version 0x11
[  230.683927] rtl8192cu: MAC address: 80:3f:5d:11:16:f0
[  230.683982] rtl8192cu: Board Type 0
[  230.684306] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  230.684359] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[  230.684744] ieee80211 phy2: Selected rate control algorithm 'rtl_rc'
[  231.721503] rtl8192cu 2-1.3:1.0 wlx803f5d1116f0: renamed from wlan0
[  231.750459] IPv6: ADDRCONF(NETDEV_UP): wlx803f5d1116f0: link is not ready
[  231.754682] rtl8192cu: MAC auto ON okay!
[  231.791362] rtl8192cu: Tx queue select: 0x05
[  232.232759] IPv6: ADDRCONF(NETDEV_UP): wlx803f5d1116f0: link is not ready
[  232.289864] IPv6: ADDRCONF(NETDEV_UP): wlx803f5d1116f0: link is not ready
[  233.369628] IPv6: ADDRCONF(NETDEV_CHANGE): wlx803f5d1116f0: link becomes ready
```

---

### Post by wildmanne39 on 2017-12-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by bierdo69 on 2017-12-08
Have done.

When I then run the next line 
_sudo iwlist scan_

I only get:

```

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

```

---

### Post by chili555 on 2017-12-08
One more step:```
lsmod | grep -e 8192 -e rtl
```

---

### Post by bierdo69 on 2017-12-08
I ran it 
```
 lsmod | grep -e 8192 -e rtl 
``` 
and restarted it, and tried to run the USB-WiFi dongle as well and no luck.
So i'm back on the wired connection again.
I do need to get WiFi going though...

---

### Post by chili555 on 2017-12-08
> **bierdo69 said:**
> I ran it 
```
 lsmod | grep -e 8192 -e rtl 
``` 
and restarted it, and tried to run the USB-WiFi dongle as well and no luck.
So i'm back on the wired connection again.
I do need to get WiFi going though...Sorry about that. I meant to ask for the *result* of the command.

---

### Post by bierdo69 on 2017-12-08
Here it is:
```
 rtl8xxxu               73728  0
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              737280  4 rtl8xxxu,rtl_usb,rtlwifi,rtl8192cu
cfg80211              565248  2 mac80211,rtlwifi
snd                    81920  22 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device

```

---

### Post by chili555 on 2017-12-08
Please do:```
sudo -i
echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and show me the result of:```
sudo iwlist scan
dmesg | grep wlx
```

---

### Post by bierdo69 on 2017-12-08
Here it is:
I ran: ```
 
sudo -i
echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit

```
Then restarted it:  




```

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

$ dmesg | grep wlx

```

---

### Post by chili555 on 2017-12-08
Please show me the result of:```
dmesg | grep -e wlx -e rtl
iwconfig
```

---

### Post by bierdo69 on 2017-12-08
I do not have the USB-WiFi dongle plugged in.
```

lo        no wireless extensions.

eno1      no wireless extensions.

```

Do you want me to plug it in ?

---

### Post by chili555 on 2017-12-08
> **bierdo69 said:**
> I do not have the USB-WiFi dongle plugged in.
```

lo        no wireless extensions.

eno1      no wireless extensions.

```

Do you want me to plug it in ?Only if you expect it to work.

---

### Post by bierdo69 on 2017-12-08
With it plugged in and running your code I get:
```

$ dmesg | grep -e wlx -e rtl
[ 4078.382382] usb 2-1.3: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 4080.239468] usbcore: registered new interface driver rtl8xxxu
[ 4080.357859] rtl8xxxu 2-1.3:1.0 wlx803f5d1116f0: renamed from wlan0
[ 4080.456992] IPv6: ADDRCONF(NETDEV_UP): wlx803f5d1116f0: link is not ready
[ 4080.713611] IPv6: ADDRCONF(NETDEV_UP): wlx803f5d1116f0: link is not ready
[ 4080.890970] IPv6: ADDRCONF(NETDEV_UP): wlx803f5d1116f0: link is not ready

$ iwconfig
lo        no wireless extensions.

wlx803f5d1116f0  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eno1      no wireless extensions.

```

---

### Post by chili555 on 2017-12-08
Excellent! Does it scan?```
sudo iwlist scan
```If it sees networks with scan, then you should be able to click the Network Manager icon and click on your network and connect.

---

### Post by bierdo69 on 2017-12-08
This is the output from the code you gave me:

```

lo        Interface doesn't support scanning.

wlx803f5d1116f0  No scan results

eno1      Interface doesn't support scanning.

```

---

### Post by bierdo69 on 2017-12-08
It does seem to be working now !!
Thanks for going through everything with me.
THANKYOU :-)

I'll let you know if I have any other issues.

(As I thought it wouldn't Wireless didn't work in the DELL computer but it does seem to work with the USB-WiFi dongle, the reason I got it)
(Now I can use Ubuntu for everything via WiFi , when I need to I can use Windows as well with this WiFi dongle)

---

