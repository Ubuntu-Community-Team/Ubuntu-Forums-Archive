---
title: "Cannot connect to network"
date: 2020-12-05
forum: Networking &amp; Wireless
---

### Post by johnhayhow on 2020-12-05
I cannot now connect to my local network. Settings/Network gives 'VPN Not set up' .
I am on ubuntu 20.04. How do I proceed. I have limited experience with Linux.

---

### Post by yancek on 2020-12-05
>  I cannot now connect to my local network.

Does the word "now" in the above statement mean that it previously worked and now does not?  If that's the case, were any changes made and if so, what were they.
Are you using wired (etherne) or wireless?   If wireless, when you go to Network Settings, do you see an option for wireless above Network?

---

### Post by johnhayhow on 2020-12-05
I had previously been connected to the network with wireless connection. Any change was unintentional, I miskeyed a command and the terminal appeared with a message I cannot remember which did not respond to 'enter' and from which I could only escape by powering down.
When I tried to access the internet the response from 'Settings/Network' had two entries.(VPN not set up) and (Network Proxy). Using a cable connection gives the same result.

---

### Post by johnhayhow on 2020-12-06
Further information,
Re. 'VPN NOT SETUP'
I find that openvpn is already installed in the following directories:-
/usr/sbin/openvpn
/usr/lib/x86_64-linux-gnu/openvpn
/etc/openvpn
/usr/include/openvpn
/usr/share/openvpn
/usr/share/man/man8/openvpn.8.gz
How do I set this up to work?

---

### Post by SeijiSensei on 2020-12-06
Why would you need OpenVPN to connect to your local network?  It's designed to create encrypted "tunnels" to remote locations.

---

### Post by johnhayhow on 2020-12-07
Settings/Network only gives the options:- VPN (Not set up) and Network Proxy (Manual)
I have not had this situation before. How else can I connect to the network?

---

### Post by SeijiSensei on 2020-12-07
I'm afraid I'll have to leave that one for the Ubuntu gurus. I use Kubuntu and when I click the network icon in the panel ("task bar"), it scans for visible wifi routers and lets me choose the one I want. If I'm connected over Ethernet, it offers a "Wired connection" option.

---

### Post by tushardesai on 2020-12-08
Can you share the first 2 lines of output from running the command, ```
ifconfig
``` It should look somewhat like this,

```
enp0s3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.0.2.15  netmask 255.255.255.0  broadcast 10.0.2.255
```

---

