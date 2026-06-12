---
title: "No 'Network' or 'Network Manager'"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by Maximum Bison on 2010-05-31
I have recently converted to Ubuntu. It all worked fine except my wireless drivers seem to be in a muddle. Sometimes my wireless will say "device not ready" and sometimes it'll simply be disconnected, with the option to 'Create New Wireless Network'

I assume I have to something different to what I'm doing there, because in the new wireless network option it doesn't connect me. I've looked around the forums and everyone is saying to go into "Network" or "Network Manager" to scan for local wireless networks but neither of these options are in my System -> Admin.

I do have "Network Tools" and had hoped it was the same thing but any guides I try to follow lose me because it would seem they are NOT the same thing.

I am on a Samsung N130 netbook. I am using the same installation of Ubuntu (9. I think it is) that my friend used on his Acer Netbook (which he was able to use with no problems)

I'm a total noob, I know. But I want to learn how all this works so any advice given, I'd appreciate how it all works too. I don't want to just remember commands to put in the terminal without any idea of what they mean...

thanks in advance. I'm going to the zoo now.

---

### Post by mbzn on 2010-05-31
Just click on the network icon in the top right next to the volume. the wireless should show all available networks.

---

### Post by Paddy Landau on 2010-05-31
I would suggest that you download and install the latest version of Ubuntu (version 10.04). It will have the latest drivers, and will be supported for three years, unlike versions 9.04 and 9.10.

---

### Post by Maximum Bison on 2010-05-31
I'm on 10. and its still not working. In fact, it now says 'device not ready' - I've tried some fixes and tried installing my windows drivers using 'windows wireless drivers' but it still says device not ready.

Before this, though, I could find my netgear but there was nothing in the way of actually connecting to it.

---

### Post by Paddy Landau on 2010-05-31
Here are two ideas for you to try.

[LIST]
[*]As you haven't connected to the Internet, it's possible that your installation hasn't been able to download the correct drivers.
[LIST=1]
[*]Connect your computer via Ethernet to the Internet.
[*]Run System > Administration > Update Manager.
[*]Press Check.
[*]Install all updates (if any).
[*]Repeat steps 3 & 4 until there's nothing left to update.
[*]Reboot.
[*]Check whether this solves the problem.
[/LIST]
 
[/LIST]

[LIST]
[*]If that doesn't solve the problem, do you have access to the Windows drivers for your wireless? You may be able to use [ndiswrapper]("http://manpages.ubuntu.com/manpages/lucid/man8/ndiswrapper-1.9.8.html"), which uses Windows drivers in your Linux installation. Again, you'll have to connect to the Internet via a wire in order to download and install (use Ubuntu Software Centre to install Ndiswrapper driver installation tool). I don't remember how to use it, but you'll find plenty of information on this forum and through Google; if you get stuck, post again.
[/LIST]
If neither of those solutions works, then post the model number of your wireless here. I'm not an expert, so someone else may be able to help.

---

### Post by Maximum Bison on 2010-05-31
Ahh I will most certainly try that. However, I dont have an ethernet connection until tomorrow (I'm currently back on my God-forsaken Windows7 Starter at a friends' house...) I will definately give it a go.

Will update you tomorrow. Thank you again for the advice.

EDIT- I installed Ndiswrapper and ngdis... something. I believe I found my Realtek .inf - but now there is no wireless option on my laptop at all. Neither "not ready" or "disconnected".

---

### Post by BandD on 2010-05-31
Go to Accessories --> Terminal.  Once the terminal window is open type the following command: ```
lshw | grep -i network
```

That will tell us what wireless card you have and maybe we'll be able to track down the right driver.

---

### Post by Paddy Landau on 2010-05-31
In addition to BandD's post:

If a native Linux driver works, that would be preferable to a Windows driver under ndiswrapper. If BandD helps you find the right driver, you'll need to uninstall ndiswrapper.

---

### Post by Maximum Bison on 2010-06-01
There are no updates for me to do. My Ndis says the driver for my wireless card are installed, but the wireless option is still completely missing from my network quicklink-thing up on my top toolbar (next to volume)

When I type what BandD said into my terminal, I get this


WARNING: you should run this program as super-user.
           *-network UNCLAIMED
                description: Network controller
           *-network


If I try "lspci | grep -i network" I get this


02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)

Beginning to feel even more lost now... can't seem to find any drivers for a Realtek 8192...

---

### Post by Paddy Landau on 2010-06-01
> **Maximum Bison said:**
> WARNING: you should run this program as super-user.
Use this:
```
sudo lshw | grep -i network
```

---

### Post by Paddy Landau on 2010-06-01
Actually, you may get a little more information with this:
```
sudo lshw -class network
```

---

### Post by Maximum Bison on 2010-06-01
*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:54:56:9b:f8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.6 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:3000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)


That's what I get...

---

### Post by BandD on 2010-06-01
you can check out this thread [http://ubuntuforums.org/archive/index.php/t-1440170.html]("http://ubuntuforums.org/archive/index.php/t-1440170.html").  There are some useful links there that might help you out.  I'm at work now so I can't do much more than point you there for now...

I'll check back though.

---

### Post by Maximum Bison on 2010-06-02
I'm going to try a reinstallation and see if that fixes anything. My problem seems to be ever-changing. First the wireless device wasn't ready, then it was just disconnected and I couldn't scan for local devices, then I couldn't even see I had a wireless device.

I have followed numerous guides and I have either hit walls with directories not being found, or the fact that ndiswrapper has installed the correct drivers but nothing has happened.

I can't reinstall until I get my USB back so I'll create a new thread once I've done a fresh install. Thanks for everyone who's tried to help.

---

### Post by Paddy Landau on 2010-06-02
> **Maximum Bison said:**
> I'm going to try a reinstallation...
Good idea.

Here's a good tip:

Connect your computer to the Internet using a wired Ethernet before you start the installation, so that the installation can access the Internet to download any drivers that it may need.

When you boot the first time, keep the Ethernet plugged in and run the Update Manager. Reboot. You may need to rerun the Update Manager and reboot again.

Test your wireless only after you've done all that.

---

