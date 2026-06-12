---
title: "Automatically detect and change wireless network"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by Shardsofmetal on 2007-08-11
For some reason, gnome network manager can't automatically connect to my wireless network. I can connect to it by running the following commands ```
sudo iwconfig wlan0 essid network
sudo dhclient wlan0
```
I don't know what the problem is. The reason i want network manager to automatically detect and connect to the network is that soon I will be using my laptop at school and at home, and would like to have it automatically switch between them. Gnome network manager can see my network, because when i click the networking icon, it is provided as an option, and shows the signal strength. However, when i select it, it icon changes to a moving icon the lets you know it's trying to connect, then goes back to the old icon with 2 computers and an X. I am using an Xterasys XN-2423G CardBus PC Card. If there is any more information I can provide that will be useful, please tell me how to find it, and I will post. Thanks

---

### Post by Shardsofmetal on 2007-08-11
Can anybody help me?

---

### Post by kevdog on 2007-08-11
Is network manager in roaming mode???

Also can you post you /etc/network/interfaces file?? If interfaces are configured in this file, network manager will skip configuring these interfaces. 

Are you using feisty??

---

### Post by Shardsofmetal on 2007-08-11
Yes, network manager is in roaming mode. Also, yes, I am using Feisty. My /etc/network/interfaces file is as follows:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
```
Does that mean that the devices are configured in that file? If so, is there a way to unconfigure them so that network-manager can do it. Thanks for the help

---

### Post by kevdog on 2007-08-12
Im going to take one step back.

Can you tell me about your wireless card and driver
lspci -nn
lshw -C network

I dont want to assume anything at this point.

---

### Post by Shardsofmetal on 2007-08-12
Here is the information you requested: ```
zach@zach-laptop-ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:02.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:02.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:02.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:02.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:03.0 CardBus bridge [0607]: Texas Instruments PCI1251B [104c:ac1f]
00:03.1 CardBus bridge [0607]: Texas Instruments PCI1251B [104c:ac1f]
00:06.0 Communication controller [0780]: Agere Systems WinModem 56k [11c1:0449] (rev 01)
00:07.0 Multimedia audio controller [0401]: ESS Technology ES1969 Solo-1 Audiodrive [125d:1969] (rev 02)
01:00.0 VGA compatible controller [0300]: Neomagic Corporation NM2200 [MagicGraph 256AV] [10c8:0005] (rev 20)
02:00.0 Network controller [0280]: Texas Instruments ACX 111 54Mbps Wireless Interface [104c:9066]
zach@zach-laptop-ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@02:00.0
       logical name: wlan0
       version: 00
       serial: 00:e0:98:bf:88:8a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci ip=192.168.2.5 latency=64 multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:24020000-24021fff iomemory:24000000-2401ffff irq:11
```
Oh, and btw, after reading some other things about the issue, I changed my interfaces file so the only the top 2 lines are in it now.

---

### Post by Shardsofmetal on 2007-08-14
I'm sorry to double post, I just wanted to bump the topic.

---

