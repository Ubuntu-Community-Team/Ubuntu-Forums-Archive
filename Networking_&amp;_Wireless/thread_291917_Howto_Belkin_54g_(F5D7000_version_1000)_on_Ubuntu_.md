---
title: "Howto: Belkin 54g (F5D7000 version 1000) on Ubuntu and Xubuntu (Dapper)"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by TiredBird on 2006-11-03
I have a Belkin 54g Wireless Desktop Network Card. (This card was not made for a laptop, it goes in a PCI slot of a rather oldish computer.) This card is officially designated as model F5D7000, version 1000. (These numbers are on the card itself.) It has a Broadcom 4306 chipset, (which I learned from the Device Manager on Ubuntu). Although I have not had any contact with either company it is my understanding from reading posts on this and other forums that neither company has been at all cooperative about providing drivers for or getting their cards to work with any OS other than Microsoft's.

THANKS to a couple others who posted their efforts on this forum, my card is working with Ubuntu 6.06 and Xubuntu 6.06. Since it took a combination from both posts, I have documented how I made it work.

The information came from the following two posts and much of 'my' wording is taken directly from one or the other. (Plagerism at its best - I hope.)

The two posts I used are [HOW TO: Configure wireless cards with Broadcom chipsets]("http://ubuntuforums.org/showpost.php?p=125537&postcount=1") and [Broadcom 4306 With Ndiswrapper 54 Mbps]("http://ubuntuforums.org/showpost.php?p=1169984&postcount=1")

Broadcom chipsets are used by many manufacturers and Belkin uses chipsets from other manufacturers too. Find out what your chances are for success by running the following command:
```
lspci | grep Broadcom\ Corporation
```
If you got 'Broadcom 4306' this is probably going to work for you; Close? It might be worth a try. But if it's not Broadcom, forget it.

Notes (assuming you're continuing on): 

1. You shouldn't use a root terminal to execute the code in this how-to; use a normal terminal session instead.

2. I used the same identical procedure for both Ubuntu and Xubuntu (both Dapper). On Xubuntu, I put a symlink into /usr/bin so I could use the command 'gedit' instead of 'mousepad'. I don't know for sure that it will work on Kubuntu but it should.

3. Most of the commands are in code boxes so you can easily copy and paste. I would recommend doing that. I have tested all of these commands and they work. Don't take a chance on typo's messing you up. Don't confuse ones and ells. Don't leave out spaces or put them in when they don't belong. Make it easy on yourself. Copy and paste.

4. If you encounter any errors that I don't mention, STOP! Find out what the problem is before you continue. This how-to wasn't meant for a robot. You are expected to do some thinking too.

These two companies are not the only ones who have made it difficult to get their hardware working on something other than Windoze. Fortunately, some very clever people have created a method, commonly known as 'ndiswrapper', to use Windoze drivers with Gnu/Linux systems. If you've made anything more than a cursory attempt to get your interface working you probably already have files, directories, modules, etc., related to ndiswrapper. The first step is to get all of that cleaned up.

If this is your first attempt or you have not tried too many combinations yet, some or all of these commands will report errors; ignore the errors. Execute the commands even if none of them work. Make sure you are starting with a clean system. 
```
sudo modprobe -r bcmwl5 
sudo rmmod ndiswrapper 
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper
```
You're going to need the Windoze driver files for the interface. I copied mine off the CD that came with the card. If you can't find them someplace in your home or office, you can probably get them from some download site. 

The files you are looking for are 'bcmwl5.inf' and 'bcmwl5.sys'. Copy them to your Desktop.

Ubuntu provides an open software driver that works with many of the Broadcom chipsets. If you did an install with this card in the machine, the installer probably attempted to configure it and may have left some files and configurations behind that you need to get rid of.
```
sudo rmmod bcm43xx
```
Make sure that the Ubuntu supplied driver does not get used at some time in the future. Make an addition to a module blacklist that is referred to by the kernel.
```
gksudo gedit /etc/modprobe.d/blacklist

```
go to the end of the file and add the following two lines:
```
# get rid of ubuntu supplied driver for belkin 54g (broadcom) wifi card
blacklist bcm43xx

```
Save the file and exit the editor.

Yes, I know I told you to uninstall this earlier. Just making sure you have clean tools.
```
sudo apt-get install ndiswrapper-utils

```
(If you don't have an internet connection, ndiswrapper-utils is also on the install CD.)

Now, to make use of those two files on your Desktop. (You do need both of them, otherwise it won't work.)
```
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
```
No need to 'sudo' the following. You're just checking to make sure everything's installed okay. This command should report hardware and driver as installed.
```
ndiswrapper -l
```
This assigns the alias 'wlan0' to the driver.
```
sudo ndiswrapper -m

```
I'm not positive but I think this makes the system aware of the new installation.
```
sudo modprobe ndiswrapper
```
Make sure the kernel knows about it everytime it starts.
```
gksudo gedit /etc/modules

```
add the line
```
ndiswrapper

```
It is unlikely that this is the only network interface you have in your system. The hardwire one may not be used anymore but it is still there, maybe even a part of the mother-board. In any event it's time to delve into the naming of network interfaces a little. 

Assuming you have two, they are probably labeled 'eth0' and 'eth1', at least they were on both of my systems, however, on one system 'eth0' was the hardwire interface and on the other one, (same machine - very confusing), 'eth0'was the wireless interface. With the scheme we are using here, 'wlan0' has got to be the wireless one and I recommend you make 'eth0' the hardwire one.

Start by editing the interface table:
```
gksudo gedit /etc/iftab
```
This file has one line for each interface and each line should include a mac address. Match it up with the mac address printed on your wireless card and change the label on that line to 'wlan0'. If you have another line in that file, name the interface 'eth0'. Here's what my interface table looks like:
```
eth0 mac 00:06:72:4a:91:2e arp 1
wlan0 mac 00:63:bd:92:21:a9 arp 1
```
Next the interfaces descriptor file:
```
gksudo gedit /etc/network/interfaces
```
Look at the 'man' pages and any other installations you might have to get an idea of what this should look like. Safest bet is to leave it as close to the way you found it as possible. However, you do have to make sure that the stuff related to the wireless connection is labeled with 'wlan0' and the hardwire one with 'eth0'. You've got to have the 'lo' for the loopback but otherwise you can get rid of all the others that are not related to actual interfaces. A copy of my interfaces descriptor file follows:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The hardwire network interface
iface eth0 inet static
address 192.168.2.5
netmask 255.255.255.0
gateway 192.168.2.1

# The wireless network interface
iface wlan0 inet static
address 192.168.2.5
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid ************************
wireless-key **************************
```
Okay, it's time to reboot and see if it worked. I'm not terribly religious but I did say a little prayer while the machine was rebooting - you might do the same. Anyway, System -> Network or something like that to get the 'network-admin' applet. See if you got it. 

If you're not even close - well we tried. But if you're close yet still not completely there you might look back at the things we did and see if a small change might fix it.

Good luck!

---

