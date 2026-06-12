---
title: "No sound, help needed. =&lt;"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by Blivia on 2010-11-17
Hello Ubuntu forums, I'm a newbie to Linux in general, but everything so far seems to be fine. Every problem I've had, has been answered in full by a few google searches, but now I've come across a more.. Simple problem that I have not been able to find an solution for. Least it seams that way.

I have no sound, well that's not true. I have very little sound- In order for me to hear anything I have to turn my surround sound up All the way. I've tried something suggested, and installed a sound server program which let me further amp up my sound, it helped a little but the sound got really choppy, and ugly.

I made many attempts not really knowing what I was doing, and I managed to break Linux, so I re-did everything today, and decided it would be best to turn to the community for an answer more specific to my problem. This is a fresh new install, with only a couple of things added, and touched on.

My computer is a Sony VGC-RB60G.

In this System Information tool, it says my sound is:
"Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)"
Also I know my card is a SigmaTel but I'm not sure what model. It's onboard, and Sony doesn't give enough information on their hardware.

If you need any more information, just give me the command for the terminal, I'll execute, and give you the output, and such.

As a side note, my volume is not muted, and I configured the hardware as it should be. When I run the command alsamixer everything is turned all the way up. Your help is much appreciated, and thanks for your time. ^.^!

Edit: Also further information about the card, it appears to be: SigmaTel CXD9872RD/K

I hope this helps some. Again, if any more detail is required, just ask.

---

### Post by Blivia on 2010-11-18
I just realized I forgot to state that I'm using Ubuntu 10.10, also I've found out a little more about my video card from somewhere or another. In my sound settings it says my card is a: "STAC92xx Analog"

I hope to get sound up, and running soon. It's one of the couple of things holding me back for using Ubuntu for everyday use. >.<

---

### Post by Blivia on 2010-11-18
I posted a new topic on the forum sometime yesterday involving my sound issues- I'm pretty sure it's in the proper forum (Video, and multimedia.) and it's gotten around 73 views.. But no posts. So I hope it's alright that I make a post here, in the beginner forum (Where I belong. XD) to hopefully attract some attention to my problem.. I'd really like to start using Ubuntu more often for average use to learn the OS, but I can't live without my music. T.T


So, if you find it in you, please take a look at my other thread, and again thank you for the time, and consideration.

[http://ubuntuforums.org/showthread.php?t=1624527](http://ubuntuforums.org/showthread.php?t=1624527)


(As a note, if I somehow missed it in the rules, and this is against forum rules please give a fair warning before you delete it so I know later that it's not permitted. ^.^!)

---

### Post by Hippytaff on 2010-11-18
> 
Hello Ubuntu forums, I'm a newbie to Linux in general, but everything so  far seems to be fine. Every problem I've had, has been answered in full  by a few google searches, but now I've come across a more.. Simple  problem that I have not been able to find an solution for. Least it  seams that way.

I have no sound, well that's not true. I have very little sound- In  order for me to hear anything I have to turn my surround sound up All  the way. I've tried something suggested, and installed a sound server  program which let me further amp up my sound, it helped a little but the  sound got really choppy, and ugly.

I made many attempts not really knowing what I was doing, and I managed  to break Linux, so I re-did everything today, and decided it would be  best to turn to the community for an answer more specific to my problem.  This is a fresh new install, with only a couple of things added, and  touched on.

My computer is a Sony VGC-RB60G.

In this System Information tool, it says my sound is:
"Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)"
Also I know my card is a SigmaTel but I'm not sure what model. It's  onboard, and Sony doesn't give enough information on their hardware.

If you need any more information, just give me the command for the terminal, I'll execute, and give you the output, and such.

As a side note, my volume is not muted, and I configured the hardware as  it should be. When I run the command alsamixer everything is turned all  the way up. Your help is much appreciated, and thanks for your time.  ^.^!

Edit: Also further information about the card, it appears to be: SigmaTel CXD9872RD/K

I hope this helps some. Again, if any more detail is required, just ask.


Posting it here for ease of use :-)

so from what I can gather it works, but it's very quiet?

---

### Post by Blivia on 2010-11-18
Yeah, so quiet that in order to really hear it, I have to turn everything almost all the way up (Including my surround sound, and system sound settings in Ubuntu.) It appears to be detecting my card, but I'm a newbie, so I'm not really sure.

Also, I can manage to get it a little higher, but it's distorted, and sounds horrible if I do. I really do appreciate your time. ^_^

---

### Post by Hippytaff on 2010-11-18
so....does everything work ok in any other os? like windows?

just trying to rule out a non-ubuntu issue like hardware, bad connections etc

---

### Post by Blivia on 2010-11-18
I'm actually on Windows right now, sound works like a champ (For an onboard chip made by Sony.. >.>, It still requires Sony specific drivers.)

This is a dual boot system, so if something goes wrong I can always switch over. I'm pretty sure this is a compatibility issue of some sort, and I really hope it's fixable.

---

### Post by Hippytaff on 2010-11-18
Might be a driver issue
in ubuntu what is the output of
```

lspci

```once we know the chipset of your audio device we can try to investigate what is going on...also might be worth checking the ubuntu studio part of the forums....they deal with audio problems all the time :-)

