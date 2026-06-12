---
title: "Need help setting up Compaq C700-series laptop."
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by Grimhound on 2008-02-26
I'm trying to set up Gutsy on a Compaq Presario C700-series laptop, and am brand new to Linux. I keep running into issues.

One: Even after using the method of installing the bcm34xx-fwcutter, the Broadcom wireless card won't pick anything up.

Two: When I try to check anything via sudo and it asks for a password, Ubuntu locks me out of my own keyboard so I can't enter the password.

Now, I'm at the point where it says the card is active, but I can't figure out how to get it to find the Wireless network. Does anyone have any tips or ideas or solutions so I can get my laptop up and running?

---

### Post by agim on 2008-02-26
hey again. First, sudo is not locking you out of your keyboard. The fact that the cursor doesn't move is a safety feature. That way, if someone is looking over your shoulder, they can't see how many characters your password is.

To make sure everything is working properly. Type iwconfig and paste the output.

after that, if you don't have an icon on your panel that looks like an internet icon type this into a terminal and you should get one.

nm-applet

---

### Post by Grimhound on 2008-02-26
> **agim said:**
> hey again. First, sudo is not locking you out of your keyboard. The fact that the cursor doesn't move is a safety feature. That way, if someone is looking over your shoulder, they can't see how many characters your password is.

To make sure everything is working properly. Type iwconfig and paste the output.

after that, if you don't have an icon on your panel that looks like an internet icon type this into a terminal and you should get one.

nm-applet

lo          no wireless extensions.

eth0     no wireless extensions.

eth1     IEEE 802.11b/g  ESSID: off/any  Nickname: "Broadcom 4311"
            Mode: Managed  Frequency= 2.472 GHz  Access Point: Invalid
            Bit Rate= 1 Mb/s    Tx-Power=18 dBm
            RTS thr: off    Fragment thr: off
            Link Quality: 0/100  Signal level= -256 dBm  Noise level= -256 dBm
            Rx invalid nwid: 0   Rx invalid crypt: 0   Rx invalid frag: 0
            Tx excessive retries: 0    Invalid misc: 0    Missed beacon: 0

Had to type it.

And now I have two internet things. How do I kill one?

And I just accidently deleted all my panels.

---

### Post by agim on 2008-02-26
Your connection looks really slow, only 1mb a second. To get rid of one network applet, just right-click and remove.

As far as the status bar goes, if you mean the panel (the bars on the top and bottom of an Ubuntu screen) then type gnome-panel into a terminal.


Are you very far from your wireless source? 1mb is extremely low.

Edit: nevermind, its low because you aren't connected. lol

---

### Post by Grimhound on 2008-02-26
> **agim said:**
> Your connection looks really slow, only 1mb a second. To get rid of one network applet, just right-click and remove.

As far as the status bar goes, if you mean the panel (the bars on the top and bottom of an Ubuntu screen) then type gnome-panel into a terminal.


Are you very far from your wireless source? 1mb is extremely low.

No, I'm not very far from my wireless source. There IS NO wireless being received. It isn't connected to or detecting the network. The network is there, it's at 15mbs a second.

So how do I get it to recognize it?

---

### Post by agim on 2008-02-26
So, when you click the network applet, it shows no sources?

PS I know that we can get the wireless going on your computer. I have a friend with the same computer (Compaq C700 series) and the same network card and it works great.

---

### Post by Grimhound on 2008-02-26
> **agim said:**
> So, when you click the network applet, it shows no sources?

PS I know that we can get the wireless going on your computer. I have a friend with the same computer (Compaq C700 series) and the same network card and it works great.

I'm not sure how to even browse to find a network, but when I enter it in manually (and I'm not even sure if I'm doing that right), I don't come up with anything.

---

### Post by Grimhound on 2008-02-26
I have to apologize if I come off in a bad way. This is my third time trying to set up Ubuntu on a computer, and I've had little luck with previous attempts. It gets unnerving after a while.

