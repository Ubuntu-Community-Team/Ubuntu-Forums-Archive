---
title: "Unstable wifi connection after 14.04 upgrade"
date: 2014-04-22
forum: Networking &amp; Wireless
---

### Post by shaansweb on 2014-04-22
Hello,

After I upgraded my PC to Ubuntu 14.04, the connection has been really unstable. The connection frequently drops, fails to connect, or is very slow. This does not occur in Windows 8. The result's to varunendra's scirpt that I have seen people using on this forum are attached. Does anybody have any idea how I can fix this, or at the very least diagnose the problem?

I also temporarily put the result of the script on pastebin in case you don't want to download the attached archive

[http://pastebin.com/KCV5R16Z](http://pastebin.com/KCV5R16Z)

Thanks in advance.

---

### Post by praseodym on 2014-04-22
Hi,

deactivate the N-mode of the driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Additionally you can deactivate the power management of the card:
```

sudo iwconfig wlan0 power off
```

---

### Post by shaansweb on 2014-04-22
Thanks!! I'm getting "modprobe: FATAL: Module iwlwifi is in use." when I run "sudo modprobe -rfv iwlwifi" but the other three commands seem to have improved things. Can you (or anyone reading this) please explain to me what exactly those commands did? What is the N-mode of the card?

---

### Post by praseodym on 2014-04-23
There are different modes your router provides (or could provide depending on the model): a, b, c, g and n. Here, the N-mode of the driver is buggy. You can check the router manual

---

### Post by chris214 on 2014-04-30
I even tried newer kernels (3.15.0-031500rc3) but the issue persists.
Disabling N mode "fixed" the issue for now.

---

### Post by chris214 on 2014-05-06
I take it back...disabling N mode does not fix the issue.
Looking at iwconfig, I have extremely high **Invalid misc **packet count. Right now, it is over 3,000, and my uptime is 5 minutes.  After a few hours of browsing, it is well over 600,000.

---

### Post by kenjiru on 2014-05-07
Disabling N mode worked for me.

```

radu@sasuke:~$ iwconfig
wlan0     IEEE 802.11abg  ESSID:"FOO"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 28:BE:9B:05:7E:68   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1093   Missed beacon:0

radu@sasuke:~$ uptime
 23:56:59 up  3:13,  2 users,  load average: 0,29, 0,46, 0,47

```

I hope they will fix the 802.11n mode, as it's really annoying to use a slower speed.

---

### Post by rrohde on 2014-10-01
This issue still persists with the latest beta of Ubuntu 14.10... You'd think that would be resolved; such a basic functionality of an OS. Hate to having to boot into Windows just to get persistent wifi connectivity. :(

---

### Post by phottomatt on 2014-10-10
This did not work for me, I may need additional help here. Sometimes I don't even get a list of available WiFis.
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.


usb0      no wireless extensions.

```

---

### Post by praseodym on 2014-10-10
Change the mtu value to 1500 instead of "Automatic" in the network manager profile

---

### Post by kowaicheong on 2014-10-28
Hi all,

I tried to apply the above fix (copying line by line) but could not disable the router's n-mode.

```

josephn@josephn-NY639AA-ABA-p6213w:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Nighthawk"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: FC:F5:28:1E:A0:41   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0

josephn@josephn-NY639AA-ABA-p6213w:~$ echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disable=1
josephn@josephn-NY639AA-ABA-p6213w:~$ sudo modprobe -rfv iwlwifi
rmmod iwlwifi
josephn@josephn-NY639AA-ABA-p6213w:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=1 
josephn@josephn-NY639AA-ABA-p6213w:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Nighthawk"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: FC:F5:28:1E:A0:41   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0


```

I checked and found that I do have the iwlwifi driver. Could somebody please help me see what I am missing.

---

### Post by praseodym on 2014-10-28
Try to deactivate the queue, too:
```

echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by kowaicheong on 2014-10-29
Still nothing, unfortunately.

```

josephn@josephn-NY639AA-ABA-p6213w:~$ echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
[sudo] password for josephn: 
options iwlwifi 11n_disable=1 wd_disable=1
josephn@josephn-NY639AA-ABA-p6213w:~$ sudo modprobe -rfv iwlwifi
rmmod iwlwifi
josephn@josephn-NY639AA-ABA-p6213w:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=1 wd_disable=1 

josephn@josephn-NY639AA-ABA-p6213w:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Nighthawk"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: FC:F5:28:1E:A0:41   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0

```

Maybe if I understood what I was doing here I could more effectively troubleshoot. If I understand right Modprobe is used to modify the linux kernal. The -rf tag removes the option line from the teed kernal, but I don't understand the third line. Any suggestions on how to narrow down the problem? Perhaps use modprobe to change something innocuous?

Thanks for your help.

---

### Post by praseodym on 2014-10-29
Please run the wireless script from the sticky thread and show the outputs.

---

### Post by kowaicheong on 2014-10-29
Here you go. Looking through it nothing stood out to me. I have attached the whole file.

[ATTACH]257591[/ATTACH]

---

### Post by praseodym on 2014-10-29
You don't have an Intel device:
```

sudo modprobe -rfv iwlwifi
```
Install this wireless driver instead (changes the native one):
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by kowaicheong on 2014-11-02
That seems to have worked. Thank you.

Joe

---

### Post by cmire on 2014-12-09
I'm currently running 12.04 and will be upgrading to 14.04. My wifi has never caused me problems until I tried to connect to an Asus RT-AC68U gigabit router. Then suddenly, the connection kept dropping, etc. Same problem noted in this thread. But on my older Netgear router at home, the connection is always stable. The fix that worked for me was to purchase an Asus USB-N53 wifi adapter. My onboard wifi used the Broadcom driver (HP dv6 laptop), and there seems to be a problem with these drivers and the newer routers. Reinstalling the driver and trying the other remedies listed in this thread did not work. The other nice thing about the USB adapter is that even though it is not a perfect solution (the connection still can drop sometimes, although rarely), it can easily be power cycled by unplugging then replugging in (versus doing "services networking restart" or rebooting).

---

### Post by sengine8 on 2015-01-05
Same here. On 14.04 LTS my wifi was unstable. Looking on the web (and here...) I've disabled "n" mode on the router.
After this (now router works only with "b+g" mode) the connection is stable.
I hope this can help other guys with same my wifi issue.

---

### Post by abhishek27 on 2015-09-20
wifi or wireless conection option is not at all visible

---

### Post by arash9 on 2016-01-04
> **praseodym said:**
> You don't have an Intel device:
```

sudo modprobe -rfv iwlwifi
```
Install this wireless driver instead (changes the native one):
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

Hi Praseodym, I have looked at my wifi card and its rtl8192ce not cu, I am wondering if there is a fix for ce version?

---

### Post by andrey41 on 2016-03-26
> **praseodym said:**
> You don't have an Intel device:
```

sudo modprobe -rfv iwlwifi
```
Install this wireless driver instead (changes the native one):
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

It worked out for me. Thank you a lot!

---

