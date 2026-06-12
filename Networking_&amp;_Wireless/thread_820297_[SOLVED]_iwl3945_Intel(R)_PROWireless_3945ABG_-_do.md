---
title: "[SOLVED] iwl3945: Intel(R) PRO/Wireless 3945ABG - doesn't work"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by gryzzly on 2008-06-06
Hi, folks.
Once again I've installed 8.04 on my laptop (it's Lenovo 3000 n200 0769 BRG). I have installed all updates.

Wifi still doesn't work :(

here is output for [FONT="System"]dmesg | grep -i iwl[/FONT] when wireless switch is off:
```
[   39.518968] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   39.518973] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   39.519128] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
[   42.024975] iwl3945: Radio Frequency Kill Switch is On:
[   42.046004] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   42.056006] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   42.075914] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   42.103390] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   42.123282] iwl3945: Tunable channels: 13 802.11bg, 0 802.11a channels
```

here is output for [FONT="System"]dmesg | grep -i iwl[/FONT] when wireless switch is ON:
```
[   39.518968] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   39.518973] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   39.519128] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
[   42.024975] iwl3945: Radio Frequency Kill Switch is On:
[   42.046004] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   42.056006] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   42.075914] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   42.103390] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   42.123282] iwl3945: Tunable channels: 13 802.11bg, 0 802.11a channels
[  126.804818] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[  128.212275] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[  128.212288] iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4418 ser 0x0000004B
[  129.204254] iwl3945: Can't stop Rx DMA.

```
uname -r: 2.6.24-18-generic

---

### Post by sagar_pg on 2008-06-06
(bump) I have the exact same problem.. no solutions. 
Lenovo T61. 
$ uname -a 
Linux Ares 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux
$ lspci | grep 3945
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

I have the same error message popping up in the logs: 
[    4.493914] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[    4.493917] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[    4.494873] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[    4.607327] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[    4.608700] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[ 4504.263059] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[ 4504.263070] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x02D4 ser 0x0000004B
[ 4506.251624] iwl3945: Can't stop Rx DMA.


Additional bit of information: I use this laptop at work and at home. I only see this at work. The 2 differences I see: work router uses WEP (WPA2 at home), and work router is a 802.11n (802.11g at home)

I've had this ever since I upgraded to hardy. (Been using gutsy for a few months before, same setup, no issues).

---

### Post by chili555 on 2008-06-06
Have either of you installed *linux-backports-modules-hardy-generic*? There is evidently a revision to iwl3945 in there.

What is the result of:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by gryzzly on 2008-06-06
> **chili555 said:**
> Have either of you installed *linux-backports-modules-hardy-generic*? There is evidently a revision to iwl3945 in there.

What is the result of:```
sudo iwlist wlan0 scan
```Thanks.
this one is when wireless switch is off:
wlan0     Interface doesn't support scanning.

this is when the switch is on:
misha@misha-laptop:~$ sudo iwlist wlan0 scan
wlan0     Failed to read scan data : Resource temporarily unavailable

I will install backports now;
will post here the result.

---

### Post by gryzzly on 2008-06-06
Installed *linux-backports-modules-hardy-generic* 

Wifi doesn't work, here is the output for **dmesg | grep -i iwl**:
(it's the same for both cases, when switch is on, and when it's off)
```
misha@misha-laptop:~$ dmesg | grep -i iwl
[   36.868659] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   36.868664] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   36.868835] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
[   36.945572] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   42.714948] iwl3945: Radio disabled by HW RF Kill switch
```

---

### Post by gryzzly on 2008-06-06
sorry, here is output for **sudo iwlist wlan0 scan**
```
wlan0     Interface doesn't support scanning : Network is down
```

---

### Post by chili555 on 2008-06-06
Please do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```Now does your card scan and connect as expected? If so, please apply the fix here: [http://ubuntuforums.org/showthread.php?t=808516](http://ubuntuforums.org/showthread.php?t=808516) in post #4.

If not, post back.

---

### Post by gryzzly on 2008-06-06
Wheeeeee!!! Thanks, chili555! You made this evening and probably next week for me! Thanks!!!

Just one question, is this something I will need to do all the time, or it's enough one time to make this:
```

sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
reboot

```

---

### Post by chili555 on 2008-06-06
> it's enough one time Indeed it is. If it came up automagically when you rebooted, it will, barring unforeseen circumstances, come up every time you boot. If not, post back.

---

### Post by gryzzly on 2008-06-06
Ok, afer reboot it didn't come.
Needed to make:
```

sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1

