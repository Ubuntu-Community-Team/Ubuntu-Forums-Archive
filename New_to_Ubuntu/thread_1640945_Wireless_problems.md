---
title: "Wireless problems"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by Powerade492 on 2010-12-08
I am having trouble connecting my Ubuntu 10.10 Remix to a wireless network.
I have a Toshiba Satellite L655D-S5110. I believe i need a network card or adaptor, so if anyone has any links to download or if there is another solution it will be greatly appreciated.

---

### Post by friv_livs on 2010-12-08
Please post results of:
```
sudo lshw -C network
```

(But do overwrite your output mac address please.)

---

### Post by Powerade492 on 2010-12-09
*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:7000(size=256) memory:f3100000-f3103fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c1
       serial: 60:eb:69:1c:5d:14
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f3000000-f303ffff ioport:6000(size=128)

---

### Post by Powerade492 on 2010-12-09
*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:7000(size=256) memory:f3100000-f3103fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c1
       serial: 60:eb:69:1c:5d:14
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f3000000-f303ffff ioport:6000(size=128)

---

### Post by friv_livs on 2010-12-09
According to your lshw, you appear to have an unrecognized Realtek wireless card.

Do you dual boot?

If yes, then go to your windows and see what model number of Realtek wireless card it gives you.

If no, then boot another live distro (Fedora, partedmagic, etc.) and see what it lists for the same terminal command.

partedmagic can be downloaded from here: [HTML]http://sourceforge.net/projects/partedmagic/[/HTML] 

FYI: "serial: yada" is your MAC address.

---

### Post by Powerade492 on 2010-12-09
Realtek RTL8188CE Wireless LAN 802.11n PCI-E NIC
I dual boot

---

### Post by canucked on 2010-12-09
I just created a thread about a Toshiba L655 laptop I configured which uses the Realtek RTL8188CE wireless adapter.

