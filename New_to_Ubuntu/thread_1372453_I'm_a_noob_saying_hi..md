---
title: "I'm a noob saying hi."
date: 2010-01-04
forum: New to Ubuntu
---

### Post by jermza on 2010-01-04
I'm completely new to this Ubuntu thing.  Right now, I'm using Windows XP, but plan on migrating across to Ubuntu as soon as I can.

The nutshell:

- I'm an artist who works digitally, using Photoshop and a Wacom tablet.  That's the biggest hindrance: Photoshop and Wacom.

- I almost went for a Mac, but then was talked into Ubuntu.  I googled it for days and have decided that I want to convert.

- Most of what I use is open source.  (Gmail, Google Docs, Audacity, Songbird, etc)  I recently installed GIMP, and it seems decent enough for my purposes.  CMYK is a problem though, but there seems to be a plugin where files can be saved using a specific CMYK profile.  If so, then I'm happy.

At the moment, I'm testing GIMP with my tablet, but having issues that I can't seem to solve.  The cursor and hotspot simply won't align, no matter what settings I change.  I don't use a standard mouse, but rather the Wacom mouse (and stylus).  If I can solve this, then I'm on my way to Ubuntu...

---

### Post by steveneddy on 2010-01-04
Maybe this will help:

[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

### Post by jermza on 2010-01-04
Thanks, but that doesn't really help.  Take a look at the attachment.  The mouse pointer and paintbrush pointer are not aligned, and I don't know how to configure that.

---

### Post by staf0048 on 2010-01-04
Well, not knowing exactly what you're trying to do in Photoshop, have you tried Inkscape or Scribus?  Both are Open Source products available through Synaptic...you may still have troubles with your mouse though - I'm not sure how to fix that.

---

### Post by slakkie on 2010-01-04
Looks like it is inverted. Do you have anything which says your mouse/wacom is inverted?

Maybe have a look here: [http://www.thinkwiki.org/wiki/Wacom_Serial_Tablet_PC_Stylus](http://www.thinkwiki.org/wiki/Wacom_Serial_Tablet_PC_Stylus) and look for xrandr rotation.

You could also try these links:
[http://en.opensuse.org/Wacom_USB_tablet_howto](http://en.opensuse.org/Wacom_USB_tablet_howto)
[http://www.gimptalk.com/forum/viewtopic.php?t=17992](http://www.gimptalk.com/forum/viewtopic.php?t=17992)
[http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom](http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom)

Roog google: gimp wacom debian ubuntu . You can leave out debian if you want, but Ubuntu is based on Debian - it can be handy :).

---

### Post by jermza on 2010-01-04
> **slakkie said:**
> Looks like it is inverted. Do you have anything which says your mouse/wacom is inverted?


Nothing says it's inverted.  I don't think it is, anyway.  Rather, the two pointers should be aligned on top of each other.  For some reason, they are apart, randomly.

Is this a GIMP problem?  I suspect it is, because Photoshop is fine.

---

### Post by staf0048 on 2010-01-04
Just thought I'd throw this out there... is there a way to calibrate the mouse?  Does it ship with software for that purpose?

---

### Post by steveneddy on 2010-01-04
> **jermza said:**
> Thanks, but that doesn't really help.  Take a look at the attachment.  The mouse pointer and paintbrush pointer are not aligned, and I don't know how to configure that.

<snip>

there was a link on top with instructions on how to align mouse and pointer here:

[https://help.ubuntu.com/community/Wacom#Extended](https://help.ubuntu.com/community/Wacom#Extended)

Did you install the wacom xorg driver suggested by the website I linked to?

```
sudo apt-get install xserver-xorg-input-wacom wacom-tools
```



<snip>



Setting up a Wacom tablet is sometimes like trying to set up another monitor and it will probably take some work, but when you are finished it will work all the time, every time. 

<snip>

EDIT:

Also what version of Ubuntu are you using?

The next post has more info for you and some links that hopefully will send you in the right direction.

---

### Post by steveneddy on 2010-01-04
From this Google search:

[http://www.google.com/search?hl=en&source=hp&q=wacom+ubuntu&aq=f&oq=&aqi=g5](http://www.google.com/search?hl=en&source=hp&q=wacom+ubuntu&aq=f&oq=&aqi=g5)

comes these links:

[http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)

[http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151)

That may get you going in the right direction and will give you a couple of forums to post to get get help from others with the Wacom tablet.

---

### Post by jermza on 2010-01-04
> Also what version of Ubuntu are you using?
I'm not using Ubuntu yet.  I'm still using Windows XP, but am trying to get myself acquainted to Gimp (and make sure it's working smoothly) before switching over. 

Which is why I don't think this will help:

> Did you install the wacom xorg driver suggested by the website I linked to?
Because I'm still on Windows.  What's worrying me is that if my Wacom and GIMP can't play nicely now, then my confidence for switching over becomes a little diluted.  Is there a way I can test my Wacom and GIMP, on Ubuntu, without ruining my Windows installation?  Perhaps I should test it while on Ubuntu.

BTW, I really do appreciate your tips and fast replies.  I'm liking "the community" already (and would like to break the stereotype that digital artists must stick to Mac / Windows).

---

### Post by adam814 on 2010-01-04
Try it with the LiveCD?  You might have to install some packages in the LiveCD environment, but as long as you have enough RAM you should be able to do that without any trouble.  And since it is a "real" ubuntu environment it would give you a better idea of how things will work in Ubuntu than running the apps you would in Ubuntu in Windows.

Even if you do install Ubuntu to the hard drive it's not like you can't keep your Windows too.  I dual boot Karmic and Vista on my laptop.  For that matter if you really wanted you could get the Mac and triple-boot assuming you had enough hard disk space.

---

### Post by jermza on 2010-01-04
How would I create a dual boot?  Is it tricky?

---

### Post by J V on 2010-01-04
no, backup your data first just in case, then you can resize the windows partition and install linux in the remaining space.

Should take 10 minutes on your first try :)

---

### Post by candtalan on 2010-01-04
> **jermza said:**
> How would I create a dual boot?  Is it tricky?

A better and safer method at this stage might be to 

1) use a live CD to test out your hardware compatibilty - sound, graphics  to be sensible not haywire, wireless if whatever, and if ok then

2) Put the live CD into a running Windows machine cd drive and use the second option to install inside windows as a windows application. Give it a bit of elbow room, say 10GB.

This will not affect your partitions so is as safe as any other install of a windows program. It uses the Windows bootloader so you can easily uninstall it without having linux boot loader and mbr consequences. 

A minor irritation after uninstall of this method (wubi) is that the windows  (ini???) file still retains th eubuntu name an dneeds a small edit to remove it, not that it causes any malfunction.

hth

---

### Post by adam814 on 2010-01-04
There are risks involved in anything.  A backup isn't a bad idea, but the Ubuntu installer can resize your Windows partition and install Ubuntu in separate partitions leaving Windows alone (except with slightly less disk space).  I've never lost anything that way and I've done it on many machines.  You'll end up with a GRUB menu letting you choose between Ubuntu and Windows.

EDIT: You could also use wubi like the previous post, I just don't like having the overhead of running Windows to use Ubuntu.  I've never used wubi, but Vista eats half my RAM just to run, so that doesn't leave so much for Ubuntu apps.

---

### Post by harrisonk on 2010-01-04
[SIZE=4]De fragment your XP drive that is another way to make sure you don't lose any data.

After that It is safer to dual-boot.

Harrisonk
[/SIZE]

---

### Post by gabo.cr on 2010-01-04
> De fragment your XP drive that is another way to make sure you don't lose any data.

After that It is safer to dual-boot.

That should be the very first thing to do.
Dual boot is not as complicated as some people think, but you should read a bit before doing it.

---

### Post by J V on 2010-01-04
> **adam814 said:**
> I just don't like having the overhead of running Windows to use Ubuntu.Wubi never actually starts up windows, instead it loads the system from a virtual partition, basicly a giant file on the NTFS harddrive...

It does recieve overhead from the file system which fragments quite a bit, but its all ubuntu :)

---

### Post by adam814 on 2010-01-04
Ah, ok.  I was confused by the "install/remove like any Windows application" and assumed (wrongly) it would mean "runs like any Windows application under the start menu."  Thanks J V.

---

### Post by steveneddy on 2010-01-04
PLEASE don't use WUBI.

You will get a better experience by using a Virtual Machine like VirtualBox and running Ubuntu on that.

Download V-Box here:

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Take my word that you would be happier with a Virtual machine over Wubi.

If it works well in a VM, THEN partition and install on your HD.

Wubi is only for a short trial period, not to really run it through it's paces.

---

### Post by steveneddy on 2010-01-04
> **gabo.cr said:**
> That should be the very first thing to do.
Dual boot is not as complicated as some people think, but you should read a bit before doing it.

Agreed - do your research first.

Look here:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

You will want to look at the links in my sig. They will help you understand.

---

### Post by jermza on 2010-01-05
Thanks for the tips.  I'm am busy reading the Pocket Guide PDF and am beginning to understand things a little better.

I will definitely try the dual boot or Wubi thing.

Why do you say not to use Wubi?

---

### Post by jermza on 2010-01-05
On a side note, does Ubuntu slow down over time?  There's that theory that Windows slows down gradually, and that Mac doesn't really slow down.

---

### Post by tom.swartz07 on 2010-01-05
> **jermza said:**
> Thanks for the tips.  I'm am busy reading the Pocket Guide PDF and am beginning to understand things a little better.

I will definitely try the dual boot or Wubi thing.

Why do you say not to use Wubi?

Wubi is generally intended for those who want to use ubuntu for very short periods of time on a small timeframe. Because of the way that it's installed, wubi faces serious slowdowns and breaks because of it's integration with Windows. That's not the case with the other methods or even when it's installed on your drive. Def go for virtualbox, or even liveCD. 

Good luck, and happy Ubuntu-ing!! :D

---

### Post by candtalan on 2010-01-05
> **tom.swartz07 said:**
> wubi faces serious slowdowns

I have never noticed any actual loss of speed when using wubi installed Ubuntu, although there said to be some.
> 
and breaks because of it's integration with Windows. 

iirc the vulnerability is from sudden power loss, or of course if the Windows file system gets messed up then you loose Ubuntu also.
> 
That's not the case with the other methods or even when it's installed on your drive. Def go for virtualbox, or even liveCD. 

True, but for real beginners, virtual box is daunting and live CD really is slow for regular use.

---

### Post by tgeer43 on 2010-01-05
> **jermza said:**
> I'm an artist who works digitally, using Photoshop and a Wacom tablet. That's the biggest hindrance: Photoshop and Wacom.
You'll find Gimp to be quite capable. To ease the transition from Photoshop you can install GIMPshop which is available [[COLOR=Blue]_here_[/COLOR]]("http://www.gimpshop.com").
Here is a quote from their website:
> GIMPshop is a modification of the free/open source GNU Image Manipulation Program (GIMP), intended to replicate the feel of Adobe Photoshop. Its primary purpose is to make users of Photoshop feel comfortable using GIMP.Give it a try. I think you will appreciate it. The only real downside to Gimp vs. Photoshop is the huge number of tutorials available for Photoshop compared to those for Gimp.
> **jermza said:**
> On a side note, does Ubuntu slow down over time?  There's that theory that Windows slows down gradually, and that Mac doesn't really slow down.
It's not a theory, it's a fact. The performance of Window _does_ degrade over time, even with regular maintenance. Ubuntu does not suffer from this malady and requires much less housekeeping and maintenance in general.
> CMYK is a problem though, but there seems to be a plugin where files can be saved using a specific CMYK profile. If so, then I'm happy.Well, get ready to be happy then. The plugin you seek can be found at [[COLOR=Blue]_this website_[/COLOR]]("http://cue.yellowmagic.info/softwares/separate-plus/index.html"). There are others but this one seems to be the best.
> BTW, I really do appreciate your tips and fast replies. I'm liking "the community" already.You've just touched on one of the best (of many) good reasons to make the switch to Ubuntu. You'll never find another OS with the support community that Ubuntu has and Ubuntu Forums is the best of the best. The fact that this thread has 25 posts in less than 12 hours pretty much says it all.
Sorry that I can't add to the help that you've already received concerning your input tablet. The bright side is that with some time and patience, almost anything can be made to work under Ubuntu. This is definitely not the case with Windows, or OS X for that matter.

Welcome to the Ubuntu community! I truly believe that in time you'll not only be completely satisfied with Ubuntu but you'll wonder why you didn't make the switch a long time ago. Not to mention all of the money you'll save on software. The retail price for Photoshop CS4 alone is currently $699.00.

tgeer

---

### Post by jermza on 2010-01-05
I'm going to attempt the dual boot option (not Wubi).  I'll first defrag and backup everything onto my second hard drive.

Perhaps GIMP and my Wacom will work better then.  (That is, perhaps they're not playing nicely because I'm using Windows.)

---

### Post by jermza on 2010-01-05
On a side note, I don't understand why more people aren't using Ubuntu.  You guys are great, and the system itself seems brilliant and FREE.

I suppose, like I've always viewed it, Linux seems like a techie thing.  Ubuntu seems very user friendly.

---

### Post by Vaphell on 2010-01-05
well, main reasons are poor gaming (win only titles, hassle to make them work 'natively' in linux), some must-have win only apps people are used to and not willing to switch to something else and poor support from hardware manufacturers. Older hardware usually works out of the box but the newest toys are often pita because some manufactures don't care about linux drivers (especially painful in case of laptops, where you can't just replace parts to linux friendly ones if you happen to have such problem). Also there are times when you need to get your hands dirty using command line and it scares people off (when in fact after some time you start to see benefits of cli because it is extremely powerful tool and is much faster to get the work done than tedious clicking through the gui).
People like what they are used to and fear anything unknown.

---

### Post by jermza on 2010-01-05
I see that Ubuntu comes bundled with media plyers which look slick.

Currently, on Windows, I use VLC.  In your opinions, is VLC even necessary on Ubuntu, where Rythmbox and Totem seem pretty good?

---

### Post by Methuselah on 2010-01-05
> **jermza said:**
> I'm going to attempt the dual boot option (not Wubi).  I'll first defrag and backup everything onto my second hard drive.

Perhaps GIMP and my Wacom will work better then.  (That is, perhaps they're not playing nicely because I'm using Windows.)


Granted, I'm no professional graphic artist but I have used the GIMP with a Wacom bamboo tablet which I still have and nothing seemed off to me.
It understood my pressure so I could create 'brush strokes' by feathering off the ends of my lines as I lifted by hand.

---

### Post by Methuselah on 2010-01-05
> **jermza said:**
> I see that Ubuntu comes bundled with media plyers which look slick.

Currently, on Windows, I use VLC.  In your opinions, is VLC even necessary on Ubuntu, where Rythmbox and Totem seem pretty good?

VLC is an excellent option on Ubuntu...many people still prefer it.

I don't remember if anyone pointed you to this but generally you'll install software using the OS tools rather than downloading things from websits manually.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by zaphod777 on 2010-01-05
I generally just use the built in media player with no issues but I installed all of the media packages. 

Throwing in a live CD and testing GIMP with the tablet should be pretty easy to make sure that everything works out of the box. You won't use it for long but will give you a good idea of what will work hardware wise without too much work.

Things like your tablet and wireless any webcams and printers, etc.

I myself am really happy with Ubuntu and I am an IT PRO who at my last job was the admin for about 500 servers across the US. Most of them were Windows servers but I am running Linux on my laptop. 

MS has more problems so thats what pays the bills. 

I have to say that 9.10 is the best yet and took a whole 5 min to get a look I liked. I'm not a big fan of the default brown and orange. 

Especially now that Chrome is out I am a very happy camper. I can't wait to see what they bring next.

---

### Post by jermza on 2010-01-05
I use Chrome too.  Is it available for Ubuntu?  How does Firefox compare?

---

### Post by zaphod777 on 2010-01-05
> **jermza said:**
> I use Chrome too.  Is it available for Ubuntu?  How does Firefox compare?

It is pretty dang fast in Ubuntu it even imported all of my favorites and passwords from Firefox it really made the transition easy. 

After changing the default theme I have not even used Firefox again. 

I spent a few min searching throw the extensions to get the ones I wanted that were available on Linux. 

Got to love the new Songbird in linux too. 

Also what I love is I am running my CPU on my dual core laptop at 100% since I am converting a video using handbrake downloading torrents and typing this post and my system does not run slow at all.

attached is a screenshot. plus one of my desktop.

---

### Post by steveneddy on 2010-01-05
I use Google Chrome browser and VLC media player for video and Audacious for playing music (because it reminds me of XMMS)

Ubuntu is very fast and I only use Ubuntu as my main OS on everything.

I do use Vista and 7 in VirtualBox.

Just go slow and you will learn as you go. Ask questions and follow instruction and you will do well.

good luck.

---

### Post by tgeer43 on 2010-01-05
> **steveneddy said:**
> I use ...Audacious for playing music (because it reminds me of XMMS)
If that's the case then why aren't you running xmms? (just out of curiosity). Perhaps because Audacity is more feature-rich?

I've been running xmms (not xmms2) on Ubuntu since 8.04 Hardy and absolutely love it's minimalism. Back in my (shudder) Windows days I ran an older version of WinAmp and xmms is virtually indistinguishable.

Xmms compiled and installed easily in every version of Ubuntu from 8.04 to 9.10 32-bit and 64-bit and I've had no real huge issues with compiling plugins for it either. Source tarballs, deb files, and links to everything xmms are here: _[[COLOR=Blue]http://www.xmms.org/[/COLOR]]("http://www.xmms.org/")_

Sure, the project's been virtually dead for years (except for the new repositories) but since it's already perfect, so what? :wink:

tgeer

OP - Sorry for the hijack.

---

### Post by s3a on 2010-01-06
Wacom tablets now work without the need to install any driver etc (out of the box) and will work nicely with gimp. Just use a live cd to test it for yourself out of Windows. If you're new to the concept of a live cd; it's basically an operating system that is loaded into your RAM which makes it temporary as soon as the computer is turned off.

---

### Post by jermza on 2010-01-06
I'm running Ubuntu (via dual boot) finally.  I'm enjoying it so far, but there are numerous things I need to fix.

Firstly, my sound is WAAAY too loud.  It's either full volume or muted.  How do I fix this?

---

### Post by jermza on 2010-01-06
What's happening is that my sounds blasts at full volume when Ubuntu starts up.  In the sound options, all look fine.  But no matter what volume I adjust the slider to, the sound is full volume, and the speakers bang / pop every few seconds.  

Unless I mute everything.

How do I fix this?

---

### Post by harrisonk on 2010-01-06
[SIZE=4]Ubuntu does that, If you have a volume control on your speakers and adjust it is should change the volume of the welcome sound.

Ubuntu sounds the welcome sound at full volume after that the settings in the sound control panel take effect.
[/SIZE]

---

### Post by jermza on 2010-01-06
I think you're misunderstanding.  The volume control can be at maximum or minimum; the volume still blasts at full.  Muting it is the only other option.

So, even if I turn the speaker's volume down, the sound control in Ubuntu will still be at full, in relation.

---

### Post by canthus13 on 2010-01-06
Go to a terminal (Applications > Accessories > Terminal), type 'alsamixer' (No quotes).  You may have some overdriven outputs somewhere in there.  try adjusting the volumes down from there (Especially if anything is over 100).  I had this happen with Hardy.

--Me

---

### Post by jermza on 2010-01-07
I'm going mad.  Every single time I boot up Ubuntu, my sound goes to max volume.  Why does this happen?  At this rate, Ubuntu will blow my speakers.

I keep lowering the levels in alsamixer.  And the main volume slider at the top right of the desktop does nothing other than mute the sound.  If I slide it from 1% to 100%, the output volume doesn't change.

I'm not a techie, but how difficult can it possibly be to fix this?

---

### Post by zaphod777 on 2010-01-07
It sounds like you might have your sound cranked way up through the hardware setting of the computer. what kind of machine do you have?

what sound is really load the login? 

Also you might get more attention posting a new thread for this perticulure issue.

---

