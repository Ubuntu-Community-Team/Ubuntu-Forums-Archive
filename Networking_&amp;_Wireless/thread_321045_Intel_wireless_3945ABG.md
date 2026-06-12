---
title: "Intel wireless 3945ABG"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by mikewhatever on 2006-12-18
I've been unable to get my Intel wireless 3945 to work. I can see the card with the help of lshw command, and the driver ipw3945. There is also an icon next to the watch indicating Loop connection. There in no wireless interface in Administrator->Network or elsewhere. After some reading I found that to be a frequent problem. There seems to be two ways to solve it: one - installing 'generic drivers', two - installing network manager. I tried the second one from here: [http://ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+wireless+3945](http://ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+wireless+3945)
but got a bunch of errors. First, extracting the file with 'tar -xzvf nm-debs.tar.gz' didn't work. It said 'tar: no such directory'. Then updating the '/etc/apt/sources.list' file didn't work too, because the file is read only. Can someone help me, please!

---

### Post by n00b@linux on 2006-12-18
Do you have the ipw3945 kernel module installed? Run:```
lsmod | grep 'ipw3945'
```to check. Also, check the link in my sig. It's an excellent reference for WPA but also includes some basic (non-WPA) wireless networking instructions as well. I have an Intel PRO/Wireless 3945ABG Mini PCI card in my laptop and I configured it using this thread.

---

### Post by mikewhatever on 2006-12-18
lsmod | grep ipw3945
ipw3945               124576  0 
ieee80211              35272  1 ipw3945

also, I don't know what "the link in your sig" is.

Thanks

---

### Post by n00b@linux on 2006-12-18
OK.  The kernel module (ipw3945) has loaded correctly.
 
It sounds like it just needs to be configured correctly.
 
Personally, I prefer to use the command line rather than the GUI - because I use various distros on my different pieces of hardware and learning one CLI is a heck of a lot easier than learning umpteen GUIs.
 
Are you using WEP or WPA or 'going commando'?
 
The link in my sig activates when you wave the mouse over the 'this thread' bit ;)

---

### Post by mikewhatever on 2006-12-18
I use WEP. As to configurations, I found no way, GUI or command, to access them.

---

### Post by n00b@linux on 2006-12-18
OK.  That makes it a lot simpler.
Run```
iwconfig
```to make sure your wireless adapted is listed.  If it's not (it should be), run ```
ifconfig -a
```to see what it's called, eg. eth1, wlan0, etc.  Then bring it 'up' by running```
ifconfig eth1 up
```which assumes the interface's ID is 'eth1'.  Replace it if it's not.  Once this is done, re-run iwconfig to check that it's listed.
Now that your wireless adapter is on line, you need to configure it.
Open a terminal and run:```
sudo iwconfig <yourinterfaceid> mode managed essid <youressid> key <yourwepkey>
```Where:
<yourinterfaceid> is what your wireless adapter is listed as (eth1 or wlan0)
<youressid> is the essid of your network
<yourwepkey> is your WEP key in hexadecimal digits OR s:<yourkeyinASCIItext>
Now re-run ```
iwconfig
``` and you should see your wireless adapter is associated with your access point (ie. ADSL modem) and your network.  You may need to restart networking to get it going properly:```
sudo /etc/init.d/networking restart
```

---

### Post by mikewhatever on 2006-12-18
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


 ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:D4:43:80:1B  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


No wireless adapter, or is it eth0?

---

### Post by n00b@linux on 2006-12-18
I doubt if it's eth0 if you have an ethernet card (ie. 'wired' connection).  That's usually eth0. 
Run```
lspci
```to double check. You should see something about 'Ethernet' listed.
It's also not lo or sit0.  Hmm.  Mysterious.
What type of card is your wireless adapter? PCMCIA? USB? MiniPCI? PCI?

---

### Post by danhm on 2006-12-18
I am also having trouble with my 3945ABG, if you don't mind me butting in.

It was working fine in Dapper (using the network manager). I upgraded to Edgy yesterday, and it still worked fine. Today, wpa-supplicant was updated and it has not worked since.

```

dan@dan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"NETGEAR"  
          Mode:Managed  Frequency=nan kHz  Access Point: FF:00:FF:00:FF:00   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:58   Missed beacon:0

sit0      no wireless extensions.

```

```

dan@dan-laptop:~$ cat /etc/network/interface
# The loopback network interface
auto lo
iface lo inet loopback

