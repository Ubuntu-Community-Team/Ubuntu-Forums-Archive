---
title: "How to make Ubuntu Stop trying to connect to a wifi network?"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by kramer65 on 2010-11-18
Hello,


I've got a build-in wireless card which cannot connect to my home network. It constantly gives an error and a prompt where it again asks for my WPA-key. Since it obviously didn't work out I used an external USB wifi-connector which now works like a charm. 

The only annoying thing is that the build-in wireless card continues to search for the wifi network. This results in the continuously re-appearing of the error message and the promp (which I now always cancel) which is very very annoying during work. :cry:

How do I stop Ubuntu from trying to connect to the wireless network through the build-in wireless card?

Any tipes are welcome to solve this issue!

---

### Post by C0derBear on 2010-11-18
I don't know the details, but there is probably a way of simply disabling the device completely.

Possibly through one of the control files in /etc/ (under network/ maybe?) - somewhere buried there will be a control file for each hardware network interface found and I dimly recall that you can disable the interface through that.

You may be able to do it through a GUI network control component via the Administration menu too.

... I'm still blundering my way about the system to find all the controls, and have a surprisingly nice lack of problems that need resolution so I haven't needed a bunch of them yet ...

regards.

---

### Post by Grenage on 2010-11-18
Can you not right-click on the network manager, select *edit connections*, select *wireless*, then delete the connections?

---

### Post by theozzlives on 2010-11-18
Most laptops have a switch to turn off the internal card.

---

### Post by miegiel on 2010-11-18
> **kramer65 said:**
> ...

How do I stop Ubuntu from trying to connect to the wireless network through the build-in wireless card?

...

If what **Grenage** doesn't work (because you need the other wifi device to connect to that network). Try finding the wifi on/off key combination on your laptop (assuming you have a laptop), it should only turn off the internal wifi.

---

### Post by kramer65 on 2010-11-18
Hi Guys, thanks for the tips, but so far no good. Grenade's tip is indeed good, but I do need to use that network (just through the external USB-connector) so I cannot delete it.

Since I do not have a laptop, but a simple desktop, I can also not disable the wifi using a switch.

Maybe the tip of COderbear would work, but I don't know much about that. Maybe somebody else knows more about that..?

---

### Post by c2tarun on 2010-11-18
just in case if nothing suggested works.
got to system>administrator>Hardware Drivers
there u'll see ur built-in wifi driver.
select it and then remove it.

---

### Post by kramer65 on 2010-11-18
> **c2tarun said:**
> just in case if nothing suggested works.
got to system>administrator>Hardware Drivers
there u'll see ur built-in wifi driver.
select it and then remove it.

I think something like this would be perfect! When I click the Harware Drivers option it starts searching for drivers after which it shows that a non-free driver is used for my Nvidea card. I do not get a list of hardware drivers that are currently in use. Any idea how else I can show a list of my hardware to disable to wifi card?

---

### Post by matt_symes on 2010-11-18
Hi

If you can determine you wifi card driver name using (from the terminal)

sudo modprobe -l

you can add an entry to black list and stop the driver being loaded at startup.

The blacklist file is in

/etc/modprobe.d/blacklist.conf

and you can add an entry of the form

blacklist driver-name

Typing (at the terminal)

cat /etc/modprobe.d/blacklist.conf

will show you what you already have blacklisted in the file.

What is you internal WIFI model and chipset?

Kind regards

---

### Post by kramer65 on 2010-11-18
> **matt_symes said:**
> Hi

If you can determine you wifi card driver name using (from the terminal)

sudo modprobe -l

you can add an entry to black list and stop the driver being loaded at startup.
............

Hi Matt, Thanks for the help, but I am not THAT advanced yet. Let me start from the beginning. I ran "sudo modprobe -l" in the terminal and got a humongous list in which I saw this:
```
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/net/wireless/strip.ko
kernel/drivers/net/wireless/arlan.ko
kernel/drivers/net/wireless/wavelan.ko
kernel/drivers/net/wireless/netwave_cs.ko
kernel/drivers/net/wireless/wavelan_cs.ko
kernel/drivers/net/wireless/orinoco/orinoco.ko
kernel/drivers/net/wireless/orinoco/orinoco_cs.ko
kernel/drivers/net/wireless/orinoco/orinoco_plx.ko
kernel/drivers/net/wireless/orinoco/orinoco_pci.ko
kernel/drivers/net/wireless/orinoco/orinoco_tmd.ko
kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko
kernel/drivers/net/wireless/orinoco/spectrum_cs.ko
kernel/drivers/net/wireless/airo.ko
kernel/drivers/net/wireless/airo_cs.ko
kernel/drivers/net/wireless/atmel.ko
kernel/drivers/net/wireless/atmel_pci.ko
kernel/drivers/net/wireless/atmel_cs.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/prism54/prism54.ko
kernel/drivers/net/wireless/hostap/hostap.ko
kernel/drivers/net/wireless/hostap/hostap_cs.ko
kernel/drivers/net/wireless/hostap/hostap_plx.ko
kernel/drivers/net/wireless/hostap/hostap_pci.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
kernel/drivers/net/wireless/rtl818x/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187.ko
kernel/drivers/net/wireless/ray_cs.ko
kernel/drivers/net/wireless/wl3501_cs.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/zd1201.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas/libertas_spi.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
kernel/drivers/net/wireless/ath/ath.ko
kernel/drivers/net/wireless/mac80211_hwsim.ko
kernel/drivers/net/wireless/wl12xx/wl1251.ko
kernel/drivers/net/wireless/wl12xx/wl1251_spi.ko
kernel/drivers/net/wireless/wl12xx/wl1251_sdio.ko
kernel/drivers/net/wireless/wl12xx/wl1271.ko
kernel/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko
```
Ehm.. here I am kinda lost. Which one is the wireless driver? And what should I do now..?

