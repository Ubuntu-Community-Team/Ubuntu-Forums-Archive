---
title: "NVidia driver in intrepid root"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Corniger on 2009-02-19
OK, sorry for causing a thread to close where some people actually tried to help me out of days of frustration.

I want to root-install my NVidia drivers but I can't. I logged in as root but the installer tells me I'm probably running an X Server that I should exit.
I can't download anything because I can't get my WLan to connect (wg111v2). So I can only install a proprietary driver for now.

I posted my specs before:

> 00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Mass storage controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (rev 11)
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
01:08.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
07:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1) 

I don't know what to do anymore. Without internet and 3d graphics the whole system doesn't make any sense, seems like I've run out of luck with my hardware.

I'll install 804 now and see what happens. After that I'll give up.

---

### Post by Perfect Storm on 2009-02-19
Well, I don't know how well Ubuntu goes with root account. Never done it.


First would be to get your internet connection up and running as you need Ubuntu to get the nvidia drivers. If you can get access via wired it would be a good start.

I'll recommend you do this the Ubuntu way by disable root account again and start on a fresh. My guess is that 99% of all ubuntu users don't have root account enabled as we use sudo instead (and for safty issues).


When ready and if you have wired connection, check in "Hardware Driver" (should be somewhere in System tab) and see if a driver is available for your wireless.

---

### Post by Corniger on 2009-02-19
Well - my wireless is the root of all evil. I have no other means of connection, not even a cable. I followed all sorts of guides, always failing because  was either supposed to use the "Networking" menu item (that doesn't exist in "my" Ubuntu, which is a bug since July 2008) or because there's "no network configuration tool available" - although the gnome tool is installed. That at least counts for the NDiswrapper installation guide.

6 fresh installs later I simply can't make heads or tails out of this anymore. If I get help, I can't follow it, because "my" Ubuntu seems to be different.

Edit: wg111v2 is supposed to work out of the box. But it never connects. I can see Wlan networks, click them, input WPA pwd and it just disconnects. Editing the connection shows a scrambled pwd. I simply can't get an IP. I'm also never asked again for the pwd (like others), it simply never connects. All I can do is ask some neighbour if I can run a cable into his flat...

---

### Post by jerome1232 on 2009-02-19
Even to use nvidia's installer you will need an internet connection because you need the tools from the build-essential packages for the installer to compile the driver.

I think wifi is the problem to tackle first and foremost.


The basic steps to use nvidia installer would be to a) copy it to your home directory, then hit ctrl+alt+f1 to get a virtual terminal. Log in then do the following commands.  when I say <tab> that means hit tab to auto complete the filename.

Once again you need the package build-essential to successfully install this driver using nvidia's installer.

```
sudo -i
service gdm stop # if your using 8.04 then you need to do "/etc/init.d/gdm stop" instead
chmod u+x NVIDIA<tab>
./NVIDIA<tab>
nvidia-xconfig
exit
sudo service gdm start  # once again if your using 8.04 use "/etc/init.d/gdm start"
```