```

```

dan@dan-laptop:~$ lsmod | grep 'ipw3945'
ipw3945               120992  1 
ieee80211              33608  1 ipw3945

```


Is something amiss? I have a Dell Inspiron E1505, if it matters.

---

### Post by mikewhatever on 2006-12-18
lshw

-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@06:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ipw3945
                resources: iomemory:52000000-52000fff irq:185

It's built into HP Pavilion laptop.

---

### Post by danhm on 2006-12-18
As far as I know, the Intel 3945ABG only comes as a mini-PCIe integrated card, as part of the Centrino platform.

[http://en.wikipedia.org/wiki/Intel_Centrino#Napa_platform](http://en.wikipedia.org/wiki/Intel_Centrino#Napa_platform)

---

### Post by n00b@linux on 2006-12-18
@mikewhatever:
Well, if it's build in AND you don't have any other network cards, then it must be eth0. Strange, laptops usually do come with wireless AND an ethernet adapter. Could you post your lspci results to be sure?
 
@danhm
Don't bother with wpa-supplicant for the ipw3945.  I went round and around in circles with that.  Cut to the chase and follow the link in my sig.

---

### Post by mikewhatever on 2006-12-18
lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d8 (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:06.0 CardBus bridge: Texas Instruments Unknown device 8039
08:06.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
08:06.2 Mass storage controller: Texas Instruments Unknown device 803b
08:06.3 Class 0805: Texas Instruments Unknown device 803c
08:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 01) 
```

Don't know what the hell it all means :-)

---

### Post by Paulo79 on 2006-12-18
> **mikewhatever said:**
> iwconfig
lo         no wireless extensions.
eth0     no wireless extensions.
sit0      no wireless extensions.


I just solved this problem. My wireless was working perfectly when I installed Edgy. But recently I could not see eth1 anymore. Although lsmod would still show that ipw3945 was loaded, the wireless network managers (both in gnome and KDE) would only show me the wired connection (eth0).

WHAT CAUSED THE PROBLEM (in my case): when I removed nvidia-glx (and installed the newest one from NVIDIA's web site), the package linux-restricted-modules-"my_kernel_version" was also removed with nvidia-kernel-common.

It seems linux-restricted-modules also has firmware and (I guess) other "stuff" that ipw3945 needs to work correctly. After I reinstalled the restricted modules, my wireless (eth1) was working again. Note that I just have entries for lo and eth0 (wired) connections in /etc/network/interfaces.

---

### Post by mikewhatever on 2006-12-18
Hi Paulo79, it does look similar and I am glad that you could solve it. How do you install stuff without internet connection? If you have the time, can you please describe the procedure. 

It's been a long day of booting and rebooting :-k

---

### Post by mikewhatever on 2006-12-18
I don't know how relevant this is, but when I boot into Ubuntu, there appear about 8-9 lines saying: 

```
 PCI: Can not Allocate resource regeon 
```

each line is preceded and followed by a string of numbers. I can see them right after Grub menu.

---

### Post by mikewhatever on 2006-12-19
Following instructions from here:

```
 http://ubuntuforums.org/showthread.php?t=286188&page=2&highlight=intel+wireless+3945 
```

and reading elsewhere how to update system files, I was able to install Gnome Network Manager. Nothing happened, other then having another icon in the panel. Still no wireless interface anywhere I looked. ](*,)

---

### Post by mikewhatever on 2006-12-19
Whoever has any working suggestions, please post. The laptop I use is HP Pavilion DV5269ea. The specs can be found here:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00777995&lc=en&cc=us&dlc=en&product=3279914&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00777995&lc=en&cc=us&dlc=en&product=3279914&lang=en)

I have no other way to connect, but wireless, so I am back in Windows. ](*,)

---

### Post by Paulo79 on 2006-12-19
Make sure the package with the restricted modules is installed. That is, run de command:

dpkg -la | grep linux-restricted-modules

and see if you get something like this:

```
rc  linux-restricted-modules-2.6.17-10-386     2.6.17.5-10                          Non-free Linux 2.6.17 modules on 386
ii  linux-restricted-modules-2.6.17-10-generic 2.6.17.6-1                           Non-free Linux 2.6.17 modules on x86_64 generic
ii  linux-restricted-modules-common            2.6.17.6-1                           Non-free Linux 2.6.17 modules helper script

```

