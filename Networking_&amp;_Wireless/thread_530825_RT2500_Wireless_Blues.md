---
title: "RT2500 Wireless Blues"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by Murrquan on 2007-08-20
It seems that [the RT2500 drivers don't work in Feisty]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500"). And the best thing the documentation can offer is "Use ndiswrapper."

Well, that's not always an option, especially when ndiswrapper doesn't cover your drivers (or you just can't find them on your driver CD). Fortunately, one kind soul on the forums came up with [a solution]("http://ubuntuforums.org/showthread.php?t=439952"). About halfway down this page, AirRaven gives instructions for how to port Edgy's rt2500 drivers over to Feisty.

He calls it an "ugly hack," but I have high hopes for it. Unfortunately, so far it hasn't worked. I'm going to post what I did, modified from the original instructions, and see if you can tell me what I did wrong. I haven't been getting responses to these messages, but at least I've been figuring things out better by laying my thoughts out in writing! So, many thanks, even if no one reasponds.

**Step One.** *Download and burn an Edgy CD, and set up the networking as usual.* I did this, and it worked like a charm. Had wireless support right out of the box.

**Step Two.** *Mount Feisty partition.* The instruction AirRaven gave was to use

```
sudo mount /dev/hdb1 /mnt/feisty
```

That didn't work. So I went into admin -> disks, looked up my partition, and used its proper name. I also just put it in /mnt instead of a subdirectory.

**Step Three.** *Open Nautilus with root access from the terminal.* It gave me an error message, but then it loaded it, so I guess that worked.

**Step Four.** *Delete the contents of /etc/network on your hard drive.* Now, **here** is where I may have done something wrong. AirRaven says "Replace the contents of the folder with the contents of /etc/network/interfaces in your LiveCD's file system." Trouble is, there is no such directory -- there's an "interfaces" *file*, but no directory.

Did he mean to delete the file and replace it? Because I deleted the files *and* folders, and replaced it with everything from /etc/network on the LiveCD. After that I replaced /etc/resolv.conf.

Is that why my network's not working right now? Because it recognizes our Essid and everything, but it's not showing up in the icon in the upper-right corner and I'm not able to connect using it. If that's not what I did, then what is?

I'm considering just using Edgy >.< but I'd really like to know what I did wrong. AirRaven insisted that this works. Please help.

---

### Post by Murrquan on 2007-08-21
BUMP in case the edit didn't bump it.

---

### Post by kevdog on 2007-08-21
You are going about it all wrong.  Take a look at it -- it deals with rt73, you need rt2500.  With a little common sense and substituting 2500 where 73 is mentioned, this solution is guaranteed to work for you:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Post back if you need help, although the post is very well worded.

---

### Post by Murrquan on 2007-08-21
Thank you, and many thanks for responding. ^.^ Actually, I did try that, substituting 2500 for 73. On step 13, though, it failed:

```
murrquan@Shadowplane:/usr/src/rt2500-cvs-2007081822/Module$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
murrquan@Shadowplane:/usr/src/rt2500-cvs-2007081822/Module$ sudo ifconfig wlan0
wlan0: error fetching interface information: Device not found
```

I'm not sure what caused that. That's why I'm trying the "ugly hack," which actually seems pretty simple IMO.

---

### Post by kevdog on 2007-08-21
The ugly hack will work, however Im not sure if its a better solution.

The problem you are having is that your interface probably isnt wlan0.  To find out check the following:
lshw -C network

Look for the wireless networking section and then look for logical name.  Its probably eth1, or ra0, but no bets on either.  Substitute what you found for wlan0.

If still in a jam, post
lshw -C network
/etc/iftab
/etc/network/interfaces

Thanks

---

### Post by Austin_KW on 2007-08-21
> **Murrquan said:**
> It seems that [the RT2500 drivers don't work in Feisty]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500"). 

Rubbish,
they work. The network manager does not have support for the drivers but the work perfectly, Otherwise how am I posting this. They don't support WPA2 but who needs it, WPAPSK is fine.

What is you network encryption type?

---

### Post by kwandar on 2007-08-22
> **Austin_KW said:**
> Rubbish,they work. The network manager does not have support for the drivers but the work perfectly, Otherwise how am I posting this. They don't support WPA2 but who needs it, WPAPSK is fine.


I think "work" is a matter of semantics.  I don't have enough experience to "make them work" and they sure as hell don't work out of the box.  I'd be thrilled if I could get my wireless NIC working with RA2500 drivers.  But without ugly hacks, etc (and most anything in linux is ugly for an inexperienced user) they do not work.  Frustrating as hell.

See bug below (and there are at least two other bug reports I'm aware of with conflicting reasons for the problem):

[http://64.233.167.104/search?q=cache...lnk&cd=1&gl=ca](http://64.233.167.104/search?q=cache...lnk&cd=1&gl=ca)

---

### Post by kevdog on 2007-08-22
You are right about not working out of the box, but its not really linux's fault, rather than the card manufactures which dont release a linux driver or source code.

As far as the link you posted, I didnt really help me.

Compilation and installation of serial monkey drivers for ra based chipset/cards is actually straightforward, and is a very good learning tool into how to install things in linux.  Yea its not as easy as Windows, but windows cant do a lot of things that linux can do fairly easy either.  

Again see this link:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
It should be a stick on how to install rtxxxx drivers.

---

### Post by Austin_KW on 2007-08-22
You still have not told us your network encryption/authentication type.  If you give this information we can tell you how to configure your wireless.

The AirRaven instructions are somewhat suspect. 
For example resolve.conf is a file that contains the dns address. It is usually updated by dhcp. What copying a version from a previous version of ubuntu could achieve, well, its beyond me. 
As for copying the default interfaces file form an old version, that is hardly going to configure networking for you individual settings. There may be some argument for copying the ifup/ifdown scripts which appear to behave better in previous versions but I did not need this.

---

### Post by Murrquan on 2007-08-22
It works now!

I burned a Feisty CD and reverse-engineered AirRaven's instructions to put the networking files back, then went back to [the RT73 how-to]("http://ubuntuforums.org/showthread.php?t=400236). Then I did as you said, kevdog, and looked up what I should use instead of wlan0 (it was ra0, sure enough).

It's a little weird not having the network-manager icon up there in the upper-right corner like I always had on Fedora, where I could monitor signal strength and things. But my wireless works now, and for that I am grateful.

Many thanks to kevdog for providing the answer, and everyone else for submitting ideas and possible solutions. You have renewed my faith in the Ubuntu community. ^.^ I'm going to post on the how-to thread with a link to this thread, so they can put in kevdog's clarification.

---

### Post by kevdog on 2007-08-23
Since you have now compiled from source, you are  "veteran".  If you need a wireless icon sitting in the system tray, I would first try rutilt -- the source code is on the exact same webpage as the serial monkey drivers.  You can configure your ra cards through the Gui and it comes with an icon that sits in the system tray.

You need to compile and install from source, however you should be able to do that.  Once you unzip the source package, look for a the INSTALL file and read it.  It will give you basic instructions, although I think the defaults are all as the should be.

The second option is WICD, which is also nice, however I would stick with option #1 for right now.

---

### Post by bigboy_pdb on 2007-08-23
You don't need to compile anything for the rt2500 chipset. I'm using the same driver. I had some trouble figuring out how to get my card running because I needed to learn some commands and how to use them, but outside of this it wasn't a problem. The module for it is already present. If you use "lsmod" in the terminal (Applications -> Accessories -> Terminal) it will be in the list (and you can use "lsmod | grep rt2500" to check if the module is present if you don't want to look through the full list of modules).

I had to set it up using the command line but that wasn't too much of a problem once I knew what programs were needed.
01 ) "iwconfig" shows the interfaces that are available (ra0 is used to interact with your wireless networking device) and it shows their settings
02 ) "iwlist ra0 scan" lets you scan for WAPs (wireless access points)
03 ) "ifconfig ra0 down" causes the driver for the card to be shut down
04 ) "ifconfig ra0 up" causes the interface to be activated
05 ) "iwconfig ra0 essid wap_ssid" sets the SSID of the WAP that is to be connected to
06 ) "iwconfig ra0 channel wap_channel" sets the channel of the WAP that is to be connected to
07 ) "iwconfig ra0 key wap_wep_key" changes the WEP key if one is needed
08 ) "iwconfig --help" will show you all the other information that can be changed using "iwconfig"
09 ) "iwpriv ra0 set AuthMode=WPAPSK" is used to change the encryption to WPAPSK
10 ) "iwpriv ra0 set EncrypType=TKIP" is used to change the type of WPA encryption to TKIP
11 ) "iwpriv ra0 set WPAPSK=wap_wpa_key" is used to set the WPA encryption key
12 ) "dhclient ra0" tells the wireless device to use DHCP
13 ) "ping ip_address" sends packets to the IP address ip_address to show you how good the connection is