```
to get things working,
sekond part from d.r.e.a.m's post didn't help.

(Should I turn the switch on or off when doing it?)

---

### Post by chili555 on 2008-06-06
Please let me see:```
cat /etc/modprobe.d/iwl3945
```Perhaps there is a typo. Also, how about:```
dmesg | grep iwl
```Thanks.

Switch on upon boot. Leave it on, please.

---

### Post by gryzzly on 2008-06-06
Here they are:
```
misha@misha-laptop:~$ **cat /etc/modprobe.d/iwl3945**
alias wlan0 iwl3945 
options iwl3945 disable_hw_scan=1
```
```

misha@misha-laptop:~$ **dmesg | grep iwl**
[   35.822087] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   35.822093] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   35.822257] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
[   35.898955] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   42.645883] iwl3945: Radio disabled by HW RF Kill switch

```

---

### Post by chili555 on 2008-06-06
> [   42.645883] iwl3945: Radio disabled by HW RF Kill switchWhat is going on?

Please switch the switch on. Do not touch it till Tuesday. Reboot. Does your wireless come up automatically? If you are absolutely certain the switch is on at all times, lets try another approach. *sudo gedit /etc/rc.local* and add two lines above 'exit 0':```
rmmod -f iwl3945
modprobe iwl3945 disable_hw_scan=1
```Now reboot. We await your report of success.

Your */etc/modprobe.d/iwl3945* looks perfect.

---

### Post by gryzzly on 2008-06-06
Ok, so the situation is following:
If I boot the system up with wireless switch turned on - so wifi works fine, it detects network and connects smoothly.
If I boot the system up with switch off and turn it on after the system is booted - then to make the driver to work I need to do:
```

sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1

```

If I turn the switch off after the boot with switch turned on - once again I need to manually make a fix.

Anyway, it's great and I can stick with this 'till the next release or something :)

Thank You very much!

---

### Post by clesage on 2008-07-12
"What is going on?"

Hi Chili, I've been following these steps as well. Same card, same problems, same basic output.

My wi-fi switch is turned ON, and the light is on. But my dmesg output still says that the kill switch is on as well. I had flawless wireless until upgrading to Hardy.

Working through the steps again. Will inform.

UPDATE: It worked! Running:
```
sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
reboot
```
from [http://ubuntuforums.org/showthread.php?t=808516](http://ubuntuforums.org/showthread.php?t=808516) worked (...on the second try, strangely enough. I hope this is a stable fix. I don't actually understand most of the these commands.)

Cheers and thanks,
-sage

---

### Post by wynoch on 2008-07-19
Thanks Chili!

```

rmmod -f iwl3945
modprobe iwl3945 disable_hw_scan=1

```

works perfect for me, on Toshiba U200.
For quite some time I have been using ipw3945 instead, but with every new kernel had to reinstall. Problem solved! :)

---

### Post by d-r-i-v-e on 2008-07-29
Thank you all for the help.
What a wonderful filling - the most annoying problem is successfully solved.

---

### Post by Ichido on 2008-07-30
gryzzly,
How do I type the character "PIPE" in between dmesg & grep as in:

"here is output for dmesg | grep -i iwl when wireless switch is off:"

Thanks.

---

### Post by chili555 on 2008-07-30
> How do I type the character "PIPE" in between dmesg & grepIt's on the upper right of your US keyboard, on the same key with \.

---

### Post by Ichido on 2008-07-30
> **chili555 said:**
> It's on the upper right of your US keyboard, on the same key with \.

Thank you for solving this mystery :)
My keyboard shows that key as two vertical 'dashes' over a Back-Slash.

---

### Post by Miss Kudos on 2008-08-03
awesome.  this worked for me.  thank you :O)

> **chili555 said:**
> Please do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```Now does your card scan and connect as expected? If so, please apply the fix here: [http://ubuntuforums.org/showthread.php?t=808516](http://ubuntuforums.org/showthread.php?t=808516) in post #4.

If not, post back.

---

### Post by Num1Deluxe on 2008-08-03
Hi,
I am having a similar problem with the same card. I was able to scan other wireless networks, But being new to Ubuntu I have not a clue of why I am not able to connect to any of them. I was also able to  get this output:
[   48.973636] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   48.973640] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   48.973826] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   49.491658] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   49.493922] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[28396.164092] iwl3945: Radio Frequency Kill Switch is On:

I am not sure what any of this means but would like to learn and get my wireless working.

help and thanks,
1

---

### Post by Num1Deluxe on 2008-08-03
Hi,
Tried- sudo apt-get install linux-backports-modules-hardy-generic
Witch did the trick. 
I would like to know what I did, but I am definitely happy that it worked.

Thanks for the help. :)

---

### Post by bachisanerd on 2008-08-07
I've got a related problem, maybe...

