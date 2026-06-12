---
title: "NetworkManager finds networks, but won't connect"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by axelquobe on 2006-07-27
My setup is an IBM **thinkpad t23** with a Harris Semiconductor **Intersil Prism 2.5** wlan chipset.
I have the newest 2.6.15-26 686 kernel in use on top of a fresh install of dapper 6.06 running gnome.

I've compiled the **hostap** drivers found in /usr/src/hostap*** myself. The compilation went fine and I modprobed **hostap** and **hostap_pci**. I removed the orinoco and hermes drivers from *`uname -r`/kernel/drivers/net/wireless*, since blacklisting them didn't work.

No problems this far. The t23 boots nicely and lsmod shows that hostap and hostap_pci are loaded. The orinoco and hermes drivers are not present on the list.

After this I fetched **network-manager-gnome** with synaptic and rebooted. The nm-applet is launched upon startup and after a while I can see a list of wireless networks on the list. If I choose "connect to other wireless networks" I can also select WPA-encryption from the list. This implies that wpa_supplicant should be working.

When I try to connect to a wireless network nothing happens though. I can't even connect to unprotected networks, not to mention encrypted ones. A weird anecdote besides this is that if I enable WPA encryption in my router configuration, network manager only suggests WEP encryption when trying to log on to the network. WPA can't be seen on the list.

This problem is really frustrating, as I've already been fighting closer to three weeks with my wlan. It seems as I've gotten fairly close now though. I can see the networks, but can't connect to them.

Oh and btw. As soon as I plug in my ethernet cable, NetworkManager detects a wired connection and connects to it.

Please help.  :(

---

### Post by jftaal on 2006-07-27
I have the exact same problem! I hope some one can help us

---

### Post by linuxNewb on 2006-07-27
Sorry for the "I have same problem", but I do. I've asked for help many times here, but nobody has had a real answer. 

I can see wireless networks with network-manager-gnome, but it doesn't connect.

---

### Post by zalzoid on 2006-07-27
Same here.  I've installed Ubuntu on a Dell D610.  I like everything about it except that the wireless (ipw2200) does not work.  network-manager-gnome seems to detect wireless-networks.  But I cannot connect to any of them.  I've googled around and read everything I could find but have not found anyone who has had success with wireless using Dapper on a D610.  If I don't solve this reasonably soon, I will regretfully have to go back to Fedora where the wireless worked fine.

---

### Post by Eversmann on 2006-07-27
I guess it's a cheap answer, but i suppose you tried to run the wifi cards using ndiswrapper, right?

i had some problems with broadcom wifi, and network manager, and using it with ndiswrapper resolved them.

---

### Post by zalzoid on 2006-07-27
I did not try ndiswrapper as Dapper already comes with the ipw2200 driver installed.  I assume it must be running for network-manager-gnome to be able to detect the wireless networks around.  Certainly lsmod indicates it is running.

When I had installed FC4 on my Dell D610, the only step I needed to get it running was to copy the latest firmware and put it in place.  But Dapper seems to have the firmware already installed.

Somehow, it seems that I am really close since the wireless card detects the networks around.  But I cannot connect.

Do you think I should nevertheless, try ndiswrapper?  If so, could you point me to any steps that have worked for you?

Thanks much.

---

### Post by plexi50 on 2006-07-27
I have a Dell M140 with ipw2200 and it works with network manager fine, but sometimes it is a bit unstable. Be sure you don't have a wireless connection  setup in your network settings. Check your etc/networks/interfaces file and comment out any ssid or passwords that are stored there. Sometimes, I have to deactivate and activate my network eth1 to get the wireless to connect or start dhcp, no idea why, because it will work perfectly other times.

---

### Post by mattfitzct on 2006-07-27
Hi. I'm new to Linux and Ubuntu (6.06 Dapper Drake), and I have the identical problem: wireless network is visible, but connecting to it is impossible. I thought it may be related to ipv6, but I didn't make any headway with that assumption. My wired network (which I am using right now) works fine.
I installed network manager, but all that did for me was to reaffirm that the wireless network wasn't connected.
I read about ndiswrapper, and I downloaded it, but I have no idea what to do with it. I got as far as uncompressing the files, but after that I was lost. The INSTALL files said to run the command "make uninstall" and I got this:
bash: make: command not found
so I gave up.
The command "dmesg" gives me (among many other things):
ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
Googling that gave me this link:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34902](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34902)
I've read elsewhere about configuring wla0 (my wireless uses ra0), but I don't know what the difference is.
Any advice is greatly appreciated. I am trying valiantly to convert to a micro$oft-free life. My wife has an iMac G5, and I am using a run-of-the-mill PC - Athlon XP 1600 (soon to be 2800) on an Abit KD-7 Raid motherboard; 160GB HD and 1GB RAM. Once my Linksys wireless router works I'll have absolutely no reason to complain.
Thanks in advance,
Matt