As you can see, I have installed ("ii") the version of the linux kernel compiled for the "generic" processor. Yours could be 386, that is fine. Just make sure the package is installed.

If it is not installed, (using windows, maybe) go to [this web page]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all") and download the package for your kernel version. 

To install it in linux you run:

sudo dpkg -i package_name_here

Restart your system and see if gnome network manager will show your wireless network this time.

Hope that helps!

---

### Post by mikewhatever on 2006-12-19
OK, I downloaded and installed linux-restricted-modules-2.6.17-10-386 from where you suggested. On reboot, there were more lines in grub, so I chose the new kernel, 2.6.17-10-386.
Upon loading, it showed the same lines as before, and nothing else was different. I still do not have wireless interface in Administrator->Networking, or elsewhere I looked. This command 
dpkg -la | grep linux-restricted-modules

produced no output at all, neither before, nor after installation. I just copied       and pasted it into Terminal.

---

### Post by mikewhatever on 2006-12-20
It worked!!!!!!!!!!!!!!!!!!!! :-D 
Right after installing linux-restricted-modules-2.6.17-10-generic 2.6.17.6-1 from here: ```
 http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all
```
Sort of like Paulo79 had suggested. After a reboot, Gnome NM was functioning and I could see all the networks around, my own and the neighbors'. :-D  As you can see, I am very very very very very ... happy. Now I can keep learning without booting and rebooting into Windows. Thanks to everyone who tried to help.

---

### Post by Paulo79 on 2006-12-20
Cool! Have fun! :-)

---

### Post by remi71 on 2006-12-20
Hi
I've the same problem on a IBM Thinkpad R60 with an embedded Wireless adapter with this chipset (Intel 3945ABG).
This was my situation:
[LIST=1]
[*] Installed Edgy Eft with standard kernel 2.6.17-10-386. The NIC works fine with the ipw3945 module. I see the Wired embedded card (NetXtreme BCM5751M) with logical name eth1 and the Wireless card with name eth2.

[*] Now I need to switch the kernel because my laptop is a Core Duo CPU and with this kernel my system use only 1 CPU core (cat /proc/cpuinfo output only cpu 0). --> Installed kernel 2.6.17-10-generic.

[*] After reboot with the new kernel, dual CPU are ok but....bingo! the Wireless card is down! :( 

[*] The module ipw3945 is loaded but something is wrong!
The problem is the modprobe rule for this module in /etc/modprobe.d/ipw3945:

```
install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; sleep 0.5 ; \
        /sbin/ipw3945d-$(uname -r) --quiet
remove  ipw3945 /sbin/ipw3945d-$(uname -r) --kill ; \
        /sbin/modprobe -r --ignore-remove ipw3945
```

Beyond loading the module with modprobe, a daemon is launched named ipw3945d-<KERNEL VERSION>

[*] The file is named /sbin/ipw3945d-2.6.17-10-386, but no file exist under /sbin with the name ipw3945d- followed by the current kernel version (in my case 2.6.17-10-generic).

[*] SOLUTION: I've symlinked the file:
```
cd /sbin
ln -s ipw3945d-2.6.17-10-386 ipw3945d-2.6.17-generic
```

[*] Remove and insert the module:
```
modprobe -r ipw3945
modprobe ipw3945
```

[*] The card is now UP ;) 
```
iwconfig eth2

eth2      IEEE 802.11g  ESSID:"................."
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:30:BD:F7:8A:FA
          Bit Rate:54 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:FC8C-EE20-9B49-239B-62C0-F06D-E98E-624E-5358-56A9-7641-99C8-73BD-0FED-6267-CC05   Security mode:open
          Power Management:off
          Link Quality=89/100  Signal level=-38 dBm  Noise level=-39 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0
```


[/LIST]

I hope this help! :p

---

### Post by nicknn on 2006-12-30
> **mikewhatever said:**
> lshw

-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@06:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ipw3945
                resources: iomemory:52000000-52000fff irq:185

It's built into HP Pavilion laptop.

try this:
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by jck3j on 2006-12-30
hello, i was having the same trouble with my intel pro/wireless 3945abg. i tried using the NetworkManager Applet 0.6.3 and it works wonders. i had a lot of trouble dealing with the ubuntu network manager so i turned everything off on that. I have connected to many wireless networks through this applet.

It is available through the package manager under network-manager. here are the things i have downloaded as an attached image.

---

