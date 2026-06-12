---
title: "New hardware, Mobo Problems"
date: 2014-01-21
forum: Networking &amp; Wireless
---

### Post by XBMC old School on 2014-01-21
Hey all, 

Been looking online for Tuts to fix my problem and have had no luck. I got a new [z87n Mobo]("http://www.gigabyte.com/products/product-page.aspx?pid=4600#sp") and none of the LANS or the WIFI work. I figure at least one of the Atheros would have worked out of the box. Right now I'm at a loss. I am going to run 13.10 as a liveCD to see if it supports it. I am on Ubuntu 12.04 now, but have a 12.3.6 compiled kernel. I have run dmidecode & lshw to determine what intel, Atheros & wifi card is on the board.

Intel Connection 1217-V
Qualcomm Atheros AR8161

---

### Post by chili555 on 2014-01-21
> have a 12.3.6 compiled kernel.What is that?? Please open a terminal Ctrl+Alt+t and show us:```
uname -r
```Your description of your network devices is plenty brief. How about:```
lspci -nn | grep -e 0200 -e 0280
```That funny pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by XBMC old School on 2014-01-21
Hey Chili555: Ya my apologise I mistyped, my Current Kernel is 3.12.3

[HTML]00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
[/HTML]

Nice NUC dude

---

### Post by chili555 on 2014-01-22
> Nice NUC dude Thanks! Unlike most of you guys, I'm not using mine as an HTPC. I use it for photo editing attached by HDMI to a 24" monitor that's calibrated regularly.> 00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)Every one of these should work with kernel version 3.12.x. The wireless does require firmware which we will address. First, the ethernet; I am surprised that your mobo has two different brands of ethernet; or did you add one? I suggest you attach the ethernet cable to one of the ports and then let's load the drivers for both and examine the logs to see what happens:```
sudo modprobe alx
sudo modprobe e1000e
dmesg | tail -n10
```Once we see what the result is, we can proceed.

Now let's load up the wireless firmware:```
cd /lib/firmware
sudo mv iwlwifi-7260-7.ucode  iwlwifi-7260-7.ucode.bak  <--If it doesn't exist, that's OK, just proceed
sudo wget https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode
```Unload and reload the driver so it sees and uses the newer firmware:

```
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```Please note and post any errors, warnings, smoke, sparks, etc.

---

### Post by XBMC old School on 2014-01-28
Hey Chili,

Feel like a douche but I did a full wipe of my install and loaded Ubuntu-gnome 13.10. Now I'm into the awesome "out of the box" functionality that is Ubuntu.

---

### Post by chili555 on 2014-01-28
> **XBMC old School said:**
> Hey Chili,

Feel like a douche but I did a full wipe of my install and loaded Ubuntu-gnome 13.10. Now I'm into the awesome "out of the box" functionality that is Ubuntu.We're glad it's working! Have fun!

---

