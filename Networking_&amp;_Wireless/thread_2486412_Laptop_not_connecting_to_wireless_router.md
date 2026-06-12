---
title: "Laptop not connecting to wireless router"
date: 2023-04-28
forum: Networking &amp; Wireless
---

### Post by jonfisher on 2023-04-28
HP laptop quit connecting to wireless router this evening.  HP Desktop still connects (via wire).

p.s. Are UbuntuForums site having a problem this evening also?  Seems slow and I have to connect t various servers around the U.S. to get into it....

t's not the wireless router - tested that.

I booted from an older USB thumb drive (probably Ubuntu 18.x lts or  around then).  I could not get online.  Perhaps tell me where to click  to enter the routers online stuff like the password.

I will stop at this step until advised further how to try to get it  online, wirelessly, using the Ubuntu thumb drive boot OS.  Prefer  instructions on where to look on the GUI at first here please.

---

### Post by jonfisher on 2023-04-29
I'm back online and trying to work on this laptop again, tonight.
If someone could make some more suggestions.  
I'm trying to eliminate things until the last step will be to buy a wireless card to put inside my laptop.

---

### Post by jonfisher on 2023-04-29
If someone could tell me what to type into terminal, to attempt to see if the wifi card is operating, I'd much appreciate it.

---

### Post by jonfisher on 2023-04-29
Some command line results:

> michael@michael-HP-Pavilion-Notebook:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED       
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:c3100000-c3107fff
  *-network
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eno1
       version: 0a
       serial: dc:4a:3e:e0:0e:61
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.19.0-41-generic duplex=full firmware=rtl8107e-2_0.0.2 02/26/15 ip=192.168.1.94 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:19 ioport:3000(size=256) memory:c3004000-c3004fff memory:c3000000-c3003fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
michael@michael-HP-Pavilion-Notebook:~$ 