---

### Post by Rabbiddog on 2006-07-27
> **zalzoid said:**
> I did not try ndiswrapper as Dapper already comes with the ipw2200 driver installed.  I assume it must be running for network-manager-gnome to be able to detect the wireless networks around.  Certainly lsmod indicates it is running.

When I had installed FC4 on my Dell D610, the only step I needed to get it running was to copy the latest firmware and put it in place.  But Dapper seems to have the firmware already installed.

Somehow, it seems that I am really close since the wireless card detects the networks around.  But I cannot connect.

Do you think I should nevertheless, try ndiswrapper?  If so, could you point me to any steps that have worked for you?

Thanks much.



I have already tried ndiswrapper. The various commands show it being enabled along with the drivers. Net manager sees my wireless network (ssid, and all) but won't let me connect.

The only thing I can think of doing is deleting my wirless network connections and hardware and starting over. I will post my reults.

---

### Post by zalzoid on 2006-07-28
To plexi50: I have nothing in /etc/network/interfaces except for my lo settings.

To Rabbiddog: I look forward to seeing your results.

More evidence that the D610 is particularly problematic with Ubuntu (see comment 18 from JPW at the end).

[http://en.magenson.de/2006/06/11/ubuntu-dapper-drake-and-wpa-encrypted-wireless/](http://en.magenson.de/2006/06/11/ubuntu-dapper-drake-and-wpa-encrypted-wireless/)

Here is someone who claims to have gotten wireless to work on the D610 using Dapper but they started out with Hoary, upgraded to Breezy and then to Dapper.  Perhaps there is some residue in that process that makes it work; or perhaps they did not try using the wireless after upgrading to Dapper.

[http://rdo.homelinux.org/ubuntu-linux-on-a-dell-latitude-d610/](http://rdo.homelinux.org/ubuntu-linux-on-a-dell-latitude-d610/)

---

### Post by mattfitzct on 2006-07-28
zalzoid wrote:
> ...
> [http://en.magenson.de/2006/06/11/ubu...pted-wireless/](http://en.magenson.de/2006/06/11/ubu...pted-wireless/)
> ...

Very interesting. I'll upgrade my encryption to WPA and try what is suggested in the above link. I'll post the results here.
The worst that can happen is that I totally hose my system and have to re-install (for the fifth time). Thankfully the install process takes all of ten minutes.

Matt

---

### Post by kabronkline on 2006-07-28
I am having very similar issues with network manager.

Gateway MX3560
IPW2200

---

### Post by namityadav on 2006-07-28
Guys,

I found one workaround (Till the good people at NetworkManager / ndiswrapper behave nicely with each other). I removed NetworkManager and installed netapplet instead (Obviously I had to enable the interfaces in /etc/network/interfaces again). It now lets me switch between eth0 and eth1 and lets me chose the wireless networks. Just what I wanted.

Hope this helps someone.

---

### Post by Eversmann on 2006-07-29
One thing: try to run networkmanager in debug mode.

I don't have NetworkManager installed right now, but run NetworkManager /? to see the switch to enable the debug manager. After that, run:

sudo killall NetworkManager

And then

sudo NetworkManager (switch to enable debug)

Keep it running and then run nm-applet and read what happens. Maybe all of this is a problem with wpa_supplicant and the driver. 

Have same problem with madwifi-ng and NetworkManager. 

Netapplet works cool, but not as cool as NM ;-)

---

### Post by TheOtherShoe on 2006-07-31
I am having the same problem with an orinoco chipset. In my case NetworkManager used to work fine, until I upgraded one day during Dapper development. From what I recall of reading the system logs, NetworkManager is now able to connect to wireless networks, but fails during the DHCP request.

My suspicion is that the latest version of NetworkManager requires your wireless card to have WPA support, even if you are not connecting to a WPA enabled network. My card is old enough not to have WPA support. Fortunately all other wifi software seems to still work, so I have also gone back to using netapplet for the time being.

---

### Post by joergenlie on 2006-10-09
What is the damn problem? I'm stuck where you are. BCM4311 with ndiswrapper 1.25. NM sees all the wired networks but won't connect. ANNOYING, since it is such a nice applet. If it works it improves linux wireless a 100 times. Anyone out there with the solution. if you have the answer you should be payed back in heaven.](*,) 
Some day hopefully this works.

We'll keep up the spirit

Jørgen

---

### Post by TheOtherShoe on 2006-10-09
This seems to be fixed in Edgy - at least it works for me after upgrading.

---