### Post by johnhayhow on 2020-12-08
lo: flags=73<up,LOOPBACK,RUNNING> mtu 65536
inet 127.0.0.1 netmask 255.0.0.0
inet6 ::1 prefixlen 128 scopeid 0x10<host>
loop txqueuelen 1000 (local loopback)
RX packets 196460 bytes 11784890 (11.7 MB)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 196460 bytes 11784890 (11.7 MB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0

---

### Post by tushardesai on 2020-12-08
OK. Looks like network interfaces (wired or wireless) are either not configured or not recognized on this machine.

Q1. Is this a physical machine or virtual machine (e.g. Ubuntu guest running inside VirtualBox or VMPlayer on another host machine)?
Q2. What network interfaces (wired and/or wireless) is it supposed to have?

---

### Post by johnhayhow on 2020-12-08
This is a physical machine.
It has been working successfully on a wireless interface for more than two years until the incident described earlier in this thread.

---

### Post by CelticWarrior on 2020-12-08
Please follow [this instructions]("https://ubuntuforums.org/showthread.php?t=370108") and post the resulting file.

---

### Post by jeremy31 on 2020-12-08
Moved to Networking and Wireless

Sounds like you might have had a kernel update that may not have installed linux-modules-extra

---

### Post by johnhayhow on 2020-12-08
[FONT=sans-serif][/FONT][FONT=sans-serif]/[/FONT][FONT=sans-serif]john@john-Hybris:~$ sudo apt update
[/FONT][FONT=sans-serif][sudo] password for john:
 [/FONT][FONT=sans-serif]Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease T[/FONT][FONT=sans-serif]emporary failure resolving ‘security.ubuntu.com’
[/FONT][FONT=sans-serif]Err:2 [http://ppa.launchpad.net/musicbrainz-developers/stable/ubuntu](http://ppa.launchpad.net/musicbrainz-developers/stable/ubuntu) focal InRelease[/FONT][FONT=sans-serif]  Temporary failure resolving ‘ppa.launchpad.net’
[/FONT][FONT=sans-serif]Err:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal InRelease                 [/FONT][FONT=sans-serif]  Temporary failure resolving ‘gb.archive.ubuntu.com’
[/FONT][FONT=sans-serif]Err:4 [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) focal InRelease[/FONT][FONT=sans-serif]  Temporary failure resolving ‘ppa.launchpad.net’[/FONT][FONT=sans-serif]
Err:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-updates InRelease[/FONT][FONT=sans-serif]  Temporary failure resolving ‘gb.archive.ubuntu.com’
[/FONT][FONT=sans-serif]Err:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal-backports InRelease[/FONT][FONT=sans-serif]  Temporary failure resolving ‘gb.archive.ubuntu.com’
[/FONT][FONT=sans-serif]Reading package lists...
 Done[/FONT][FONT=sans-serif]Building dependency tree       [/FONT][FONT=sans-serif]Reading state information...
 Done[/FONT][FONT=sans-serif]139 packages can be upgraded.
 Run 'apt list --upgradable' to see them.
[/FONT][FONT=sans-serif]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/focal/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/focal/InRelease)
  Temporary failure [/FONT][FONT=sans-serif]resolving ‘gb.archive.ubuntu.com’[/FONT][FONT=sans-serif]W:
 Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease)
  Temporary [/FONT][FONT=sans-serif]failure resolving ‘gb.archive.ubuntu.com’[/FONT][FONT=sans-serif]W:
 Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease) 
 Temporary [/FONT][FONT=sans-serif]failure resolving ‘gb.archive.ubuntu.com’[/FONT][FONT=sans-serif]W:
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/focal-security/InRelease](http://security.ubuntu.com/ubuntu/dists/focal-security/InRelease)
  Temporary [/FONT][FONT=sans-serif]failure resolving ‘security.ubuntu.com’[/FONT][FONT=sans-serif]W:
 Failed to fetch [http://ppa.launchpad.net/musicbrainz-developers/stable/ubuntu/dists/focal/](http://ppa.launchpad.net/musicbrainz-developers/stable/ubuntu/dists/focal/)[/FONT][FONT=sans-serif]InRelease
  Temporary failure resolving ‘ppa.launchpad.net’[/FONT][FONT=sans-serif]W:
Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/focal/](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/focal/)[/FONT][FONT=sans-serif]InRelease
  Temporary failure resolving ‘ppa.launchpad.net’[/FONT][FONT=sans-serif]W: 
Some index files failed to download. They have been ignored, or old ones used instead

.[/FONT][FONT=sans-serif]john@john-Hybris:~$ sudo apt dist-upgrade
[/FONT][FONT=sans-serif]Reading package lists...
 Done[/FONT][FONT=sans-serif]Building dependency tree       [/FONT][FONT=sans-serif]Reading state information... 
Done[/FONT][FONT=sans-serif]You might want to run 'apt --fix-broken install' to correct these.
[/FONT][FONT=sans-serif]The following packages have unmet dependencies.[/FONT][FONT=sans-serif] linux-image-generic : Depends: linux-modules-extra-5.4.0-54-generic but it is not installed
[/FONT][FONT=sans-serif]E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution)

.[/FONT][FONT=sans-serif]john@john-Hybris:~$ apt --fix-broken install
[/FONT][FONT=sans-serif]E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
[/FONT][FONT=sans-serif]E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?

[/FONT][FONT=sans-serif]john@john-Hybris:~$ cd ../../

[/FONT][FONT=sans-serif]John@john-Hybris:/$ sudo apt dist-upgrade
[/FONT][FONT=sans-serif]Reading package lists...
 Done[/FONT][FONT=sans-serif]Building dependency tree 
      [/FONT][FONT=sans-serif]Reading state information... 
Done[/FONT][FONT=sans-serif]You might want to run 'apt --fix-broken install' to correct these.
[/FONT][FONT=sans-serif]The following packages have unmet dependencies.[/FONT][FONT=sans-serif] linux-image-generic : Depends: linux-modules-extra-5.4.0-54-generic but it is not installed
[/FONT][FONT=sans-serif]E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
[/FONT][FONT=sans-serif]john@john-Hybris:/$[/FONT]

---

### Post by CelticWarrior on 2020-12-08
Without internet connection at all there's no point in running commands that depend on it. You can use an alternative connection like USB tethering from your phone though. If even that is not available or is too complicated then please download the file in another computer and follow the remaining instructions.

