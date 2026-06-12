---
title: "Full network tools missing"
date: 2020-09-11
forum: Networking &amp; Wireless
---

### Post by user-333 on 2020-09-11
First install of Ubuntu on ARM, using 20.04.1 LTS.  Once installed and booted with a desktop, I want to manage the network devices (wifi or wired) Clicking Settings:Network only gives me the option to add a VPN. There is no network icon in the main taskbar at the top of the desktop either. I thought managing network settings and devices would be included on any distro. What am I missing and where do I get it?

I want to set up fixed IP addresses for my interfaces and typically this is done through tools in the Settings area.

Thanks

---

### Post by TheFu on 2020-09-11
Sounds like something is wrong with the install.  [https://help.ubuntu.com/stable/ubuntu-help/net-wired.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-wired.html.en)
The Gnome3 Ubuntu desktop definitely has a control center and network area.

If there isn't any networking found, then perhaps the driver for the NIC isn't being loaded?  Exactly which ARM computer is being used? From where, exactly was the Ubuntu downloaded?

I've never tried Ubuntu on any ARM devices, so don't have experience. Sorry.
Actually, I don't use desktop controls for network setup. I prefer to configure using netplan text YAML files, but those are beyond what a typical end-user would use.

---

### Post by user-333 on 2020-09-11
Thanks for writing back.  I created the image on the SD card using the RPi imager for windows recommended on this page ([https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#2-prepare-the-sd-card](https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#2-prepare-the-sd-card)) I selected the 64bit Ubuntu 20 image.  From there I just booted the image, logged in as ubuntu (changed PW of course), then did the apt get update / upgrade. I then did a apt install ubuntu-desktop for the graphical interface. 

I have tried this install process several times using different desktops (Kubuntu (slooooow), Mate and now Ubuntu) thinking that perhaps it was the graphical packages causing the problem. Each time, the full network tools were missing.

Thanks for any insight you can provide.

---

### Post by CelticWarrior on 2020-09-11
What you did should work for RPi, but may not include support for others' network devices. So, again, *[COLOR=#000000]Exactly which ARM computer is being used?[/COLOR]*

---

### Post by TheFu on 2020-09-11
If you didn't get a desktop ISO, then you have the base internals for a server.  Servers are configured using text files. They don't have a GUI.
If you want a GUI that is fully integrated, then you'll want to install from a GUI, desktop ISO installer.

I bet the tools are on the system, but the NIC isn't recognized for some reason. Run:
**sudo lshw -C network ** and post the output. This will tell us much.

Also, a common troubleshooting technique is to boot into the desktop installer, but choose the "Try Ubuntu" option. This will run a live environment so sound, audio, networking and some other hardware stuff can be tested.  Does that allow the network to work or not?

And please answer ALL the questions already asked.  Not all ARM SoCs are the same, so swapping a r-pi image onto a different vendor's SoC probably won't work.  Pine64 needs a completely separate installer, for example.

---

### Post by CelticWarrior on 2020-09-11
> [COLOR=#000000]Also, a common troubleshooting technique is to boot into the desktop installer, but choose the "Try Ubuntu" option. This will run a live environment so sound, audio, networking and some other hardware stuff can be tested. Does that allow the network to work or not?[/COLOR]


AFAIK there's no "live mode" for ARM computers. The usual way doesn't even imply installation in the traditional way we understand for X86/x86_64, it implies "burning" the image to a SD card (or to an external USB drive in much more complex configurations) like the OP did by following the instructions in the link.

---

### Post by user-333 on 2020-09-11
I am using the Canakit 8 GB set ([https://www.amazon.com/CanaKit-Raspberry-4GB-Starter-Kit/dp/B08956GVXN/ref=pd_di_sccai_7?_encoding=UTF8&pd_rd_i=B07V5JTMV9&pd_rd_r=b0379250-241b-4c48-b5da-cb00c5df0a98&pd_rd_w=p4oWV&pd_rd_wg=n5zsc&pf_rd_p=5415687b-2c9d-46da-88a4-bbcfe8e07f3c&pf_rd_r=5Q3XBHGZ9K35SXGX0Z75&refRID=5Q3XBHGZ9K35SXGX0Z75&th=1](https://www.amazon.com/CanaKit-Raspberry-4GB-Starter-Kit/dp/B08956GVXN/ref=pd_di_sccai_7?_encoding=UTF8&pd_rd_i=B07V5JTMV9&pd_rd_r=b0379250-241b-4c48-b5da-cb00c5df0a98&pd_rd_w=p4oWV&pd_rd_wg=n5zsc&pf_rd_p=5415687b-2c9d-46da-88a4-bbcfe8e07f3c&pf_rd_r=5Q3XBHGZ9K35SXGX0Z75&refRID=5Q3XBHGZ9K35SXGX0Z75&th=1)) with the 32 GB.

I have just downloaded the Ubuntu ARM ISO and written it to the card using Etcher in case teh RPi imager I mentioned earlier isn't giving me everything.  I can't boot the image right now but will later and let you know what I find out.

Thanks for the help.

---

### Post by TheFu on 2020-09-11
ah. That's pretty expensive for a pi.  I bought a KIT w/ my v2 r-Pi just to be certain I had everything.  Quickly learned that only need 3 things:
[LIST]
[*]r-pi SoC - any model based on required performance, ram, etc. 
[*]cheapest case possible, there are sligt differences, especially of gpio adaptors are planned. 
[*]quality PSU - I use a 4-port, powered, USB hub. The pi4 models have largerpower needs, so f there is any doubt, get the official plug power device.
[/LIST]
Everything else is standard and better quality for less is available separately.

Also, any bit-for-bit copy tool can be used to get the bits from an image to the boot storage.  This applies for x86 Linux too. dd, ddrescue, mkusb, etcher (a hog), rufus, and plenty others exist.  R-pi don't have any BIOS, which is great and terrible.

fyi, [https://www.phoronix.com/scan.php?page=news_item&px=Raspberry](https://www.phoronix.com/scan.php?page=news_item&px=Raspberry) .  Price/performance isn't great for unscaled r-ps.

So others don't need to lookup the information, OP has a [COLOR="#FF0000"]**raspberry-pi v4 8G**[/COLOR].  And 64-bit Pi4 image should *just work* with the network hardware.  If the cable is connected and the switch port active and the network has a working dhcp server.  If the system has a netplan config file, just handle that.  /etc/netplan/ is the location.

---