When I click on it, it shows Wired Networks greyed out, and Wireless Networks black, but I can't click on it or anything.

---

### Post by agim on 2008-02-26
Ok, I think we are talking about two different things. after you type nm-applet, a network icon should appear. Left-Click on it and it should read a network. If it doesn't, we may need to try a different approach. I personally use something called ndiswrapper to connect my broadcom wireless card. If we need to we will do that. It should only take 10 minutes.

Also, just to be sure. I assume you are on a wired connection right now, using Ubuntu. Correct?

---

### Post by Grimhound on 2008-02-26
> **agim said:**
> Ok, I think we are talking about two different things. after you type nm-applet, a network icon should appear. Left-Click on it and it should read a network. If it doesn't, we may need to try a different approach. I personally use something called ndiswrapper to connect my broadcom wireless card. If we need to we will do that. It should only take 10 minutes.

Also, just to be sure. I assume you are on a wired connection right now, using Ubuntu. Correct?
Nope. I'm on a desktop while I try to set up Ubuntu. I don't have the extra ethernet cables.
When I left-clicked before, no network showed up. I just got done with a fresh reformat after I screwed up the panels. @_@

Though I can get files on it via USB thumbdrive. Which I did for the firmware.

---

### Post by agim on 2008-02-26
Ok, thats about where my knowledge of that method ends. But as I said, I usually use ndiswrapper when I configure network cards. Thats how I did it on a previous compaq c700.

If you have your wireless driver, this will take 10 minutes.

---

### Post by Grimhound on 2008-02-26
> **agim said:**
> Ok, thats about where my knowledge of that method ends. But as I said, I usually use ndiswrapper when I configure network cards. Thats how I did it on a previous compaq c700.

If you have your wireless driver, this will take 10 minutes.

Where would I get ndiswrapper and the driver?

---

### Post by agim on 2008-02-26
The first place to look would be your driver directory on Windows.

---

### Post by Grimhound on 2008-02-26
> **agim said:**
> The first place to look would be your driver directory on Windows.

I'm not doing a dual boot. My Windows install fuggered (was using XP when Vista was the only thing supported in the first place), and I wiped it out.

Alright. I found the Vista driver, if that will work.

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3466274&prodNameId=3619344&swEnvOID=2093&swLang=8&mode=2&taskId=135&swItem=ob-57604-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3466274&prodNameId=3619344&swEnvOID=2093&swLang=8&mode=2&taskId=135&swItem=ob-57604-1)
What next?

---

### Post by agim on 2008-02-26
Okay, we have a few options here. This is the driver you are looking for:

bcmwl5.inf

I have heard it is also good to have bcmwl5.sys.

Option 1) look for a way to download it to windows. Copy it to a disk, and transfer it to Ubuntu.

2) Find a way to get a wired connection to Ubuntu. Follow these steps

mkdir drivers # This will make a driver directory
cd drivers # this will switch you to that directory

wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)
sudo apt-get install cabextract
cabextract sp33008.exe

sudo modprobe -r bcm43xx
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

sudo aptitude update
sudo aptitude install build-essential
sudo aptitude install linux-headers-2.6.22-14-generic

sudo ln -s /usr/src/linux-2.6.22-14-generic /lib/modules/2.6.22-14-generic/build


# now make a separate directory for ndisrapper
# move into that directory
# download ndiswrapper from [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

make distclean
make
sudo make install

#switch to your driver directory
sudo ndiswrapper -i bcmwl5.inf
sudo modprobe ndiswrapper
iwconfig

sudo gedit /etc/modules
#Add this word to the file that opens
ndiswrapper.

3) If you are a real trusting soul, I have the driver here. If you use IM I can send it to you.

If at all possible, go with step two.

---

### Post by agim on 2008-02-26
Great! You found the driver.

now download ndiswrapper as above (Note: I use version 1.49, which I can confirm works on a c700, but there are newer ones)

