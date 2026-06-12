---
title: "Disable Wireless"
date: 2013-09-28
forum: Networking &amp; Wireless
---

### Post by CrzPW74 on 2013-09-28
How can I disable the wireless driver or chip? To clarify, I do Not want the wireless to work or be turned on unless I turn it on (via terminal).
Thanx in advance

---

### Post by TheFu on 2013-09-28
> **CrzPW74 said:**
> How can I disable the wireless driver or chip? To clarify, I do Not want the wireless to work or be turned on unless I turn it on (via terminal).
Thanx in advance

I don't5 know the official way, but removing the driver will certainly disable it. On my laptops, there is also a BIOS enable/disable Fn+some-function-key to enable/disable it.  After it ihas been disabled through the Fn key-chord, a few manual steps are necessary to re-enable wifi. Those will be different based on your Ubuntu desktiop.

---

### Post by Hadaka on 2013-09-28
Hi, please post the output of..
```
lspci -nnk | grep -iA3 net
```
so we can determine your wireless driver.
thanks.

---

### Post by CrzPW74 on 2013-09-29
Thank you  both for responding 
It is very scary inside the sacred terminal but I made it in and out safely and here is the output lol,
~$ lspci -nnk | grep -iA3 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0504]
    Kernel driver in use: r8169
    Kernel modules: r8169
09:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0013]
    Kernel driver in use: wl
    Kernel modules: wl, bcma, brcmsmac
So what can I do now?:P

---

### Post by Hadaka on 2013-09-29
Hi, you are in luck!..your wireless is probably on
but..its not working. You have 3 drivers currently
attached to it. The best and eaisest way to disable your
wireless it to click the wireless icon..next to the envelope
upper right corner. Then, simply uncheck **Enable Wireless**
from the command prompt you can enter these commands
..not needed if you do the above..but...
```
sudo modprobe -rf bcma
sudo modprobe -rf wl
sudo modprobe -rf brcmsmac
```
~~ **or**~~
you can turn the wireless feature **off** in your router.
so there ya go..3 differnt ways.

---

### Post by varunendra on 2013-10-02
Don't like unnecessarily bumping, but I found the topic interesting.

I am not sure if removing the driver also saves power on the wireless card. Most probably it does, I'm just not sure. However -
> **Hadaka said:**
> The best and eaisest way to disable your
wireless it to click the wireless icon..next to the envelope
upper right corner. Then, simply uncheck **Enable Wireless**
Easiest method indeed, if you don't have a hot key or hardware switch to do it on your laptop/netbook.

If you want to do it via terminal, then -
```
sudo rfkill block wlan0
```
Replace "wlan0" with whatever you wireless interface appears as in the output of "rfkill list" command. It is the same thing as what Hadaka suggested above, just the commandline way.

It sends the wifi card to "low power state" which is almost equivalent to totally turning its power off.

To bring it back again -
```
sudo rfkill unblock wlan0
```
..or tick again the "Enable Wireless" option in NM-applet menu.

**PS:**
This was answer to your original question. However, you clearly have a driver conflict as Hadaka mentioned. So if you wanted to do it due to some connection issue, you should instead ask for help on solving that (probably in a new thread).

---

### Post by CrzPW74 on 2013-10-05
Thank all of you ffor the help . Sorry to be so long in replying but was fishing. I will try the suggestions and i apologise for not being more detailed. The reason for disabling via terminal is that we gave my son my old laptop and he logs into the neighbors wifi when we cut him off lol. So if *I just toggle to applet switch he would toggle it back. So I thought I would just disable it entirely and let him use the* ethernet hook up.  Again thank all of you and I will try these asap.:P Alos I guess i should resolve that 3 driver issue and will start new thread if that is appropriate way.

---

### Post by TheFu on 2013-10-05
> **CrzPW74 said:**
> Thank all of you ffor the help . Sorry to be so long in replying but was fishing. I will try the suggestions and i apologise for not being more detailed. The reason for disabling via terminal is that we gave my son my old laptop and he logs into the neighbors wifi when we cut him off lol. So if *I just toggle to applet switch he would toggle it back. So I thought I would just disable it entirely and let him use the* ethernet hook up.  Again thank all of you and I will try these asap.:P Alos I guess i should resolve that 3 driver issue and will start new thread if that is appropriate way.

You could 
a) disable the built-in wifi
b) help the neighbor lock down their wifi with WPA2
c) get a cheap USB wifi dongle - take the dongle, no network access.
d) put the new dongle MAC into your router, so only that one works (plus your other parent devices).
This [blog post ]("http://blog.jdpfu.com/2011/06/10/kid-safety-checklist") and the comments discusses network access techniques for kids.

Of course, at some point, they need to be read for the full internet when they leave home.  I have friends who are freaked out by the level of network control on my home network. They think the kids should see it all and discuss the different parts of the internet with them. A different method, but just as valid.

---

