---
title: "Accidentally killed network connection"
date: 2015-11-22
forum: Networking &amp; Wireless
---

### Post by pete46 on 2015-11-22
Hi, I have an HP MicroServer running Ubuntu 12.04 and was trying to add a new hard-drive. I was SSHing in and something went wrong and the drive stopped showing up in fdisk. Following a suggestion on a thread, I tried running pvdisplay and was told it wasn't installed but I could install it with apt-get, so I tried that.

Then, while installing the package, it removed a load of existing stuff - the last thing I saw it do was 'removing network-manager' or something along those lines.
Unsurprisingly, the connection hung and then dropped out at that point, and I was unable to reconnect.

I've plugged a monitor in and had a poke around but it's clearly got no kind of connection.

ifconfig gives the following (retyped by hand!)

> 
Link encap: Local Loopback
inet addr: 127.0.0.1 Mask: 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets: 3390 errors:0 dropped:0 overruns:0 frame:0
TX packets: 3390 errors:0 dropped:0 overruns:0 carrier:0
collisions: 0 txqueuelen:0
RX bytes 324110 (324.1KB) TX bytes:324110 (324.1KB)


Any suggestions of what to try? Looks like it's a bit of a mess..

Cheers

Pete

---

### Post by tgalati4 on 2015-11-22
Welcome to the forums.  Reinstall *network-manager*.  Before you do that, you will have to manually configure your network--[Old School]("http://http://askubuntu.com/questions/431682/how-do-i-use-etc-network-interfaces-instead-of-network-manager") style.  You will set up your /etc/network/interfaces, and use *ifup* to wake the ethernet connection or simply reboot.  Once connected and you can ping google, then you are in business.  Reinstall *network-manager* and hopefully things will return to normal.

```
sudo apt-get install network-manager
```

---

### Post by pete46 on 2015-11-23
Thanks for the reply. I've tried your suggestion and managed to reconnect to the network but was unable to reinstall network-manager.
The package installation that seemed to remove network-manager also removed some other packages first, so it may have killed off some dependencies.

Attempting to install it returned the following:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 network-manager : Depends: isc-dhcp-client (>= 4.1.1-P1-4) but it is not going to be installed
                   Recommends: modemmanager
E: Unable to correct problems, you have held broken packages.


I tried installing 'isc-dhcp-client' but it said 'isc-dhcp-client is already the newest version'. Same for 'modemmanager'.

I Googled the held broken packages message and found a suggestion to run 'dpkg --get-selections | grep hold' to find the held packages, but it doesn't return anything.

I noticed under 'dpkg --get-selections' that network-maanger (and network-manager-gnome) are marked as 'deinstall' 

Here's the full list of deinstall items:

aptdaemon					deinstall
gnome-disk-utility				deinstall
gnome-mplayer					deinstall
libpam-systemd:amd64				deinstall
network-manager					deinstall
network-manager-gnome				deinstall
policykit-1					deinstall
policykit-1-gnome				deinstall
systemd						deinstall
udisks2						deinstall
update-notifier					deinstall
usb-creator-common				deinstall
usb-creator-gtk					deinstall
xfce4-power-manager				deinstall

I used 'sudo echo "network-manager install" | sudo dpkg --set-selections' to reset it to install, but I'm not really sure what the effect of this is meant to be, or what to do next...

Any further suggestions? Thanks in advance.

Pete

---

### Post by tgalati4 on 2015-11-23
```
sudo apt-get install -f
```

---

### Post by pete46 on 2015-11-24
That gives:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  genisoimage libavdevice53 libavfilter2 libdc1394-22 libpolkit-backend-1-0
  wpasupplicant
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

---

### Post by tgalati4 on 2015-11-24
OK, so apt seems to be OK.  Few more things:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get check
sudo apt-get upgrade
```

---

### Post by pete46 on 2015-11-25
Thanks. I tried those.

'clean' returned nothing.
'update' gave a mixture of successes and failures.
'check' gave:

Reading package lists... Done
Building dependency tree       
Reading state information... Done

'upgrade' gave:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  genisoimage libavdevice53 libavfilter2 libdc1394-22 libpolkit-backend-1-0
  wpasupplicant
Use 'apt-get autoremove' to remove them.
Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

---

### Post by tgalati4 on 2015-11-26
Well, your apt system seems OK.  Go ahead and remove the unneeded packages.

```
sudo apt-get autoremove
```

It's not clear what happened as described in your original post.  *pvdisplay* only relies on PERL, so why would it remove *network-manager*?

> tgalati4@Mint17 ~ $ apt-cache search pvdisplay
liblinux-lvm-perl - Perl module to access LVM status information
tgalati4@Mint17 ~ $ apt-cache depends liblinux-lvm-perl
liblinux-lvm-perl
  Depends: perl
  Recommends: lvm2
    lvm2:i386
tgalati4@Mint17 ~ $ apropos pvdisplay
pvdisplay (8)        - display attributes of a physical volume


If your network is now working, and you can ssh into your machine, then don't worry about network-manager.  You have a subtle issue going on, and it's not clear what the fix is, at this point.

---

### Post by pete46 on 2015-11-26
OK, thanks for the help.

---