### Post by imdano on 2007-08-14
You could give [wicd](http://wicd.sourceforge.net) a shot and see if it works any better.  You'll have to uninstall network-manager though.  If it doesn't work out you can just remove it, connect manually and redownload network-manager.

---

### Post by Shardsofmetal on 2007-08-15
OK, I got wicd to connect, which is more than I ever got from network manager. However, when I reboot, it doesn't automatically connect to the network. Also, I have it automatically run the tray icon at boot, and when it runs, it is just a blank icon. If i click on it, after like a minute of the computer appearing like it's doing nothing, the wicd window pops up, saying that no wireless networks were found. If I refresh, then it finds my network, and I can connect. (After I connect, the icon shows 2 computers and a bar with the signal strength.) But it should find the network as soon as it starts up. Also, in the sessions box, a program called Network Manager has an entry, which runs the command nm-applet --sm-disable. Should I disable that, or would it make a difference? Also, should I change any settings in network-admin? network-admin currently says wlan0 is not configured. 

Another minor issue, ever since I installed wicd, my cursor appears more jumpy. It's getting annoying, because the laptop only has 2.5MB video RAM, so as it is scrolling in firefox is not smooth, because after scrolling down 3 lines, it has to rewrite the whole screen before scrolling down any more. Anyway, I don't know if this is being caused by wicd, but I was wondering if anyone knew any way to fix this.

---

### Post by imdano on 2007-08-15
You should disable the nm-applet entry in Sessions, but you can leave network-admin alone.  I think the slow start-up problem might have been fixed in the latest version of wicd on the SVN.  What version did you download?  I can give you instructions on getting the lastest version from the SVN once I know that.  As for your video problems, if you kill the wicd tray/gui and as well as the daemon, does it go away?  I know I've heard of one person with a very, very old computer having trouble with wicd slowing his computer down a lot, so it could be causing problems for you.

---

### Post by Shardsofmetal on 2007-08-15
I have version 1.3.1 from the repository currently installed. Also, I killed tray.py, and so far my cursor hasn't jumped at all. It's a shame, because I think the tray icon is really useful. Maybe in the SVN version whatever causes this has changed. I didn't see any daemon running in system monitor, just killing that one python file fixed the curson issue. Anyway, I would appreciate hearing the instructions on upgrading to the SVN version. And thank you for telling me about wicd, it's much better than network-manager. :)

---

### Post by kevdog on 2007-08-15
Imdano is the best person to help you with this, but you first need to install the subversion package to download from svn:

sudo aptitude install subversion

