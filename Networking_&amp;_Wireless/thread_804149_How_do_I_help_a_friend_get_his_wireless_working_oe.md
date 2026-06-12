---
title: "How do I help a friend get his wireless working oer the phone?"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by nubyrchrd on 2008-05-22
I am ok with Windows computers, but completely unfamiliar with Linux and Ubuntu. Today by phone I helped a friend who is completely inept with computers install Ubuntu into his 3 year old Compaq laptop (his XP was riddled with viruses). He is up and running, but has no wireless, thus no internet. I have examined the Ubuntu documentation somewhat and will try to help him tomorrow morning, but if someone can give me a few pointers re what to try, I would appreciate it very much.

---

### Post by Ayuthia on 2008-05-22
> **nubyrchrd said:**
> I am ok with Windows computers, but completely unfamiliar with Linux and Ubuntu. Today by phone I helped a friend who is completely inept with computers install Ubuntu into his 3 year old Compaq laptop (his XP was riddled with viruses). He is up and running, but has no wireless, thus no internet. I have examined the Ubuntu documentation somewhat and will try to help him tomorrow morning, but if someone can give me a few pointers re what to try, I would appreciate it very much.

One of the things that you need to do is figure out what wireless card he has.  Most likely it is going to be an Intel or Broadcom.  With him not having a connection, I am going to guess it is a Broadcom.  

I am going to give you a few links.  There are two options for Broadcom--b43 driver or NDISwrapper.  Both will need something downloaded in order to make it work.

b43 option:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

NDISwrapper options:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

You will need to first find the Terminal.  Once you get that opened, you will need to type:
```
lspci -nn
```
Look for something called Ethernet controller or Network controller.  It will look something like this:
03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

If it is a Broadcom card, look for the last portion ([14e4:43XX] (rev XX)).  That will tell you what type of card you have.  In the b43 link, there is a section that tells you what cards are known to not work with the b43 driver.  The rest should be able to work.  If his is in the list, he will need to install NDISwrapper.  I would try the b43 route first.  If it does not work, it is easy to blacklist it so that it will not work and then you can use the NDISwrapper install.

The first NDISwrapper link is a decent step by step guide to getting it up and running.  The second link gives more detail.  I prefer the second guide more, but the first guide should work pretty well because it is using an HP driver which should work for Compaq.

Hopefully this helps.

You might also want to check this link out and get the pdf:
[http://ubuntuforums.org/showthread.php?t=793553](http://ubuntuforums.org/showthread.php?t=793553)

It has a lot of good information for HP laptops which will most likely work for Compaq too.

Good luck!

---

### Post by nubyrchrd on 2008-05-23
Hi and thanks for your reply. It appears his chipset will be ok.  I do have a question before starting to work. In your post, you say the following:

For those without a working internet connection
If you have a Hardy install CD, insert your CD and do the following:
Code:

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install b43-fwcutter

You then go on to address those without an internet connection who do not have a Hardy install cd. I am not clear where those instructions leave off and the instructions for those with the cd, of which my friend is one, pick up. I.e. I am unclear how to proceed after the above code.

Thanks.

---

### Post by nicedude on 2008-05-23
What he was trying to say if I understand correctly is that if your friend has a hardy cd on his possession he can use it and run the following commands which I will explain what each is now for you.

sudo apt-cdrom add # adds the cd rom to the list of places Ubuntu will install stuff from
sudo aptitude update # updates the known software available from sources so that the first  command will take effect
sudo aptitude install b43-fwcutter # installs b43-fwcutter which is a driver for broadcom wireless chipsets

So at that point after you get the b43 cutter driver installed you need to follow the instructions at the first link he gave to get it working please pay attention and read those directions carefully for best chance of success, although apparently after the driver package is installed it asks if it should download the newest driver and you will be unable to do this so if the driver that comes with the package doesn't work than I don't know if it will work for you without a connection to obtain things from, so please just read the guide that link points to.
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

The other rooute so to speak to possibly get his wifi working would be to use Ndiswrapper in conjunction with a windows XP driver for his wifi chipset. Ndiswrapper is just a software that allows the use of a windows driver while using linux to control a wifi device. I would try to see if the first method works before using the Ndis one. The Ndiswrapper method is outlined in his second & third links so if you end up having to use that method I suggest you readup again to figure out what to do. I realize it is difficult to accomplish these things but at least you will only have to learn this once and it should work correctly once set up.

I have no broadcom cards so I am unfamiliar with its setup or I would help you more but the guides listed by the member above will no doubt serve you much better than I could. Good luck with this and I hope this info is of help to you.

PS if for any reason Ubuntu is not as fast on your friends machine than he might like you could also look at Xubuntu which is Ubuntu with a different desktop manager than Gnome called XFCE4 which requires much less resources to run than Gnome does and therefore is quite a bit faster. I just mention this since you said his laptop is older and I wanted to point Xubuntu out just in case he finds the Gnome desktop sluggish. Hope that helps as well, good looking out by the way to take care of your friend like this :-)

