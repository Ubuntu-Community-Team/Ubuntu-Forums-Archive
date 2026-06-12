---
title: "Can't connect to Internet"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by tlinux on 2007-10-11
I have a dual boot setup with Windows XP and Kubuntu 7.04. I can connect to the Internet via Windows. However, the Kubuntu 7.04 connection has stopped working. I have a Linuxant-wrapped driver. I've gone through some of the files, and with my limited knowledge of the subject, it seems that Kubuntu is recognizing my driver but isn't connecting. That's all that I can determine. I have saved four files related to this and they are shown in the following pastebins:

ifconfig:  pastebin.com/m5cc281e
interfaces:   pastebin.com/m46807f1d
iwconfig:   pastebin.com/m11f556beb
lsub:   pastebin.com/m68278d8b

Any help you can give me getting reconnected will definitely be appreciated.

---

### Post by ScoPi on 2007-10-11
I'll throw this your way even though I don't have any reason to think it applies in your situation, plus from your post you're probably more of an advanced user than myself.

When I installed Ubuntu, I had to use a tool called "fwcutter" (I think that was it) to extract the requisite binaries from the Windows driver package for my wireless LAN device. Once I did that, things worked fine. I keyed off the presence of a Broadcom-related message about firmware not being present when I ran dmesg.

This probably has nothing to do with your situation, but good luck.

---

### Post by tlinux on 2007-10-13
I really could use some help on this. I don't know what to do.

Thanks to anyone who will help!

---

### Post by kevdog on 2007-10-13
Is this a USB device -- If it is can you post the following with the device plugged in:
lshw -C usb


Are you trying to use ndiswrapper for this one??

---

### Post by tlinux on 2007-10-14
"Is this a USB device -- If it is can you post the following with the device plugged in:
lshw -C usb"

Here's the output:

[INDENT]tom@emachine:~$ lshw -C usb
\WARNING: you should run this program as super-user.
tom@emachine:~$ \sudo lshw -C usb
Password:
tom@emachine:~$
tom@emachine:~$[/INDENT]

I don't use ndiswrapper. Instead, I use Linuxant's wrapper. I contacted them about this problem and they requested I send them some data. After looking at it they said nothing was wrong with it. I think they're right. I can connect to the Internet through Kubuntu, but to do so I have to type in the following instructions everytime I log  onto Kubuntu:

[INDENT]sudo iwconfig wlan0 essid linksys
sudo iwconfig wlan0 key [key number]
sudo dhclient wlan0[/INDENT]

I don't really know what these commands do,  I execute them because they were the last commands I executed before I first logged onto Kubuntu.

My obvious problem is that the values these instructions set are not retained when I log off and I don't know how to have them saved.

---

### Post by kevdog on 2007-10-14
You can see if this works for you -- edit you /etc/network/interfaces file:

gksu gedit /etc/network/interfaces

Add the following
auto wlan0
iface wlan0 inet dhcp
wireless-essid "linksys"
wireless-key [key]

See if that helps.

---

### Post by tlinux on 2007-10-14
Couldn't get the command

[INDENT]gksu gedit /etc/network/interfaces
[/INDENT]

to work. gksu wasn't installed on my system so I had to install it using apt-get. Then I got an error message trying to execute the above command. Is gksu associated with Gnome? KDE doesn't like it. 

Anyway, I went to /etc/network/interfaces  and the instructions you recommended I add are already there.

---

### Post by tlinux on 2007-10-15
I've found the problem but am not sure I've solved it permanently. The key is a hex number but the program was trying to read it as an ASCI number. Changing that allows the system to run properly.

My concern now is how do I prevent that error from occurring again. If you have any ideas as to what's causing the key type to change, I'd sure like to hear them.

Thank you!!!

---

### Post by santy_kushwaha on 2007-10-15
i'm not sure but i think that if u have safe the settings probebly i wont gave u tha hard time next time

---

### Post by tlinux on 2007-10-15
"Linux is easier if u know what are u doing Otherwise it will suck u "

This is a noble sentiment, but the problem is that much of the information needed to learn how it works isn't readily available. Many of the commands used in Linux aren't listed in any of the six Linux books I have. For example, for my current problem, it is recommended that I use the command "gksu". That's not in my books. In fact, there's almost nothing in them of any value in setting up a wireless Internet connection. I did a web search and found an article entitled, WifiDocs/WirelessTroubleshootingGuide." It's a 26 page instruction manual for solving Wireless problems. I tried to follow it as best I could, but it didn't help. In fact, I've concluded that all such Help articles are worthless. You have to be a computer geek to understand what happens when their instructions are followed, and if you're a computer geek, you don't need the Help.

---

### Post by santy_kushwaha on 2007-10-15
thats true boy that why i have that quotation there  now i can say that to u WELCOME TO LINUX

---

