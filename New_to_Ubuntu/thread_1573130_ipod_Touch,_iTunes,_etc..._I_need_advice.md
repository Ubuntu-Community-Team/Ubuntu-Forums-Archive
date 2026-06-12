---
title: "ipod Touch, iTunes, etc... I need advice"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by kendoori on 2010-09-12
My 12-year old daughter's XP laptop finally gave me enough fits that I  followed through on my threat ("Next time we run into issues like this,  I'm butting Linux on it!") She's actually OK with this, but I need to  figure out a way for her to manage her iPod touch, and also interact  with iTunes if possible (please no sermons or lectures).

Her machine is a Thinkpad X41, and I did give a shot at installing  iTunes under Wine. I never got to the point where I was connecting her  device to it, but it did see her library, but the display looked pretty  funky. Anyway, I suspect the device would have connected OK, but I just got nervous that Wine was just not going to perform that well. Perhaps someone can suggest otherwise.

This is an older machine with not a great graphics card, and only 1.5GiB  of RAM. Obviously I can install either VMWare or VirtualBox, but I hate  the idea of having her have to fire up a virtual machine (she is not  exactly patient) every time she needs to run iTunes.

I would love to communicate with someone who navigated through this  whole thing and has found a user-friendly solution suitable for a  12-year old.

If I run something like Banshee, what will she not be able to do that  she can do now with iTunes (except itunes store)? She has a bunch of IOS  apps, how are these managed/backed up if she doesn't use iTunes? Also I  suspect that she has a bunch of older DRM music purchased from the  iTunes store, what impact does this have? how can one navigate around  this?

---

### Post by evictkite on 2010-09-12
I don't know anything about ipods except that they have an analog output that you can record from with your soundcard using a program like audacity if you are like me and don't know how to break the drm on the itunes files.  I've read that the official itunes software doesn't work on linux but you might be able to use gtkpod or rythmbox to copy the mp3s onto the ipod.

---

### Post by nagaraj on 2010-09-12
i am using gtkpod and pix pod ( u can search and install them using  synaptic or any package manager). there are a few more as well. the following pages might be of help.
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)
[http://www.cyberciti.biz/faq/linux-software-for-itunes-ipod-classic-ipod-touch-iphone/](http://www.cyberciti.biz/faq/linux-software-for-itunes-ipod-classic-ipod-touch-iphone/)

---

### Post by clive littlewood on 2010-09-12
Hi

I connect my ipod touch using Rythmnbox for music where I can transfer and remove music.

Any apps or itunes store use is done direct from the touch.

Shotwell will import any pictures from the touch.

Good Luck     ;)

Clive

---

### Post by kendoori on 2010-09-12
@Clive Littlewood How have you dealt with legacy DRM itunes purchased music? if so, how?

---

### Post by TCHebb on 2010-09-12
> **kendoori said:**
> @Clive Littlewood How have you dealt with legacy DRM itunes purchased music? if so, how?
You should just be able to put the DRMed music into Rhythmbox. It won't play on the computer, but it should sync and play fine on the iPod.

---

### Post by cj13579 on 2010-09-12
+1 with clive littlewood. I am using Rythmbox for iPod management. Has been a dream so far and you don't even have to install anything else.

I think the hardest part of the whole thing was that I had to go: Edit > Plugins and turning on the "Portable Players - iPod" plugin!!

---

### Post by kendoori on 2010-09-12
Any downside to using Banshee instead of RhythmBox, other than a matter of preference? For my daughter, upside is that it has access to Amazon music store, which she has used before and can deal with.

Also, if someone can point me in the right direction of how to determine which songs have DRM vs. which do not. We paid for this music, so I have no issues working through the process for stripping the DRM. I'm not sure how much DRM music she actually has.

---

### Post by sandyd on 2010-09-12
> **kendoori said:**
> Any downside to using Banshee instead of RhythmBox, other than a matter of preference? For my daughter, upside is that it has access to Amazon music store, which she has used before and can deal with.

