---
title: "RT2500 works in feisty but not in gutsy"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by theharshone on 2007-10-19
Hi
I have D-Link DWL-122 rrev. B1 (uses the ralink rt500 chipset)card that worked on fiesty but not on gutsy. I belive the problem is the driver. Fiesty used the legacy driver while gutsy uses the beta driver. The beta driver *sees* my network but cannot actually connect. when i run dhclient wlan0, it says no dhcpoffers. Also, for some reason, i cannot compile the legacy driver on gutsy even though i could compile it on fiesty. I am stumped. Any help is greatly appreciated.

---

### Post by matt2ss on 2007-10-19
Same problem here. Although rt2500 has been detected, I am not able to connect (using default network manager in KDE).
After entering essid, wpa key etc., manager outputs an error.

---

### Post by theharshone on 2007-10-19
I think i cannot install the legacy driver because of my smp system. That is weird though because i compiled the same tar package on feisty earlier with smp. I wish someone could just package the legacy module and release it.  I went to packages.ubuntu.com but they only had the source which doesnt compile for me.

---

### Post by theharshone on 2007-10-20
I installed openSUSE and using the same drivers as gutsy, it worked! the only difference i made was instead of using dhclient <interface> i used dhcpcd <interface>.
Maybe this may solve your problems. Post if it works

-TheHarshOne

---

### Post by odiseo77 on 2007-10-20
Weird, I've just installed Gutsy, and used network-manager to connect to my router (had to play a bit with it, but could finally connect); which encryption type are you people using? (I'm using WPA-TKIP, if it helps).

---

### Post by matt2ss on 2007-10-20
I'm using AES, but will try TKIP. (in Kubuntu)

---