[http://ubuntuforums.org/showthread.php?t=1641931]("http://ubuntuforums.org/showthread.php?t=1641931")

This is what I did to get wireless working:

In Terminal, run:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```

It's much simpler than compiling code yourself, and should also work when a new linux kernel is installed.

If you have audio issues with your Toshiba laptop, referring to my above thread my help resolve them.  Best of luck!

---

### Post by Powerade492 on 2010-12-10
It isn't recognizing it when i put in terminal i might be doing it wrong though could you put beginners explanation please?

---

### Post by canucked on 2010-12-10
You probably want to confirm that you have the same Realtek wireless card as the Toshiba I configured, **RTL8188CE**.

In Terminal, run:
```
lspci -nn
```
and please post the output.

If you do have the same wireless card and you're trying to add the lexical/hwe-wireless PPA I mentioned but it's not working, please post what happens in Terminal after you run the first command.  You will need to be connected to the internet via ethernet for it to work.

---

### Post by canucked on 2010-12-10
If you can't connect to the internet via ethernet with the Ubuntu machine on which you're trying to set up wireless, here is another method:

You can download the deb package from the PPA I mentioned directly from the PPA website:
[https://launchpad.net/~lexical/+archive/hwe-wireless]("https://launchpad.net/~lexical/+archive/hwe-wireless")

Make sure you download the appropriate build: **rtl8192ce-dkms** (2.6.0003.0628.2010ubuntu2) **maverick**

rtl8192ce-dkms_2.6.0003.0628.2010ubuntu2_all.deb also requires three other deb packages: **dkms**, **fakeroot**, and **patch**.  These can all be downloaded from:
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

If you download those four deb packages with an internet-accessible computer and copy them to your Ubuntu maverick installation with a USB flash drive, you can install rtl8192ce-dkms and get wireless support.

After your wireless is working properly, you can then correctly install the PPA source so that you get updates through the package manager.
```
sudo add-apt-repository ppa:lexical/hwe-wireless
```

---

### Post by Powerade492 on 2010-12-15
I cann't find the packages in the site. i have the rtl8192ce-dkms_2.6.0003.0628.2010ubuntu2_all.deb i just need the rest. Sorry for not getting back sooner i am deployed and not much time to get on the internet. thanks

---

### Post by canucked on 2010-12-16
@Powerade492: The other packages you need (dkms, fakeroot, and patch) will not be downloaded from the same PPA website from which you downloaded the rtl8192ce-dkms deb.

You need to go to this site to download those three packages:
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

Search for each of those packages and make sure you download the appropriate one for your distribution.

---

### Post by canucked on 2010-12-16
Here are links for those three debs you need:

[http://packages.ubuntu.com/maverick/dkms]("http://packages.ubuntu.com/maverick/dkms")

[http://packages.ubuntu.com/maverick/fakeroot]("http://packages.ubuntu.com/maverick/fakeroot")

[http://packages.ubuntu.com/maverick/patch]("http://packages.ubuntu.com/maverick/patch")

Download the appropriate deb: i386 or amd64.

---

### Post by Powerade492 on 2010-12-19
I am having trouble installing the packages

---

### Post by canucked on 2010-12-24
Powerade492: sorry for the slow reply.  i haven't been online for the last week.

What happens when you try to install the deb packages?

If you prefer the GUI, you can just double-click on each deb package you downloaded, and Ubuntu Software Center will be opened.  You can then click "Install".

Or, you can use the Terminal:
[https://help.ubuntu.com/community/InstallingSoftware#Using%20GDebi%20to%20install%20packages]("https://help.ubuntu.com/community/InstallingSoftware#Using%20GDebi%20to%20install%20packages")
```
sudo dpkg -i package_name.deb
```

If you have the Nautilus file manager open, you can drag the file into Terminal, instead of having to type out the full path.

---

### Post by Powerade492 on 2010-12-27
It doesn't let me install the install button in the software center is unclickable.

---

### Post by canucked on 2010-12-27
Try installing the packages in Terminal.  See my last post for a link and instructions.  And make sure rtl8192ce-dkms is installed after dkms, fakeroot, and patch.  If there is an error message, please paste it.

---

### Post by Powerade492 on 2010-12-27
it shows package then access denied

---

### Post by canucked on 2010-12-28
What is the output in Terminal when you try installing the packages with dpkg?

```
sudo dpkg -i package_name.deb
```

---

### Post by Powerade492 on 2010-12-30
torres@ubuntu:~$ sudo dpkg -i rtl8192ce-dkms_2.6.0003.0628.2010ubuntu2_all.deb
[sudo] password for torres: 
dpkg: error processing rtl8192ce-dkms_2.6.0003.0628.2010ubuntu2_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 rtl8192ce-dkms_2.6.0003.0628.2010ubuntu2_all.deb
torres@ubuntu:~$

---

### Post by canucked on 2010-12-30
The command you used would only work if:
-rtl8192ce-dkms is located in your user's Home directory: /home/torres (According to what you copied from your Terminal, this was the directory you were working in.)
and
-The other three required packages (dkms, fakeroot, and patch) were installed first.

Next time, try typing this in Terminal:
```
sudo dpkg -i 
```
Then open the Nautilus file manager, find the deb package you want to install, and drag the package into the Terminal window.  The package name, including the full path, will be pasted into the Terminal window.

I'm assuming that Terminal couldn't find rtl8192ce-dkms because it wasn't in the directory you were working in.

---

### Post by Powerade492 on 2011-01-02
It got to were i could install and said it wasn't for my computer.

---

### Post by canucked on 2011-01-07
Do you know if you're using the 32-bit or 64-bit Ubuntu?  You need the debs for either i386 (32-bit) or AMD64 (64-bit).  The debs also need to be for the correct version of Ubuntu (10.10 Maverick).

This is all I can think of for the installation not working - that you have the wrong deb version.

If you can find a way to plug your computer directly into an ethernet connection, it would be much easier to directly download and install the correct deb packages using the Synaptic package manager.

---