---

### Post by Sylslay on 2010-11-18
Laptops have a switch to turn off the wi-fi and if they don't theree is an BIOS option to turn it off, see PCI option in bios.

---

### Post by matt_symes on 2010-11-18
Hi

Lets take a step back here actually. Have you tried disabling the internal wifi card from the BIOS?

EDIT: Sorry Sylslay. Missed your post.

Kind regards

---

### Post by kramer65 on 2010-11-18
> **matt_symes said:**
> Hi

Lets take a step back here actually. Have you tried disabling the internal wifi card from the BIOS?

EDIT: Sorry Sylslay. Missed your post.

Kind regards

I have no idea how to do that. Could you help me out here a bit..?

---

### Post by matt_symes on 2010-11-18
Hi

No problem. What you will need to do is reboot your PC and as it is restarting (i.e. displaying the very first text or boot screen and when it beeps) press and hold a particular key on your keyboard and this will take you to the BIOS menu.

Unfortunately, the key you need to press is different depending on the make of your PC. 

So, in the first instance, what is the make of your PC?

Kind regards.

---

### Post by freak42 on 2010-11-18
get a command line shell type

```
ifconfig
```


it will list your network adapters like this:
```
wlan0     Link encap:Ethernet  HWaddr 00:16:ea:XX:XX:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
eth0      Link encap:Ethernet  HWaddr 00:23:7d:XX:XX:XX  
          inet addr:111.111.111.111  Bcast:111.111.55.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:45892718 (45.8 MB)  TX bytes:5908583 (5.9 MB)
          Memory:db300000-db320000 
```
where eth0 and wlan0 are the names needed to configure.
Find the internal wlan reference (like wlan0 or wifi0 or wlan1,..etc) (The wifi one that obviously is not connected)

and then disable the adapter like this

```
sudo ifconfig wlan0 down
```
(enter your password)
where wlan0 reflects your internal wifi.

hth, I don't know whether this will survive a reboot though.

---

### Post by matt_symes on 2010-11-18
Hi

> hth, I don't know whether this will survive a reboot though.

Unfortunately it will not. :(

Kind regards

---

### Post by kramer65 on 2010-11-18
> **matt_symes said:**
> 
So, in the first instance, what is the make of your PC?

I must admit I have no idea. It is put together by the local pc-shop. Is there a way to find out?

---

### Post by matt_symes on 2010-11-18
Hi

Actually my question should have been, what is the make of your BIOS. When you first start your machine, it will flash it up as text for a second or so. It will also tell you what key you need to press to enter the BIOS, but it might also be called setup or some other. Usually its DEL, F2, F12, F10 or ecsape, but it could also be different.

Below is a list of standard PC makes and the key presses needed to get into the BIOS.

[http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm](http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm)

What you need to do is identify the BIOS. In your BIOS there should be an option to disable the internal wifi card.

If you can identify the BIOS and post it back on here, i will see if i can get some screen shots from the web showing you what you need to change.

Kind regards

---

### Post by kramer65 on 2010-11-24
Hi Matt_symes. Last time I suddenly had to leave and after that I went on a long weekend away. I just got back to my pc and I have time right now, so I hope you or somebody else who knows about disableing my wifi from bios is around.

So I got into my (ami)bios using the delete key. Within the bios I am kinda lost though. Does anybody know what to do from there?

---

### Post by matt_symes on 2010-11-24
Hi

On the main BIOS menu there should be a number of options. You use the up and down arrow keys and press the enter key to select that option.

One of them should be Integrated Peripherals, or something similar.

Navigate to this using the up and down arrow keys and press enter when it is selected.
Hopefully one of the options will be to disable the on board wireless card. 

If it is there, hit enter to disable it. It should say disabled, or something.

Press the Esc key to exit the page and it should take you back to the main menu.

You then need to save the changes and exit the BIOS. Make sure they are saved.

I don't have Amibios myself, so this is a bit of a hunch.

Kind regards.

---