**NOTE**: You can the command "man" followed by another command to see the manual for the second command. For example, "man iwlist" show the manual for the command "iwlist". There's also other commands that are related to the command at the end of the manual (hit the END key to go to the end).

I would recommend that you try to connect using the commands that I mentioned from the command line. The following order should work: 03, 04, 01, 02, 05, 06, 07 (for WEP) or {09, 10, & 11} (for WPA), and 12. You can check that there is a connection using 13. You should first check using the IP address of your router (to check that you can connect to it) and then with a web page such as "www.google.ca" (to check that you have an internet connection). Once you've learned how to connect using the command line you can use these commands to connect on startup within the file "/etc/network/interfaces" by using "gksudo gedit /etc/network/interfaces". However, they will be slightly different in this file. I provided an example but you can also use "man interfaces" to find out more information on the "/etc/network/interfaces" file.

I added something similar to the following lines to my file:
```

auto ra0
iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid FAMILY_WIRELESS
        pre-up iwconfig ra0 mode Managed
        pre-up iwconfig ra0 key off
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK=A1B2C3D4E5F678910
        pre-up ifconfig ra0 up

```

The point is that it looks as though you did more than what you needed to do. If a working module is already present then it's a waste of time compile another one. It doesn't hurt to do the things that I mentioned because if you can do them and you write down the steps for what you did then setting up your wireless internet connection will be much easier if you re-install Ubuntu in the future.

