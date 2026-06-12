---
title: "I don't see any wireless networks.."
date: 2010-05-07
forum: New to Ubuntu
---

### Post by kramer65 on 2010-05-07
Hello,

We have wifi in our home, but when I click the network manager I don't see any wireless networks. On my android phone I see more than 10 wifi networks, so it must at least see something..

Does anybody have any idea what my problem could be?

---

### Post by bredman on 2010-05-07
Without knowing the type of wireless hardware, you are stuck.

Use the terminal (Ctrl-Alt-t) to enter the following commands to find out more about your hardware

lspci
lsusb
lshw

These list your PCI-connected hardware, your USB-connected hardware, and all your hardware. Look for anything which mentions wireless, WiFi, or 802.11.

Once you know the name of your wireless hardware, search the internet for Ubuntu and the name of your hardware. You should find loads of info.

Some wireless devices have restricted drivers which cannot legally be  distributed within Ubuntu, so you may have to add them manually. A very common problem is with Broadcom hardware, starting with a name like BCM43. In this case, you will need to download a program called b43-fwcutter which will install the correct firmware for you.

---

### Post by kramer65 on 2010-05-07
Ok, I've got this:

```
*-network
                description: Wireless interface
                product: AR5007G Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 1
                bus info: pci@0000:05:01.0
                logical name: wlan0
                version: 01
                serial: 00:13:f7:e2:ff:b9
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:febf0000-febfffff
```

I googled for "AR5007G Wireless Network Adapter" and indeed found some things talking about madwifi. As far as I understood however, these are already included in the kernel, and should therefore work. So I wouldn't know what now.. Any more tips..?

---

### Post by Dhee on 2010-05-07
Try right-clicking on the applet, and see if Wireless is is activated?

---

### Post by kramer65 on 2010-05-07
I tried that, and it is activated there..  :(

---

### Post by anewguy on 2010-05-07
Post the output of:

lsmod


Thanks
Dave ;)

---

### Post by kramer65 on 2010-05-07
Ehm.. In themeantime, I got myself another problem. The [Applications menu isn't showing anymore]("http://ubuntuforums.org/showthread.php?t=1476190") after Ubuntu totally froze.

If you have any idea about that? Or how would I start a terminal without the menu..?

---

### Post by the-edmeister on 2010-05-08
{Ctrl + Alt + T} to open the Terminal

---

### Post by anewguy on 2010-05-10
Sorry - didn't check the post for a couple of days.  Glad the-edmeister was able to get you to a terminal. 

As for getting your Applications menu back, I tried deleting mine to figure out how to get it back, but it deleted the entire Applications/Places/System menus.  To add them back in, I had to right-click on a blank spot in the top bar, select "Add to Panel", select "Menu Bar" and click "Add".

If you are just missing a single piece of that menu bar I'm not sure yet how to add it back in.

Dave ;)

---