&
> 
michael@michael-HP-Pavilion-Notebook:~$ lspci
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5500 (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Broadwell-U Processor Thermal Subsystem (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.1 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #2 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
08:00.0 Network controller: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 0a)
michael@michael-HP-Pavilion-Notebook:~$ 


AND

> 
michael@michael-HP-Pavilion-Notebook:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

tun0      Interface doesn't support scanning.

michael@michael-HP-Pavilion-Notebook:~$ 

& 

> 
michael@michael-HP-Pavilion-Notebook:~$ nmcli d
DEVICE  TYPE      STATE                   CONNECTION         
eno1    ethernet  connected               Wired connection 1 
tun0    tun       connected (externally)  tun0               
lo      loopback  unmanaged               --                 
michael@michael-HP-Pavilion-Notebook:~$ nmcli r wifi on
michael@michael-HP-Pavilion-Notebook:~$ nmcli d wifi list
michael@michael-HP-Pavilion-Notebook:~$ 


---

### Post by jonfisher on 2023-04-30
I will continue to troubleshoot, things you guys/gals tell me to type into terminal mostly (or GUI is even better).  Perhaps I put this in the wrong forum, as I'm not getting any bites yet (for help)...

However, at this time, I'd like recommendations on a recommended wifi card for my HP Pavilion 17-g161us - either used or new.

Perhaps I should replace it with the original one that was in it?  I know when I first got this computer, the wifi card was bad and they put another one in it - I don't know if it was the same one or a different one that was originally in it.

According to Terminal, the one in it now is:  Broadcom BCM43142  802.11 b/g/n

I know the one it has in it has limited my wireless connection to 50 Mbps, even though my HP desktop, wired to the router, gets 400 Mbps and sometimes slightly higher.

Perhaps I could get a wireless card for it that allows it to run faster than 50Mbps and close to my ISP's guaranteed 400 Mbps for what I'm paying for (?).

 

Much appreciation for help.  I would also appreciate any url's of wifi cards on Amazon, which is where I want to get one - again, either new or used.

---

### Post by jonfisher on 2023-04-30
& from this page: [https://www.technolaty.com/how-to-install-wireless-drivers-on-ubuntu/](https://www.technolaty.com/how-to-install-wireless-drivers-on-ubuntu/)

```

michael@michael-HP-Pavilion-Notebook:~$   sudo apt install git build-essential dkms  
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
build-essential is already the newest version (12.9ubuntu3).
build-essential set to manually installed.
dkms is already the newest version (2.8.7-2ubuntu2.1).
dkms set to manually installed.
The following packages were automatically installed and are no longer required:
  fonts-mplus fonts-roboto fonts-roboto-unhinted libflashrom1 libftdi1-2
  libglew2.2 libretro-core-info
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  git-daemon-run | git-daemon-sysvinit git-doc git-email git-gui gitk gitweb
  git-cvs git-mediawiki git-svn
The following NEW packages will be installed:
  git git-man liberror-perl
0 upgraded, 3 newly installed, 0 to remove and 189 not upgraded.
Need to get 4,121 kB of archives.
After this operation, 20.9 MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 liberror-perl all 0.17029-1 [26.5 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 git-man all 1:2.34.1-1ubuntu1.8 [953 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 git amd64 1:2.34.1-1ubuntu1.8 [3,141 kB]
Fetched 4,121 kB in 1s (4,556 kB/s)
Selecting previously unselected package liberror-perl.
(Reading database ... 221522 files and directories currently installed.)
Preparing to unpack .../liberror-perl_0.17029-1_all.deb ...
Unpacking liberror-perl (0.17029-1) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a2.34.1-1ubuntu1.8_all.deb ...
Unpacking git-man (1:2.34.1-1ubuntu1.8) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a2.34.1-1ubuntu1.8_amd64.deb ...
Unpacking git (1:2.34.1-1ubuntu1.8) ...
Setting up liberror-perl (0.17029-1) ...
Setting up git-man (1:2.34.1-1ubuntu1.8) ...
Setting up git (1:2.34.1-1ubuntu1.8) ...
Processing triggers for man-db (2.10.2-1) ...
michael@michael-HP-Pavilion-Notebook:~$   git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)  
Cloning into 'rtlwifi_new'...
Username for 'https://github.com': git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git) 
Password for 'https://git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git) @github.com': 
remote: Support for password authentication was removed on August 13, 2021.
remote:  Please see  [https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls)  for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/lwfinger/rtlwifi_new.git/'
michael@michael-HP-Pavilion-Notebook:~$ git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git) 
Cloning into 'rtlwifi_new'...
Username for 'https://github.com': git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
Password for 'https://git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git@github.com':](https://github.com/lwfinger/rtlwifi_new.git@github.com':) 
remote: Support for password authentication was removed on August 13, 2021.
remote:  Please see  [https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls)  for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/lwfinger/rtlwifi_new.git/'
michael@michael-HP-Pavilion-Notebook:~$   sudo dkms add ./rtlwifi_new  
Error! Could not find module source directory.
Directory: /usr/src/.-rtlwifi_new does not exist.
michael@michael-HP-Pavilion-Notebook:~$ sudo dkms add ./rtlwifi_new
Error! Could not find module source directory.
Directory: /usr/src/.-rtlwifi_new does not exist.
michael@michael-HP-Pavilion-Notebook:~$ sudo dkms add .rtlwifi_new
Error! Arguments <module> and <module-version> are not specified.
Usage: add <module>/<module-version> or
       add -m <module>/<module-version> or
       add -m <module> -v <module-version>
michael@michael-HP-Pavilion-Notebook:~$ sudo dkms install rtlwifi-new/0.6 
Error! Could not find module source directory.
Directory: /usr/src/rtlwifi-new-0.6 does not exist.
michael@michael-HP-Pavilion-Notebook:~$ sudo dkms install rflwifi-new/0.6
Error! Could not find module source directory.
Directory: /usr/src/rflwifi-new-0.6 does not exist.
michael@michael-HP-Pavilion-Notebook:~$ sudo modprobe -r rtl8723de && sudo modprobe rtl8723de
modprobe: FATAL: Module rtl8723de not found.
michael@michael-HP-Pavilion-Notebook:~$ echo &#8220;options rtl8723de ant_sel=3&#8221; | sudo tee /etc/modprobe.d/rtl8723de.conf 
&#8220;options rtl8723de ant_sel=3&#8221;
michael@michael-HP-Pavilion-Notebook:~$ sudo apt install firmware-b43-installer
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-mplus fonts-roboto fonts-roboto-unhinted libflashrom1 libftdi1-2
  libglew2.2 libretro-core-info
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 189 not upgraded.
Need to get 33.1 kB of archives.
After this operation, 135 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 b43-fwcutter amd64 1:019-7build2 [27.9 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/multiverse amd64 firmware-b43-installer all 1:019-7build2 [5,212 B]
Fetched 33.1 kB in 0s (76.3 kB/s)                 
Preconfiguring packages ...
Selecting previously unselected package b43-fwcutter.
(Reading database ... 222507 files and directories currently installed.)
Preparing to unpack .../b43-fwcutter_1%3a019-7build2_amd64.deb ...
Unpacking b43-fwcutter (1:019-7build2) ...
Selecting previously unselected package firmware-b43-installer.
Preparing to unpack .../firmware-b43-installer_1%3a019-7build2_all.deb ...
Unpacking firmware-b43-installer (1:019-7build2) ...
Setting up b43-fwcutter (1:019-7build2) ...
Setting up firmware-b43-installer (1:019-7build2) ...
No chroot environment found. Starting normal installation
No supported device found.
But firmware is installed unconditionally
Unsupported device(s) found: PCI id  * 14e4:4365 
Trying to install latest firmware 6.30.163.46 .
--2023-04-30 01:35:21--  [https://www.lwfinger.com/b43-firmware/broadcom-wl-6.30](https://www.lwfinger.com/b43-firmware/broadcom-wl-6.30).
163.46.tar.bz2
Resolving [www.lwfinger.com](www.lwfinger.com) ([www.lwfinger.com](www.lwfinger.com))... 173.254.30.178
Connecting to [www.lwfinger.com](www.lwfinger.com) ([www.lwfinger.com)|173.254.30.178|:443](www.lwfinger.com)|173.254.30.178|:443)... connect
ed.
HTTP request sent, awaiting response... 200 OK
Length: 7684610 (7.3M) [application/x-tar]
Saving to: &#8216;broadcom-wl-6.30.163.46.tar.bz2&#8217;

broadcom-wl-6.30.16 100%[===================>]   7.33M  4.99MB/s    in 1.5s    

2023-04-30 01:35:23 (4.99 MB/s) - &#8216;broadcom-wl-6.30.163.46.tar.bz2&#8217; saved [76846
10/7684610]

broadcom-wl-6.30.163.46.tar.bz2: OK
broadcom-wl-6.30.163.46.wl_apsta.o
This file is recognised as:
filename   :  wl_apsta.o
version    :  784.2
MD5        :  29c8a47094fbae342902d84881a465ff
Extracting b43/lcn1bsinitvals26.fw
Extracting b43/n0bsinitvals22.fw
Extracting b43/lcn0bsinitvals26.fw
Extracting b43/ac1bsinitvals42.fw
Extracting b43/ucode24_lcn.fw
Extracting b43/ht0bsinitvals26.fw
Extracting b43/ucode24_mimo.fw
Extracting b43/n20initvals36.fw
Extracting b43/ucode15.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/lcn405initvals35.fw
Extracting b43/ac1initvals42.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/ucode43.fw
Extracting b43/lp0initvals16.fw
Extracting b43/lp1bsinitvals20.fw
Extracting b43/lcn1initvals25.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/lcn402initvals33.fw
Extracting b43/sslpn3bsinitvals21.fw
Extracting b43/ht0initvals29.fw
Extracting b43/n2bsinitvals19.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/ucode25_lcn.fw
Extracting b43/lcn0initvals24.fw
Extracting b43/lcn404initvals33.fw
Extracting b43/sslpn1bsinitvals27.fw
Extracting b43/lcn404bsinitvals33.fw
Extracting b43/ucode22_sslpn.fw
Extracting b43/lcn1bsinitvals25.fw
Extracting b43/lcn406initvals37.fw
Extracting b43/ac3initvals43.fw
Extracting b43/lcn2initvals26.fw
Extracting b43/ucode20_sslpn.fw
Extracting b43/lcn403bsinitvals33.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/n0initvals17.fw
Extracting b43/ht0bsinitvals29.fw
Extracting b43/ucode21_sslpn.fw
ucode time:     21:35:19
Extracting b43/sslpn1initvals20.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/lcn0initvals26.fw
Extracting b43/ucode27_sslpn.fw
Extracting b43/ucode29_mimo.fw
Extracting b43/ucode21_sslpn_nobt.fw
ucode time:     21:35:19
Extracting b43/lp0initvals15.fw
Extracting b43/ucode19_sslpn.fw
Extracting b43/lcn1bsinitvals24.fw
Extracting b43/lcn401bsinitvals33.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/ucode16_sslpn_nobt.fw
ucode date:     2012-08-15
Extracting b43/n16bsinitvals30.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/lcn402bsinitvals33.fw
Extracting b43/ucode19_sslpn_nobt.fw
Extracting b43/ucode40.fw
Extracting b43/lcn1initvals24.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/ac2initvals41.fw
Extracting b43/n16initvals30.fw
Extracting b43/ucode16_lp.fw
Extracting b43/n0initvals22.fw
Extracting b43/sslpn3initvals21.fw
Extracting b43/lp1initvals22.fw
Extracting b43/ac2bsinitvals41.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/lcn2bsinitvals26.fw
Extracting b43/ucode34_mimo.fw
Extracting b43/n1initvals20.fw
Extracting b43/lcn2initvals25.fw
Extracting b43/ucode37_lcn40.fw
Extracting b43/n0initvals16.fw
Extracting b43/n0bsinitvals24.fw
Extracting b43/n1bsinitvals20.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/lcn0bsinitvals24.fw
Extracting b43/lcn2bsinitvals25.fw
Extracting b43/sslpn4bsinitvals22.fw
Extracting b43/ucode11.fw
Extracting b43/n2initvals19.fw
Extracting b43/pcm4.fw
Extracting b43/ucode13.fw
Extracting b43/lcn0initvals25.fw
Extracting b43/sslpn1initvals27.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals14.fw
Extracting b43/lp1bsinitvals22.fw
Extracting b43/n18initvals32.fw
Extracting b43/lcn405bsinitvals35.fw
Extracting b43/ucode41.fw
Extracting b43/lcn400initvals33.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/lcn401initvals33.fw
Extracting b43/ucode33_lcn40.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/ucode32_mimo.fw
Extracting b43/lcn400bsinitvals33.fw
Extracting b43/lcn404bsinitvals35.fw
Extracting b43/n19initvals34.fw
Extracting b43/ac3bsinitvals43.fw
Extracting b43/n0initvals25.fw
Extracting b43/ucode26_mimo.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lcn404initvals35.fw
Extracting b43/lp2bsinitvals19.fw
Extracting b43/n19bsinitvals34.fw
Extracting b43/ucode20_sslpn_nobt.fw
Extracting b43/ac0bsinitvals40.fw
Extracting b43/lcn2initvals24.fw
Extracting b43/sslpn4initvals22.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/n0bsinitvals25.fw
Extracting b43/lp2initvals19.fw
Extracting b43/n18bsinitvals32.fw
Extracting b43/lcn0bsinitvals25.fw
Extracting b43/n0initvals11.fw
Extracting b43/lcn2bsinitvals24.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/pcm5.fw
Extracting b43/ucode35_lcn40.fw
Extracting b43/ucode14.fw
Extracting b43/ucode36_mimo.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode17_mimo.fw
Extracting b43/lp0initvals13.fw
Extracting b43/ucode25_mimo.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/lcn406bsinitvals37.fw
Extracting b43/ac0initvals40.fw
Extracting b43/ucode30_mimo.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/n20bsinitvals36.fw
Extracting b43/ucode42.fw
Extracting b43/lcn407initvals38.fw
Extracting b43/lcn1initvals26.fw
Extracting b43/ht0initvals26.fw
Extracting b43/ucode38_lcn40.fw
Extracting b43/lcn407bsinitvals38.fw
Extracting b43/lcn403initvals33.fw
Extracting b43/ucode16_sslpn.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/n0bsinitvals17.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/n0initvals24.fw
Extracting b43/lp1initvals20.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ucode9.fw
Extracting b43/ucode5.fw
Extracting b43/ucode22_mimo.fw
Processing triggers for man-db (2.10.2-1) ...
michael@michael-HP-Pavilion-Notebook:~$  
```

---

### Post by jonfisher on 2023-04-30
Another note:

"Software & Updates" reports it's "using broaqdcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)...

I dunno if that helps or not...

---

### Post by jonfisher on 2023-04-30
After a software update everything is working again!

---