I also get the "iwl3945: Radio Frequency Kill Switch is On" message, and as much as I'd like to turn the kill switch off, I've only got a button above the keyboard and it seems to have no effect. (A HAL problem, maybe?)  I don't particularly care about being able to turn the card on and off, so is there a way to tell the card to be on by default and not off by default, skipping the need for the button altogether?

The card shows up in lspci,

and sudo iwlist scan yields:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:1C:DF:89:50:BD
                    ESSID:"SUTECH"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=93/100  Signal level=-37 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=00000079c4c10f24

```

Using the Network Manager applet, I tried entering the name of a known ESSID, with no result.  Hope the above data is bogus because I did that.

HP Pavillion dv8000,  PRO/Wireless 3945ABG, Ubuntu Studio

---

### Post by royfeldman on 2008-08-24
I also am having problems with my Intel Pro/Wirless 3945ABG Network Connection (rev 02) card in my Dell 1530 running Hardy.  I just upgraded a few days ago.

I have installed linux-backports-modules-hardy-generic and I am otherwise up to date.

If I execute the recommended commands:

sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1

and then reboot, I can see the wireless networks that are active.

However, when I reboot, I no longer see any networks, so for know I have
to repeat the procedure every time I want to connect to a wireless lan.

Any ideas on what I can do, besides going back to Gutsy, which worked fine.

thanks in advance,

roy

---

### Post by frenchsquared on 2008-08-24
I know this thread say solved but I am having the same problem with the same card only my output inst the same as theres

gordon@Gateway:~$ sudo rmmod -f iwl3945
[sudo] password for gordon: 
ERROR: Removing 'iwl3945': No such file or directory

gordon@Gateway:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

gordon@Gateway:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

gordon@Gateway:~$ sudo rmmod -f iwl3945
ERROR: Removing 'iwl3945': No such file or directory

gordon@Gateway:~$ sudo modprobe iwl3945 disable_hw_scan=1
FATAL: Module iwl3945 not found.
gordon@Gateway:~

---

### Post by yosva on 2008-09-12
Hi!

I've a Fujitsu Siemens Amilo Li 2735 laptop, this is the second week trying to have working the Intel Pro Wireless 3945abg. I've tested debian, kubuntu, kanotix and last night i've found this thread and i'm needing your help, hopping can you help me.

I've read and do all instruction by chili555 (thanks):

1. installed linux-backports-modules-hardy-generic

2. sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1

3. sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
reboot

and after that sudo cat /var/log/messages | grep switch show

```
 Sep 12 09:55:42 yosva-laptop kernel: [    9.835872] SMP alternatives: switching to UP code
Sep 12 09:55:42 yosva-laptop kernel: [   10.345817] SMP alternatives: switching to SMP code
Sep 12 09:55:42 yosva-laptop kernel: [   10.439818] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep 12 09:55:44 yosva-laptop kernel: [   28.420315] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:00:05 yosva-laptop kernel: [   92.782405] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:00:08 yosva-laptop kernel: [   93.222077] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:09:09 yosva-laptop kernel: [   13.049157] SMP alternatives: switching to UP code
Sep 12 10:09:09 yosva-laptop kernel: [   13.561895] SMP alternatives: switching to SMP code
Sep 12 10:09:09 yosva-laptop kernel: [   13.655989] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep 12 10:09:11 yosva-laptop kernel: [   32.439076] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:11:55 yosva-laptop kernel: [   64.368741] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:11:55 yosva-laptop kernel: [   64.403176] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:11:55 yosva-laptop kernel: [   64.439201] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:11:55 yosva-laptop kernel: [   64.491739] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:11:55 yosva-laptop kernel: [   64.492306] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:11:57 yosva-laptop kernel: [   65.100373] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:12:22 yosva-laptop kernel: [   66.454334] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:12:28 yosva-laptop kernel: [   67.295850] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:12:34 yosva-laptop kernel: [   73.507294] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:12:36 yosva-laptop kernel: [   74.766802] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:12:38 yosva-laptop kernel: [   76.856043] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:12:51 yosva-laptop kernel: [   83.465218] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:12:54 yosva-laptop kernel: [   84.379888] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:16:17 yosva-laptop kernel: [  107.689423] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:17:56 yosva-laptop kernel: [   12.016101] SMP alternatives: switching to UP code
Sep 12 10:17:56 yosva-laptop kernel: [   12.530701] SMP alternatives: switching to SMP code
Sep 12 10:17:56 yosva-laptop kernel: [   12.625436] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep 12 10:17:57 yosva-laptop kernel: [   31.614017] iwl3945: Radio disabled by HW RF Kill switch
Sep 12 10:19:38 yosva-laptop kernel: [   65.235556] iwl3945: Radio disabled by HW RF Kill switch
 