Then download the svn wicd sources:
svn co [https://wicd.svn.sourceforge.net/svnroot/wicd](https://wicd.svn.sourceforge.net/svnroot/wicd) wicd_svn

Then:
cd wicd_svn
There will be 3 directories experimental, stable, testing

Once this is done, I would first uninstall wicd -- however you installed, ie Synaptic, you the same method to uninstall the old version (ie sudo aptitude purge wicd)

Hopefully imdano should provide the details.  I can remember which of these versions to choose (likely stable), and where to compile the files. (I think /opt/wicd).

---

### Post by imdano on 2007-08-15
The easiest way is probably this:
- Go to [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573), then download version 1.3.3
- Follow kevdog's instructions to get the wicd branches from the SVN.  
- Uninstall version 1.3.1 of wicd
- Install version 1.3.3
- Go into the wicd_svn/testing directory (normally I would say use experimental, but we just added some pretty drastic changes to it that are somewhat unstable right now), copy all the .py (autoconnect.py, daemon.py, gui.py, etc.) files in there, and paste them into the /opt/wicd folder.  Make sure they are all set with execute permissions using the comand ```
sudo chmod +x /opt/wicd/*.py
```
- Start the wiccd daemon with ```
sudo /etc/init.d/wicd start
```
- Start the tray icon and/or gui.

Hopefully that will work alright for you.  We're in the process of getting another testing release pushed out, so a lot of files are getting moved around on the SVN repo, and which means sometimes things get broken.  Let me know if you have trouble and I'll help you out.

Also what are you system specs?  I'm curious about why the tray is giving you slow down troubles.  I have a couple of ideas that might help a little bit.  No guarantees though.

---

### Post by kevdog on 2007-08-15
Imdano

Perhaps these svn installation instructions should be posted on the wicd website.  I went through the exercise once, but forgot how to do it later.  I appreciate your help.

---

### Post by imdano on 2007-08-15
Yeah, they probably should.  I'll ask Adam to add it to the download instructions page.

---

### Post by Gary.M on 2007-08-15
I have been running wicd on Kubuntu Feisty for some time now. I followed the instructions on the wicd site, added the repository listed...

deb [http://wicd.longren.org](http://wicd.longren.org) feisty extras

Then installed with the Adept package manager. Simple.

It installed without any fuss, said it was deinstalling Knetwork manager in the process (great because that never seemed to know what it was doing with my wireless).

I configured wicd to connect automatically to my wireless network using its conf screen and re-booted, held my breath, and....  connect.!  no problems, and sliently in the background...

No odd behaviour as reported in this thread with jerky mice etc...

---

### Post by imdano on 2007-08-15
I'm glad it's working out well for you.  For most people it does work fine, but there is (or was, my fix for it actually works) a bug with slow startup times if autoconnect is on but wicd fails to connect to the network.  The mouse slowdown problem I think is limited to people with *very* old hardware.  Every three seconds the tray icon updates your network information (which also redraws the icon picture in most cases), which for almost all people causes no problem, but on old machines where cpu cycles are scarce it can hurt system performance quite a bit.  I could try doing some things to ease the load (only redrawing the icon when it absolutely has to, updating the info less often), and see if it makes any difference.

---

### Post by Gary.M on 2007-08-16
Actually I have no tray icon... should I? Not that I need it...

---

### Post by yogo on 2007-08-16
> **Gary.M said:**
> I have been running wicd on Kubuntu Feisty for some time now. I followed the instructions on the wicd site, added the repository listed...

deb [http://wicd.longren.org](http://wicd.longren.org) feisty extras

Then installed with the Adept package manager. Simple.

It installed without any fuss, said it was deinstalling Knetwork manager in the process (great because that never seemed to know what it was doing with my wireless).

I configured wicd to connect automatically to my wireless network using its conf screen and re-booted, held my breath, and....  connect.!  no problems, and sliently in the background...

No odd behaviour as reported in this thread with jerky mice etc...


Mine was seamless, kinda freaked me out, I did not miss a step. I installed wicd and it removed network manager and I was connected "on the fly" no restart, configuration or anything.

---

### Post by imdano on 2007-08-16
> **Gary.M said:**
> Actually I have no tray icon... should I? Not that I need it...Hit alt+F2, type ```
/opt/wicd/tray.py
``` and it should start running.  You might want to add it to System->Preferences->Sessions as well.

---

### Post by Shardsofmetal on 2007-08-16
after removing 1.3.1, installing 1.3.3, then copying the svn .py files to /opt/wicd, the daemon does not run. I typed sudo /etc/init.d/wicd start, and it says that it's starting, but then i run the GUI program of the icon, and it was to start the daemon. Should I remove 1.3.3, download the most recent svn files again, then start the process over again?

---

### Post by imdano on 2007-08-16
When did you download the files from the SVN?  I fixed a couple of bugs in it a few hours ago that might have caused you some trouble.  Try running the daemon like this ```
sudo /opt/wicd/daemon.py
``` and paste any error messages you get here.

---

### Post by Shardsofmetal on 2007-08-16
The error I got was in intentation error in networking.py. I downloaded the newest files, copied networking.py and gui.py to /opt/wicd, and things work good now. When I have they tray icon running, the arrow does jump a little bit still. The icon doesn't slow my computer down in any other way, it just makes the arrow a little jumpy. I have a ThinkPad 390X with a 15" screen, PIII 500Mhz processor, 256MB RAM, and a NeoMagic MagicMedia 256AV 2.5MB video card. Any other specs can be found at [The ThinkWiki 390X Page](http://thinkwiki.org/wiki/Category:390X). Thanks

---

### Post by imdano on 2007-08-16
Ok, you could try this and see if the mouse behaves a little bit better.  Open /opt/wicd/edgy.py, and scroll down to the bottom of the file.  Look for a line that reads
```
gobject.timeout_add(3000,set_signal_image)
```That number means that every 3000ms (3 seconds) the tray gets updated.  Try raising that number a few thousand (a few seconds) and see if the mouse acts a little bit better.  Not sure if it will make a difference or not.

---

### Post by drippy on 2007-08-17
I have the same problem with the icon taking a very long time to show up at startup.. I installed 1.3.3 from the .deb file and that seems to have made the startup much faster than before, though still a little bit of lag.  I have a Dell 6400 with 54Mbps Dell 1390 Wireless (Broadcom driver).

---

### Post by imdano on 2007-08-17
Did you also download the new files from the SVN repository?

---

### Post by mastergunner on 2007-08-19
I dont even get an icon I get a plain white box. Can someone help me with this. Also I get 2 of these boxes at startup. I am a noob so can someone explain how to stop 2 boxes from coing up as well as what exactly is the icon I shoould be seeing.Thanks.

---