---

### Post by imdano on 2007-08-23
The default module isn't very good, and apparently doesn't work for some people.  I don't think it's a waste of time to learn a little about how things work in Linux while also getting an improved driver.

---

### Post by essexman on 2007-08-23
> **kevdog said:**
> You are right about not working out of the box, but its not really linux's fault, rather than the card manufactures which dont release a linux driver or source code.

As far as the link you posted, I didnt really help me.

Compilation and installation of serial monkey drivers for ra based chipset/cards is actually straightforward, and is a very good learning tool into how to install things in linux.  Yea its not as easy as Windows, but windows cant do a lot of things that linux can do fairly easy either.  

Again see this link:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
It should be a stick on how to install rtxxxx drivers.

This is why I stick with Dapper - RT2500 worked out of the box with Hoary Hedghog, badger and dapper.

But ubuntu developers do not accept that there is a bug just because someones hardware stops working with a new ubuntu version. They do not accept two or three people with a problem.

Compilation is easy, but RT2500 should work out of the box.

---

### Post by AirRaven on 2007-08-23
Woah! I wasn't expecting this. >_>

I looked over the instructions I left in that thread, and noticed a rather glaring mistake- the instructions to copy weren't supposed to apply to /etc/network/interfaces, but rather the whole directory. Silly typo there- sorry about that.

If you copy the entirety of /network, it should work perfectly. Although if there's a better solution, like stated in this thread, I'd say that my method shouldn't be used if possible- regardless of whether it works or not, it still requires access to a CD of a previous version of Ubuntu- a waste of a blank CD, in short.
> **Austin_KW said:**
> For example resolve.conf is a file that contains the dns address. It is usually updated by dhcp. What copying a version from a previous version of ubuntu could achieve, well, its beyond me. 
That's just for convenience's sake- if you're on a Static IP, you'll not have the benefit of that. It means things will work straight off, rather than requiring going into Network Config and inputting them yourself. Should help out newbie users.

> **Austin_KW said:**
> As for copying the default interfaces file form an old version, that is hardly going to configure networking for you individual settings. There may be some argument for copying the ifup/ifdown scripts which appear to behave better in previous versions but I did not need this.
Sorry about that- that's just resulting from the typo in my tutorial. Copying the entire /network folder should sort it all.

---

### Post by Austin_KW on 2007-08-23
Airraven,

Re-reading my post, I did not mean to sound quite so harsh. 
I do realise what you were trying to achieve; if you configure networking on a live cd, then the settings will be carried over in the install. Or as you did, you can manually copy the settings to HD from a configured live CD.

My problem is more down to people blindly following howtos that they don't understand, but even then I know we have all done that. 
But they is nothing quite like trying to convince someone following a 20 step howto, that all they need is the configuration in step 20 :)

---

### Post by bigboy_pdb on 2007-08-25
> **imdano said:**
> 
The default module isn't very good, and apparently doesn't work for some people.


I don't think that I had read anything about this when I was trying to get a wireless connection when I first installed Ubuntu. I looked around a little bit and it appears that what you stated is correct (so I might compile a new module myself).

> **imdano said:**
> 
I don't think it's a waste of time to learn a little about how things work in Linux while also getting an improved driver.


I think it's good to learn about those things as well and I'd say that it is good to get the improved driver. However, I think that a person should try to see if his/her default rt2500 module works first and then if he/she wants to then he/she should compile the other module (or if the person had previously compiled the newer module then he/she could use that one). I posted the last paragraph of my first post knowing that someone might come across this thread when attempting to get a wireless connection working (for a rt2500 chipset) and then the person might be overwhelmed by the idea that he/she has to perform so many steps (and that can deter the person from attempting to try anything). Also, if Ubuntu were to be shipped later with an updated module a person might recompile the module with every install thinking it's necessary (even though it wouldn't be).

---

### Post by kevdog on 2007-08-25
I think the rt modules went "buggy" with feisty, and worked better with earlier versions -- edgy and previous.  Someone might want to confirm this statement.

As far as an updated kernel module being included by default - I heard rumors Gusty was supposed to include one -- but I dont believe in the "pre-release" versions as of yet this has happened.  Austin_KW may want to confirm this since he is kind of a "guru" in this area.

---

### Post by videodrome on 2007-08-28
Works fine. RT2500:

iwlist ra0 scan
sudo iwconfig ra0 essid XXX key XXX
sudo dhclient ra0

easy.

---

