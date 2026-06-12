---
title: "Support for Atheros 802.11 wireless LAN cards?"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by rokumanxes on 2010-03-21
In Hardware Drivers there are three ... things, and they are..

Atheros Hardware Access Layer (HAL) - Enabled - In Use

NVIDIA accelerated graphics driver (latest cards) - Enabled - In Use

Support for Atheros 802.11 wireless LAN cards. -Enabled - In Use


And with that... my wifi isn't working...
It says it's enabled, and in use, but...  It's not working.

Help is appreciated.

---

### Post by lkraemer on 2010-03-21
What is the Ubuntu Version? 8.04x, 8.10, 9.04, 9.10, 10.04, ????
32 bit or 64 Bit? .....Yes, it makes a difference!...Depending....
Laptop or Desktop?
USB Wifi Dongle or onboard Wifi?

First we need to know what hardware your Laptop/Desktop has installed.

Just use "copy & paste" for the commands.
And, there is a difference in LSPCI and lspci.
```

uname -r
lspci
lspci -nn
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig
ifconfig

```
Just copy & paste the commands in a Terminal window,
one at a time, and post the results.
(If you are using versions earlier than 9.10, or 9.04 use:
cat /etc/modprobe.d/blacklist)

If you connect via Ethernet cable, SYSTEM -> ADMINISTRATION -> UPDATE MANAGER
and then try connecting the Wifi it most likely will work.

lk

---

### Post by rokumanxes on 2010-03-21
I'm on a mac for actual internet.  Ethernet cable is not an option, so wifi on the laptop isn't happening.

So... On a laptop, eh... 8.04, I believe, onboard wifi, and 32 bit.

Copy and Pasting commands isn't going to work, and the output is going to be a real pain to retype...
=_='

---

### Post by 3rdalbum on 2010-03-21
EDIT: This information is not useful to the original poster, but might be useful to somebody having a similar problem on a later version of Ubuntu.

Have you tried looking up the chipset name of your wireless card, plus the words "ubuntu 9.10" on Google? For instance, "AR5108 ubuntu 9.10". You can find out the chipset name by using the "lspci" and "lsusb" commands.

---

### Post by rukiaEnix on 2010-03-21
why don't you try downloading madwifi-hal it worked for my atheros wifi:

[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)

---

### Post by 3rdalbum on 2010-03-21
> **rokumanxes said:**
> So... On a laptop, eh... 8.04, I believe, onboard wifi, and 32 bit.

Ahh, I wish you'd mentioned sooner that you're on 8.04. No wonder you're having trouble.

Install 9.10, or even 9.04, or 10.04 beta and $10 says that thing will 'just work'. Ubuntu 8.04 had some problems with Atheros wifi cards, because the drivers were undergoing a big change, and it's so old now that the latest drivers won't work with it.

---

### Post by k3lt01 on 2010-03-21
My dad's laptop had to use ndiswrapper with 8.04, 8.10 used madwifi, 9.04 and 9.10 worked out of the box with the drivers in the kernel.

---

### Post by lkraemer on 2010-03-21
rokumanxes,
We will still need the output of the commands posted to be able to help you.
Your hardware might be different.......GUESSING won't get it working.

Just highlight and copy the commands to a text file, save the file, copy
to a USB Flash Drive, insert the USB Flash Drive into the Ubuntu Machine,
open the file with gedit, copy and paste to a Terminal Window.  The results
of the commands can be piped to another text file, or copied and pasted the
same way to another file.  Then copy to the MAC and post.  Easy as can be.
What is so hard about copy & paste and pipe to a file?
PIPE info...   Open a Terminal Window and do:
```

ls -alt
ls -alt > abc.txt

```
Checkout the result of the pipe command.......in file abc.txt

Or you can pick one of the two following ways, if your hardware is supported:

Pick one method and stick with it. Don't mix-n-match.

Your options that can be used:
1. Ndiswrapper and a Windows Driver (32 Bit)....??????.inf & sys
   Your M$ Windows experience should be used to locate the proper driver....
2. Madwifi Drivers
(you will need to install.....build-essential.......meaning you need to download & install)

[http://ubuntuforums.org/showthread.php?t=1142199&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=1142199&highlight=madwifi)

You results might vary....You WILL have to Blacklist some loaded drivers that
were installed by Ubuntu 8.04x, etc.......results from the previous executed commands (lsmod).

Extra Info:
[http://ubuntuforums.org/showthread.php?t=1257103&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=1257103&highlight=madwifi)

madwifi - if yours is supported:
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
Then go to the hal-0.10.5.6 at
[http://snapshots.madwifi-project.org...-hal-0.10.5.6/](http://snapshots.madwifi-project.org...-hal-0.10.5.6/)


REF:
[http://madwifi-project.org/](http://madwifi-project.org/)
[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://linux.die.net/man/8/modprobe](http://linux.die.net/man/8/modprobe)

32 Bit - Reference URl'S:
[http://www.dailygeeks.com/howto/how-...ers-in-ubuntu/](http://www.dailygeeks.com/howto/how-...ers-in-ubuntu/)
[http://h20000.www2.hp.com/bizsupport...riesId=3739787](http://h20000.www2.hp.com/bizsupport...riesId=3739787)
[http://www.linuxforums.org/network/w...and_linux.html](http://www.linuxforums.org/network/w...and_linux.html)
[http://www.ubuntukungfu.org/blog/200...k-with-ubuntu/](http://www.ubuntukungfu.org/blog/200...k-with-ubuntu/)
[http://ubuntuforums.org/showthread.p...s+AR242+Driver](http://ubuntuforums.org/showthread.p...s+AR242+Driver)

lk

---

