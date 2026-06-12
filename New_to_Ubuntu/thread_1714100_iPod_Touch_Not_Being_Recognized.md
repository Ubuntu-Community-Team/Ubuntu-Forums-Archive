---
title: "iPod Touch Not Being Recognized"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by hoosier1104 on 2011-03-24
I bought a iPod Touch and Rhythmbox/Banshee does not recognize that it is plugged in.  I have the gtk iPod Manager installed but the mount area cannot be created.  Any help would be greatly appreciated.  Please no smart *** comments.

---

### Post by goldaryn on 2011-03-26
So far, I can't get my iPod Touch working in Linux. I admit that I haven't tried that hard, however.

I got my Touch to work by installing Windows into a [VirtualBox]("www.virtualbox.org") virtual machine and then using iTunes.

This sounds like a pain in the behind but it isn't really all that bad. It's a shame to have to use Windows, but hey ho. 

Advice:

1) You need to use the version of VirtualBox from the VirtualBox website: [www.virtualbox.org]("www.virtualbox.org"). The open-source version in Ubuntu Software Centre seems to lack USB support :-(

2) If you do this, do not under any circumstances attempt to upgrade the firmware on your iPod! It will go crazy and you will have to reinstall native Windows to fix it (oops).

I might write a tutorial if anyone is interested.

---

### Post by hoosier1104 on 2011-03-26
I upgraded to 10.10 and now it was with Banshee.  Go figure.

---

### Post by hoosier1104 on 2011-03-30
It is now giving me the following error message:
 DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
 
 How do I go about fixing it?

---

### Post by dniMretsaM on 2011-03-31
> **hoosier1104 said:**
> It is now giving me the following error message:
 DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
 
 How do I go about fixing it?

