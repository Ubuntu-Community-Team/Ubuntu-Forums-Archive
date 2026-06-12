---
title: "See wireless network, but cannot connect"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by YML on 2007-04-20
Hey everyone,

I have a problem with my ubuntu 7.04 and sitecom wireless usb dongle wl 113 v1 002. Ubuntu shows me my wireless network (WEP) and asks for a password. When I enter the password however it does not connect (and yeah: its the correct password ;) ) Any ideas on how to fix it would be greatly appreciated! :)

---

### Post by xhentil on 2007-04-20
I'll bump this.

I'm having a similar problem with my Dell Truemobile 1390 (Broadcom 4311) internal wireless. Thanks to the bcm43xx-fwcutter  I can see networks, with signal strength. However, my schools network has a WPA key. Network-manager asks for the key, i give it, but i never connects.

Wicd doesn't work either.

I have no open wireless connections to test either.

---

### Post by chimpus on 2007-04-20
Not a bump lol, but having the same problem as above, wireless can see my home network but asks for password once then just returns to wired network after not accepting the correct password. I don't want to open up my network just yet so any help would be appreciated.

p.s. I have just wiped my vista install 1 hour ago for feisty and not ready to go back yet ;) .

---

### Post by Yoeri on 2007-04-20
Same here, seeing the network, cannot connect. Turned off all the security, still no wireless network :( 

I was glad to see the ZD1211 drivers included ... if they could only work now ...

---

### Post by reauthor on 2007-04-20
Welcome to the club...same problem...Everything seems OK but just wont to connect...

---

### Post by chimpus on 2007-04-20
Update: I opened up my home network and still no joy! 

What i did notice is that when it was open one of the "connecting balls" was green, when locked down and asking me for the passphrase none are green while however connecting wired both are green - does that make sense??

---

### Post by chimpus on 2007-04-20
now time for a bump

---

### Post by Mituness on 2007-04-20
I'm having this issue too. I can see my wireless network and when I try to connect (WEP Encryption) and enter the password, I get no error message, but hovering the cursor over NetworkManager gives me the message 'Wireless network connection to (my network name) 0%'. Of course, it isn't actually connected at all.

Any help would be much appreciated! I've just returned to Ubuntu after a couple of years, and didn't even have this much trouble back then with my old wireless card! ;) I'm really enjoying  Feisty so far, though this is proving to be rather problematic now! :(

---

### Post by bootslap on 2007-04-21
Hey ... looks like a lot of guys are having similar problems. When I installed 7.04, I was happy that the installation went without  a hitch, and definitely it has many features that lacked in 6.10. I am happy that I installed 7.04 ..... But this is a problem ... It identifies all the wireless networks but fails to log on to my home network even though I am giving the right passphrase... kind of weird, but I'm sure there is somebody out there with the same problem who worked it around... and maybe they can offer some help...Thanks guys and keep the hope alive...

---

### Post by Yoeri on 2007-04-21
Little breakthrough ... when issueing **sudo iwlist scan**, I noticed that my wireless ad-hoc network is at channel 1 while networkmanager uses channel 6 by default. This is probably the cause of my laptop not being able to connect to the network.

BUT when trying to change the channel, I get an error saying that I cannot change it.
"**sudo iwconfig eth1 channel 1**" How can I change the channel?
Do I have to stop the networkmanager in order to do so?

---

### Post by xhentil on 2007-04-21
I was poking around a bit more today. I found that when i blacklisted **bcm43xx**, I lost all interfaces and wireless connectability completely (On my Dell Latitude, no wireless light). Trying to use **ndiswrapper** and its GUI, I forget what it's called, it says that the proper **bcmwl5** driver (from Dell) is installed, but in the GUI it says no hardware found. So, there is a disconnect between hardware and proper drivers... that's all I've got. I'll try some more tomorrow.

---

### Post by pertti on 2007-04-21
I was having that problem (Feisty asking for the WEP password every few seconds, but not connecting at all) last night, after upgrading. But I solved them following the instructions on this thread: [http://ubuntuforums.org/showthread.php?t=399913]("http://ubuntuforums.org/showthread.php?t=399913"). I had to blacklist bcm43xx and install the window drivers through ndiswrapper (just like with Edgy, as far as I remember). The guide is for a Dell 6400/E1505 laptop with a Dell 1390 (Broadcom 4311) wifi card, but it might be useful.

---

### Post by Echo35 on 2007-04-21
Same issue with my WUSB54G. Worked fine before the update. What's going on? I know for a fact I had to compile the Linux driver for the specific kernel, which is different now, but it won't compile. Is this an issue with the Kernel or something?

---

### Post by lakrids404 on 2007-04-21
Hi 

It seems that i do have the same problem. I can see the network but I can not connect. The network I use does not use any form of encryption. 
I am using Ubuntu 7,04 and the wireless connection is Asus wl-167g

---

### Post by shalashazka on 2007-04-21
Good thing I'm not alone in this, someone's bound to fix it eventually.

(same problem here)

---

### Post by shalashazka on 2007-04-21
> **Yoeri said:**
> Little breakthrough ... when issueing **sudo iwlist scan**, I noticed that my wireless ad-hoc network is at channel 1 while networkmanager uses channel 6 by default. This is probably the cause of my laptop not being able to connect to the network.

BUT when trying to change the channel, I get an error saying that I cannot change it.
"**sudo iwconfig eth1 channel 1**" How can I change the channel?
Do I have to stop the networkmanager in order to do so?

(doublepost, sorry)

I looked and it's the same for me. This is [apparently] part of the problem.

Except that I have near zer0 knowledge of how to fix things. So we have to get someone smart to do it. Could someone smart come save us, please?

---

### Post by prilesje18 on 2007-04-21
Same problem here. I can see the network but am not able to connect. Network manager attempts to join network but eventually fails. When I enter the iwlist command it sees my home network and says its on the channel 11.
Please someone help us :-)

---

### Post by Mituness on 2007-04-21
> **Mituness said:**
> I'm having this issue too. I can see my wireless network and when I try to connect (WEP Encryption) and enter the password, I get no error message, but hovering the cursor over NetworkManager gives me the message 'Wireless network connection to (my network name) 0%'. Of course, it isn't actually connected at all.

Any help would be much appreciated! I've just returned to Ubuntu after a couple of years, and didn't even have this much trouble back then with my old wireless card! ;) I'm really enjoying  Feisty so far, though this is proving to be rather problematic now! :(

I've now managed to get my problem working thanks to [this guide]("http://ubuntuforums.org/showthread.php?t=400236")  about RT73 wireless cards. :D I hadn't even realised I had this card to be honest, my new laptop's system software CD came with drivers for some Intel wireless card, which had confused me!

---

### Post by endoscopy on 2007-04-21
I m having the same problem with Ubuntu 7.04.  I earlier tried Kubuntu 7.04 and the wireless worked fine???

I went to Ubuntu because of different problems with Kubuntu.  I noticed that the gui for Kubuntu wireless is different for some reason.  Maybe Gnome vs KDE??

---

### Post by Ichijin on 2007-04-21
same problem...but this is the first time installing ubuntu, using feisty and my wireless mini pci card is Cisco MPI350

---

### Post by Rusna on 2007-04-21
Almost same problem here.
The only difference is that sometimes, occasionally NetWorkManager connects to a wireless connection, but I have to try many, many times and sometimes it just won't connect at all.
I have bcm4318 adapter and using native Linux drivers through fwcutter.

Solutions are welcome....

---

