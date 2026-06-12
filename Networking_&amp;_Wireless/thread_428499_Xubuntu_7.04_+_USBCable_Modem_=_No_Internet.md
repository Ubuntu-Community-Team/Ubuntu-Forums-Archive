---
title: "Xubuntu 7.04 + USB/Cable Modem = No Internet"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by rfs1970 on 2007-04-30
Hi There,

My wife has a (kind of old) notebook (Gateway Solo 2550 - 500mhz, 128mb ram and 6gb HD), and after 6 months trying to convince her how good is ubuntu, finally she agreed and let me instal (via the alternative) xubuntu 7.04

Everything is great, and her notebook is running xubuntu very smoothly. 
But, I just cannot make it detect the cable modem (motorola surfboard 5120) when I connect the usb cable.

Her computer haven't a network port, so there is no way to connect this modem in another port.

When she was using windows, everything was working, but now, 
I am here without a clue what to do about that.

I included a file containing the ifconfig, lsmod and lspci content

Thank you in advanced for any help.


r.

---

### Post by dmizer on 2007-05-01
don't have much for you here.

did some cursory searching and didn't come up with anything.  your best bet is probably going to be a pcmcia ethernet adapter.  that, or go wireless, but that would require the addition of a router.

if you decide to go wireless, pick your card from this list: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wireless%29)

---

### Post by rfs1970 on 2007-05-06
Hi There,

Finally I figured it out what was going on !
And right now, I am writing this post in my lovely ubuntu 
connected in internet via my nice usb cable modem.

So, let me share with you guys what was the solution.
:)

After one entire week looking for a solution about
how to connect my linux distro (ubuntu/xubuntu) to the internet
via my usb modem (surfboard 5120) I found the problem.

It will not be easy/fast to fix it, 
but I can guarantee that you will not be disapointed at the end
( I am not !)

Well, I couldn't accept the majority of the answers/replies
that I got from million forums that I asked for help:

"- Hey dude! Buy a network board / pcmcia"

Why for Christ sake ? 
Linux is more than 10 years old already!
Why I can't connect to the internet via a simple usb modem connection????
how it could be possible ???

Well..

The biggest problem for linux to recognize your usb cable modem
(in my case : Motorola Surfboard 5120) is a bug that come
with the kernel included in ubuntu/xubuntu 6.10 and 7.04 (as well)

If you connect your usb cable (from the modem) and then you
type at the terminal: 
> cat /var/log/syslog

probably you will see the follow error message at the end :
**usb: no configuration chosen from 1 choice**

Its because, according to this page:
[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg313403.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg313403.html)
there is a bug in these versions of the kernel (2.6.17 and 2.6.20) 
to recognize this kind of equipment.

So, to fix this issue, you will have to download the newest stable version
of the kernel where this problem was completely fixed 
(the latest one is 2.6.21.1 - Pick a mirror here: [http://kernel.org/mirrors/](http://kernel.org/mirrors/))

After you download the file,
open the terminal window and type the follow commands:
> 
sudo su
apt-get install build-essential libncurses5-dev kernel-package
cd /usr/src
cp [the-path-where-you-download-the-linux-source-file]/linux-2.6.21.1.tar.bz2 linux.tar.bz2
tar xvjf linux*
cd linux-2.6.21.1
cp /boot/config-[your-currently-version]-generic .config
make menuconfig


(if you haven't any extra settings to define, just exit the menuconfig
after you started, so it will create any extra variable that wasn't present
in your current kernel config file)

Ok, so... after its all done, now you have to compile the new kernel.
But before, I have to warn you that this process will take a quite long time
to finish. My computer is very old, and it took me almost 4 hours !!!!!!

Let's compile the kernel:
> 
make-kpkg -initrd kernel_image kernel_headers modules_image


After the compilation is done, let install it :
> 
cd ..
dpkg -i *.deb


Before you reboot your computer, add the follow line into the file /etc/modules:
> 
usbnet


And the follow lines into the file /etc/network/interfaces:
> 
auto eth0
iface eth0 inet dhcp
hwaddress ether [your-usbmodem-mac address]


The last line "hwaddress" is very important, 
You have to replace the [your-usbmodem-mac address] to
your usb modem mac address to the usb port for dynamic ip address... 

That is it.
Reboot your computer and once you are logged again,
you can access the terminal just to check it out if everything went all right
by running this command:
> 
ifconfig


You should see a eth0 port enabled.
If yes, you can browse your internet now without any trouble.

I hope it helps.


r.


PS: Sorry my s**t english, I gave my best here. :)

---

### Post by dmizer on 2007-05-06
> **rfs1970 said:**
> Well, I couldn't accept the majority of the answers/replies that I got from million forums that I asked for help:

"- Hey dude! Buy a network board / pcmcia"

Why for Christ sake ? 
Linux is more than 10 years old already!
Why I can't connect to the internet via a simple usb modem connection????
how it could be possible ???

well ... the problem with usb is that it's crap for a network connection.  less speed, less flexibility, less stability.  working or not working ... you REALLY are better off with an actual lan connection instead.

that said ... congrats for getting it to work.

---

### Post by rfs1970 on 2007-05-07
Hi Dmizer

I really apreciate your comment!
Its always good to hear a point of view from someone
with more experience !

But to be honest with you, my connection is quite good,
(I have a 4mb internet connection, and I can download files at 460kb/s)
and it's very stable with the latest kernel (2.6.21.1).

Maybe this situation was a ghost in the past,
and finally it was exorcized !!!!

Anyway, thank you very much for your post!


r.

---

### Post by JoeMama057 on 2008-04-23
Hey even though this is an older post - Thanks!

I am having a similar issue with a friend of mine. Her cable modems ethernet port doesn't work (but USB does) and she recently bought a router. (I know this is a slapstick way to get her wireless but...) I think I should set her up one of my junk boxes with Ubuntu and IPCop, connect the modem via USB and use the ethernet port to uplink to the 'Router' (which will just be acting like a WAP now)

She is too cheap to go out and buy a new cable modem (as she just bought the wireless router). 

Great post! I cant wait to try this!
Thanks
-Me

---

### Post by David the man on 2008-06-16
> **rfs1970 said:**
> 

Why for Christ sake ? 
Linux is more than 10 years old already!
Why I can't connect to the internet via a simple usb modem connection????
how it could be possible ???

just to tell you my windows [COLOR="Red"]_**XP**_[/COLOR] does not have the drivers for a usb cable modem.

But thanks anyway i had a similar problem

---