### Post by Architeuthis on 2007-10-20
> The beta driver sees my network but cannot actually connect. when i run dhclient wlan0, it says no dhcpoffers.
I think I have the same problem (see my thread about it: [http://ubuntuforums.org/showthread.php?t=581365](http://ubuntuforums.org/showthread.php?t=581365) ). My wireless card (asus wl-167g) uses the rt2500usb driver on the Gutsy live cd, it can see the network but it can't connect. I don't know which version it's using exactly (how do I check this?). On feisty it uses the rt2570 driver.

---

### Post by Shaffox on 2007-10-20
I'm having the same problem. It would be great if someone knows to fix this.

---

### Post by Whateverist on 2007-10-20
Same here. I'm using wicd with an rt2500 card. It sees the network and the router sees the card, but it can't connect.

---

### Post by rustybronco on 2007-10-20
[http://ubuntuforums.org/showpost.php?p=3566989&postcount=17](http://ubuntuforums.org/showpost.php?p=3566989&postcount=17)

---

### Post by Whateverist on 2007-10-20
> **rustybronco said:**
> [http://ubuntuforums.org/showpost.php?p=3566989&postcount=17](http://ubuntuforums.org/showpost.php?p=3566989&postcount=17)

Doesn't change diddely-squat, I'm afraid. Is this working for anyone else?

---

### Post by sles on 2007-10-20
I got my msi rt2500-based card working with 7.10 only when I compiled rt2500 (legacy)  driver from [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)...
I have no ideas why this driver is not included in 7.10.
rt2500 was in 7.04 and it worked out of box.
IMHO, this should be considered as bug.

---

### Post by Kisil on 2007-10-20
I'm having this problem too.  Right now I'm posting from my Gentoo build, where ndiswrapper + rt2500usb works just fine.  When I try to connect to my network from Gutsy (same machine), it sits for a while and then nothing happens.  Manual config through the utility also doesn't work.

I'm using a Linksys WUSB54G card with a prism chip.  I'd steal my configuration from Gentoo, but they're really not analogous.

The really funny thing is that I just got wireless working in Gentoo last week.

---

### Post by Shaffox on 2007-10-20
Ndiswrapper and stuff ..

It just worked out of the box in feisty, and hearing gutsy would be better for wireless ..

Yet I'm giving it a shot, I'll update when I'm done.

I triend to compile the driver myself (from rt2x00 serialmonkey), it worked, but yet I don't have a connection to the internet.

Anyone else who can come up with a solution?

---

### Post by wieman01 on 2007-10-20
> **Whateverist said:**
> Doesn't change diddely-squat, I'm afraid. Is this working for anyone else?
Feisty requires you to blacklist "rt2570". Did you try that guide? And what problems did you encounter?

---

### Post by lmohdlp on 2007-10-20
I'm having the same problem, it recgonizes my wireless card (a linksys network adapter that goes along with my linksys router) and the wireless network but when i say connect.... pfft.... nothing happens. I had to downgrade back to feisty because of this.... I really liked gutsy but can't use it if I can't get internet

---

### Post by Trueno22 on 2007-10-20
Use Wicd as a network manager replacement.  The network manager is borked when it comes to Wireless.

---

### Post by Whateverist on 2007-10-20
> **wieman01 said:**
> Feisty requires you to blacklist "rt2570". Did you try that guide? And what problems did you encounter?

If I blacklist nothing, or blacklist "rt2570", the network manager applet rcognises all the networks in the street but can't connect to them (tries to connect with the swirly animation for half a minute, then stops). 

If I blacklist "rt2500usb", my wireless disappears.

---

### Post by wieman01 on 2007-10-20
> **Whateverist said:**
> If I blacklist "rt2500usb", my wireless disappears.
That means that "rt2500usb" is probably the right driver, but you have not install "ndiswrapper" and the driver correctly. What does that yield:
> ndiswrapper -l

---

### Post by Whateverist on 2007-10-20
> What does that yield:

```
netu2g54 : driver installed
        device (0411:008B) present (alternate driver: rt2500usb)
```

This is the driver that worked under Feisty.

---

### Post by wieman01 on 2007-10-20
Ok. Now do this for me and restart the computer:
> sudo gedit /etc/network/interfaces
Add these lines:
> auto wlan0
iface wlan0 inet dhcp
After a restart Network Manager should be able to detect & use the device. What about scanning:
> sudo iwlist scan

---

### Post by Whateverist on 2007-10-20
I added the lines to /interfaces and rebooted (with rt2500usb still added to the blacklist); the wireless is still missing.

Running iwlist scan with 2500usb blacklisted gives me this:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

Removing 2500usb from the blacklist and scanning again gives me a list of all detected networks.

---

### Post by matt2ss on 2007-10-20
I found out something interesting.
Wireless connection (rt2500pci) works fine for me, but only with enabled ssid broadcasting.
It does not work when ssid is hidden, neither via network-manager, nor wicd.

---

### Post by theharshone on 2007-10-20
I think something is wrong with the gutsy driver since the same driver works fine with openSUSE. Can someone plz package and amd64 version of the legacy driver? 

Thanks in advance:)

---

### Post by wieman01 on 2007-10-20
> **Whateverist said:**
> I added the lines to /interfaces and rebooted (with rt2500usb still added to the blacklist); the wireless is still missing.

Running iwlist scan with 2500usb blacklisted gives me this:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

Removing 2500usb from the blacklist and scanning again gives me a list of all detected networks.
Is there any other step you might have missed? Could you please check my tutorial and try once again? I know it does work for some people, so I am sure we have missed something more or less obvious.

---

### Post by theharshone on 2007-10-21
I'm giving up on gutsy. I'm downgrading to feisty and upgrade when a solution has been found. I wish gutsy wireless could work out of the box like it does in opensuse. :sigh: I still cannot believe they use the same drivers...

---

### Post by Kisil on 2007-10-21
I thought I was using the exact same driver in gutsy as I was in feisty - since it's through ndiswrapper, it's a binary supplied by the manufacturer.

I haven't tried blacklisting the other driver, becuase a. I don't know how and b. I don't see how that could have any effect.  ndiswrapper -l shows my card installed correctly using rt2500usb as expected.  I don't get any real errors out of any of the wireless networking gui tools.  ifconfig and iwconfig give output you'd expect from an unconnected network card.  I'm submitting this from the same card, using the same driver, on the same connection, running a different OS, so I think I can rule out hardware/driver failure.

Should I submit a bug about this?  Does anyone know of an open one on this issue?

---

### Post by hambudge on 2007-10-21
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

Tried your tutorial but same problem on my DV6000 after Gutsy upgrade

ndiswrapper -l  yields:bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)
any other ideas?
Regards

---

### Post by theharshone on 2007-10-21
> **hambudge said:**
> lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

Tried your tutorial but same problem on my DV6000 after Gutsy upgrade

ndiswrapper -l  yields:bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)
any other ideas?
Regards

did you try 
```

sudo modprobe ndiswrapper
ifconfig -a
ifconfig wlan0 up

```

Hope you have better luck than me.:)