--edit--- I just saw this in another thread perhaps you can use it to use another computer to download build-essential to a usb thumb disk, it's just a thought.
[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

---

### Post by Corniger on 2009-02-19
Thanks Jerome!

The file I have is a *run file. I really need internet for that? :(
I've been fiddling around with a USB drive all the time, saving websites to it and so on.

The main problem with the Network: I can't get a connection. Or IP or whatever it is that keeps it from connecting. The device is there, wlan0, but it's going nowhere, the WPA pwd gets scrambled, but except for disconnecting nothing happens. I also can't run the ndiswrapper routine because an item in my menu is missing - networking. It simply isn't there and I'd have to access that.
I already tried to manually configure, but I simply can follow the instructions satisfactory due to my n00bdom. I have pages of code on my USB stick, but somehow I need to input a driver name somewhere and when I do the command seems wrong.

I tried to install 804, but Wubi won't download the installation files. I can't configure my system to boot from a specific device/HD, just general terms, so I can't install a "real" version of Ubuntu onto the dedicated drive. Some things that don't work in intrepid seem to work in hardy, what do I know :( I just know stuff is missing and I don't know how to get it to display in the gui...

---

### Post by Corniger on 2009-02-19
Just tried keryx. It just tells me, when I want to create a new project, that I should do this in the plugin's supported OS. Well. It's Win32 OS, so it should work.

I'm installing intrepid for the 7th time now... tomorrow I'll try to somehow get a Dual boot system up without intrpid but hardy. I read there's some weird partitioning required... Or is there a way to do it like WUBI does? Wubi doesn't create a boot partition for Grub, so how does that work? Or should I just leave Wubi as it is, not uninstall and install hardy over the actual inrepid install? That's a very naive approach, I know, but I don't know how this works and this is really killing me.

Edit: btw, is there some boot log? I always get 4 lines of notification about some memory aperture pointing somewhere and please set something, but it's always way too fast to read and ctrl-break doesn't work.

---

### Post by jerome1232 on 2009-02-19
> **Corniger said:**
> Thanks Jerome!

The file I have is a *run file. I really need internet for that? :(


Well no but that installer will fail without the build-essential package to build the driver, the build-essential package is a collection of programs that are necessary to compile programs.

Unfortunately I can't help with the wireless problem since mine is an artheros chip and works with madiwifi, totally different thing from your situation.

---

### Post by Corniger on 2009-02-19
OK, thanks anyway :) I'll just ry to find out more tomorrow, although I said to myself my time is running out.

I was just hoping that SOMEONE has an explanation why menu items aren't there. I even tried to install qdifferent language version to see if this was the problem. But no, it isn't there :(

Right now I'm stuck in a fabulous loophole trying to install packages for keryx.

python-wxgtk doesn't want to install without python-wxversion. wxversion doesn't wanna install without wxgtk. I'm going to sleep now. Good night.

---

### Post by jerome1232 on 2009-02-19
As for menu items not being there your probably following an outdated guide, since in intrepid that menu item isn't there anymore, you get the equivalent configurations through the network-manager applet in the top right of your screen. (says options or something I don't remember I use wicd instead of network manager.)

Along those lines you might want to try wicd as your network manager, it can work with some cards that network manager doesn't work with, there's some guides around here just search for them. Boils down to adding their ppa and installing it, which requires an internet connection :(

---

### Post by mac9416 on 2009-02-19
> **Corniger said:**
> OK, thanks anyway :) I'll just ry to find out more tomorrow, although I said to myself my time is running out.

I was just hoping that SOMEONE has an explanation why menu items aren't there. I even tried to install qdifferent language version to see if this was the problem. But no, it isn't there :(

Right now I'm stuck in a fabulous loophole trying to install packages for keryx.

python-wxgtk doesn't want to install without python-wxversion. wxversion doesn't wanna install without wxgtk. I'm going to sleep now. Good night.

Coringer, thanks for trying Keryx. This is a known problem with the dependencies. If you install all those packs by typing "sudo dpkg -i --force-depends <packname>", everything will install fine.
Good luck!

---

### Post by Corniger on 2009-02-20
> **jerome1232 said:**
> As for menu items not being there your probably following an outdated guide, since in intrepid that menu item isn't there anymore, you get the equivalent configurations through the network-manager applet in the top right of your screen. (says options or something I don't remember I use wicd instead of network manager.)

Along those lines you might want to try wicd as your network manager, it can work with some cards that network manager doesn't work with, there's some guides around here just search for them. Boils down to adding their ppa and installing it, which requires an internet connection :(OK, as it looks I might get Keryx to run, so chanvces are growing :)

For the missing menu items: I thought and read this was a [bug]("http://ubuntuforums.org/showpost.php?p=5376804&postcount=1"), but obviously not. I found one more guide from 2007 that doesn't comprise any of the "missing" items, maybe that will work :(

---

### Post by Corniger on 2009-02-20
@mac9416: OK, cool :) Is that a general problem or just on "my" Ubuntu? I'll try out right now!

---

### Post by Corniger on 2009-02-20
OK, I did as the tutorial said, downloaded a bunch of packages. But something did't work out, this is what I got:

>  sudo dpkg -i --force-depends *.deb
(Reading database ... 100662 files and directories currently installed.)
Preparing to replace acpi-support 0.114-0intrepid2 (using acpi-support_0.114-0intrepid2_amd64.deb) ...
 * Disabling power management...                                         [ OK ] 
Unpacking replacement acpi-support ...
dpkg-deb: unexpected end of file in version number in avahi-daemon_0.6.23-2ubuntu2.1_amd64.deb
dpkg: error processing avahi-daemon_0.6.23-2ubuntu2.1_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Preparing to replace cups-client 1.3.9-2ubuntu7 (using cups-client_1.3.9-2ubuntu7_amd64.deb) ...
Unpacking replacement cups-client ...
Preparing to replace gnome-cards-data 1:2.24.1.1-0ubuntu1 (using gnome-cards-data_2.24.1.1-0ubuntu1_all.deb) ...
Unpacking replacement gnome-cards-data ...
dpkg-deb: unexpected end of file in version number in gnome-control-center_2.24.0.1-0ubuntu7.1_amd64.deb
dpkg: error processing gnome-control-center_2.24.0.1-0ubuntu7.1_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Preparing to replace gnome-games-data 1:2.24.1-0ubuntu2 (using gnome-games-data_2.24.1.1-0ubuntu1_all.deb) ...
Unpacking replacement gnome-games-data ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing gnome-games-data_2.24.1.1-0ubuntu1_all.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/gnect/white_ob.cn4.gz')
Preparing to replace gnome-power-manager 2.24.0-0ubuntu8.2 (using gnome-power-manager_2.24.0-0ubuntu8.2_amd64.deb) ...
Unpacking replacement gnome-power-manager ...
dpkg-deb: unexpected end of file in version number in gnome-terminal_2.24.1.1-0ubuntu1_amd64.deb
dpkg: error processing gnome-terminal_2.24.1.1-0ubuntu1_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: unexpected end of file in version number in gnome-terminal-data_2.24.1.1-0ubuntu1_all.deb
dpkg: error processing gnome-terminal-data_2.24.1.1-0ubuntu1_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Preparing to replace gvfs-fuse 1.0.2-0ubuntu2 (using gvfs-fuse_1.0.2-0ubuntu2_amd64.deb) ...
Unpacking replacement gvfs-fuse ...
dpkg-deb: unexpected end of file in version number in language-pack-gnome-en_8.10+20081107_all.deb
dpkg: error processing language-pack-gnome-en_8.10+20081107_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: unexpected end of file in version number in libavahi-common-data_0.6.23-2ubuntu2.1_amd64.deb
dpkg: error processing libavahi-common-data_0.6.23-2ubuntu2.1_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Preparing to replace libbind9-40 1:9.5.0.dfsg.P2-1ubuntu3.1 (using libbind9-40_9.5.0.dfsg.P2-1ubuntu3.1_amd64.deb) ...
Unpacking replacement libbind9-40 ...
Preparing to replace libcupsimage2 1.3.9-2ubuntu7 (using libcupsimage2_1.3.9-2ubuntu7_amd64.deb) ...
Unpacking replacement libcupsimage2 ...
dpkg-deb: unexpected end of file in version number in libpam-runtime_1.0.1-4ubuntu5.3_all.deb
dpkg: error processing libpam-runtime_1.0.1-4ubuntu5.3_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: unexpected end of file in version number in libpango1.0-common_1.22.2-0ubuntu1_all.deb
dpkg: error processing libpango1.0-common_1.22.2-0ubuntu1_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Preparing to replace libpulsecore5 0.9.10-2ubuntu9.3 (using libpulsecore5_0.9.10-2ubuntu9.3_amd64.deb) ...
Unpacking replacement libpulsecore5 ...
dpkg-deb: unexpected end of file in version number in libscrollkeeper0_0.3.14-16ubuntu1_amd64.deb
dpkg: error processing libscrollkeeper0_0.3.14-16ubuntu1_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: unexpected end of file in version number in libsmbclient_3.2.3-1ubuntu3.4_amd64.deb
dpkg: error processing libsmbclient_3.2.3-1ubuntu3.4_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: unexpected end of file in version number in login_4.1.1-1ubuntu1.2_amd64.deb
dpkg: error processing login_4.1.1-1ubuntu1.2_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: unexpected end of file in version number in network-manager_0.7~~svn20081018t105859-0ubuntu1.8.10.1_amd64.deb
dpkg: error processing network-manager_0.7~~svn20081018t105859-0ubuntu1.8.10.1_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: unexpected end of file in version number in pulseaudio-utils_0.9.10-2ubuntu9.3_amd64.deb
dpkg: error processing pulseaudio-utils_0.9.10-2ubuntu9.3_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: unexpected end of file in version number in scrollkeeper_0.3.14-16ubuntu1_amd64.deb
dpkg: error processing scrollkeeper_0.3.14-16ubuntu1_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: unexpected end of file in version number in splix_2.0.0~rc2-0ubuntu2.3_amd64.deb
dpkg: error processing splix_2.0.0~rc2-0ubuntu2.3_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: unexpected end of file in version number in tracker_0.6.6-1ubuntu5.1_amd64.deb
dpkg: error processing tracker_0.6.6-1ubuntu5.1_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Preparing to replace ttf-opensymbol 1:2.4.1-11ubuntu2.1 (using ttf-opensymbol_2.4.1-11ubuntu2.1_all.deb) ...
Unpacking replacement ttf-opensymbol ...
Setting up acpi-support (0.114-0intrepid2) ...
 * Checking battery state...                                                    
/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
                                                                         [ OK ]

Setting up gnome-cards-data (1:2.24.1.1-0ubuntu1) ...
Setting up gnome-power-manager (2.24.0-0ubuntu8.2) ...

Setting up gvfs-fuse (1.0.2-0ubuntu2) ...
Setting up libcupsimage2 (1.3.9-2ubuntu7) ...

Setting up libpulsecore5 (0.9.10-2ubuntu9.3) ...

Setting up ttf-opensymbol (1:2.4.1-11ubuntu2.1) ...
Updating fontconfig cache...

Setting up cups-client (1.3.9-2ubuntu7) ...

dpkg: libbind9-40: dependency problems, but configuring anyway as you request:
 libbind9-40 depends on libdns43 (= 1:9.5.0.dfsg.P2-1ubuntu3.1); however:
  Version of libdns43 on system is 1:9.5.0.dfsg.P2-1ubuntu2.
 libbind9-40 depends on libisc44 (= 1:9.5.0.dfsg.P2-1ubuntu3.1); however:
  Version of libisc44 on system is 1:9.5.0.dfsg.P2-1ubuntu2.
 libbind9-40 depends on libisccfg40 (= 1:9.5.0.dfsg.P2-1ubuntu3.1); however:
  Version of libisccfg40 on system is 1:9.5.0.dfsg.P2-1ubuntu2.
Setting up libbind9-40 (1:9.5.0.dfsg.P2-1ubuntu3.1) ...

Processing triggers for man-db ...
Processing triggers for python-support ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 avahi-daemon_0.6.23-2ubuntu2.1_amd64.deb
 gnome-control-center_2.24.0.1-0ubuntu7.1_amd64.deb
 gnome-games-data_2.24.1.1-0ubuntu1_all.deb
 gnome-terminal_2.24.1.1-0ubuntu1_amd64.deb
 gnome-terminal-data_2.24.1.1-0ubuntu1_all.deb
 language-pack-gnome-en_8.10+20081107_all.deb
 libavahi-common-data_0.6.23-2ubuntu2.1_amd64.deb
 libpam-runtime_1.0.1-4ubuntu5.3_all.deb
 libpango1.0-common_1.22.2-0ubuntu1_all.deb
 libscrollkeeper0_0.3.14-16ubuntu1_amd64.deb
 libsmbclient_3.2.3-1ubuntu3.4_amd64.deb
 login_4.1.1-1ubuntu1.2_amd64.deb
 network-manager_0.7~~svn20081018t105859-0ubuntu1.8.10.1_amd64.deb
 pulseaudio-utils_0.9.10-2ubuntu9.3_amd64.deb
 scrollkeeper_0.3.14-16ubuntu1_amd64.deb
 splix_2.0.0~rc2-0ubuntu2.3_amd64.deb
 tracker_0.6.6-1ubuntu5.1_amd64.deb


I'm downloading all packages now and I'm gonna restart, as Ubuntu is giving me a STOP-Sign telling me the update didn't finish or so. I'll get back later :)

---

