---
title: "Idea and example: utility to automatically configure ANY wireless card in Ubuntu"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by pytheas22 on 2008-06-11
Even though more and more wireless cards are supported out of the box these days, many still aren't.  Worse, a lot of the devices that promise to work painlessly out of the box (and that people buy specifically because they think they'll work easily with Linux) require special tweaking to work well.  Of the three wireless devices that I own, only one (an Atheros card) really "just works" to my satisfaction.  My Broadcom 4306 card doesn't work in Hardy until I revert to the bcm43xx driver, and my DWL-G122 rev. C (rt73 chipset) sort of works out of the box but crashes arbitrarily and doesn't support ad-hoc or monitor modes; I therefore have to install the legacy driver from serialmonkey to get the device working reliably.

I know from browsing these forums that there are plenty of other people whose wireless cards also don't come close to working out of the box in Ubuntu.  This is a source of a lot of frustration, especially for newcomers who don't know where to find the resources to get their wireless working well.  And not having reliable wireless is a major deal-breaker for people trying to switch to Linux.

In light of this, I was thinking that it would make a lot of sense to write a script that would be able to automatically figure out which kind of driver to use for a particular device and then apply it, along with any necessary tweaks, with minimal effort by the user, à la Automatix (I know there are a lot of issues with Automatix, but the concept behind it, not its problematic execution, is what I'd like to emulate).  [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"), a utility to automatically set up nvidia and ATI graphics cards, is another example of what I'd like to do for wireless drivers.  As far as I know, nothing like this exists.

So I started writing a (pretty dirty) bash script to make wireless configuration as easy as possible.  The strategy is very simple: use lspci/lsusb to figure out which kind of device we're dealing with, and then run the commands necessary to install drivers and firmware as needed.  It also provides an option to manually select which drivers to install if the user wishes, which would be useful in cases where there is more than one way to get a card working (e.g. next-generation drivers vs. legacy drivers).  In cases where no native driver exists for a particular device, the script could automatically install ndiswrapper and the appropriate Windows driver.

The script that I have now is meant merely for proof-of-concept purposes, and only supports the Broadcom and Ralink cards that I own.  With the help of other people, however, it would be easy to extend the script to support many more devices.  All it would take is the lspci/lsusb output for devices you own that don't work well out of the box and the steps you took to get them working (ideally, the steps would be reduced to bash commands, but if used a GUI for some steps, we can figure out how to translate it into bash commands).  So if you think this is a worthwhile idea and would be willing to help expand the script, please post.  If this becomes a project worth pursuing, I'll get web space, but I'm making this post now just to see how much support there is.

I would also be grateful to anyone who could give me tips on making the bash script cleaner.  I don't officially have any idea how to program--I only learned how to muck my way around bash by accident--and I know that there are some problems with the script as it exists now, so suggestions are welcome.

I think that a utility like this would be useful to a lot of people, especially Ubuntu neophytes.  If it works out, we could look into writing a GUI for the script to make it more user-friendly, as well as packaging it into a .deb.

If you have comments on the idea or its execution, or want to contribute information about your wireless card and what you did to make it work, please post.

Here's my proof-of-concept script (I emphasize that it's for concept-proving only and has been very lightly tested; I wouldn't run it as root without first making sure that it's not going to disturb your system.  Without root it shouldn't be able to do much beyond ask a few questions.):

```
#!/bin/bash
#
#This is a script to automatically configure wireless devices in Ubuntu
tput bold
echo 'Welcome to the wireless-driver autoconfiguration program for Ubuntu.
'
echo 'Enter 1 to make the utility try to automatically detect and configure your card (please make sure the device is connected and powered on).'
echo 'Enter 2 to manually select the appropriate driver from a list.
>>>'
read choice

if echo $choice | grep -q '2' > /dev/null
then echo '		Manual driver selection

1. rt73 (Ralink legacy driver) from http://rt2x00.serialmonkey.com
2. bcm43xx (Broadcom)

Please enter your choice
>>>'
read driver
fi

tput reset

if lsusb | grep -q 07d1:3c03 #DWL-G122 rev C1
then driver=rt73
fi

if lspci | grep -q 'BCM4306*rev 03' #Broadcom 4306
then driver=bcm43xx
fi

############################ rt73 ##################################
if (echo $driver | grep -q '1' || echo $driver | grep -q rt73)
then mkdir ~/tmp ###create temporary directory for build process
cd ~/tmp
echo 'Grabbing driver source code...'
wget -q http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz
tar -xzvf rt73* > /dev/null
cd rt73*/Module
echo 'Preparing tools to build driver...'
apt-get install build-essential rutilt > /dev/null
echo 'Compiling and installing driver...'
make -s
make -s install
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
rm -rf ~/tmp ###remove temporary directory
tput bold
echo '



The rt73 (Ralink) driver from http://rt2x00.serialmonkey.com\ has been installed.  Please reboot your computer to activate it.

		>>>Important<<<

Please note that your wireless card will most likely *NOT* work properly with Network Manager, the default wireless connection manager in Gnome.  You should use the Rutilt utility to control the card.  Rutilt can be found under the System>Administration menu.

Please also note that you will probably have to reinstall your wireless driver again if you change your kernel or upgrade Ubuntu (e.g. from Ubuntu 8.04 to Ubuntu 8.10).'
tput reset
fi

########################## bcm43xx ###################################
if (echo $driver | grep -q '2') || (echo $driver | grep -q bcm43xx)
then echo 'Blacklisting conflicting drivers...'
sed -e 's/bcm43xx/b43/' /etc/modprobe.d/blacklist > /dev/null
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'Downloading bcm43xx firmware...'
apt-get install bcm43xx-fwcutter ###get firmware cutter; user will be prompted to also automatically fetch firmware file.
modprobe bcm43xx
tput bold
echo 'The bcm43xx (Broadcom) driver has been installed.  You should now be able to connect using Network Manager or your favorite wireless connection manager.'
tput reset
fi
```

---

### Post by jtmedin on 2008-07-10
Tried to run ur bash script & got trouble on the 'read choice' line. How to you run a bash script in terminal? TIA

---

### Post by pytheas22 on 2008-07-11
I had given up on hoping for support on this idea; thanks for your interest.

To run the bash script, you should paste it into a text file and save it with a name ending in ".sh" (for example, "wifi.sh").  Then make sure it's executable:
```

chmod +x wifi.sh
```

Then either of these commands should run it, with differences in the way they do it, but for a simple script like this the behavior should be the same:
```

sudo ./wifi.sh
sudo sh wifi.sh
sudo bash wifi.sh
```

I should warn you that this script has hardly been tested extensively; the point of it was really just to prove my concept.  I don't *think* it will hurt anything, but I can't guarantee it.  But if you try it, please let me know how it goes.

---

### Post by jtmedin on 2008-07-24
did sudo ./wifi.sh         and got unable to find ...
did sudo bash wifi.sh      and got to enter 1/2

entered a 2 & got 
.ifi.sh:line 34 syntax error near unexpected token

then it echoed line 34:if (echo $driver | grep -q '1' || ...


_________________________________________________________________

Wonder if i was unable to copy ur script correctly from ur original post. If i read ur script correctly i should have got: Manual driver selection

1. rt73 ...
2. bcm43xx ...

Please enter you choice
>>>



????

---

### Post by pytheas22 on 2008-07-25
Thanks for reporting back.  

The script seems to work for me so using both 'sh' and 'bash' so I'm not sure what's up; maybe we have different versions of sh and bash.  What does the command 'bash --version' tell you?  Mine says that I use "GNU bash, version 3.2.39(1)-release (x86_64-pc-linux-gnu)."

In any case, it may help to change line 34 to this:
```

if ((echo $driver | grep -q '1') || (echo $driver | grep -q rt73))
```

As I say, I don't know much about bash programming (or programming in general), but I think that maybe that change will help.  And anyway, the script that I wrote is a mess; I only did it to demonstrate the feasibility of writing something to auto-configure wireless in Ubuntu.  If it ever becomes something real (which is unlikely, I think, given the apparent lack of enthusiasm for the idea, but that's ok), I would hope that someone who has more programming experience would help to clean it up.  It might also not be a bad idea to write the script in Python or Perl instead of bash; they'd make it more extendable, faster and easier to add a GUI.

Also, running the script with:
```

sudo sh wifi.sh
```

is probably best.  From what I understand, bash and sh are basically the same thing (interpreters of bash scripts), but in some situations they work differently, and sh is the standard interpreter on modern Linux.  There are lots of other variants too (ash, sash, ksh, zsh...) but again, they're not used by many people.

If you get a change to try a second time, please post the results.

---

### Post by jtmedin on 2008-07-30
Ok here is what i got from teminal attempting to do as u suggested:

ted@tm-laptop:~/Desktop$ sudo sh wifi.sh
[sudo] password for ted: 
'put: unknown terminfo capability 'bold
Welcome to the wireless-driver autoconfiguration program for Ubuntu.

Enter 1 to make the utility try to automatically detect and configure your card (please make sure the device is connected and powered on).
Enter 2 to manually select the appropriate driver from a list.
>>>
2
: bad variable name
: not found: 
wifi.sh: 34: Syntax error: word unexpected (expecting "then")
ted@tm-laptop:~/Desktop$ gedit wifi.sh
ted@tm-laptop:~/Desktop$ bash --version
GNU bash, version 3.2.39(1)-release (i486-pc-linux-gnu)
Copyright (C) 2007 Free Software Foundation, Inc.
ted@tm-laptop:~/Desktop$ sudo sh wifi.sh
'put: unknown terminfo capability 'bold
Welcome to the wireless-driver autoconfiguration program for Ubuntu.

Enter 1 to make the utility try to automatically detect and configure your card (please make sure the device is connected and powered on).
Enter 2 to manually select the appropriate driver from a list.
>>>
2
: bad variable name
: not found: 
wifi.sh: 34: Syntax error: word unexpected (expecting "then")
ted@tm-laptop:~/Desktop$ sudo bash wifi.sh
'put: unknown terminfo capability 'bold
Welcome to the wireless-driver autoconfiguration program for Ubuntu.

Enter 1 to make the utility try to automatically detect and configure your card (please make sure the device is connected and powered on).
Enter 2 to manually select the appropriate driver from a list.
>>>
2
': not a valid identifierchoice
: command not found
'ifi.sh: line 34: syntax error near unexpected token `
wifi.sh: line 34: `if ((echo $driver | grep -q '1' || echo $driver | grep -q rt7'))
ted@tm-laptop:~/Desktop$ 






__________________________________________________________________________
and here is what wifi.sh looks like after i added the ()'s to line 34
#!/bin/bash
#
#This is a script to automatically configure wireless devices in Ubuntu
tput bold
echo 'Welcome to the wireless-driver autoconfiguration program for Ubuntu.
'
echo 'Enter 1 to make the utility try to automatically detect and configure your card (please make sure the device is connected and powered on).'
echo 'Enter 2 to manually select the appropriate driver from a list.
>>>'
read choice

if echo $choice | grep -q '2' > /dev/null
then echo '		Manual driver selection

1. rt73 (Ralink legacy driver) from [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
2. bcm43xx (Broadcom)

Please enter your choice
>>>'
read driver
fi

tput reset

if lsusb | grep -q 07d1:3c03 #DWL-G122 rev C1
then driver=rt73
fi

if lspci | grep -q 'BCM4306*rev 03' #Broadcom 4306
then driver=bcm43xx
fi

############################ rt73 ##################################
if ((echo $driver | grep -q '1' || echo $driver | grep -q rt73))
then mkdir ~/tmp ###create temporary directory for build process
cd ~/tmp
echo 'Grabbing driver source code...'
wget -q [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)
tar -xzvf rt73* > /dev/null
cd rt73*/Module
echo 'Preparing tools to build driver...'
apt-get install build-essential rutilt > /dev/null
echo 'Compiling and installing driver...'
make -s
make -s install
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
rm -rf ~/tmp ###remove temporary directory
tput bold
echo '



The rt73 (Ralink) driver from [http://rt2x00.serialmonkey.com\](http://rt2x00.serialmonkey.com\) has been installed.  Please reboot your computer to activate it.

		>>>Important<<<

Please note that your wireless card will most likely *NOT* work properly with Network Manager, the default wireless connection manager in Gnome.  You should use the Rutilt utility to control the card.  Rutilt can be found under the System>Administration menu.

Please also note that you will probably have to reinstall your wireless driver again if you change your kernel or upgrade Ubuntu (e.g. from Ubuntu 8.04 to Ubuntu 8.10).'
tput reset
fi

########################## bcm43xx ###################################
if (echo $driver | grep -q '2') || (echo $driver | grep -q bcm43xx)
then echo 'Blacklisting conflicting drivers...'
sed -e 's/bcm43xx/b43/' /etc/modprobe.d/blacklist > /dev/null
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'Downloading bcm43xx firmware...'
apt-get install bcm43xx-fwcutter ###get firmware cutter; user will be prompted to also automatically fetch firmware file.
modprobe bcm43xx
tput bold
echo 'The bcm43xx (Broadcom) driver has been installed.  You should now be able to connect using Network Manager or your favorite wireless connection manager.'
tput reset
fi

---

### Post by pytheas22 on 2008-07-30
Thanks for trying it again.  It seems like the way you're copying and pasting the script is throwing something off...like the first letter of some commands is being cut off (e.g tput > put).  Try downloading the script from my website:
```

wget http://burnthesorbonne.com/files/wifi.sh
```

and then run it with
```

chmod +x wifi.sh
sudo ./wifi.sh
```

hopefully that will get around these formatting issues.

---

### Post by jtmedin on 2008-09-28
Ok finally got back to this problem but now my notebook is dead with a bad hard drive. Downloaded your script on my desktop & now the script is working. Will let you know what happens when my notebook comes back up. Thanks for your patients.

---

### Post by jtmedin on 2008-10-03
Ok finally have the notebook running & have ubuntu 8.04 up & running. Downloaded ur script by connecting with a cable. Ran the script & it flashed something on the screen & then returned the prompt. Went to the connect to wireless network but got only the wirling circles & then finally failure.

---

### Post by jtmedin on 2008-10-03
Ok did: sudo sh wifi.sh > temp
to find out what it was doing. It did a lot of downloding & configuring & then came back with the prompt. So ur script did its thing but there must be other problems. BTW the bcm34?? (forget what the actual device name is) device works fine in windowns :-(.

---

### Post by pytheas22 on 2008-10-04
Again, thanks for giving this another shot.  At this point, however, I don't know how much more effort anyone should spend on this script.  As the wireless stack in the kernel is becoming more and more stable, this script will be less and less useful--in Intrepid more wireless cards should "just work."

I'd still like to solve your troubles though, of course.  Please post the output of these commands, and we can figure out how to solve the issue manually:
```

lspci -nn
lsusb
lshw -C Network
```

---