### Post by cody50 on 2007-04-21
I am having the problem of seeing but not being able to connect as well. I am using a WG111 v2 adapter. However, I took my adapter and used it on two different access points one at where I work and one at my School, and they both connected fine (one with wep one unsecured). This leads me to believe that it is purely a router setup issue with my home network (and the wg111v2). It will connect to my home network every once in a bluemoon, almost as if on a whim.  Perhaps that will offer some insight. another note, All my testing was done from live CD.

I hope we can figure this out because this is the only thing keeping me from loading feisty up for my family!

---

### Post by xhentil on 2007-04-21
> **pertti said:**
> I was having that problem (Feisty asking for the WEP password every few seconds, but not connecting at all) last night, after upgrading. But I solved them following the instructions on this thread: [http://ubuntuforums.org/showthread.php?t=399913]("http://ubuntuforums.org/showthread.php?t=399913"). I had to blacklist bcm43xx and install the window drivers through ndiswrapper (just like with Edgy, as far as I remember). The guide is for a Dell 6400/E1505 laptop with a Dell 1390 (Broadcom 4311) wifi card, but it might be useful.

I went through this howto (I do have Dell 1390), except is updated to the **ndiswrapper 1.42** build, which is the latest. Strange thing is, i still had **bcm43xx** blacklisted, and when I booted things up today, the wireless light was on, although there were no interfaces. The plus side is, that howto DID get the interfaces to read and show up. But I'm back to the same problem: Try to connect to the WPA with the proper key and it tries.. tries.. then kicks me back to the wired. I haven't been able to test a non-WPA connection.

I honestly don't expect it to work anymore. I'm probably going to see if I can go by the store today and pick up a PCMCIA card that supports linux/has a supported chipset like Atheros.

---

### Post by psyke83 on 2007-04-27
Hi everyone,

There's a bug in the softmac-based (zd1211rw and bcm43xx) drivers that prevents successful associations, see here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103768](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103768)

Try the workaround posted by Tim Gardner and see if it helps.

---

### Post by SwaroopKunduru on 2007-04-27
> **YML said:**
> Hey everyone,

I have a problem with my ubuntu 7.04 and sitecom wireless usb dongle wl 113 v1 002. Ubuntu shows me my wireless network (WEP) and asks for a password. When I enter the password however it does not connect (and yeah: its the correct password ;) ) Any ideas on how to fix it would be greatly appreciated! :)

I cannot see wireless Icon in network manager. What steps I have to follow inorder to see wireless icon.

Regards,

Swaroop Kunduru.

---

### Post by marcelop on 2007-04-27
+1 having these problems.

Here's the post where I've described the symptoms - and also ranted about it ;-) 
[http://ubuntuforums.org/showthread.php?t=419915](http://ubuntuforums.org/showthread.php?t=419915)

---

### Post by Reducer on 2007-04-27
Another one here having the problem.  ipw3945, connects fine in OpenSuse, Vista, and all betas of Feisty.  My WAP is on channel 10.

---

### Post by osxdude on 2007-04-27
I have a Linksys WUSB54G (ver. 4) that I use always. I cannot connect to my home wireless network with it in Lunix. It appears to have 0% signal, even though it appears in the list. I am using WEP ecryption (with numbers!).

Yes, I have the same problem.

---

### Post by Yoeri on 2007-04-28
Thanks for all the advice but I am sick of it and just reinstalled and reconfigured Edgy ... a bit more configuration work to recompile with the zydas drivers but definitely worth it ... I won't try Feisty again before I know a good solution to the wireless problems ...

---

### Post by nagilum on 2007-04-28
I ran into the same problem with my laptop's bcm4309 wireless card, with Edgy the wireless worked flawlessly with ndiswrapper. Got it working once (don't ask me how, just installed the Dell driver again and I could connect for a short while) but it did not survive a reboot.

With the wpa_supplicant in debug mode it could associate with the AP and complete the 4way handshake, the status changed to "connected". Yet it wouldn't send / receive any packets and was unable to receive an IP via DHCP. The debug output reported lots of dropped packages due to some counter not increasing (sorry for the sloppy description, I did not save the output).

Anyway, I just downgraded the kernel back to 2.6.17 from Edgy, as well as the wpasupplicant and ndiswrapper-utils package (to 1.8 ). I did not yet test which packages actually need to be downgraded, but afterwards wireless worked again without any problems just like before.

To downgrade add a source to /etc/apt/sources.list for Edgy's main:
```

deb http://de.archive.ubuntu.com/ubuntu edgy main

```

and install linux-image-2.6.17-10-generic (or whichever flavour you like), ndiswrapper-utils-1.8 and wpasupplicant 0.5.4-5 with:
```

apt-get install linux-image-generic=2.6.17-10 wpasupplicant=0.5.4-5 ndiswrapper-utils-1.8

```

Upgrades to these packages can be prevented by pinning them to the version numbers above, add the following lines to /etc/apt/preferences:
```

Package: linux-image-generic
Pin: version 2.6.17*
Pin-Priority: 1001

Package: wpasupplicant
Pin: version 0.5.4*
Pin-Priority: 1001

```

Note the pinning for the kernel only ensures the latest kernel is always installed for the 2.6.17 tree, not 2.6.20 which is distributed with Feisty. After a reboot with the new kernel it should work again.

---

### Post by chocolatedude91 on 2007-05-05
I'm having the same problem as the other 30 above me.  Did anyone find a fix?

Thanks.

---

### Post by Reducer on 2007-05-05
I think I read in a different thread that the first kernel update for Feisty would have fixes for this and a host of other problems.

---

### Post by CyberAlyMan on 2007-05-05
Yeah, same problem. I have no WEP key on my network, and I can see it on the menu, but it's no go joe. If you turn off roaming mode and go back to how it used to be in Edgy, it's still no go.

It's a real shame coz everything else in Feisty beats every other Linux distro. I'm stuck using Mandriva right now, which isn't half bad but it's not open enough and installing things is much cooler in Ubuntu.

---

### Post by Daveski on 2007-05-05
I have the described problem on my machine with Feisty with all 3 of my Wifi cards:

PCCard Belkin F5D7010 ver 6 uk
PCCard LinkSys WPC11 ver 4
USB Belkin F5D7050

The modules load and the cards are identified (although I do have to remove a blacklisted module for the LinkSys). However I often see both wlan0 and wmaster0 listed at the same time.

The Network Manager sometimes allows me to see networks (mine does not broadcast an SSID) but the strength is often 0%.

With or without 'Roaming' I am unable to connect to my WEP 128 network. If I mess around with 'manual config' in Network Manager I usually end up with the card disappearing - if I try to up the card from the command line (ifconfig wlan0 up) I sometime see

SIOCSIFFLAGS: Input/output error

I know this is not very specific with 'sometimes' and 'often' but it is difficult to be specific as behaviour does not seem consistent. All cards work, and I have had both the Belkins working in Edgy by downloading native drivers / firmware and editing config files.

Having seen the live CD of Feisty on many machines and laptops with great success in Wireless networking, I KNOW the Network Manager does work on many machines - why not mine?

---

### Post by Dorsai on 2007-05-05
I had the very same problem, my PC could see the network but it would not accept my wireless key. First step is to turn off your encryption and see if you can connect. I could but obviously I did not want to leave my network exposed so I kept playing and came up with what I posted in the thread below. To me it seemed there were far too many adapters listed in the "interfaces" file so I removed all but the ones I list in the how to below. Possibly you folks can modify this to suit your needs regarding encryption.