```

and sudo lshw -C network show

```

*-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0a:e4:cd:ba:2e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=84.127.206.94 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:44:c6:7e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11a

```

Please help you are my last hope to get a fully functional linux and forget the stupid windows vista.

---

### Post by mykrob on 2008-09-29
i am having trouble, but slightly different. I do have backports installed.. here is what happens with mine:

```

[  151.400423] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[  151.426843] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 18
[  151.453526] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[  151.458822] Registered led device: iwl-phy1:RX
[  151.458860] Registered led device: iwl-phy1:TX
[  151.463867] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  154.735997] wlan0: Initial auth_alg=0
[  154.736011] wlan0: authenticate with AP 00:1e:e5:a2:6d:4d
[  154.738412] wlan0: RX authentication from 00:1e:e5:a2:6d:4d (alg=0 transaction=2 status=0)
[  154.738423] wlan0: authenticated
[  154.738427] wlan0: associate with AP 00:1e:e5:a2:6d:4d
[  154.740826] wlan0: RX AssocResp from 00:1e:e5:a2:6d:4d (capab=0x411 status=0 aid=1)
[  154.740835] wlan0: associated
[  154.740952] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  154.740959] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  154.740966] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  154.740972] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  154.744868] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  159.514558] wlan0: no IPv6 routers present
**[  237.898268] iwl3945: Microcode SW error detected.  Restarting **0x82000008.
[  237.898291] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x02BA ser 0x0000004E
[  238.891921] iwl3945: Can't stop Rx DMA.
[  239.039108] Registered led device: iwl-phy1:RX
[  239.039151] Registered led device: iwl-phy1:TX

```

I have even replaced the iwlwifi firmware with newer firmware, thinking that based on my error message it has something to do with that..

help?

---

### Post by mykrob on 2008-09-29
on a side note, i have always been able to scan networks. The problem i have is that it will connect for a time, usually very short, then even though my networkmanager still shows it connected, i cannot pull any pages,  cant even ping. Cant do anything..

just giving a short history.
here's a full story, if anyone's interest:

[http://forums.pcpitstop.com/index.php?showtopic=160231](http://forums.pcpitstop.com/index.php?showtopic=160231)

thanks,
-myk

---

### Post by ckonstantinos on 2008-10-08
> **chili555 said:**
> Have either of you installed *linux-backports-modules-hardy-generic*? There is evidently a revision to iwl3945 in there.

What is the result of:```
sudo iwlist wlan0 scan
```Thanks.

Oh, No! What a mess! I had a similar problem with my intel 3945 card unable to detect the wifi network and installed the above package (*linux-backports-modules-hardy-generic*).

Now my graphics card is not recognised, my audio is not working and I don't know what else is working or not!

I had 8.04 hardy and all the above were recognized and working well before (except the wifi card) how can I roll back the system?? 

Please help

---

### Post by muadib on 2008-11-14
First off I use a Toshiba U200.
[http://opalescent.ca/Toshiba%20U200%20Ubuntu%20Feisty.html](http://opalescent.ca/Toshiba%20U200%20Ubuntu%20Feisty.html)
I have a WEP protected network at home.

My card is not working in 8.10 either. I can confirm that I booted with kill switch off (that is that my card was on the whole time). I tried using knetwork manager as well as the iwconfig tools in 8.10.

I tried using the 2.6.27-7-generic kernel's iwl3945 with limited success. I was able to scan for networks using the 2.6.27-7-generic kernel in 8.10 but when I tried adding a network key I was getting the error in dmesg: 

[ 259.371082] wlan0: disassociating by local choice (reason=3) [ 261.368183] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate

I'm back using kernel version 2.6.20-16-386 with the ipw3945 driver which is working well with knetworkmanager which up to now has worked with my 8.10 installation.

Mathieu Allard

---

### Post by muadib on 2009-01-18
Just a quick update. I want to write that this is solved for me. I had been using an older kernel and upgrading to the new kernel seems to have done the trick. I now use the iwl3945 driver and things are working.

---

### Post by dwilinux on 2009-01-20
hello, when i read this FAQ i consider that i have same problem with my wireless, the hardware is pro/intel 3945, and i have installed linx backports modules hardy generic now, but the problem is, when i type :
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1

the output is :
"WARNING: /etc/modprobe.d/alsa-base line 40: ignoring bad line starting with 'option'"

what is that mean ? what i have to do?hope your help please.thx before

---

### Post by florinbrasov on 2011-04-27
For me did work:
```
sudo modprobe acer-wmi
```For run thi command every time when computer starts add this comand in **/etc/rc.local**, but the last line must be always 
```
exit 0
```

---