nicedude

---

### Post by nubyrchrd on 2008-05-23
Hi and thanks for your reply. I am trying to determine where to go after I install the driver package with the three commands cited - his instructions divert for those who have no connection and no Hardy disc. My friend has the disc, so after he installs the package by executing those three commands, I am unclear as to where to pick up the instructions in that post.

---

### Post by nicedude on 2008-05-23
First when you install the b43 cutter package head this line from the above mentioned guide

Make sure that you say no or cancel when the installer asks you to find/download the firmware for you. It will get stuck because it is thinking that there is an internet connection.

oops I am sorry as I now see that an internet connection will be required at some point to get some files needed ( I am sorry I didn't read the whole thing myself I just saw "for those without an internet connection" and thought that it was possible to complete this without one, my bad. If you live near your friend you could down load the things it recommends you need and then visit him to complete this or if this is a long distance friend then he would need to go somewhere ( friends, Internet cafe etc ) and download the things he will need. I don't think that was written the best it could be in that guide but hey we are all just trying to help and for zero pay :-)

** Here are the things from that guide that it says you will need to finish the job

Both 32-bit and 64-bit:
You will still need to find someplace with a working internet connection and download the following files:
Code:

[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

** Then do this with them

Copy those files to your home directory. In the Terminal/Konsole/xterm window do the following:
Code:

cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up

** He lists this as a final note

For those of you who are configuring your /etc/network/interfaces, you might need to do:
Code:

sudo /etc/init.d/networking restart

That will restarting your network and will read through the /etc/networking/interfaces to connect.

That should be it!

-------------------------------------------------------------

Sorry again that I misled you somewhat as I said I have no experience with this wifi card family or its drivers. I hope you can find a way for your friend to obtain the things he needs and if I could beam them to him like star trek I most surely would :-)

PS Does he not have an ethernet internet connection and just lives somewhere where there is public wifi or something I just was curious. If he is say at college somewhere then he should be able to get the access he needs to download those two files easily. 

Hope you sort this all out and hook your buddy up. And please post your final outcome as I am now curious.

nicedude

---

### Post by Ayuthia on 2008-05-23
What nicedude said is correct (thanks!).  I still have to revise the thread.  Apparently you should not proofread a document late at night...

---

### Post by nubyrchrd on 2008-05-23
Well, first of all, thanks again to both of you, but I have to say that after months of curiosity, this experience has made one thing  crystal clear: Ubuntu is nowhere near what the hype is trying to sell it as. I was surprised that a 3 year old mainstream computer could give it so much trouble re the wireless, but when I tried to follow your instructions and found that it could not "mount" the cd rom, that was the final straw.  It's back to windows, albeit with a good virus scanner, for my friend.

---

### Post by nicedude on 2008-05-26
Sad to hear it, sorry but wifi isn't that hard it just isn't click click dummyfied like Microsoft is as the Hardware manufacturers don't give you installers for Ubuntu or any Linux. If they didn't give you those installers for Windows it wouldn't be easy either ( Try building a Windows driver from source code LOL ). So with Linux there isn't always a click click fix, so you instead learn something and in the end you will end up with knowledge of more than how to just click a mouse :-)

---