[http://ubuntuforums.org/showthread.php?t=426598](http://ubuntuforums.org/showthread.php?t=426598)

---

### Post by Sweet Mercury on 2007-05-05
I'm having a similar problem.

I don't have a wireless "card," WiFi is built into my Dell laptop.  If I go to Network Settings, it shows "Wireless" as an option, it just won't connect to my home network.

It connects fine if I run an Ethernet cable from the router, though.

---

### Post by Sweet Mercury on 2007-05-06
> **Reducer said:**
> I think I read in a different thread that the first kernel update for Feisty would have fixes for this and a host of other problems.

And now I display my complete lack of knowledge on how Linux works: are the kernel updates the ones that come out every six months? Or are there smaller updates in between major releases?

---

### Post by pertti on 2007-05-06
> **Sweet Mercury said:**
> And now I display my complete lack of knowledge on how Linux works: are the kernel updates the ones that come out every six months? Or are there smaller updates in between major releases?

The Ubuntu policy is that once a Ubuntu version is released (one is released every six months, the las one is 7.04, Feisty Fawn) it only gets security and bug fixing updates. This updates may come for every part of the system, not just the kernel (which is the core of the system). So your current version of Ubuntu will only get this kind of updates for the following months. When the next version is released it will come with bigger updates in every aspect, and you can choose to upgrade to that version or stick with your current one (which will still have small updates for about one more year).

This is the case with Ubuntu. New versions of the kernel and other programs come out frequently, and it's on the distributions hands (be it Ubuntu, Debian, Fedora, or whatever) to decide which version to push on the distro and when.

Hope this cleared it up a bit for you.

---

### Post by matc on 2007-05-06
Same Problem here with Intersil PRISM 3886 Mini PCI.

Already tried the downgrade of kernel, wpa_supplicant, network-manager and dbus. Did not help.

Since I occasionally  use my laptop in hotel/foreign environments this is starting to p*** me off....

---

### Post by Sweet Mercury on 2007-05-06
> **pertti said:**
> The Ubuntu policy is that once a Ubuntu version is released (one is released every six months, the las one is 7.04, Feisty Fawn) it only gets security and bug fixing updates. This updates may come for every part of the system, not just the kernel (which is the core of the system). So your current version of Ubuntu will only get this kind of updates for the following months. When the next version is released it will come with bigger updates in every aspect, and you can choose to upgrade to that version or stick with your current one (which will still have small updates for about one more year).

This is the case with Ubuntu. New versions of the kernel and other programs come out frequently, and it's on the distributions hands (be it Ubuntu, Debian, Fedora, or whatever) to decide which version to push on the distro and when.

Hope this cleared it up a bit for you.

Yeah, I think I understand it better now. I just downloaded Feisty Fawn on a whim (and because I want an OS that will continue to be supported, unlike XP).

So, the next bug update will likely take care of this wireless issue that a lot of people seem to be having?

---

### Post by ericdegen on 2007-05-07
Same symptoms here on an HP 8430 / intel 3945 when trying to connect with WEP. I can use wired in my office, but I'm hoping for a fix before I need to go on the road in a couple of weeks.

---

### Post by Yoeri on 2007-05-07
Went back to Edgy :(  ... I'll reinstall Feisty when there is a bug-fix available

---

### Post by joebox on 2007-05-07
Same problem here. :( I have a D-link PCI  card (forget which model, but it's an atheros chipset) as well as an RTL8187 chipset onboard wifi (from Asus P5B mobo). I got the RTL8187 to work in Edgy a while back using  NDISWrapper, but it stopped working after I added a WEP key to the network. I bought the D-link because I  heard the atheros cards work "out of the box" in Edgy. It did, but promptly stopped after I re-installed with Feisty. 

Amazingly, Feisty sees both cards right away, and I can configure them, but I never receive an IP address from the router: it's always 169.192.whatever. I tried a number of things suggested on the forums, like re-installing  mad-wifi from a fresh compile, et al, but it's the same issue every time.

I really like Feisty, and I loathe to go back to Edgy, but a computer without internet access is useless in this day and age. I'll be using  EE until I know the wifi problems in FF have been fixed. Hopefully I won't have to wait for Gnasty Gnu for that  to happen. :) Best of luck to every one  working  on a fix for this problem. :)

---

### Post by sdswingr on 2007-05-07
I am still running v.6.10 and am also having the same problem. I can connect to unsecured wireless but when putting in a password nothing happens...so I guess v.7.10 didn't fix this problem?

---

### Post by Yoeri on 2007-05-08
I don't have the problem on 6.10 since I am not using Network Manager there. I do have to manually install the device drivers on 6.10 since they are not included in the kernel ...

Still hoping for a fast solution so I can make the switch ...

---

### Post by ishift on 2007-05-08
i have the same problem with my bcm4306 on feisty. i don't understand. it worked quite well on edgy. oh well, until this problem is fixed on feisty, i'll just go back to edgy.

*subscribes to thread*

---

### Post by darwin_te on 2007-05-27
Kubuntu 7.04 (Feisty)
ASUS G1

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

WEP 104-bit (128-bit) setting connecting to Windows AP:

/etc/network/interfaces:

########################
#home - wifi
########################

auto eth1
iface eth1 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid youressidhere

# passphrase is test
# see [http://www.powerdog.com/wepkey.cgi](http://www.powerdog.com/wepkey.cgi) (Passphrase To Hexadecimal WEP Keys)
wireless-key1 9FDF3BFDFB10AFEB0925EF9605

wireless-defaultkey 1
wireless-keymode open

command line to bring wireless network up:

>ifup eth1

---

### Post by cetol on 2007-05-27
I had the same issue. I disables MAC address filtering on my router then rebooted and it connected right up. Only a little annoyance now is that I had to create a key ring password and every time I start it asks for the pw before it will connect.

Dell Inspiron 8600 with the broadcom internal wireless

---

### Post by Daveski on 2007-05-27
> **cetol said:**
> I had the same issue. I disables MAC address filtering on my router then rebooted and it connected right up. Only a little annoyance now is that I had to create a key ring password and every time I start it asks for the pw before it will connect.

Ah well, at least it is not just Ubuntu that suffers from these sorts of problems:

[http://www.theregister.co.uk/2007/05/25/vista_upgrade_revisited/page2.html](http://www.theregister.co.uk/2007/05/25/vista_upgrade_revisited/page2.html)

---

### Post by bgissal on 2007-05-27
I installed a wireless chip yesterday, and have been having the same problem until I grabbed a terminal and entered:

sudo iwconfig wlan0 essid asdf 

I have an unsecured wireless network for the time being. This seemed to do the trick.

However, I have another problem.

Everytime I want to connect to the network, I have to enter the commands:

sudo modprobe ndiswrapper 
sudo iwconfig wlan0 essid asdf

Does anyone know how to get these to run at startup?????

---

### Post by hoboken on 2007-05-27
I HAD (;)) the same problem. My network password was a phrase, and I was trying to enter it as a 128 bit passphrase (made sense...) It turns out I had to enter it as a 64 bit ASCII password. So before installing NDISwrapper and such:

TRY ALL PASSWORD TYPES!!!!

---

### Post by maarten80 on 2007-06-16
same problem here, can see al the networks but can not connect!

using wifi-radar in xubuntu (works better than the network-manager-gnome package which would nog load the network applet)

---

### Post by never been to spain on 2007-07-04
Same problem...

Wifi Radar helps, but it has problems. I sometimes have to hit the "connect button" three or four times, but it will connect.

---

### Post by Yoeri on 2007-07-04
My problems are solved. I removed the standard Feisty driver and installed ndiswrapper with windows-drivers instead. NM works like a charm ...

---

### Post by #Reistlehr- on 2007-07-04
hey i didnt rad the whole thread, but just tossing an idea out there for those who didnt fix it.. check to see if you have mac filtering turned on.

---

### Post by dgermann on 2007-07-04
#Reistlehr- and Yoeri--

How did you do what you did?

1. How do you turn off and on the mac filtering?

2. How do you remove the standard Feisty driver?

I have a System76 laptop, just got it last week, Ubuntu 7.04 and whatever network cards come with it. I cannot connect via either wired or wireless, but it can see the network.

Actually, wired it says I am connected, but can only ping one other machine on the network. Wireless it does not connect at all.

:- Doug.

---

### Post by #Reistlehr- on 2007-07-04
for the mac filtering, and wireless security, you need to go into the router. so you are going to have to read the router documentation. 

when you are connected via wired, type the command, ifconfig, then look for the default gateway, and see if you can ping it.

---

### Post by fallingcow on 2007-07-04
"Me too".

I noticed that wireless broke when I upgraded, but I figured that it was because I'd messed with my Edgy system quite a bit, so the upgrade just didn't go as smoothly as it should have.  It was the only thing that broke.

Wireless wasn't that important, so I put off wiping and reinstalling until yesterday, when I discovered that it wasn't the upgrade process that broke it--it's just Feisty.

NM picks up the netwoks in my area (most of the time...  sometimes, it picks up maybe one or two of the 4 within range, but not the others, just a few minutes after it was getting all of them so I know they're all on) but shows my router, in the same room, as being at 30-50% signal strength, which is only marginally better than the ones that are presumably in some other house entirely.  Windows on another laptop shows it at full strength when it's on another level of our house, so the router's fine.  From time to time, my router doesn't even show up (!?).

I've got the router totally open.  I double-checked the MAC filtering as suggested, though I doubted that it would be on by default, and it wasn't.  I've tried several channels, including 6, but neither my signal strength nor my connectivity were affected in any way, and anyway  it really can't be an interference problem since Windows can connect just fine.

NM just spins when I try it, for maybe 3-4 minutes, then stops and goes back to "not connected".  I have managed, ONE time, to get a connection for maybe 30 seconds, by telling NM to connect and then running dhclient on wlan0 a few seconds later as root.

I'll try going back to Edgy, I guess.

For the record, this is a USR PCMCIA card, ACX 111, which worked *perfectly* with no tweaking whatsoever in Edgy.

Also, re-selecting the network while it's trying to connect, which was mentioned as a workaround in one of the pages linked on this thread, does not help.

---

### Post by zigarth on 2007-07-04
Ah yes... I also have a similar problem. I can see the unsecure wireless network in the drop down menu, but I can't connect to it. I can connect to it through windows, and I can connect to it by wire. When I actually click on it, it fails to connect. 
Any suggestions?

---

### Post by dgermann on 2007-07-04
#Reistlehr-:

Thanks for the quick response.

OK, NM reports that it has a wired connection, but I can only ping the server and no other machines on the network, nor can I get a browser connection. I ran ifconfig as you suggested and voila! there is a new listing, eth1:avah. What is that??

Anyway, it shows an inet addr:169.254.9.239; neither eth1 nor eth2 show an inet addr. I don't know what that address is; certainly is not local, nor is it my ipaddress.

So I pinged that, and it worked. But cannot ping google.com nor yahoo.com.

What is the way to remove the feisty driver?

I will try the mac filtering and report back.

Oh, I had thought it was perhaps the system76 drivers I installed, or the firestarter. I checked firestarter and it says it is disabled. I might also try uninstallying the system76 drivers--

---

### Post by #Reistlehr- on 2007-07-04
just so you know, ANY ip addresses starting with 169 are considered APIPA.. (Automatic Private IP Address).. It means that the OS cannot get a respsonse from the DHCP server, which, means it cannot get an IP, so it makes on up. 

i've read around that the system76 drivers have been causing some people problems liike this, so it's always a possibility to trouble shoot.

---

### Post by dgermann on 2007-07-04
#Reistlehr-:

OK, I checked MAC address filtering, and the website for my router, a netgear WNR854T, says this is an alias for Access Control List. That, on this router, is a place where you can enter MAC addresses for specific machines that are allowed in the door. Is that what you were referring to?

In any case, I had filled in the ipaddresses I got from ifconfig, but then switched this option off before my latest tests.

Does this make any difference? I have dhcp enabled from the router out to the internet, but inside the network is all static ip addresses (exept for this machine). I do not know how this machine is able to get an ipaddress assigned, since I do not have the router set up as a dispenser of such ipaddresses, and I do not think I have set up anything on the server (a redhat 9.0 box).

---

### Post by dgermann on 2007-07-04
#Reistlehr-:

Thanks. Did not know that about 169 addresses. Good to know. Thanks.

I will also post on the private system76 site for help.

Anybody else have any solutions that worked for them?

---

### Post by nbussiere on 2007-07-11
Hi,

I just installed 7.04 and have the same problem. I have a wireless card bcm43xx, so I had a lot of other troubles, but I succeeded in the previous version to make my wireless adapter to function.

But in this version of Ubuntu? Nothing, either with ndiswrapper or the native 43xx drivers (in the lasts version, I was using the native drivers). So I think the 7.04 has a bug. Remember : my configuration worked well until I installed 7.04.

What is my turn around? I am not pretty sure exactly, but I decided to turn off security (WEP) on my router, diffuse the ESSID (I was not) and turn off the MAC filtering. With all the security off, my wireless adapter works well. 

I will some more tests, but this is at least a good start.

Have fun !:guitar:

UPDATE : MAC Filtering is doing the troubles.

---

### Post by mbeierl on 2007-07-11
Joining the me too crowd.

Over many combinations of Ubuntu (Dapper, Edgy, Fiesty) and different laptops/wireless cards (latest: Intel PRO 3945ABG) I have had the same problem:

nm-applet can reliably connect to WEP network at work, but my unsecured home network is more often than not  left spinning, and never connecting.

I **can** connect to unsecured network if I use manual config/dhcp.  Here's the output I see in /var/log/daemon.log.  Note the section in bold about drop unencrypted.  Anyone have any ideas as to why it would want to do that when I am specifically asking it to connect to an unencrypted network?
```

Jul 11 22:29:50 ottws58 NetworkManager: <debug info>^I[1184207390.486947] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'Ashton Station' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/eth1 / Ashton Station 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^IDeactivating device eth1. 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^IDevice eth1 activation scheduled... 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^IActivation (eth1) started... 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^IActivation (eth1/wireless): access point 'Ashton Station' is unencrypted, no key needed. 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^ISUP: response was 'OK' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^ISUP: response was 'OK' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^ISUP: response was '0' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 417368746f6e2053746174696f6e' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^ISUP: response was 'OK' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^ISUP: response was 'OK' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^ISUP: response was 'OK' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Global control interface '/var/run/wpa_supplicant-global' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): RX global ctrl_iface - hexdump_ascii(len=49): 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74   INTERFACE_ADD et 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868):      68 31 09 09 77 65 78 74 09 2f 76 61 72 2f 72 75   h1__wext_/var/ru 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868):      6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e 74   n/wpa_supplicant 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868):      09                                                _                
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Initializing interface 'eth1' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wp
a_supplicant' bridge 'N/A' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Initializing interface (2) 'eth1' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): EAPOL: SUPP_PAE entering state DISCONNECTED 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): EAPOL: SUPP_BE entering state INITIALIZE 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): EAP: EAP entering state DISABLED 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): EAPOL: External notification - portEnabled=0 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): EAPOL: External notification - portValid=0 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): SIOCGIWRANGE: WE(compiled)=22 WE(source)=16 enc_capa=0xf 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868):   capabilities: key_mgmt 0xf enc 0xf 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): WEXT: Operstate: linkmode=1, operstate=5 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): d 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): wpa_driver_wext_set_wpa 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): wpa_driver_wext_set_countermeasures 
**Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): wpa_driver_wext_set_drop_unencrypted **
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Setting scan request: 0 sec 100000 usec 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Added interface eth1 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Wireless event: cmd=0x8b06 len=8 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): RX ctrl_iface - hexdump_ascii(len=9): 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1        
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): RX ctrl_iface - hexdump_ascii(len=11): 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): CTRL_IFACE: ADD_NETWORK 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): RX ctrl_iface - hexdump_ascii(len=47): [REMOVED] 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): CTRL_IFACE: SET_NETWORK id=0 name='ssid' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): =28): [REMOVED] 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): ssid - hexdump_ascii(len=14): 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868):      41 73 68 74 6f 6e 20 53 74 61 74 69 6f 6e         Ashton Station   
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): RX ctrl_iface - hexdump_ascii(len=27): [REMOVED] 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): CTRL_IFACE: value - hexdump_ascii(len=4): [REMOVED] 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): key_mgmt: 0x4 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): RX ctrl_iface - hexdump_ascii(len=16): 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
:Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): CTRL_IFACE: ENABLE_NETWORK id=0 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Setting scan request: 0 sec 0 usec 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): State: DISCONNECTED -> SCANNING 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Starting AP scan (broadcast SSID) 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Trying to get current scan results first without requesting a new scan to speed up
 initial association 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Received 228 bytes of scan results (1 BSSes) 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Scan results: 1 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Selecting BSS from priority group 0 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): 0: 00:16:b6:c0:0d:0b ssid='Ashton Station' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868):    skip - no WPA/RSN IE 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868):    selected non-WPA AP 00:16:b6:c0:0d:0b ssid='Ashton Station' 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Trying to associate with 00:16:b6:c0:0d:0b (SSID='Ashton Station' freq=0 MHz) 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Cancelling scan request 
Jul 11 22:29:50 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): WPA: clearing own WPA/RSN IE 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): c auth_alg selection: 0x1 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): WPA: clearing AP WPA IE 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): WPA: clearing AP RSN IE 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): WPA: clearing own WPA/RSN IE 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): No keys have been configured - skip key clearing 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): wpa_driver_wext_set_drop_unencrypted 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): State: SCANNING -> ASSOCIATING 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): WEXT: Operstate: linkmode=-1, operstate=5 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): wpa_driver_wext_associate 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Setting authentication timeout: 10 sec 0 usec 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): EAPOL: External notification - portControl=ForceAuthorized 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): CTRL_IFACE monitor attached - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74
 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 36 34 33 38 2d 31 30 00 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Wireless event: cmd=0x8b06 len=8 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Wireless event: cmd=0x8b1a len=22 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Authentication with 00:00:00:00:00:00 timed out. 
Jul 11 22:30:00 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): CTRL_IFACE monitor send - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 
6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 36 34 33 38 2d 31 30 00 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): ed BSSID 00:16:b6:c0:0d:0b into blacklist 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): State: ASSOCIATING -> DISCONNECTED 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): WEXT: Operstate: linkmode=-1, operstate=5 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): No keys have been configured - skip key clearing 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): EAPOL: External notification - portEnabled=0 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): EAPOL: External notification - portValid=0 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Setting scan request: 0 sec 0 usec 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): State: DISCONNECTED -> SCANNING 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Starting AP scan (broadcast SSID) 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Scan timeout - try to get results 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Received 228 bytes of scan results (1 BSSes) 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Scan results: 1 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Selecting BSS from priority group 0 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): 0: 00:16:b6:c0:0d:0b ssid='Ashton Station' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868):    skip - no WPA/RSN IE 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868):    selected non-WPA AP 00:16:b6:c0:0d:0b ssid='Ashton Station' 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Trying to associate with 00:16:b6:c0:0d:0b (SSID='Ashton Station' freq=0 MHz) 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): CTRL_IFACE monitor send - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 
6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 36 34 33 38 2d 31 30 00 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): Cancelling scan request 
Jul 11 22:30:03 ottws58 NetworkManager: <information>^Iwpa_supplicant(24868): WPA: clearing own WPA/RSN IE 

```

---

### Post by philcolbourn on 2007-08-10
I too had problems with ZD1201 and Netgear Wg111v2 (which is actually a v1 according to Negear web site).

I just got my zd1201 going.

The thing that seemed to work was changing my channel number from 13 to 1 on my router. Instantly the zd1201 connected.

I did a lot of other things as well, so I will undo them and check that all is OK.

This is what is currently in my /etc/network/interfaces file

iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid XXXX
pre-up iwconfig wlan0 mode managed
pre-up iwconfig wlan0 key open XXXX
wireless-essid XXXX
wireless-key open XXXX
wireless-mode managed

I have the zd1201 firmware in /lib/firmware.

I hope this helps.

I found that my zd1201 (even though it was working) was on channel 6 using iwconfig but my router was on channel 1.
I added the following

wireless-channel 1

and I removed the pre-up stuff (it doesn't seem to do anything)

It is not reliable: I needed to insert it a few times before it came up.

I will test more.

---

### Post by philcolbourn on 2007-08-10
The problem that remains is that if you unplug the zd1201 and re-insert it it will not come up automatically.

Perhaps dhclient3 needs to be shut down if the usb is unplugged?

If you 

sudo ifdown wlan0
sudo ifup wlan0

it comes up.

Also on boot, it does not appear to be reliable. Best to plug it in after you have the login prompt.

---

### Post by philcolbourn on 2007-08-10
In my previous postings I forgot to mention that I am running Feisty on a Compaq Evo N620c.

This morning the ZD1201 would not connect to the router again.

After much silliness I checked the router. 

It had changed channel from 1 to 13 again. 

I then remembered that I put my router on a timer so that it did not run at night (my Billion 7407VGP was my 4th highest consumer of electricity - ~0.5 kWHr/day - after my fridge, electric oven and dishwasher! The timer, which only consumes 0.024kWHr/day, dropped the router to 7th place below my kettle, TV and microwave.)

So I must not have saved the configuration change and when it started up this morning if went back to channel 13.

After changing it back to channel 1 it worked again.

UPDATE:

I put the laptop to sleep and woke it again. The ZD1201 woke up fine.

---

### Post by proalan on 2007-08-14
another wg111v2 user here, can see all surrounding networks can't connect. 

Hope a solution emerges soon

---

### Post by dog2525 on 2007-08-14
just another noob with 7.04 out there having the same problem. lol all we have to do now is wait for a fix i guess.

---

### Post by DARKGuy on 2007-08-25
Hm. Why not, the ones who can, switch to Gutsy once and see if their problem can be solved? with upgrade from Fiesty of course... just as a test...

---

### Post by stuismad on 2007-09-02
I hate to bump this...but it obviously quite clear that many people have this problem.

Any solutions yet?

---

### Post by FuzzMaster on 2007-09-03
Hello!  I have a TEW-424UB and was suffering the same problem.  I don't know what version of Ubuntu I'm using (newbie here), but my Update Manager tells me I need to upgrade to 7.04, and I am just wondering if that would be a bad idea, because a lot of people say their wireless worked fine prior to upgrade??

Edit:  I should mentions it's funny how last night wireless refused to work in Linux (I could see network, connect to it, but nothing internetty worked), but this morning it stopped working in Windows. Go figure.

---

### Post by stuismad on 2007-09-04
solutions/ ideas/ tweaks are welcome.
thanks in advance.

---

### Post by Gflo on 2007-09-18
im joining the group belkin f5d7050 v3000 here we should make jackets

---

### Post by Gflo on 2007-09-18
[IMG]http://i152.photobucket.com/albums/s184/gflo_photo/jacket.jpg[/IMG]
and here it is(sorry if its a little messy not much time to make)post it either in your sig or avatar

---

### Post by ghaz on 2007-09-19
It seems that I am not the only one with this problem. I don't know if that's a good or a bad thing.

Yesterday morning I could "see" the connection, but when I tried to connect, it failed without error. After moving everything around for a stronger signal, it seems to connect. (I get the little histogram looking bar in the top right corner).

I live in a complex where we use wireless to connect to a server with a adsl line. If everything works correctly, firefox should open with a login page, but in feisty I can't reach that page (and I can't ping the server). In windows everything works fine.

I should probably mention that I don't know anything about wireless networking.

---

### Post by piuma12 on 2007-09-19
same problem here: it sees the connection but when i put WEP key doesnt connect :(
i have
**Acer Aspire 5680 + Feisty + PRO/Wireless 3945ABG**

help please guys...

---

### Post by Yoeri on 2007-09-19
have you tried using NDiswrapper to use your windows drivers?

I searched for my problems (exact the same as described but with a Zydas ZD1211 chipset) for a couple of weeks, after using my windows drivers with NDsiwrapper, everything worked fine, even better than under windows :D

---

### Post by piuma12 on 2007-09-19
> **Yoeri said:**
> have you tried using NDiswrapper to use your windows drivers?

I searched for my problems (exact the same as described but with a Zydas ZD1211 chipset) for a couple of weeks, after using my windows drivers with NDsiwrapper, everything worked fine, even better than under windows :D

i installed ndiswrapper with the drivers
but i dont know how to let it works
with the GTK interface doesnt show the drivers too...


:(

---

### Post by ghaz on 2007-09-19
Whoohoo! It is finally working.

And the only problem is that I can't remember from where I got the solution and the person who deserves the credit is now unknown. If you read this and you are the person who posted it on another thread,  thanks a lot.

This worked for me:
1> remove Network Manager (when I left it installed, everything only worked for about 10 seconds before it tried to "fix" the connection)

2> *sudo iwlist eth1 scan*
      example ouput:
      Cell 01 - Address: 99:9C:41:19:58:77
                    ESSID:"myrouter1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=83/100  Signal level=-51 dBm  Noise level=-51 dBm
                    Extra: Last beacon: 260ms ago

3> *sudo iwconfig eth1 essid myrouter1*

4> *sudo iwconfig eth1 key 0123456789*

I hope this helps

[edit] I searched a bit and found the other thread [http://ubuntuforums.org/showthread.php?t=511627]("http://ubuntuforums.org/showthread.php?t=511627") and many thanks to chili555

---

### Post by Yoeri on 2007-09-19
have you tried installing the drivers via the terminal (without the gtk gui)?

ndiswrapper -i [your inf filename here]

It must respond with the message:
xxx driver present, hardware present

---

### Post by KrotBot on 2007-09-26
Another n00b adding to the list.
My RaLink RT2500 802.11g Cardbus/mini-PCI, sees things but doesn't want communicate with them. Here is my ifconfig readout

```
eth0      Link encap:Ethernet  HWaddr 00:0F:20:33:D1:A6  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:fe33:d1a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:721366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:347862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:970706662 (925.7 MiB)  TX bytes:28783997 (27.4 MiB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7734 (7.5 KiB)  TX bytes:7734 (7.5 KiB)

ra0       Link encap:Ethernet  HWaddr 00:80:5A:22:DF:15  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1960571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:78422840 (74.7 MiB)
          Interrupt:16 Base address:0x8000
```

+ my iwconfig readout 
```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and last but not least my sudo iwlist scan readout
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:11:50:D2:7E:DF
                    Mode:Managed
                    ESSID:"home"
                    Encryption key:on
                    Channel:11
                    Quality:0/100  Signal level:-23 dBm  Noise level:-192 dBm
          Cell 02 - Address: 00:15:6D:53:B7:F4
                    Mode:Managed
                    ESSID:"RadioA"
                    Encryption key:off
                    Channel:9
                    Quality:0/100  Signal level:-59 dBm  Noise level:-192 dBm
          Cell 03 - Address: 00:19:5B:75:FE:C8
                    Mode:Managed
                    ESSID:"Teamovil"
                    Encryption key:on
                    Channel:1
                    Quality:0/100  Signal level:-81 dBm  Noise level:-192 dBm

```

Any help greatly appreciated as am getting it in the ear about the long as cable going from my room to the router :P

---

### Post by graywizard on 2007-09-27
I am not sure if this helps anyone....

I read the first 6 pages of this thread.

I had a new acer laptop a year ago and tried ubuntu and mint - never  could get the wireless going - yes different cards  for wifi but had issues.  Bought s premade ubuntu laptop most of the time worked but too many glitches and hassles - sent it back. Tried mint too with that machine and it worked better but still had some issues.

I just bought a refurb thinkpad R51 with intel wireless.  Loaded mint Celena. no wireless.  Tried ubuntu feisty and dapper live CD and no wireless.

I asked and begged for help and tried everything - and nothing and no help at all in both forums.

I tried every possible hex and asci and pasphrase etc. that my airport extreme was setup with wep encryption.

Frustrated as ****, I almost said OK live without wirless.

signal strength excellent but could not connect.  anyway, I tried every possible combination and I to had a linksys wireless shown but I do not have linksys wireless but a 4 port router. my nearest neighbor is 2 acres away. and I am one of the only people around here that has wifi.  so I tired all combos on linsys - no deal. started trying all possible combos on the main airport that I have and it finally worked.

i used 64/128 bit  instead of the normal 128 that I use, and I used the long 18 odd digit hexbin ID, I also used SHARED - and this time it worked - open did not work.

I sent and received a few emails wireless and I am connected and tryping this wireless.

Maybe some more detailed instructions as to what the heckk all of these various things mean and do would help many of us out.

Hope this helps!


edit: p.s.  the Keyring comes up too - asks for a password or a new one I used the regular password that I connected to my airport with the actual text password not the hexbin 28 odd digit number. I did not chance creating a new one so I used the airport one....might also be something to that if you enter a password that does not relate to the airport or wireless situation.  also hope this helps.

---

### Post by Bonder5678 on 2007-10-05
I've been trying to get wireless working on my desktop running Feisty.  I've tried 3 different wireless adapters, all with the exact same result: I can see the network (though it shows no signal, despite being in the same room as the router) but I cannot connect.  I know the router is fine because I can connect on my laptop (also running Feisty) anywhere in my house.  Once or twice I did manage to get the desktop computer to say it was connected to my home network, but got no response when I tried to ping the router.

EDIT:  I managed to get my wireless working with ndiswrapper.  Once I found a windows driver for my adapter (linksys wusb54g ver 4) that would play nice with ndiswrapper, it took less than 5 minutes to get working.  If you've not tried using ndiswrapper to get a driver for your card, I would recommend it, and it's not hard to do, so long as you're not afraid to roll up your sleeves and use the command line.

---

### Post by LinuxNewGuy on 2007-10-17
I was first researching how to make ubuntu 7.04 work with the WPA1 Personal encryption ... no luck :-( ... Then I started with the basic, i.e. no encryption at all.  It's still seeing all nearby wireless routers but can't connect to any one of them (including my own).  Took one more step back by "resetting" my Linksys router security parameter to the default.  Eventually, it worked and I could surf wirelessly on my Thinkpad T43p/Ubuntu 7.04 for the 1st time!  This confirmed me that my built-in wireless card as well as the driver which came with the std installation do work (at least to a certain extent).  I gained some confidence and tried to make it work with WPA1 Personal encryption.  To make the long story short, this in fact works right out of the box with one condition .... that is I have to set my router to broadcast my SSID.  Once the broadcast option is enabled, it works with no encryption, with WEP or even WPA1 Personal with no tweaking of any kind.  In the contrary, if my SSID broadcast is disabled, I can only see the network but can't connect.  I am only one step away from making this work exactly the way I'd like to see it.  Anyone knows how?  Or should I simply wait for one more day and see if ubuntu 7.10 Gutsy Gibbon will take care of this problem?

---

### Post by LinuxNewGuy on 2007-10-19
installed ubuntu 7.10 and am happy to report wireless connection (with my same T43p) work like a charm out of the box ... WPA, WPA2 with TKIP or AES and even with SSID broadcast disabled ... all work flawlessly!

---

### Post by IzeHouze on 2007-10-22
It works!

Installed Gutsy and tried to use DLink USB wireless adapter.  I saw the same issue as everyone else.  I can see the SSID, but after entering security key, it never connects.  After messing with it for a few days, I took a look at the linksys router config.  I found that I had enabled MAC Filtering on the wireless.  Even with my MAC in the access list I could not gain a connection.  Just for kicks I disabled MAC Filtering and voila!  It works!   Which brings to mind some other people giving reviews on various wireless routers and MAC Filtering not working correctly all of the time.

Which it worked fine on my laptop running XP.

So final setup is D-Link DWL-G122-B1 connected to Linksys WRT54G V6.  WPA2 Personal, MAC Filtering Disabled.

---

### Post by Sim777 on 2007-10-22
7.10 on Inspiron 1501. I enabled restricted drivers Broadcomm 43xx which seems to install normally. I can see networks. I can ping 127.0.0.1. I can connect to unsecure network (network manager displays connection bars), yet can't get an IP address, nor serf net. When I try to connect to WPA AP, it keeps asking for WPA key over and over. 

Any idea?

---

### Post by Sim777 on 2007-10-22
I installed wifi-radar and now I can connect to any network, But it is horribly slow.

---

### Post by Blind Buzzard on 2007-10-22
I think I may be having the same issue as Sim777.

I have a Broadcom 4306 brand, and I have installed the restricted drivers for its use, but after entering my wireless network information under system>admin>network>wireless info, I get nothing.  Can't even ping the router.

I have a non-broadcasted ssid, and a WPA encrypted connection, with DHCP.

I looked at my /etc/network/interfaces and it appears to have the correct information for everything including the WPA/SSID.

Any thoughts anyone?

---

### Post by Blind Buzzard on 2007-10-22
Hmmm.   I just finally got the wireless to work in 7.10.

All I did was re-install the os fresh, then updated all the security updates, rebooted, then installed the restricted drivers for the Broadcom that I have, then rebooted again, went into Bios on startup and turned wifi back on (not sure why it was off), it booted up, I input my ssid, and I was able to see my network along with several others in the community, I clicked on my network and it asked for my pw for wpa, I input it and I am now connected...

I have rebooted several times and it has come up successfully on each restart/pwr down.

This is one of the only reasons that I have held out on switching totally to Linux from MS.

All I can say now is.....  Bye Bye Windoz........

So Happy!  :)

---

### Post by Sim777 on 2007-10-22
> **Sim777 said:**
> I installed wifi-radar and now I can connect to any network, But it is horribly slow.

I removed NetworkManager and now everything seems to be working fine. Odd.

---

### Post by brancheb on 2007-10-22
I don't have a solution that will make a usb network interface work, I can tell you that it's hard. I tried to use a D-link USB dongle on my PowerSpec 6390.  I had all the problems described above.  In researching this issue I discovered that USB network interfaces are the weak link in Ubuntu because many vendors won't give up the secret sauce to build drivers and ndiswrapper works sometimes and not others--highly chipset dependent.

I also run Ubuntu on a old HP laptop and I use a wireless PCMCIA network card manufactured by Netgear, which has never given me a moment's problem.  So I went out and bought a Netgear WG311T Wireless card. It takes up a PCI slot, but it worked out of the box.

Elliott

---

### Post by Sim777 on 2007-10-22
> **Sim777 said:**
> I removed NetworkManager and now everything seems to be working fine. Odd.

...and then I rebooted.....dead in water again. It's like wifi requires a sacrifice of a sheep to get this working....

---

### Post by Sim777 on 2007-10-23
> **Sim777 said:**
> ...and then I rebooted.....dead in water again. It's like wifi requires a sacrifice of a sheep to get this working....

So, here's my solution. I uninstalled wifi-radar and followed following directions. 
The only changes I made was to get 1.48 ndsiwrapper instead of 1.47

[http://ubuntu1501.blogspot.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html](http://ubuntu1501.blogspot.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html)

The only downside after each reboot I have to manually enable it in terminal. 

```


sudo modprobe ndiswrapper
sudo iwconfig  <-to see if wifi is on
sudo iwlist scanning  <-to see if it picks up your network
sudo iwconfig eth1 essid yournetworkname
sudo iwconfig eth1 key whateveryourkeygoeshere
sudo dhclient eth1  

(eth1 is my id, your may vary)






```

---

### Post by Blind Buzzard on 2007-10-23
I have noticed after getting my wifi working last night, that if I disconnect it may take four or five reconnection attempts to get access to the network again.  It is also very slow at times, much slower than my Mac or PC.  Not sure about this issue, has anyone else experienced the same issue with speed?

---

### Post by Sim777 on 2007-10-23
> **Blind Buzzard said:**
> I have noticed after getting my wifi working last night, that if I disconnect it may take four or five reconnection attempts to get access to the network again.  It is also very slow at times, much slower than my Mac or PC.  Not sure about this issue, has anyone else experienced the same issue with speed?

When I just enabled drivers through restricted drivers, it would intermittently work when ever it felt like it but at much lower speeds. 
(Inspiron 1501 Broadcom 43xx)

---

### Post by Selcal on 2007-10-24
I had the same problem.  To fix it i did all of the available broadcom-wifi installation guides.  This had given me the complete lack of wlan0.  I get nothing on it now.  NM-Applet doesn't see my wireless abilities any more at all.  I would like to start back fresh without re-installing Gutsy.  If anyone knows how to reset my wlan stuff what is the way to do that?

then i can be on the same page as you guys, and get back to trying to solve this problem.

I am kicking a Gateway MX6448.  The really weird thing is the loss of disk space when i installed linux.  My HD doesn't register about 10Gig anymore.  Another problem for another time.

Ubernoob
Selcal

---

### Post by Blind Buzzard on 2007-10-24
> **Sim777 said:**
> When I just enabled drivers through restricted drivers, it would intermittently work when ever it felt like it but at much lower speeds. 
(Inspiron 1501 Broadcom 43xx)

This is a Dell Latitude D600 with Broadcom 43XX as well.  

I'll walk through the link you posted here, do I have to uninstall the proprietary drivers first?

---

### Post by starlily on 2007-10-24
I had my rt2500 working fine in Feisty with ndiswrapper, and it broke when I upgraded to Gutsy. I could see APs but not connect at all. I tried a lot of things, but the fix finally was this: I have both "rt2500" AND "rt2500pci" in /etc/modprobe.d/blacklist, everything else is exactly as it was before. 

I hope this helps someone else.

---

### Post by ser_virtual on 2007-10-25
Hi, I'm new to Linux. I've just got Gutsy running on a Dell 1501.
The wireless card is a Dell Broadcom 4311 
I tried to enable the restrictec driver from the manager but an error:
source for bcm43xx-fwcutter not enable
Following the alternative configuration howto for the wirelles card in 
[ubuntu1501.blogspot.com]("http://ubuntu1501.blogspot.com")
I somehow got the card able to see the network, wich uses WAP. However, I just cannot get online. The network monitor doesn't display a wireless option, is there another way to get conneted? I'm also confused since once I set the key for the network in the System>Administration>Network ans I return the keyword field is empty again. Any ideas for these probems?

I don't have access to wire connection and I cannot make the dial-up way run.

Thanks in advance.

---

### Post by ser_virtual on 2007-10-25
> **Sim777 said:**
> So, here's my solution. I uninstalled wifi-radar and followed following directions. 
The only changes I made was to get 1.48 ndsiwrapper instead of 1.47

[http://ubuntu1501.blogspot.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html](http://ubuntu1501.blogspot.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html)

The only downside after each reboot I have to manually enable it in terminal. 

```


sudo modprobe ndiswrapper
sudo iwconfig  <-to see if wifi is on
sudo iwlist scanning  <-to see if it picks up your network
sudo iwconfig eth1 essid yournetworkname
sudo iwconfig eth1 key whateveryourkeygoeshere
sudo dhclient eth1  

(eth1 is my id, your may vary)






```

I've followed these comments but I'm a little confused: How do I uninstall Network Manager (is this the same network monitor on the task bar?)? I wasn't able to activate the drivers from the Restricted Driver Manager since a Error like: bcm43xx-fwcutter software source package not enable (I have a Broadcom4311 card) but somehow I managed to get the  card see the network. How do I install/unistall wifi-radar? and finally, I've read something about WICD replacing NetworkManager (which is automatically installed right?) but I have not idea of howto get it and where from (I don't have access to the net yet!) and how to install it.

Sorry, I'm totaly new to Linux as well as to Gutsy.

---

### Post by Selcal on 2007-10-28
It works !!!! it works!!! HOly friggin Sheit it works!!!

> **Sim777 said:**
> So, here's my solution. I uninstalled wifi-radar and followed following directions. 
The only changes I made was to get 1.48 ndsiwrapper instead of 1.47

[http://ubuntu1501.blogspot.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html](http://ubuntu1501.blogspot.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html)

The only downside after each reboot I have to manually enable it in terminal. 

```


sudo modprobe ndiswrapper
sudo iwconfig  <-to see if wifi is on
sudo iwlist scanning  <-to see if it picks up your network
sudo iwconfig eth1 essid yournetworkname
sudo iwconfig eth1 key whateveryourkeygoeshere
sudo dhclient eth1  

(eth1 is my id, your may vary)






```

i have been working on this for weeks.  I uninstalled the NM-Applet and wifi-radar and just followed what it says above.  I just didn't use the key i am blocking network addresses, and my eth1 is eth0.

big thanks Sim.  I will post this on my guide thread for my particular laptop.

---

### Post by Sim777 on 2007-10-30
> **ser_virtual said:**
> I've followed these comments but I'm a little confused: How do I uninstall Network Manager (is this the same network monitor on the task bar?)? I wasn't able to activate the drivers from the Restricted Driver Manager since a Error like: bcm43xx-fwcutter software source package not enable (I have a Broadcom4311 card) but somehow I managed to get the  card see the network. How do I install/unistall wifi-radar? and finally, I've read something about WICD replacing NetworkManager (which is automatically installed right?) but I have not idea of howto get it and where from (I don't have access to the net yet!) and how to install it.

Sorry, I'm totaly new to Linux as well as to Gutsy.

I just spotted this thread.... I don't know if you found out how, but. 

To fix 'bcm43xx-fwcutter software source package not enable'   

System > Admin > Software Sources. Check top 4 options (main, universe, restricted and multiverse) 

But for my work-around, I did not enable that driver. 

To uninstall Network Manager icon, System > Admin > Synopsis Software Manager. Find network manager and select it for removal. I think name of it is "NM-Applet"

---

### Post by Sim777 on 2007-10-30
> **Blind Buzzard said:**
> This is a Dell Latitude D600 with Broadcom 43XX as well.  

I'll walk through the link you posted here, do I have to uninstall the proprietary drivers first?


I did not enabled proprietary drivers.

---

### Post by kiybaci on 2007-11-05
hi,
I just would like suggest you to check the inner modem settings if your mac (ethernet) address is banned by an adminstrator. (or the other way; if your mac-adress is not listed in allowed computers list.)
(just by typing the address of your modem on the same network: mostly 192.168.1.1 or 1.2)

I'm writing this, because we were pulling the legs of a friend who lives with us. maybe finally he finds this message and will be enlighted why he cannot connect to internet sometimes. it's been several days and I feel sorry for him :)

---

### Post by Gflo on 2007-11-28
i dont know if wehave already established this or not but i decided to install my little wireless usb network adapter on my windows computer and i had the same problem as this. it turns out that the device is set to wireless b only.

---

### Post by legoman666 on 2007-11-28
I am having the same problem on Feisty 7.10 using the drivers out of the box for the AR5212 wireless chipset. It connects perfectly fine to an unencrypted network (at home) but refuses to connect at school to the WEP network no matter how many times I enter the wireless key (correctly).

---

### Post by mpm on 2007-12-15
Same thing, I can see multiple (unsecure) wireless networks and cannot connect to most.

---

### Post by peevee07 on 2007-12-16
I was having the same problem Wifi-Radar had been doing the job for me for about a year. Then one day I couldn't connect. There's a lot of advice out there and I fiddled and fuddled for countless hours until SIM77's solution. Using Synaptic I removed Wifi-Radar (and the config files) and followed his suggestions, finally connecting via dhclient. Thank you. A whole bunch of beans and a hat off to SIM77.

---

### Post by mj_ja55 on 2007-12-16
I was having a similar problem to those reporting that they can see the wireless network but can not connect.  Mine was a little different because I could connect to an open wireless network at school, but I couldn't connect to my wireless network at home.

After much frustration, I found the problem. For some reason, I have to manually set my encryption key to "open" rather than "restricted", which seems to be the default.  Once I enter my WEP key and set the mode to "open", it works great.  Hope this helps.

Here is an example of the command I use:

sudo iwconfig eth0 essid XXXXX key XXXXXXXXXX key open

The "X"s are just substitute characters for my essid and WEP key.

---

### Post by linuxman07 on 2007-12-16
I have installed gutsy on my Toshiba Laptop.  I am having similar problems I think.
I run DSL with an Actiontec modem.  Eth0 with cable works fine. Wireless without WEP also works fine.  But when I set the WEP key, which is the one I have been using for several years with  MS XP, it does not work with UBUNTU 7.10.  Without WEP I have wireless, but with encryption no wireless.  I do enter the correct key when prompted.  But no go.  I have tried some of the suggestions noted here but still have the problem.  Does  anyone have a solution?

---

### Post by adasilva on 2008-01-04
Same problem here:
Using Gutsy 7.10 on my (new) hp laptop with an atheron AR5007EG wireless card.

The wired connection works fine, and ndiswrapper works when I disable the encryption on the wireless router, but when it is encrypted, the connection reads 0% signal, even right next to the router.

---

### Post by Digger78 on 2008-01-04
[http://ubuntuforums.org/showthread.php?t=658573](http://ubuntuforums.org/showthread.php?t=658573)

try my suggestion.

---

### Post by adasilva on 2008-01-04
Thanks, but it did not work. That line was not in the file, originally, so I tried to add it both with and without the s:
My key is a passphrase, so I think that i need the s in there?

When I tried the second command (sudo /etc/init.d/networking restart), I got errors about eth9, but this is a wired channel/connection, but nothing else appears to have changed.

---