then on ubuntu, put your driver in a driver directory, the ndiswrapper in an ndiswrapper directory and follow the tutorial from option two starting from

sudo modprobe ...

should do it

---

### Post by Grimhound on 2008-02-26
> **agim said:**
> Great! You found the driver.

now download ndiswrapper as above (Note: I use version 1.49, which I can confirm works on a c700, but there are newer ones)

then on ubuntu, put your driver in a driver directory, the ndiswrapper in an ndiswrapper directory and follow the tutorial from option two starting from

sudo modprobe ...

should do it

By directory do you mean just put them in their own folders?

I am completely inexperienced with anything but Windows, and even then I never delved into framework.

---

### Post by agim on 2008-02-26
yes, put them into their own folders. To do this from the command line

mkdir driver
cd driver

you have just made a drivers folder with the first command
and enterted it with the second. 

you will need to enter the directories as stated in the tutorial.

what you could do. For clarity's sake, is make a folder on the desktop called ndiswrapper, and put ndiswrapper inside

then put the driver into a folder called driver

From there, when you are in a terminal, you will type cd Desktop/driver to enter the driver directory, for instance

To go back to the home directory, type cd

If you want to learn the terminal later on, which will make things so much easier and is a very powerful tool. Start here

[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

---

### Post by Grimhound on 2008-02-26
> **agim said:**
> yes, put them into their own folders. To do this from the command line

mkdir driver
cd driver

you have just made a drivers folder with the first command
and enterted it with the second. 

you will need to enter the directories as stated in the tutorial.

what you could do. For clarity's sake, is make a folder on the desktop called ndiswrapper, and put ndiswrapper inside

then put the driver into a folder called driver

From there, when you are in a terminal, you will type cd Desktop/driver to enter the driver directory, for instance

To go back to the home directory, type cd

If you want to learn the terminal later on, which will make things so much easier and is a very powerful tool. Start here

[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

This is all just confusing me. I'm not very quick when it comes to computer things.

Where do I get cabextract?

Edit: I've decided this will be a dummy format until I figure out how to do this. Then I'll do a clean wipe when everything is hammered out and make sure nothing ended up fubar'd.

---

### Post by agim on 2008-02-26
Check out the tutorial on the link. It will explain the terminal and directories. Its pretty short, and you only have to focus on whats important to you. Rght now, that would be using the terminal to move around directories and execute commands. After you do that, the rest will be a piece of cake.

to get cabextract, you will type this

sudo apt-get sudo cabextract

in a terminal. Make sure your install cd is in the cd drive when you do this.

If it won't install, then google for something like cabextract .deb
download the .deb file to windows and transfer it to Ubuntu.
I am not sure how to install debs, you will have to google it.

Edit: Checked the unix tutorial. You will only need parts 1 and 2 to continue (and the intro). Its an absolute must read.

---

### Post by Grimhound on 2008-02-26
I connected the laptop to the internet. On it now. Doing your first install list. Having an issue with:

make distclean
make
sudo make install

Results were:

make: *** No rule to make target `distclean'.  Stop.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.


I'm currently in the ndiswrapper directory.

---

### Post by Grimhound on 2008-02-26
Anyone around that can pick up in helping me? @.@

---

### Post by agim on 2008-02-27
Hey, glad to see you're still working on it. Post part of the error code to goole, you'll usually find an answer. Try searching this, for instance:
No rule to make target `distclean'

What is the name of the ndiswrapper file in your ndiswrapper directory? if it ends with .tar.gz or somthing like that, you still need to unzip it and unarchive it.

---

### Post by Chxta on 2008-03-09
I have the same laptop.

Follow the instructions given [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). Worked like a charm...

---

### Post by Chxta on 2008-04-25
Seems to have issues with Hardy. I'm going back to Gutsy...

---

### Post by agim on 2008-04-26
I had issues with hardy as well until I found this.

[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html](http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html)

Hope it helps.

---

