---
title: "Messed up Interfaces file when using Ndiswrapper"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by RockabyeRy87 on 2006-09-12
I have a broadcom wireless card I was working on configuing in Ubuntu Dapper Drake.  I went through various tutorials, tried the fwcutter but had no success.  I decided to try the ndiswrapper route and somewhere along there I messed up my Interfaces file.


ryan@ryan-laptop:~$ sudo ifdown wlan0
/etc/network/interfaces:18: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
ryan@ryan-laptop:~$ sudo ifup wlan0
/etc/network/interfaces:18: duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"
ryan@ryan-laptop:~$

I would appreciate any help.  I am new to linux.

---

### Post by spd106 on 2006-09-12
Open the file in the gnome text editor using this command **gksudo gedit /etc/network/interfaces**.

Now read through and delete the duplicate wlan0 entry. If you are unsure what to do then by all means copy and paste the file here for us to take a look.

You may also want to have a read through **man interfaces** first.

---

### Post by RockabyeRy87 on 2006-09-12
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface wlan0 inet dhcp
wireless-essid wlan0

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




That is what I have.  For whatever reason it will not allow me to just do sudo gedit /etc/network/interfaces  anymore.  The gksudo command you provided didn't load the file either.

---

### Post by spd106 on 2006-09-12
You need to remove the last line. Can you access it with **sudo nano** or **sudo vi** instead? What about ejecting the card? or **sudo modprobe -r ndiswrapper**.

---

### Post by RockabyeRy87 on 2006-09-12
I edited it with sudo vi successfully.  When I type iwconfig I get this.

IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I have network manager installed but it's not allowing any wireless network options.  I can also no longer open system-->administration-->networking.

I also did a sudo iwlist scan and it finds the available networks.  When I start ubuntu it fails basic networking...  Also my lo network connection is disabled.

---

### Post by spd106 on 2006-09-12
If you want to use Network Manager then you will need to edit the interfaces file again. It's best to comment out all lines except those for lo and any other interfaces you don't want NM to manage.

Do you completely remove the bcm43xx driver? It's usually best to blacklist it in the /etc/modprobe.d/blacklist file. There are other threads around this forum for the details. Check lsmod to see if it's still being loaded.

---

### Post by RockabyeRy87 on 2006-09-12
I blacklisted it awhile ago, it is no longer being loaded. 

Do I have to disable my wired connection to allow my wireless to scan properly?  I am using network manager, it shows the option for wireless.  But it is no longer bringing my network up.  The iwlist scan is no longer bringing my network up either.  The Ndiswrapper is being loaded.  Wireless is active under system-->administration-->network.  What else do I need to do? :D   Thank you for all your help so far.

---

### Post by spd106 on 2006-09-12
I haven't used Network-Manager extensively yet so I'm not sure whether the wired connection will prevent the wireless from scanning. I believe that it was designed to use the best source, prefering wired over wireless. You can always uncomment the lines for it in the interfaces file.

Just be wary that this can mess up the default route, though if they're pointing to the same device it shouldn't be too much of a concern.

I would think that you should still be able to do iwlist scan even when N-M has control.

---

### Post by RockabyeRy87 on 2006-09-12
Now after about 10 after my restart it locates the networks and they appear under network manager.  I have no idea why it didn't find them sooner.  The network doesn't require a password or anything of the like.  However it still refuses to connect.  It loops around and eventually fails to connect.  No encryption key or anything.  Any ideas?  I am at a university and am considering bring my laptop down to the network administrator...but he is very rude.  He also would probably not like me connecting through linux because it allows me to bypass CCA.

---