---

### Post by CelticWarrior on 2020-12-08
Why are you posting the same things like you didn't even read the other posts?

---

### Post by jeremy31 on 2020-12-09
You could reboot, go into Grub menu, advanced options and select an older kernel to boot into to reinstall the kernel

---

### Post by johnhayhow on 2020-12-09
```
######### wireless info START ##########

Report from: 09 Dec 2020 12:24 GMT +0000

Booted last: 09 Dec 2020 00:00 GMT +0000

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal

##### kernel ############################

Linux 5.4.0-54-generic #60-Ubuntu SMP Fri Nov 6 10:37:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, acpi_os_name=Linux, acpi_osi=, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: CLEVO/KAPOK Computer RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1558:8509]

03:00.0 Network controller [0280]: Intel Corporation Wireless 8265 / 8275 [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Dual Band Wireless-AC 8265 [8086:1010]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2b Intel Corp. 
Bus 001 Device 003: ID 5986:112d Acer, Inc BisonCam, NB Pro
Bus 001 Device 006: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

SecureBoot disabled
Platform is in Setup Mode

##### lsmod #############################

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

##### route #############################

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root         845       1  0 Dec07 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: Permission denied

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/yourAp]] (600 root)
[connection] id=yourAp | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=yourAp
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TALKTALK39DD04]] (600 root)
[connection] id=TALKTALK39DD04 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TALKTALK39DD04
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TALKTALK-D7D3AC 1]] (600 root)
[connection] id=TALKTALK-D7D3AC 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TALKTALK-D7D3AC
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TALKTALK-D7D3AC]] (600 root)
[connection] id=TALKTALK-D7D3AC | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TALKTALK-D7D3AC
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TALKTALK9AB581]] (600 root)
[connection] id=TALKTALK9AB581 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TALKTALK9AB581
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DIRECT-B1-HP OfficeJet 4650]] (600 root)
[connection] id=DIRECT-B1-HP OfficeJet 4650 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=DIRECT-B1-HP OfficeJet 4650
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo        no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

########## wireless info END
```

---

### Post by johnhayhow on 2020-12-09
If I reboot holding 'ESC' key I get the following:-
GNU GRUB version 2.04
normal BASH-like editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completion.
No grub menu is shown for boot.
grub> prompt is shown for entry.

What grub function should I call?

---

### Post by jeremy31 on 2020-12-09
With any luck this might work ```
sudo apt install --reinstall linux-modules-extra-5.4.0-54-generic
```
Reboot

---

### Post by johnhayhow on 2020-12-10
1) result from post 20

john@john-Hybris:~$ sudo apt install --reinstall linux-modules-extra-5.4.0-54-generic
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  linux-modules-extra-5.4.0-54-generic
0 to upgrade, 1 to newly install, 0 to remove and 139 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/38.5 MB of archives.
After this operation, 190 MB of additional disk space will be used.
(Reading database ... 251413 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.4.0-54-generic_5.4.0-54.60_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-54-generic (5.4.0-54.60) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0-54-generic_5.4.0-54.60_amd64.deb (--unpack):
 unable to open '/lib/modules/5.4.0-54-generic/kernel/drivers/net/wireless/atmel/at76c50x-usb.ko.dpkg-new': Operation not permitted
Segmentation fault
john@john-Hybris:~$ 
Progress: [ 14%]

This has a similar problem to post 14 in previous thread. What is preventing dpkg lock and how is it resolved?

2) Ref instructions in former post 12, Does the 'wireless info' file in former post 18 give any indication of the problem?

3) Grub does not now provide a boot menu. How do I access earlier kernel versions to replace current fault?

---

### Post by jeremy31 on 2020-12-10
The dpkg lock error was the result of not using sudo on that command
The wireless info results just show that no modules are loaded
We might be able to change a file so that you get a grub menu at boot, post results for ```
cat /etc/default/grub
```

---

### Post by johnhayhow on 2020-12-10
john@john-Hybris:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_os_name=Linux acpi_osi="
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
john@john-Hybris:~$

---

### Post by jeremy31 on 2020-12-10
Edit it to change ```
GRUB_HIDDEN_TIMEOUT=0
```
to
```
#GRUB_HIDDEN_TIMEOUT=0
```
Save, exit text editor and do ```
sudo update-grub
```

Reboot or try the SHIFT key at boot and see if the menu appears

