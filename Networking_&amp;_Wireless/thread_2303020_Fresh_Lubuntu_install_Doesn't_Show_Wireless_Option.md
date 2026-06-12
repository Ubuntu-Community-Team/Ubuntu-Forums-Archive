---
title: "Fresh Lubuntu install Doesn't Show Wireless Options"
date: 2015-11-15
forum: Networking &amp; Wireless
---

### Post by Gibson295 on 2015-11-15
So i did a fresh dual boot of Lubuntu v 15.10 (latest build) alongside Windows XP Professional SP3
on an older Dell D250 Laptop. Specifications Intel Celeron 2.40, 1G of DDR/333 Ram has a fully function Wi-fi, ethernet and even a Modem, yah She old.
Anyways the wi-fi works fine on the Windows, but in Lubuntu i can't figure out how to set this up, I've done some research, maybe not enough. I Dual booted this on another computer alongside windows 7 and the WI-Fi options came up instantly
i had no problems their, But on this older laptop i am. All i can see is the the Little icon on the bottom next to the clock with an X Linking 2 screens. When i click on this I have Enable Networking checked but all i see are

Ethernet network (Blanked out, cause i'm not using a Cord)
disconnected (Blanked out
VPN Connections (nothing selected as i don't use)
(Checked) Enable Networking
a Blanked out Connection information
and a selectable edit connections, witch i did try to manually enter in a Wi-Fi connection with all my information, but it wouldn't let me save?? all i can do is Cancel.

not sure what the problem is here. During initial installation and setup it couldn't detect anything either.
yet the OS can update itself somehow???

plz help, thx >< Im new.

---

### Post by Hadaka on 2015-11-15
Hi,please open a terminal ctrl/alt/t and do..
```
lspci -n | awk '/0200|0280/{print $3}'
lsmod | awk '/wl|b43/{print$0}'
rfkill list all
```
post the output please
thanks.

---

### Post by Gibson295 on 2015-11-15
lspci -n | awk '/0200|0280/{print $3}' 
[B]Awk: Line 1: syntax error at or near {
[/B]lspci -n | awk '/wl|B43/{print$0}'
> rfkill list all
[B]>
[/B]

Cmd then result in bold
i tried putting that all in one command that did nothing
i also am not able to do this from the effected computer because of no internet So i'm just keying the results in to you

---

### Post by Hadaka on 2015-11-15
hi, all 3 commands are correct, the syntax has to be valid for them to work,
please COPY and paste....one line at a time.

this is one line....

lspci -n | awk '/0200|0280/{print $3}'

thanks

---

### Post by Gibson295 on 2015-11-15
8086:3580
8086:3584
8086:3585
8086:3582
8086:3582
8086:24c2
8086:24c4
8086:24c7
8086:24cd
8086:2448
8086:24cc
8086:24ca
8086:24c5
8086:24c6
14e4:4401
14e4:4320
104c:ac56


2nd cmd

b43                  401408 0
bcma                49152 1 b43
mac80211         659456 1 b43
cfg80211           483328  2 b43,mac80211
ssb                   57344 2 b43,b44


3rd cmd rfkill list all does nothing.
Example 
user@ubuntu:~$ Rfkill list all
User@ubuntu:~$

---

### Post by Hadaka on 2015-11-15
ok, so to make sure we are on the same page here please correct me
if i am not correct. You loaded 15.10 on to an old computer and dont currently
have any internet access on it. yet it has the b43 wireless driver in the module report
and b43 is not a default driver on a load. how did you get b43 on there?

---

### Post by Gibson295 on 2015-11-15
i have no clue man. All i know is i can't find any option to connect via wi-fi witch is odd because it's dual booted on another computer i tested in on prior to this and the wi-fi options come up right away.
It is the same version of Linux to, same router, all that.. only options i have are VPN Connections/Edit connections.

i enter in the 2 cmd lines you said, of course 1 at a time and posted what it showed me after.
It does not have internet acces on it currently in Lubuntu no, In Windows XP it will.
during the install process it tried to but failed so i opted to continue without that.

---

### Post by Hadaka on 2015-11-15
ok, i dont know how b43 got on there either, and unless the wifi cards are the same
and the machines are the same, copying from one machine to another doesnt always
work,so. lets try to clean up some stuff and reload the b43 with the offline no internet method.
first lets clear the stuff that got on there by osmosis. please COPY and paste...
```
sudo apt-get remove --purge firmware-b43-installer
sudo apt-get autoremove && sudo apt-get autoclean
```
ok now for the offline method. be sure to drag and drop the zip file first.
go here post #7 and follow directions.
[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)
once that is done configure your ipv4 and ipv6 in network mgr to look like the attached
[ATTACH=CONFIG]265601[/ATTACH][ATTACH=CONFIG]265602[/ATTACH]

---

### Post by Gibson295 on 2015-11-15
its not a copy from another system. it's the Exact same Bootable ISO disc, just tried it on another computer to see how'd i'd like the OS before putting it on the old one.
course that was before i realized i could dual boot, i'll give this a go, I can't copy and paste im using another computer to do this, but the laptops infront of me i can type it up

---

### Post by Gibson295 on 2015-11-15
unable to locate package firmware-b43-installer

---

### Post by Gibson295 on 2015-11-15
Ok so i did the following....

step 1. [COLOR=#000000]Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:

[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo mkdir /lib/firmware/b43[/FONT][/COLOR]sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43



My results were 
Reading
package lists... Done

Building
dependency tree       


Reading
state information... Done

E:
Unable to locate package firmware-b43-installer

john@ubuntu:~$
sudo apt-get autoremove && sudo apt-get autoclean

Reading
package lists... Done

Building
dependency tree       


Reading
state information... Done

0
upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Reading
package lists... Done

Building
dependency tree       


Reading
state information... Done

john@ubuntu:~$
sudo apt-get autoremove

Reading
package lists... Done

Building
dependency tree       


Reading
state information... Done

0
upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

john@ubuntu:~$
sudo apt-get autoclean

Reading
package lists... Done

Building
dependency tree       


Reading
state information... Done

john@ubuntu:~$
sudo mkdir /lib/firmware/b43

john@ubuntu:~$
sudo mkdir/lib/firmware/b43

sudo:
mkdir/lib/firmware/b43: command not found

john@ubuntu:~$
sudo mkdir /lib/firmware/b43

mkdir:
cannot create directory &#8216;/lib/firmware/b43&#8217;: File exists

john@ubuntu:~$
sudo cp Desktop/b43/* /lib/firmware/b43

john@ubuntu:~$
sudo cp desktop/b43/* /lib/firmware/b43

cp:
cannot stat &#8216;desktop/b43/*&#8217;: No such file or directory

john@ubuntu:~$
sudo cp desktop/b43

cp:
missing destination file operand after &#8216;desktop/b43&#8217;

Try
'cp --help' for more information.

john@ubuntu:~$
sudo cp desktop/b43/*/lib/firmware/b43

cp:
missing destination file operand after
&#8216;desktop/b43/*/lib/firmware/b43&#8217;

Try
'cp --help' for more information.

john@ubuntu:~$
Sudo cp desktop/b43/*

No
command 'Sudo' found, did you mean:


Command 'udo' from package 'udo'
(universe)


Command 'sudo' from package
'sudo' (main)


Command 'sudo' from package
'sudo-ldap' (universe)

Sudo:
command not found

john@ubuntu:~$
sudo mkdir /lib/firmware/b43

mkdir:
cannot create directory &#8216;/lib/firmware/b43&#8217;: File exists

john@ubuntu:~$
sudo cp desktop/b43/* /lib/firmware/b43

cp:
cannot stat &#8216;desktop/b43/*&#8217;: No such file or directory

---

### Post by Gibson295 on 2015-11-15
cp: cannot stat 'Desktop/b43/*: no such file or directory
its unziped onto the desktop.

---

### Post by Hadaka on 2015-11-15
hi,its D as in capital Desktop

sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

you will notice in Ubuntu for Downloads,Desktop,Document and a few others start with an uppercase letter
this usually means its a folder. It looks like you managed to create ........ /lib/firmware/b43
so you only have 4 commands left...i wrote COPY and paste for a reason.

---

### Post by Gibson295 on 2015-11-15
yeah thats weird, tried everything on that thread hmm..
My computer uses a Dell wireless 1350 WLAN connects in windows XP without a hitch.
i just don't get the option for wi-fi at all. it just tells me their's no Ethernet connection.

---

### Post by Gibson295 on 2015-11-15
Fyi i was copying and pasting
And ironically i just booted into windows XP to concern the Specifications of the wi-fi card i';m using...

All of a sudden i reboot into Lubuntu, and The Wi-Fi is now working.
Heh, Thanks Boss!!

---

### Post by Hadaka on 2015-11-15
Good news ! glad its working, please log back in to this thread
and click tools ...upper right and mark as SOLVED
thanks
and dont forget to...
```
sudo apt-get update
```

---