I have this exact problem. I have an iPod Touch 2g running on 4.2.1 and jailbroken with Greenpois0n RC6 (or RC6.1, can't remember). I can't really use virtualbox or anything like that because my system is just too slow. Any help would be appreciated!

---

### Post by spillage2 on 2011-03-31
Hi,

My boys ipod touch 1g (i think) ran fine until he needed to restore it.

10.04 shows it on desktop and rhythembox shows the ipod icon. But I cant drag and drop music onto it anymore.

gtkpod will not allow me to create a directory structure..

You gotta love apple...

---

### Post by wolfen69 on 2011-03-31
For me, I did:
```
sudo apt-get install ipheth-utils
```
then
```
mkdir /tmp/packages && cd /tmp/packages
```
then
```
wget -nc -c http://archive.ubuntu.com/ubuntu/pool/main/{libi/libimobiledevice/libimobiledevice0_0.9.7-1ubuntu1,libm/libmtp/libmtp-dev_1.0.2-1ubuntu1,libm/libmtp/libmtp8_1.0.2-1ubuntu1,libu/libusb/libusb-0.1-4_0.1.12-14ubuntu0.2,libu/libusb/libusb-dev_0.1.12-14ubuntu0.2}_`dpkg --print-architecture`.deb
```
then
```
sudo dpkg --install *.deb
```
then
```
sudo apt-get hold libmtp8 libmtp-dev libusb-dev libusb-0.1-4
```
My ipod touch now works in 10.10 with gtkpod.

But with the release of 11.04 soon, these devices should work out of the box.

---

### Post by spillage2 on 2011-03-31
@ wolfen69

```
sudo apt-get hold libmtp8 libmtp-dev libusb-dev libusb-0.1-4

```

saying invalid operation hold



spill

---

### Post by wolfen69 on 2011-03-31
I'm just going by what is [here.]("https://help.ubuntu.com/community/PortableDevices/iPhone")
Maybe there is a typo.

---

### Post by dniMretsaM on 2011-04-01
Same here. When I copy it from the site you linked to, I get a command not found. Weird. Could it have something to do with FW version because I could downgrade to 4.0, 4.0.1, or 4.1 if I need to (assuming that's possible on Linux...).

---

### Post by hoosier1104 on 2011-04-04
I tried the above mentioned options with no success.  This is the error I get when I plug it in.

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

---

### Post by dniMretsaM on 2011-04-07
Ok, I figured this out. In the repositories, the latest version of libimobiledevice is 1.0.1-1 or something but for iOS 4.2+, you need at least version 1.0.4 (the current version is 1.0.6). So you need to add a PPA to get the latest. If you want to look at the PPA site, go [here]("https://launchpad.net/%7Epmcenery/+archive/ppa"). Open up terminal and run:
```
sudo add-apt-repository ppa:pmcenery/ppa
```then
```
sudo apt-get update
```Now open Synaptic Package Manager and click Mark All Upgrades then click Apply. If you get an error while installing libimobiledevice1, you may need to uninstall libimobiledevice0.

---

### Post by dirt912 on 2011-04-13
I'm using maverick meerkat on a macbook 2.1.  I've tried all the suggestions in this thread and I'm still getting the following error message:

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

---

### Post by Rasa1111 on 2011-04-13
I just got a friends ipod touch working, no problem. 

 It also was not able to mount,
But I simply followed these instructions...
and once the last command was finished, and terminal closed...

ipod touch opened right up, perfectly.
Using Ubuntu 10.10

Instructions~ 3 simple commands.
 [http://www.webupd8.org/2010/12/get-ios4-mountsync-working-in-ubuntu.html](http://www.webupd8.org/2010/12/get-ios4-mountsync-working-in-ubuntu.html)

---

### Post by hoosier1104 on 2011-04-13
Yeah I tried that and I am still getting the same error message.

---

### Post by Rasa1111 on 2011-04-13
> **hoosier1104 said:**
> Yeah I tried that and I am still getting the same error message.

Hmm...

Im sorry. :???:

 I really didn't expect it to work properly myself..
But was pleasantly surprised when it started right up afterwards. 
(my friend even more so) lol

What about GTKPod? Have you tried that? 
(I dont know much about "i-devices" sorry.)

 I installed that for him after I got the ipod mounted,
and it seems to be nice little tool that works quite well.

Though Im unsure if it will help in your situation. 

 The friend I just did this for..
Had called the store he bought the ipod touch from, and told the lady on the phone that he could not mount it..
She told him.. _'I'm sorry, you can only use windows 7"_lol
:lol:
:rolleyes:

---

### Post by dirt912 on 2011-04-14
Same here.  i tried your suggestion, but just got the same error message.  Thanks anyhow!

---

### Post by Cpierce on 2011-04-14
Try this :

[http://ubuntuforums.org/showthread.php?t=1638433&page=2](http://ubuntuforums.org/showthread.php?t=1638433&page=2)

---

### Post by dirt912 on 2011-04-15
I tried it, but the result is still the same error message.  :(

Also, now that i've been messing around with apt-get  I'm not able to download programs from the ubuntu software center.

whenever i try i get the attached message

[IMG]file:///home/ben/Desktop/Screenshot.png[/IMG]

---

### Post by dniMretsaM on 2011-04-15
> **dirt912 said:**
> I tried it, but the result is still the same error message.  :(

Also, now that i've been messing around with apt-get  I'm not able to download programs from the ubuntu software center.

whenever i try i get the attached message

[IMG]file:///home/ben/Desktop/Screenshot.png[/IMG]


Try opening up Terminal and running ```
sudo killall synaptic
```
This should end the synaptic process and will allow you to install stuff from the Software Center. And for everybody else, make sure that libimobiledevice0 is NOT installed while trying to install libimobiledevice1 from the PPA a posted earlier.

---

### Post by dirt912 on 2011-04-15
I tried the terminal command:

sudo killall synaptic

but it just gives me this responce:

synaptic: no process found

Then when I tried to download from the software center it still tells me the same error message as before, but under details it says, "The package indexes are currently changed by apt-get."

Any idea what could be going on?

---

### Post by dniMretsaM on 2011-04-15
Try ```
sudo killall update-manager
```

If that doesn't work, restart the computer. You might also try turning off automatic updates.

---

### Post by dirt912 on 2011-04-16
Thanks!  that seems to have taken care of my directory problem.  :)

Now does anyone have any new ideas about the ipod problem?

---

### Post by dniMretsaM on 2011-04-16
What error are you getting?

---

### Post by hoosier1104 on 2011-04-16
Dbus message error is what I am still getting.  The same as the one I posted earlier.

---

### Post by dniMretsaM on 2011-04-16
Did you remove libimobiledevice0 before trying the steps I mentioned earlier?

---

### Post by earthpigg on 2011-04-16
I skimmed the thread, and one ***long-term*** approach doesn't seem to have been mentioned:

Look into methods to cease software/firmware updates to the device.

Wait for the open source hackers to work around Apple's shenanigans as of the last time you *did* get an update, and thus your device will eventually work again.

Continue to not update the device.



This would be implemented *in addition* to the short-term solutions outlined in this thread and other threads like it that pop up once a month.

It is a cycle. Don't be surprised if the methods outlined in last month's version of this thread no longer work.

If your iOS device is receiving updates, one *will* eventually break all currently existing non-iTunes & non-Steve-approved support. 

That is by design, not accident, and that is the entire point of many of Apple's so-called security updates... updating ***Apple***'s security & control. Over you.

---

### Post by dniMretsaM on 2011-04-16
> **earthpigg said:**
> I skimmed the thread, and one ***long-term*** approach doesn't seem to have been mentioned:

Look into methods to cease software/firmware updates to the device.

Wait for the open source hackers to work around Apple's shenanigans as of the last time you *did* get an update, and thus your device will eventually work again.

Continue to not update the device.



This would be implemented *in addition* to the short-term solutions outlined in this thread and other threads like it that pop up once a month.

It is a cycle. Don't be surprised if the methods outlined in last month's version of this thread no longer work.

If your iOS device is receiving updates, one *will* eventually break all currently existing non-iTunes & non-Steve-approved support. 

That is by design, not accident, and that is the entire point of many of Apple's so-called security updates... updating ***Apple***'s security & control. Over you.

I didn't even know it was possible to update an iDevice in Ubuntu. Anyway, depending on his device (2g or lower), it WILL be supported because it the max FW (for 2g) is 4.2.1 and that and all FWs below that (afaik) are supported by libimobiledevice. I believe there are only 2 devices that are supported that could be at a higher FW than is supported: iPhone 3gs and iPod Touch 3g. So, since he bought a Touch, as long as it's not a 3g, your statements do not really apply. Now obviously, it's good advice. I highly recommend not upgrading until you know what you're REALLY getting into. I'm just saying it's not the most applicable in this situation.

---

### Post by earthpigg on 2011-04-16
I type the above about once every two months.

This time, though, I have a blog. Now I can just link to [that post]("http://ctmason.wordpress.com/2011/04/16/ios-ipod-ipad-devices-on-linux-long-term-non-jailbreaking-solution/") (based on my above forum post) every 2 months without having to dig through forum archives to find the version of this thread from previous months. :)

---

### Post by earthpigg on 2011-04-16
> I didn't even know it was possible to update an iDevice in Ubuntu.

was referring to either over the air updates, or ones that happen when plugged into iTunes.

but, ya, if someone gave me an iOS device for free I would 'sudo apt-get upgrade', plug it in, and see if it worked. If it didn't work immediately, I'd toss it in a drawer (turned off) and check again once a month. While also looking into possible methods (short of jailbreaking) to disable any potential forced over the air updates.

:)

---

### Post by robsoles on 2011-04-16
> **earthpigg said:**
> I skimmed the thread, and one ***long-term*** approach doesn't seem to have been mentioned:

Look into methods to cease software/firmware updates to the device.

Wait for the open source hackers to work around Apple's shenanigans as of the last time you *did* get an update, and thus your device will eventually work again.

Continue to not update the device.



This would be implemented *in addition* to the short-term solutions outlined in this thread and other threads like it that pop up once a month.

It is a cycle. Don't be surprised if the methods outlined in last month's version of this thread no longer work.

If your iOS device is receiving updates, one *will* eventually break all currently existing non-iTunes & non-Steve-approved support. 

That is by design, not accident, and that is the entire point of many of Apple's so-called security updates... updating ***Apple***'s security & control. Over you.

+10,000,000!! Much clearer and much much more helpful than I've ever managed about this topic!!

> **dniMretsaM said:**
> I didn't even know it was possible to update an iDevice in Ubuntu. Anyway, depending on his device (2g or lower), it WILL be supported because it the max FW (for 2g) is 4.2.1 and that and all FWs below that (afaik) are supported by libimobiledevice. I believe there are only 2 devices that are supported that could be at a higher FW than is supported: iPhone 3gs and iPod Touch 3g. So, since he bought a Touch, as long as it's not a 3g, your statements do not really apply. Now obviously, it's good advice. I highly recommend not upgrading until you know what you're REALLY getting into. I'm just saying it's not the most applicable in this situation.

I'm sure earthpigg is talking about updates that the 'iDevice' itself manages, either solely via wifi in the case of an ipod, or via #g (#=2|3|4 whatever) or wifi in iphones. (Oh! iTunes, of course they can each update via tether!)

Any of Apple's devices which take updates can be updated, by Apple developers, to block previous methods that 3rd party developers had managed to come up with.

earthpigg's statements all seem pretty darn applicable to me :roll:

---

### Post by earthpigg on 2011-04-16
the permanent version of that post i currently have up is a bit long and drawn out, due to the fog of war. my approach is drawn from my rudimentary understanding of [wargaming theory]("http://www.mca-marines.org/gazette/tactical-decision-games"), and not from ever owning an iPhone.

so, question:

> I have no idea if disabling updates is currently possible without jailbreaking an iOS device (...snip...) Only its system update software needs to be turned off, disabled, or have its knee caps busted with a sledge hammer. Ideally, the (...redacted...) at the Apple Store will not be able to tell at a that this was done when casually going through the itemized warranty verification checklist.

If there is already such a method that you anyone is aware of, please share it (...so we can get the word out...)

---

### Post by robsoles on 2011-04-16
To the best of my knowledge/understanding of Apple's EULA: 

It is against their EULA to stop their updates or work on methods by which to do anything remotely resembling tethering their devices with 3rd party software.

The only way, short of jailbreaking, that I can think of to stop updates (where Apple try to maintain a position capable of 'shoving it down your throat') is to isolate the device. Can't be done to a phone, if you want to keep that functionality, but it can be done to an ipod and it can even be done to itunes - don't let the ipod on wifi and don't let itunes access the internet.

I wouldn't be surprised if someone can find the part of the EULA wherein you must connect to itunes or wifi semi-regularly to receive updates if your device isn't a phone!

---

### Post by dniMretsaM on 2011-04-17
As far as I know, you can't block updates the way you do on a Wii. You just simply don't click the Update button. For me, I don't have a problem with this because I'm at the max FW for my 2g.

@robsoles: I'm not sure I understand your previous post. No updates that the iDevice itself manages will do anything to the ability to connect to a non-iTunes program.

---

### Post by hoosier1104 on 2011-04-23
Ok. I went back to 10.04 LTS hoping that it would fix the problem.  No dice.  Tried everything mentioned in this thread.  The libimobile01 will not install completely.  Anyone have any ideas on a fix action.

---

### Post by dniMretsaM on 2011-04-24
There is no such thing as libimobiledevice01. It's either 0 or 1. When you try to install libimobiledevice1 in Synaptic, what error is it giving you?

---

