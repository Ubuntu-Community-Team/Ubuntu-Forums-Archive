---
title: "Broadcom BCM4313: 14.04 wireless keeps disconnecting"
date: 2015-02-27
forum: Networking &amp; Wireless
---

### Post by Crissie on 2015-02-27
I've already tried most of the things I found on internet. I updated the kernel from 3.13 to 3.18, I deactivated that N thing, but it keeps getting disconnected every minute. It's not the internet, since I can connect perfectly on other PCs, and even on this one with Windows (dual boot), so it's not the PC either.

I'm not good with terminal or commands or anything, all I can do is paste commands from internet, so I made a thread because I really need help since I don't know how to fix this myself and internet has not helped.

I have Ubuntu 14.04, everything was fine on 12.04 and 13.10, but since I updated it's been a nightmare to stay connected for more than a minute.
My computer is a Dell Inspiron N5050 laptop.

And I saw someone else post this on a similar thread, so I guess it might be helpful:

iwconfig
> eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Demian"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: B4:75:0E:8E:38:7A   
          Bit Rate=65 Mb/s   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:24   Missed beacon:0


lo        no wireless extensions.




---

### Post by jeremy31 on 2015-02-27
I would guess this might be an intel wifi card but post the results from ```
lspci -nnk | grep -iA2 net
```
and post ```
cat /etc/modprobe.d/iwlwifi.conf
```

---

### Post by Crissie on 2015-02-27
> **jeremy31 said:**
> I would guess this might be an intel wifi card but post the results from ```
lspci -nnk | grep -iA2 net
```
and post ```
cat /etc/modprobe.d/iwlwifi.conf
```

Here's the result:

lspci -nnk | grep -iA2 net
> 05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0504]
    Kernel driver in use: r8169
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0013]
    Kernel driver in use: bcma-pci-bridge

cat /etc/modprobe.d/iwlwifi.conf
> options iwlwifi 11n_disable=1

---

### Post by Hadaka on 2015-02-27
hi,please open a terminal..ctrl/alt/t then copy
and paste one line at a time...ignore any error or warnings.
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit 0
```
then do
```
sudo modprobe brcmsmac
sudo modprobe bcma
```
and since you dont have an inel card..you have a broadcom card
let's remove the driver you inserted in error to avoid any possible
conflict.
```
sudo rm /etc/modprobe.d/iwlwifi.conf
```
reboot and test

---

### Post by Crissie on 2015-03-01
Did it. It was working fine but it just disconnected. ):

I'll give it some more time, just in case.

---

### Post by Crissie on 2015-03-03
It doesn't disconnect as frequent as it did before, but it still does it every day.

---

### Post by Hadaka on 2015-03-03
please run and post the wireless info text from here
 [http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
thanks

---

### Post by Crissie on 2015-03-04
Here it is: [ATTACH=CONFIG]260447[/ATTACH]

---

### Post by Hadaka on 2015-03-04
hi,please do..
```
sudo iw reg set VE
sudo sed -i 's/^REG.*=$/&VE/' /etc/default/crda
```
then do and reboot after,,
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
thanks.

---

### Post by Hanjonah on 2015-03-06
-

---

### Post by jeremy31 on 2015-03-06
> **Hanjonah said:**
> Hey guys, 

Actually I have the same problem - and I also tried everything I found online unsuccessfully until now. I am also pretty new to ubuntu and don't know anything about fixing problems, so I am happy to have found this post. 

I ran the commands you suggested and these are my results:

```
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:2246]
	Kernel driver in use: r8169
09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Hewlett-Packard Company Device [103c:2231]
	Kernel driver in use: rtl8723be


```


and 


```
options iwlwifi 11n_disable=1
```

Any suggestions on how to keep me connected? Thank you a lot!

You may have the same problem but different wifi card and need a different solution.  This should work for you [http://ubuntuforums.org/showthread.php?t=2267853&p=13239947#post13239947](http://ubuntuforums.org/showthread.php?t=2267853&p=13239947#post13239947)

And if your kernel updates look a couple posts down to see how to fix it then

---

### Post by Hadaka on 2015-03-06
@Hanjonah, hi this...>options iwlwifi 11n_disable=1
is a command for an Intel radio not a realtec.
your radio..wifi card and ethernet card are both realtec cards.
The wifi card for this thread is a broadcom. Please start you own thread.
thanks

---

### Post by Crissie on 2015-03-08
> **Hadaka said:**
> hi,please do..
```
sudo iw reg set VE
sudo sed -i 's/^REG.*=$/&VE/' /etc/default/crda
```
then do and reboot after,,
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
thanks.

Did it, it's still disconnecting.

---

### Post by MrSteve on 2015-03-09
a search in the software centre for broadcom shows drivers/firmware for the broadcom wifi chipsets
but am unsure which driver/firmware you require ...

---

### Post by Hadaka on 2015-03-09
@crissie
please do..
```
echo "options b43 11n_disable=1" | sudo tee -a /etc/modprobe.d/blacklist-b43.conf 
sudo modprobe -rf b43
sudo modprobe b43
```
and post the output of..
```
cat /etc/default/crda
```
thanks

---

### Post by Crissie on 2015-03-09
Done.

Output of: [COLOR=#000000][FONT=Ubuntu Mono]cat /etc/default/crda

[/FONT][/COLOR]```
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.


REGDOMAIN=VE
```

> **MrSteve said:**
> a search in the software centre for broadcom shows drivers/firmware for the broadcom wifi chipsets
but am unsure which driver/firmware you require ...

I'd update it/change it if I knew how or which one I can use, and also if it might help solve the problem.

---

### Post by MrSteve on 2015-03-10
looking at your code it maybe the last entry on the list b43 firmware installer
but also the 3rd entry down broadcom-sta-common has the 4313 driver 

open the software centre and place broadcom in the search box 
this will give you a list of about 12 install options the entry's are stated above

i don&#8217;t believe it will cause any problems installing the driver then using the firmware installer  
a restart maybe required after install of the b43 firmware ...

---

### Post by Crissie on 2015-03-10
I only get one result when I search for broadcom, "Ubuntu User 05 (Edición en Español)", it's a magazine.

---

### Post by MrSteve on 2015-03-11
have you enabled all the repositories in the software centre ? ...

---

### Post by Crissie on 2015-03-12
I believe so. How can I check that?

---

### Post by MrSteve on 2015-03-12
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Crissie on 2015-03-13
They're all enabled.

---

### Post by wildmanne39 on 2015-03-13
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 

The driver you need does not require you to install firmware.

Why are you using the 3.18 kernel?
Thanks

---

### Post by Crissie on 2015-03-15
> **Wild Man said:**
> Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 

The driver you need does not require you to install firmware.

Why are you using the 3.18 kernel?
Thanks

Hi, here it is.

Before making this thread I read updating the kernel would help solve my problem, so I gave it a try.

---

### Post by wildmanne39 on 2015-03-15
I have just left town, I am on my cell phone. Hopefully some one else can look at the file you posted and get your WiFi going.

---

### Post by Crissie on 2015-03-15
It's okay, thank you! (:

---

### Post by wildmanne39 on 2015-03-15
I have a minute so I was looking at the file you posted it says the file is from the 4th of March and that the computer has not been rebooted since then either, could you please reboot and post a new report.
Thanks

---

### Post by Crissie on 2015-03-16
> **Wild Man said:**
> I have a minute so I was looking at the file you posted it says the file is from the 4th of March and that the computer has not been rebooted since then either, could you please reboot and post a new report.
Thanks

Rebooted a few hours ago, here's the new report.

---