Edit -> I live music...I know your potential pain :-)

---

### Post by Blivia on 2010-11-18
~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
02:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)
05:01.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
05:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)



I'm not exactly sure how to paste text as Code.. Or is that the quote function altered? =o

---

### Post by Hippytaff on 2010-11-18
You can either use the # icon or type - [code] text to be wrapped [/code ]

but as to your main reason for posting here...I am stuck...to be honest :-)

---

### Post by Blivia on 2010-11-18
lol, Thanks a lot for your help though, maybe someone else can figure out the cause of my problem with the information given. Hopefully a much more advanced Ubuntu user, or possibly even programmer will take notice.


Looks like I'm stuck without sound for now, at least I can still get eye-candy effects.. XD

---

### Post by Hippytaff on 2010-11-18
> **Blivia said:**
> lol, Thanks a lot for your help though, maybe someone else can figure out the cause of my problem with the information given. Hopefully a much more advanced Ubuntu user, or possibly even programmer will take notice.


Looks like I'm stuck without sound for now, at least I can still get eye-candy effects.. XD

What confuses me is that you can hear sound...so the hardware works ok and the driver for the hardware works ok!?

---

### Post by Blivia on 2010-11-18
Yep, I if I turn everything up to max (Including Alsamixer, my surround sound, and other volume switches I can find.) I can hear sound as if it were on medium low. I almost died of a heart attack when I had to log back into XP.. That soft login sound can be so very loud. O.O

---

### Post by jtarin on 2010-11-18
I see you've tried Alsa Mixer......did you adjust all volumes to at least 80% or more?

---

### Post by Blivia on 2010-11-18
Thanks for the source jtarin, I actually decided to check the link before I made a reply. There are a few arguments I didn't know about before. I'll post back with a result if anything has changed.


Edit: That didn't solve my problem at all, but thanks for the attempt.

---

### Post by Peterfc on 2010-11-18
Hi Blivia

I don't know if this will help go to System Preferences Sound. Now go to Sound Hardware and check that where is says " choose a device to configure. " Sometimes if i have a sound issue and there is nothing where it says Choose a device to configure there is nothing listed. If i reboot sometime all then is ok. I do not not why but it works for me.

---

### Post by Blivia on 2010-11-18
I've seen that screen more times then I've wanted to, and I've messed with every possible option- Even your inspiration caused me to fidget with it a little, but I still get almost no sound. The time you took is much appreciated though- Somehow I don't think this is a simple issue as that. But I really hope it is! >.>, Sure, then I'll feel dumb, but I'll feel dumb with SOUND. >=D

Also yes I did, everything is maxed out. But if I put PCM up to 100, I don't get that much of a boost, and the sound is slightly distorted. (I can turn my surround sound up to max, and it would sound as if it were on medium/low. On medium I hear nothing.)

---

### Post by DogMatix on 2010-11-18
Here is a thread which mentions SigmaTel CXD9872RD/K (5th post down) which may be worth a read: 