Also, if someone can point me in the right direction of how to determine which songs have DRM vs. which do not. We paid for this music, so I have no issues working through the process for stripping the DRM. I'm not sure how much DRM music she actually has.
easy.
open itunes, and burn the music to a cd.
rip it in ubuntu.
no DRM pronto.
for more info, see [http://en.wikipedia.org/wiki/FairPlay](http://en.wikipedia.org/wiki/FairPlay)
(and yes, sorry for the short replies... im watching the VMAs...)

---

### Post by cj13579 on 2010-09-13
> open itunes, and burn the music to a cd.
rip it in ubuntu.
no DRM pronto.

You will experience a loss of quality with this method however. I believe there are some 3rd Party Apps though that you can strip DRM with though. However, [this thread]("http://www.google.co.uk/url?sa=t&source=web&cd=1&ved=0CBUQFjAA&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D668976&ei=ZtONTJ2zMNi4jAe1ysDMBg&usg=AFQjCNFUvRo8jQFa5L8ME46WUQzRvPZj7A&sig2=yjIrzhckK8XjQgMvajHPCA") discussed this on the forums and the Admin's didn't take to kindly to it.

@kendoori I believe that at the beginning of 2009 Apple removed the DRM from it's iTunes tracks. But it was phased in so some post then may still have it.

---

### Post by mr_luksom on 2010-09-13
What iOS has she got? If she has updated to iOS4.1, you will have to wait for the next libimobiledevice...

I switched to ubuntu a month ago, and my only regret is the iPhone, it is the only thing keeping me from ditching xp on my other machine...

---

### Post by Grenage on 2010-09-13
The only thing I really need Windows for is upgrading the IOS on my iphone, and that's something I haven't done since 3.1.2.

---

### Post by sandyd on 2010-09-13
> **cj13579 said:**
> You will experience a loss of quality with this method however. I believe there are some 3rd Party Apps though that you can strip DRM with though. However, [this thread]("http://www.google.co.uk/url?sa=t&source=web&cd=1&ved=0CBUQFjAA&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D668976&ei=ZtONTJ2zMNi4jAe1ysDMBg&usg=AFQjCNFUvRo8jQFa5L8ME46WUQzRvPZj7A&sig2=yjIrzhckK8XjQgMvajHPCA") discussed this on the forums and the Admin's didn't take to kindly to it.

@kendoori I believe that at the beginning of 2009 Apple removed the DRM from it's iTunes tracks. But it was phased in so some post then may still have it.
thats likely the closest we can get without violating the CoC.
HINT: OP, search on wikipedia for "Fairplay" that is what apple's DRM is called...

---

### Post by kendoori on 2010-09-14
> **sandyd said:**
> thats likely the closest we can get without violating the CoC.
HINT: OP, search on wikipedia for "Fairplay" that is what apple's DRM is called...

FOLLOWUP HINT: Yes, it appears a Requiem maybe called for in this situation

---

### Post by scouser73 on 2010-09-14
Unfortunately iTunes won't work on Ubuntu, but there is good news in that the iPod Touch will sync to Rhythmbox (which is the standard music player in Ubuntu).  I know this because I have one myself and it's simple plugged in via the USB lead and detected straight away.

If you need to transfer photographs to and from your iPod Touch, I think that is going to be a bit difficult unless you ""jailbreak" the iPod Touch (but I'm not exactly sure on that).

My iPod Touch software currently stands at version 3.1.3, and I've not updated it, so if you really need iTunes to keep your software upto-date then you're best keeping a small partition of Windows XP but at the next update of iPod software may stop it working under Ubuntu.

---

### Post by phredbull on 2010-10-12
My iPod, (3g? 20gig, click wheel, b&w screen) mostly works w/Rhythmbox, but when I make or edit playlists, the changes aren't saved on the iPod its self. I'm not at all opposed to a Linux compatible iTunes!
:(

---

### Post by PaulReaver on 2010-10-12
yeah rhytymbox has an ipod plugin you can just drag and drop the files :)

you  could just buy your music drm free from the ubuntu music store or 7digital  :)

works with my ehPod

---