**edit: the bug report is here [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/126407]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/126407")

---

### Post by wieman01 on 2007-10-21
> **hambudge said:**
> lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

Tried your tutorial but same problem on my DV6000 after Gutsy upgrade

ndiswrapper -l  yields:bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)
any other ideas?
Regards
Mmm... that's a Broadcom chipset you have got there. You ought to take a look at this:

[http://ubuntuforums.org/showthread.php?t=405990]("http://ubuntuforums.org/showthread.php?t=405990")

---

### Post by enjahova on 2007-10-21
I have the same problem as others here. ndiswrapper -l shows the same rt2500usb that worked in 7.04. I blacklisted bcm43xx and it can see my AP and others in the neighborhood. It just can't connect to any.

No ideas still?

---

### Post by theharshone on 2007-10-21
I would have thought a thread with a 1000+ views would have attracted at least one developer's attention to say, "Oh look, we have a problem." My simple solution to the problem is simply to include all the legacy drivers in the repos(i still have to check gutsy backports). Problem solved.

---

### Post by wieman01 on 2007-10-21
> **enjahova said:**
> I have the same problem as others here. ndiswrapper -l shows the same rt2500usb that worked in 7.04. I blacklisted bcm43xx and it can see my AP and others in the neighborhood. It just can't connect to any.

No ideas still?
Look, RT2500 is a Ralink adapter whereas bcm43xx is a Broadcom. There are two different pairs of shoes and have nothing in common. To get the RT2500 (e.g. WUSB54G V4) working you need to blacklist "rt2500usb" in Gutsy for instance.

---

### Post by enjahova on 2007-10-21
Ok, I'm a little confused.
I have a WUSB54G v4, and the driver that i downloaded which worked in Feisty, is rt2500usb.inf

When I blacklisted rt2500 wlan0 disappears. I don't know why I would blacklist the driver that I'm going to install.

When I tried ndiswrapper -r rt2500usb it says "inappropriate ioctl for device"

---

### Post by wieman01 on 2007-10-21
> **enjahova said:**
> Ok, I'm a little confused.
I have a WUSB54G v4, and the driver that i downloaded which worked in Feisty, is rt2500usb.inf

When I blacklisted rt2500 wlan0 disappears. I don't know why I would blacklist the driver that I'm going to install.

When I tried ndiswrapper -r rt2500usb it says "inappropriate ioctl for device"
The .INF file is not the only one you need. Another other files that came with the driver e.g. .CAB?

Moreover you need to blacklist "rt2500usb" in Gutsy... the name has changed.

---

### Post by Ludwik on 2007-10-22
The same problem here. We have 20 laptops with ASUS rt2500-based PCI cards and after upgrade to Gutsy the Network Manager shows available networks, but when we try to connect to our WPA-protected (TKIP) network, it asks for the key and than tries to connect for about 30 seconds, but fails.

Its a major problem for our school. Any ideas?

---

### Post by Tomosaur on 2007-10-22
Exactly the same problem, there's a bug report on Launchpad about it, the devs have confirmed the problem but they've marked it as low priority.

I really don't want to use the ndiswrapper approach to fixing this, so if anyone has any other solution I'd be very grateful. I'm about to try the legacy driver to see if that will fix the problem.

---

### Post by rustybronco on 2007-10-22
Possibly an answer in this thread.
 [http://ubuntuforums.org/showthread.php?t=584657](http://ubuntuforums.org/showthread.php?t=584657)

---

### Post by Ludwik on 2007-10-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/134962](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/134962) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The [bug 134962]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/134962") seems to describe this issue

---

### Post by enjahova on 2007-10-22
> **wieman01 said:**
> The .INF file is not the only one you need. Another other files that came with the driver e.g. .CAB?

Moreover you need to blacklist "rt2500usb" in Gutsy... the name has changed.

Yes, there are other files in there including the .CAB

The point is, the driver I installed under Feisty  with ndiswrapper is the binary from the linksys site. Why can't that exact same driver work in Gutsy? If I blacklist the rt2500usb driver, what driver am I supposed to replace it with? rt2500usb is the driver I got from linksys website. What has the name changed to?

---

### Post by wieman01 on 2007-10-22
> **enjahova said:**
> Yes, there are other files in there including the .CAB

The point is, the driver I installed under Feisty  with ndiswrapper is the binary from the linksys site. Why can't that exact same driver work in Gutsy? If I blacklist the rt2500usb driver, what driver am I supposed to replace it with? rt2500usb is the driver I got from linksys website. What has the name changed to?
By blacklisting "rt2500usb" you actually disabled the Linux drive. Then you load Linksys' binary driver. No idea why that does not work for you.

---

### Post by kevdog on 2007-10-22
I didnt read this entire post, however it seems in other posts if downloading and installing the serial monkey rt2500 driver, that it seems to work better than the built-in driver.  I dont know why.  Basically defaulted to the feisty solution.

---

### Post by wieman01 on 2007-10-22
> **kevdog said:**
> I didnt read this entire post, however it seems in other posts if downloading and installing the serial monkey rt2500 driver, that it seems to work better than the built-in driver.  I dont know why.  Basically defaulted to the feisty solution.
You could be right, Kevdog. Or replacing it with "ndiswrapper" or whatever. 

Another thing I noticed... We had a discussion a while ago whether Ubuntu ships with Serialmonkey's drivers or not... It doesn't. So you were right.

---

### Post by odiseo77 on 2007-10-22
> **kevdog said:**
> I didnt read this entire post, however it seems in other posts if downloading and installing the serial monkey rt2500 driver, that it seems to work better than the built-in driver.  I dont know why.  Basically defaulted to the feisty solution.

You're right; I think it's because Gutsy has included the integrated rt2x00 driver into the kernel; the rt2x00 driver aims to integrate all the rt*-based family cards into one single driver, but it's still in beta stage (read more [here]("http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page#Latest%20News")).
I'm using a PCI rt2500-based card and I found this:

```
locate rt2500usb
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2500usb.ko
```

Then I navigated to '/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/' to see which drivers it contains, and I found this:

```
cd /lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/
vicente@ubuntu-box:/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00$ ls
eeprom_93cx6.ko  rt2500pci.ko  rt2x00lib.ko  rt2x00usb.ko  rt73usb.ko
rt2400pci.ko     rt2500usb.ko  rt2x00pci.ko  rt61pci.ko
```

So I assume Gutsy uses the rt2x00 driver.

Feisty, instead used the old legacy rt2500 driver which is more stable in my opinion (for example, I found that in Gutsy, the rt2500pci driver doesn't accept the 'set' command when invoking iwpriv).

A good idea would be to notify the developers of the rt2x00 project about this issue with the rt2x00 driver (though, maybe, it has been fixed in the latest CVS hourly version (it would be a matter of testing it to see how it behaves, but at the moment, I'm kind of busy to do this)).

Regards.

---

### Post by bigboy_pdb on 2007-10-23
For those of you who don't want to use ndiswrapper (and you'd prefer to use the modules that came with Gutsy) you might want to try the solution that worked for me. It can be found here:
[http://ubuntuforums.org/showthread.php?t=587727](http://ubuntuforums.org/showthread.php?t=587727)

---

### Post by kevdog on 2007-10-23
Hmm,

Are you sure the rt2500usb and rt2500pci drivers aren't the serial monkey drivers?? After are old discussion, you had me convinced that the default drivers where made by serial monkey.  I looked around for a long time, and came to the conclusion that serial monkey was the only one putting out ra-based drivers.

Has anyone, (including bigboy_pd) had success (no matter how much tweaking) had success in getting the buit-in drivers to work??  Something tells me that has to be a trick.

---

### Post by wieman01 on 2007-10-23
> **kevdog said:**
> Hmm,

Are you sure the rt2500usb and rt2500pci drivers aren't the serial monkey drivers?? After are old discussion, you had me convinced that the default drivers where made by serial monkey.  I looked around for a long time, and came to the conclusion that serial monkey was the only one putting out ra-based drivers.

Has anyone, (including bigboy_pd) had success (no matter how much tweaking) had success in getting the buit-in drivers to work??  Something tells me that has to be a trick.
Perhaps I have confused both of us... ;-) I thought so for a long time but I came to believe that it must some other OS driver... I found this link (search for the wireless section):

[http://www.poplarware.com/everexlinux.html]("http://www.poplarware.com/everexlinux.html")

Could it be that they use Ralink's own OS driver?

[http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

Another interesting link: [http://ralink.rapla.net/]("http://ralink.rapla.net/")

You see I am slightly confused as well.

---

### Post by bigboy_pdb on 2007-10-23
> **kevdog said:**
> 
Are you sure the rt2500usb and rt2500pci drivers aren't the serial monkey drivers??


I never stated that they weren't serial monkey drivers. I said the modules that came with Gutsy, which are the ones that everyone is having problems with.

**[EDIT]**Sorry, I didn't realize this wasn't a response to me. I should have re-read the posts above (I read this thead a while ago)**[/EDIT]**

> **kevdog said:**
> 
Has anyone, (including bigboy_pd) had success (no matter how much tweaking) had success in getting the buit-in drivers to work??  Something tells me that has to be a trick.


Yes I've had success with my method, otherwise I wouldn't have posted it. I doubt that anyone else has had success with it yet because I was the one who came up with this solution. I posted my solution to find out if it really works. I searched for an alternate solution because I wanted to figure out why the Gutsy drivers weren't working and I wanted to create a solution that was simpler than the ones that I've seen.

If you read my other posts then you should realize that there's no reason not to trust me. Aside from this, I don't understand why someone would post a fake solution to a problem, and I don't see what anyone has to lose by trying it. A person can simply change his/her modules that are black listed, comment out some of the current lines in the "/etc/network/interfaces", and then add the lines that I gave (with the correct changes).

**[EDIT]**I should have also mentioned that if my method is a work around for getting the modules to work then I'll post it on launchpad.**[/EDIT]**

---

### Post by kevdog on 2007-10-23
wieman 

good links -- wow, now Im really confused b/c it does seem like ra makes their own ra drivers.  Interestingly however on their download page:
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

There is no 2500 driver, although somehow rt2500pci and rt2500usb were included in the default install.

Its been a while since Ive compiled my own vanilla kernel from source, but I dont believe that they were included in the vanilla kernel either (this link is a few months old) but shows default wireless drivers included by default in the vanilla kernel:
[http://ubuntuforums.org/attachment.php?attachmentid=43599&d=1189921495](http://ubuntuforums.org/attachment.php?attachmentid=43599&d=1189921495)

Definitely confusing to me also -- and I cant imagine drivers would be included by default that wouldnt work!:confused:

---

### Post by wieman01 on 2007-10-23
> **bigboy_pdb said:**
> If you read my other posts then you should realize that there's no reason not to trust me. Aside from this, I don't understand why someone would post a fake solution to a problem, and I don't see what anyone has to lose by trying it. A person can simply change his/her modules that are black listed, comment out some of the current lines in the "/etc/network/interfaces", and then add the lines that I gave (with the correct changes).
I don't think Kevdog meant to discourage you from helping others and posting your solutions. In fact your expertise is highly appreciated and of course we trust you. Just to dispel your concerns. This is a very friendly & open-minded community so you are most welcome.

---

### Post by kevdog on 2007-10-23
bigboy

Im really glad that you posted a solution that works (i dont have an ra based card to test), however your basic solution is to cycle the interface (bring down, set wpa parameters, bring back up).  It is an easy and elegant solution, but just wondering did this cycling need to be done, if wpa was not being used??  Seems like you shouldnt need to do this if connecting to an unencrypted network??  Based on the logic of your post however, WEP parameters would need to go through the same cycling to get a connection.  Can you confirm?

---

### Post by wieman01 on 2007-10-23
> **kevdog said:**
> Definitely confusing to me also -- and I cant imagine drivers would be included by default that wouldnt work!:confused:
I think that is exaclty what happened... They are in the process of replacing the default drivers and included drivers that are not functional. Embarrassing I'd say.

---

### Post by wieman01 on 2007-10-23
> **kevdog said:**
> bigboy

Im really glad that you posted a solution that works (i dont have an ra based card to test), however your basic solution is to cycle the interface (bring down, set wpa parameters, bring back up).  It is an easy and elegant solution, but just wondering did this cycling need to be done, if wpa was not being used??  Seems like you shouldnt need to do this if connecting to an unencrypted network??  Based on the logic of your post however, WEP parameters would need to go through the same cycling to get a connection.  Can you confirm?
In fact when you read my WPA tutorial, I do the exact same think. You need to bring down the interface once and up it again. Otherwise you have to do so after a reboot. Very ugly but apparently a bug. Others have experienced it as well. Restarting the interface is the only workaround that works.

As fa as unencrypted networks are concerned, however, I am not sure if you need to do so.

---

### Post by kevdog on 2007-10-23
Ahh -- its all coming together for me now!!  
Weiman 
I saw that in your tutorial, but for some reason a lightbulb just came on now!!

Just to confirm, this cycling is needed for WEP, but not for an unencrypted network!  Maybe that sleep statement does do something after all!! (like wait for something else to be activated before passing along the wpa parameters to the router -- who knows!)

---

### Post by bigboy_pdb on 2007-10-23
> **kevdog said:**
> 
Based on the logic of your post however, WEP parameters would need to go through the same cycling to get a connection.  Can you confirm?


I haven't been able to try the solution without any encryption and with other forms of encryption because the computer my router is connected to is currently in use. I don't think that I'll be able to check it this evening (and I may be leaving the city tomorrow). I'll try to check it beforehand if I can.

> **wieman01 said:**
> 
As fa as unencrypted networks are concerned, however, I am not sure if you need to do so.


It might not need to be done for unencrypted networks. I probably should have mentioned WPA encryption in the title. Once I've tested my solution without encryption and with WEP, I can probably request a title change from forum staff (or is there some way that I can do that myself?).

---

### Post by wieman01 on 2007-10-23
> **bigboy_pdb said:**
> It might not need to be done for unencrypted networks. I probably should have mentioned WPA encryption in the title. Once I've tested my solution without encryption and with WEP, I can probably request a title change from forum staff (or is there some way that a person can do that myself?).
No big deal, mate. You can always ask the staff to do so as you cannot change the title yourself.

---

### Post by Whateverist on 2007-10-23
> **wieman01 said:**
> Is there any other step you might have missed? Could you please check my tutorial and try once again? I know it does work for some people, so I am sure we have missed something more or less obvious.

Sorry for the late reply - it's working now, I think; I redid the guide, this time blacklisting *all* the RTxxxx drivers and the connection started working. It sometimes fails for no obvious reason, but it's usable.

---

### Post by Ludwik on 2007-10-26
BigBoy's solution with adding "sleep 20" didn't work form me. Odiseo's one, that is installing the legacy driver worked perfectly, though. It can be found under [http://ubuntuforums.org/showpost.php?p=3595458&postcount=6](http://ubuntuforums.org/showpost.php?p=3595458&postcount=6)

---

### Post by odiseo77 on 2007-10-26
Hi Ludwik, thanks for the feedback; I'm happy my guide worked for you (and I hope it can be helpful other people having the same issue) :)

Regards.

---

### Post by dabotsonline on 2007-11-15
> **matt2ss said:**
> I found out something interesting.
Wireless connection (rt2500pci) works fine for me, but only with enabled ssid broadcasting.
It does not work when ssid is hidden, neither via network-manager, nor wicd.

I have exactly the same problem in Gutsy 32-bit with an unsecured, but hidden, network.

My /etc/network/interfaces:

> 
auto lo
iface lo inet loopback


Here's my nm-tool output when my Ethernet cable had been removed and I was trying to connect to BeBox:


> NetworkManager Tool

State: connecting

- Device: eth0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/eth0
  Type:              Wired
  Driver:            8139too
  Active:            no
  HW Address:        00:40:D0:7B:CE:C0

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Settings
    Hardware Link:   no


- Device: wlan0 ----------------------------------------------------------------
  NM Path:           /org/freedesktop/NetworkManager/Devices/wlan0
  Type:              802.11 Wireless
  Driver:            rt2500pci
  Active:            yes
  HW Address:        00:10:60:27:99:97

  Capabilities:
    Supported:       yes

  Wireless Settings
    Scanning:        yes
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Networks (* = Current Network)
    OrangeE899C2:    Infrastructure Mode, Freq 2.462 MHz, Rate 62 Mb/s, Strength 62%, Encrypted (WPA WPA2)
    NETGEAR17mel:    Infrastructure Mode, Freq 2.437 MHz, Rate 62 Mb/s, Strength 61%, Encrypted (WPA)
    *BeBox:          Infrastructure Mode, Freq 0.000 MHz, Rate 0 Mb/s, Strength 71%, Hidden

  IP Settings:
    IP Address:      0.0.0.0
    Subnet Mask:     0.0.0.0
    Broadcast:       0.0.0.0
    Gateway:         0.0.0.0
    Primary DNS:     0.0.0.0
    Secondary DNS:   0.0.0.0


---

### Post by Kisil on 2007-11-16
I had some trouble with my hidden network for a while.  I followed the directions and blacklisted the old driver, but still had to manually enable my network on login.  I eventually fixed the problem by adding:

```
pre-up iwconfig wlan0 essid myESSID
pre-up iwconfig wlan0 key  myHexkey
pre-up iwconfig wlan0 ap 00:00:00:00:00:00
pre-up iwconfig wlan0 key open
auto wlan0
```

to /etc/network/interfaces.  

With the SSID hidden, I had to manually specify my access point (except using my actual access point, not zeros), as the essid alone didn't get the job done.  With these lines, everything works.  For an unsecured network, skip the lines about the key.

I hope that helps!

(And yes, I know WEP and hidden networks both aren't secure.  It's not my network.)

---

### Post by sadffffff on 2007-11-26
im also using the usb wifi dwl-g122 rev B1. Like others, the network manager applet shows the wireless networks in range and when I select mine, it fails to connect. my network is completely unsecured. and its a fresh install of 7.10.

After reading through this thread im not really sure what, if there even is one, is the right solution for this problem. I'm not experienced with linux at all.

so any updates on this problem? suggestions? links?

edit: is the ndiswrapper sticky "HOWTO: RT2500, etc. wireless cards" my only option? suppose i could also install an older version of ubuntu, i hear the last one worked?

---

### Post by Kisil on 2007-11-26
For $0.02, I think it's a lot easier to install ndiswrapper than to drop back to 7.04, especially if you want no-hassle desktop effects.  WIth an unsecured network, several of the approaches on this page should work - it's not always either-or.  That said, I did have to blacklist the default driver, as discussed above.

---

### Post by sadffffff on 2007-11-26
tried the ndiswrapper howto. the only change I made to the instructions was that i used the driver from d-link for my dwl-g122 (which strangely  has files called 'netprism' rather than ralink, like I would expect).

I blacklisted all the others listed since i wasnt sure.

after installing it with ndiswrapper and then doing "sudo ndiswrapper -l" i only got the following output:

netprism : driver installed

without any device present info. so did the driver not take to the hardware?

after the rest of the instructions, I rebooted, and found that my wireless interface wlan0 is now gone from network manager.

Edit: hang on, I think I'm dumb. Trying something.
Edit#2: Yep, after looking again at how odd 'netprism' seemed when I knew mine was ralink, I realized that I foolishly downloaded the wrong windows driver. Got the right one and I'm on the network! Thanks! Hope to see the next version with this 'bug' squashed

---