[http://ubuntuforums.org/archive/index.php/t-584178.html](http://ubuntuforums.org/archive/index.php/t-584178.html)

Sorry I can't offer any more help.

---

### Post by Peterfc on 2010-11-18
Hi Blivia

Don't give up there is an answer. I am going now to work but i will look when i can.

Good luck

---

### Post by JustinR on 2010-11-18
Hi,

Can you go to Applications > Accessories > Terminal and type this:
```

sudo apt-get install gnome-alsamixer

```

Then go to Sound and Video > Gnome ALSA Mixer, then raise 'Master' and 'PCM' Up to max and then exit it, and adjust your volume from the sound applet.

---

### Post by Blivia on 2010-11-18
Thanks for the replies, and support.

DogMatix, I looked over that site pretty closely. I'm sure I've been to that exact page before, and it didn't offer much help- I think that's because the topic is very outdated. It dates back to 2007, and a much older version of Ubuntu.

Edit: JustinR, The funny thing is I already have that downloaded. It's one of the things I downloaded during troubleshooting. 

```
sudo apt-get install gnome-alsamixer
[sudo] password for blivia: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-alsamixer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
Is my terminal output,

---

### Post by jtarin on 2010-11-18
Not on my Linux box at the moment, but try going into System>Control Panel and look for sound applet and open it up. I remember more than once my sound became muted or minimized for no apparent reason and adjusting the level or checking/unchecking mute did the trick.

---

### Post by Blivia on 2010-11-18
That didn't seem to make a difference either- I've even adjusted the volume while the sound is playing to listen to the difference. Something odd I might note though- If I change the headphone jack setting in that Sound menu, it my sound actually becomes quieter. I'm not sure if this will be of any help in my case, but it further leads me to believe it's some driver issue. I am using a Sony computer, and finding information out about my Motherboard alone is a task... Seriously, why can't Sony just leave intel hardware alone? T.T

---

### Post by DogMatix on 2010-11-18
Seems you are not alone here is a Launchpad bug report (2008-2010) featuring SigmaTel CXD9872RD/K

> UBUNTU 9.1 with latest updates. Sony VAIO VGC RB57G SigmaTel CXD9872RD/K

LOW SOUND, TRIED EVERYTHING I COULD FIND. I believe it is STILL A BUG? Please confirm!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/244754](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/244754)

Seems to be a predominently Sony issue

---

### Post by Blivia on 2010-11-18
That's what I was afraid of, I was wondering if there was some work-around, or something I could try to fix the issue. That's why I came to the forums, and made my own case more specific to my problem, instead of trying to relate to other people's problem.

Trust me, I've done a whole TON of research on my problem, and it's just been frustrating- Usually I don't join a forum specifically to post my own problems, but find a way to solve them myself. And if I couldn't solve it, usually I just drop it and turn somewhere else, but I really want to start using Ubuntu more often. It's an awesome OS, surrounded by a usually equally awesome community. This doesn't mean I'll be ditching Windows of course, that was never my intention upon install, but I'd love to start using it more, and getting to know this Meerkat. ^_^

---

### Post by DogMatix on 2010-11-18
Just to settle a question.

Have you tried a live CD/USB of a different distro. to see if the issue persists i.e. Redhat's Fedora?

Apologies if you're way ahead of me on this.

---

### Post by Blivia on 2010-11-18
No I haven't, I actually have the Mint ISO, but I'm not going to burn it until I'm sure I'm going to install it. I've got a limited supply of CDs laying around, and I don't have a flash drive. My sound works when I run Ubuntu in a virtual machine.. And I came up with the crazy idea of maybe trying to emulate my sound driver... But I don't think that's even possible. XD

---

### Post by DogMatix on 2010-11-18
> **Blivia said:**
> My sound works when I run Ubuntu in a virtual machine.

That's intriguing! How about a [WUBI]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer") install of Ubuntu?

A bit more reading here >> [link]("http://www.seandeasy.com/installing-ubuntu-the-easy-way/")

---

### Post by Blivia on 2010-11-18
I actually considered Wubi! But I'm not sure how well it'd co-exist with Windows XP, and my current needs. My original idea was to use Linux as a backup OS, to store all of my un-replaceable data on the Linux drive every week or so, and if Windows ever breaks, I could possibly use Ubuntu to fix it.

With Wubi, wouldn't Linux be broken if Windows breaks? That sounds like it could be a lose-lose situation to me. XD, But I haven't looked enough to know if that's true.

Anyway, for something a little more on-topic, I did a little more trouble shooting. I streamed a song from Youtube, and proceeded to plug my sound wire into the six various ports in the back to see if I got any increase in sound, the result was sound only comes out of the middle speaker port. I don't know if I mentioned this, but when I change my Headphone volume, it also effects my surround sound volume by half. (All the way down reduces what little volume I have, by half.)

Thanks a lot for your ideas, and suggestions though. Your time is much appreciated.

---

### Post by Blivia on 2010-11-19
Sorry for the double post in advance.


Seeing as no one can offer me a solution, is it possible to install the drivers Sony provides onto Linux using Wine, or some other method? Has this trick ever worked for getting hardware to work properly in the past? 

Again, thanks for your time. I appreciate what people have already contributed to the topic.

---

### Post by Hippytaff on 2010-11-19
You can use Ndiswrapper to install windows XP drivers, should work for audio drivers

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Blivia on 2010-11-19
Awesome! I love you! XD, I'm going to have to jump over to Linux and try this.

Hey... Are you always lurking the newbie forums? >=D

---

### Post by Hippytaff on 2010-11-19
Usually pop in a few times a day...my life is that exciting :-)

Off for beers tonight though...good luck with Ndiswrapper (there is a gui version called gtkndis or something - you might have to google it, I can't remember what it's called and gotta go for now :-)

---

### Post by cariboo on 2010-11-19
I've merged your three threads. If in the future you post in the wrong section, use the report button, to ask us to move it to the correct sub-forum

---

### Post by Blivia on 2010-11-19
Thanks Cariboo, I actually didn't realize it was in the wrong forum. ^_^!

Also Taff, I looked into the situation, and heard of someone else with the exact same issue. But I'm not sure if this fix will break Linux or not, so I'm going to need to try it Via my virtual machine. Do you (Or anyone else who has some knowledge in this subject.) have any suggestions on how to go about doing this? ^_^

---

### Post by Jeremyray on 2011-03-04
Hey Did you ever figure out the issue? I am having the same problem with the same vcg-rb60g. I have some sound, I can hear it on my speakers when I have it cranked all the way up, but just barely. wtf. [email]jeremyr.mcclellan@gmail.com[/email] if you figured it out.

---

