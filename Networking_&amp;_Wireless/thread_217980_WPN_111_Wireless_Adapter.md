---
title: "WPN 111 Wireless Adapter"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by OctopusTwo on 2006-07-17
Hello

So I am attempting to install my WPN 111 Wireless Adapter.  So I followed a how to guide see below.
First, go into Synaptic Package Manager, and search for "ndiswrapper-utils"
2. Install it.
3. Go into Terminal and go to the directory where the .inf file and .sys file(s) are for the driver. (I had the CD for mine, but if you don't have one, research how to find your driver.)
4. Type in "sudo ndiswrapper -i driver.inf", where "driver" is the name of the .inf file.
(example: My .inf file was called "netwg111.inf". Yours will probably be different unless you have a Netgear WG111 usb or laptop card.)
5. Type in "sudo modprobe ndiswrapper"
6. Type in "sudo ndiswrapper -m"
7. Go into Networking (System > Administration > Networking
8. There should be a choice that says "Wireless Connection". It should also say that it is inactive.
9. Click "Wireless Connection" and then click properties.
10. Click "Enable this connection" and fill out the information accordingly. Make sure that you have the correct network name filled out. The Key type will normally be Hexadecimal. I don't know what the WEP key is, but I left it blank and it works fine. My network is configured with DHCP, so I chose DHCP as mine. If your network is not configured with DHCP, select "Static IP Address" and fill out the information accordingly.

So I attempted to what was said in the terminal at least twice.  (that is why it says files are already installed)  Through the sudo modprode… did not work and I wondering why.

oem@Jake:~$ sudo ndiswrapper -i netwpn11.inf
netwpn11 is already installed. Use -e to remove it
oem@Jake:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-amd64-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
oem@Jake:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

Also on step 8 I do not have a wireless option to click on.  Why?  I can do the steps after step 8 but I need something to click on.

This is my first time running Ubuntu.  It also told me once I logged in and was happy with it I was to install sudo-oem-config-prepare… not sure what that is or where it is or if this makes a difference for what I am trying to do.  I am running ubuntu-6.06-alternate-amd64 version.
Thanks for your help.  I am very much at loss of what to do.  So any help will be much appreciated.  Thanks

---

