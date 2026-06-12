---
title: "Failed to install icewm"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by g2c on 2009-04-22
I followed the howto for low memory machines in [http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm) and succeeded to install Ubuntu 7.10 alternate on my Armada (300MHz cpu, 64M ram, 4G disk) – I asked to erase win 98 so all 4G are available to Ubuntu. 

After rebooting, I logged in and tried to install the GUI and other stuff recommended in [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) by typing the two commends referred to there:

[I]sudo apt-get update
sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic[/I]

am getting *could'nt find package icewm*


Note that the CD is unloaded and I am connected to the Internet.

Thanks for your help

Guy

---

### Post by snowpine on 2009-04-22
Ubuntu 7.10 is no longer supported. The repositories are closed and you will not be able to install new applications/packages from them. I suggest installing a more recent version of Ubuntu--8.10 or newer. (I just noticed your system specs; 8.04 will not install with only 64mb of ram).

---

### Post by g2c on 2009-04-22
The alternate 8.10 does not have the options described in the howto; How do one launches the *install a command line system?* in this version?

---

### Post by JK3mp on 2009-04-22
upgrade your hardware and install a newer version. Sorry

---

### Post by snowpine on 2009-04-22
> **g2c said:**
> The alternate 8.10 does not have the options described in the howto; How do one launches the *install a command line system?* in this version?

I think you press F4 on the first screen (after you choose a language and before you choose Install) to select the command line option. If that doesn't work, try the minimal install cd (mini.iso) a 10mb netinstaller than can be used to install just a CLI system.

Understand however that your system is well below the minimum specs for Ubuntu (256mb of ram is the recommended minimum) and you might be better served with a distro like DSL (damn small linux) specifically designed for older hardware. Good luck!

---

### Post by kerry_s on 2009-04-22
grab this:
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

press <tab>, type> **vga=791 lowmem**, press <enter> to boot and start the install.

at software selection uncheck "**desktop**" & "**standard**" that will give you a base install.

log in as root
type> **apt-get install xorg icewm menu epiphany pcmanfm leafpad gksu sudo**

type> **exit** <to get out of root

log in as your user
type> **startx**

epiphany = light web browser, uses like 16mb->18mb compared to firefox 20+mb that grows with use.
pcmanfm = file manager
leafpad = text editor

i left out synaptic cause its a big dog, will use up lots of memory and it's slow, better you learn to use apt-get or aptitude.
[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

---

### Post by g2c on 2009-04-23
Thank you all, 

I hoped I could avoid buying a new lap as to replace the stolen one and that Linux would allow me to reuse that old Armada disdained by the thieves 
Thanks again

Guy

---

### Post by Eisenwinter on 2009-04-23
You should try Arch Linux. You will more than likely be able to set up a minimal system for your wishes with that distro.

---

### Post by g2c on 2009-04-23
> **kerry_s said:**
> grab this:
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

press <tab>, type> **vga=791 lowmem**, press <enter> to boot and start the install.

at software selection uncheck "**desktop**" & "**standard**" that will give you a base install.

log in as root
type> **apt-get install xorg icewm menu epiphany pcmanfm leafpad gksu sudo**

type> **exit** <to get out of root

log in as your user
type> **startx**

epiphany = light web browser, uses like 16mb->18mb compared to firefox 20+mb that grows with use.
pcmanfm = file manager
leafpad = text editor

i left out synaptic cause its a big dog, will use up lots of memory and it's slow, better you learn to use apt-get or aptitude.
[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

Hi Kerry,

Indeed I have a working debian now. Thank you!
Little problem though; when Application > www browsers > (w3m or Links) a black window appears and disappear can not see no epiphany.

Guy

---

### Post by kerry_s on 2009-04-23
run> update-menus
in terminal, see if that helps.

run> epiphany
in terminal, see if it works or what the error is.

---

### Post by g2c on 2009-04-24
Kerry darling, epiphany-browser not epiphany :) Yet, if it were not you i'd have given up.

Writing this from my old dusty armada

Guy

---

### Post by kerry_s on 2009-04-24
> **g2c said:**
> Kerry darling, epiphany-browser not epiphany :) Yet, if it were not you i'd have given up.

Writing this from my old dusty armada

Guy

:lolflag: my bag, i haven't done a debian build up in a while. i'm using arch now, in arch it's just epiphany.

---

### Post by kerry_s on 2009-04-28
hey g2c, you should try some of the gpe programs, there made for low resource handheld devices, there very small and fast.
i used them on a friends setup a couple of days ago to keep it lite, he only has 64mb ram to work with.

instead of thunar, try gpe-filemanager, it doesn't do hidden files or create files, but other than that works great.

instead of leafpad, try gpe-edit for text editor.

there's other things to like a calendar, notes, etc...

just letting you know, it's worth looking at.

---

### Post by g2c on 2009-04-29
Hi Kerry,
i left the lap running all the night to install Hebrew. In the morning it was dead. Won't boot from hdd nor cd.

i'll have to restitute the borrowed Toshiba in a couple of days and will have and buy another lap. It's got to be light as to always carrying it in my bag; Was thinking of either asus 1000he or hp 2140; may be in Israel I'd better buy the hp for the support.

May i contact you to get help for installing dual boot? (Won't have no cd drive)

Btw the file system you recommended was 'fileman' something (not thunar). i liked it very much as it showed the pics as icon on jpg's

See you

Guy

---

### Post by kerry_s on 2009-04-29
go for the eee 1000he or 901, they have 9 hour battery's, the hp 2140 is only a 3 cell, thats only like 2 maybe 2.5 hours of battery. i been looking at the netbooks to, but i think i'm going to wait till the dual core atoms are out. the 901 is already supported in linux, but the 1000he is still new so expect some problems with linux. anyways do your home work, most netbooks are the same internally, so just make sure you get 1 with a battery that suits your needs, the 1000he has the newer n280 atom aswell, while most still have the n270 atom.

---