---

### Post by johnhayhow on 2020-12-11
I now have a boot menu.
Selecting advanced operations, these are:-
resume, clean, dpkg, failsafeX, fsck, grub, network, root, system summary.

Running fsck
/lib/recovery-mode/recovery-menu
line 80 /etc/default/rcS no such file or directory
fsck from util-linux 2,34
/dev/sda2 is mounted
e2fsck Cannot continue aborting

Running dpkg
-------long list of failures
restoring original system state
Aborting

Suggestions?

---

### Post by jeremy31 on 2020-12-11
What result for ```
ls /boot
```

---

### Post by johnhayhow on 2020-12-12
Result for ls /boot

john@john-Hybris:~$ ls /boot
config-5.4.0-48-generic      memtest86+.elf
config-5.4.0-51-generic      memtest86+_multiboot.bin
config-5.4.0-52-generic      System.map-5.4.0-48-generic
config-5.4.0-54-generic      System.map-5.4.0-51-generic
efi                          System.map-5.4.0-52-generic
grub                         System.map-5.4.0-54-generic
initrd.img                   vmlinuz
initrd.img-5.4.0-48-generic  vmlinuz-5.4.0-48-generic
initrd.img-5.4.0-51-generic  vmlinuz-5.4.0-51-generic
initrd.img-5.4.0-52-generic  vmlinuz-5.4.0-52-generic
initrd.img-5.4.0-54-generic  vmlinuz-5.4.0-54-generic
initrd.img.old               vmlinuz.old
memtest86+.bin
john@john-Hybris:~$

---

### Post by jeremy31 on 2020-12-12
Try a kernel in the advanced options that doesn't show (recovery mode) or the -54 kernel

---

### Post by johnhayhow on 2020-12-12
Making progress slowly.
I now have access to the network and the internet.
Firefox web browser demands proxy server which it never did before.
I tried unsuccessfully to install squid.(unmet dependancies)
I tried to install software upgrades. The code loaded but failed to install.
Running 'sudo apt-get install -f' gives the following:-

john@john-Hybris:~$ sudo apt-get install -f
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-5.4.0-52-generic linux-modules-5.4.0-52-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-modules-extra-5.4.0-58-generic
The following NEW packages will be installed
  linux-modules-extra-5.4.0-58-generic
0 to upgrade, 1 to newly install, 0 to remove and 196 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/38.6 MB of archives.
After this operation, 190 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 252749 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.4.0-58-generic_5.4.0-58.64_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-58-generic (5.4.0-58.64) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.4.0-58-generic_5.4.0-58.64_amd64.deb (--unpack):
 unable to open '/lib/modules/5.4.0-58-generic/kernel/drivers/thermal/intel/int340x_thermal/int3400_thermal.ko.dpkg-new': Operation not permitted
Segmentation fault
john@john-Hybris:~

---

### Post by jeremy31 on 2020-12-13
Are you running some antivirus software?

---

### Post by johnhayhow on 2020-12-13
I have sophos downloaded and thought it was installed but I cannot find it with 'apt list --installed'

---

### Post by jeremy31 on 2020-12-13
If it is not in the Ubuntu repos it will not show in that command, try
```
sudo /opt/sophos-av/bin/savdctl disable
```
Then try the updates

---

### Post by johnhayhow on 2020-12-13
I disabled sophos and was then able to complete version 20.04 update.
I took the opportunity to upgrade to version 20.10. Upgrade proceeded well towards completion but was stopped (too many errors) and a restore program run. After this I had version 20.10 working but after rebooting could only get 'safe' version. Rebooting with the other advanced options still only gives 'safe' version. Perhaps gnome is corrupted ?

---

### Post by johnhayhow on 2020-12-14
Booting in recovery mode (latest version) runs in terminal mode up to 'started bluetooth service' then in 'Recovery menu' to 'Finished daily man-db regeneration' then stops and on 'entry' exits recovery mode.

---

### Post by johnhayhow on 2020-12-14
On further consideration I believe the system is working properly but some simplified GUI is in use in place of gnome. How can I recover it?
Additionally although the system appears normal after booting, the response to commands is very slow and at each command the fan starts up (presumably the processors are very busy doing something apart with dealing with the current command)

---

### Post by johnhayhow on 2020-12-23
The problems have all now been solved and the computer is operating correctly.
This thread can now be counted completed.
Thanks to all for the help given.
Merry Christmas.

---

