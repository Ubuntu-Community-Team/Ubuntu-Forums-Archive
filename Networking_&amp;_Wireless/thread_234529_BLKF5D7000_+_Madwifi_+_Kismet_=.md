---
title: "BLKF5D7000 + Madwifi + Kismet = ?"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by xEternus on 2006-08-11
Hello,

I've been lurking around countless message boards and read and executed about a half-dozen tutorials... yet somehow my wireless setup is far less then optimal.  I'm looking forward to any advice you can send my way. 

Things to know about me:
I'm relativly new to the Linux enviroment.  I'm comfortable navigating the filesystem, ifconfig and iwconfig, grep, less, cat, etc.  My knowledge ends at about modprobe, depmod, etc.  I'll figure it out eventually, but be gentle :rolleyes:.

My story:
My wireless card "just works" out of the box.  That was one of the qualifications when I bought the thing.  What doesent work out of the box is Kismet.  I've been led to beleive the reason for this is two fold.  

1) the madwifi drivers that ship with Ubuntu are out of date
2) the kismet package in the Ubuntu repositories is out of date

The solution to me seemed pretty simple.  get newer versions! ](*,) 

After compiling, installing, and configuring per each sites instructions things looked promissing.  Kismet would work and it spotted a a bunch of networks in my area.  packets were flowing and all was well... until I wanted to browse.  

I shutdown kismet and popped open Opera.  No internet connectivity at all.  I took this to mean my card was stuck in monitor mode.  I needed it back in managed mode and to connect to my AP and get it self an IP.  Should be easy, right?  No... madwifi seems to use VAPs?  I dont quite know what that means except that ath0 is realy wifi0 and even though ath0 says Managed wifi0 might be monitor... suffice to say im confused in that area.

So I get frustrated, reboot a few times.  reenact some tutorials, and tinker a bit.. I'm connected!  sorta... im getting about 7kb/s and im on 1.5Mbit DSL...

So my question to you is twofold.  
1) How can I restore the Madwifi drivers that came packaged with Ubuntu.   I.E. What package are they in?

2) What on earth happened to my connection speed?

Sorry for being so longwinded and thanks for any help you can send my way.

---

### Post by tturrisi on 2006-08-11
Yes, it sounds likme the card is gettinmg stuck in monitor mode when kismet exits.  This is NOT a problem with the drivers but is an issue with kismet.  In fact, every time kismet exists it will give a message re stuck in monitor mode.  One thing you can do to get it back to managed again is go to system/administration.networking/wireless/disable & re-enable the connection.  On my laptop w/ a pcmcia atheros card, if it gets stuck in nmonitor I just pull out the card & stick it back in.

But really, there's no need to use kismet w/ a pci wifi card anyway...laptops are better w/ kismet.

---

### Post by cantormath on 2006-08-11
> **xEternus said:**
> Hello,

I've been lurking around countless message boards and read and executed about a half-dozen tutorials... yet somehow my wireless setup is far less then optimal.  I'm looking forward to any advice you can send my way. 

Things to know about me:
I'm relativly new to the Linux enviroment.  I'm comfortable navigating the filesystem, ifconfig and iwconfig, grep, less, cat, etc.  My knowledge ends at about modprobe, depmod, etc.  I'll figure it out eventually, but be gentle :rolleyes:.

My story:
My wireless card "just works" out of the box.  That was one of the qualifications when I bought the thing.  What doesent work out of the box is Kismet.  I've been led to beleive the reason for this is two fold.  

1) the madwifi drivers that ship with Ubuntu are out of date
2) the kismet package in the Ubuntu repositories is out of date

The solution to me seemed pretty simple.  get newer versions! ](*,) 

After compiling, installing, and configuring per each sites instructions things looked promissing.  Kismet would work and it spotted a a bunch of networks in my area.  packets were flowing and all was well... until I wanted to browse.  

I shutdown kismet and popped open Opera.  No internet connectivity at all.  I took this to mean my card was stuck in monitor mode.  I needed it back in managed mode and to connect to my AP and get it self an IP.  Should be easy, right?  No... madwifi seems to use VAPs?  I dont quite know what that means except that ath0 is realy wifi0 and even though ath0 says Managed wifi0 might be monitor... suffice to say im confused in that area.

So I get frustrated, reboot a few times.  reenact some tutorials, and tinker a bit.. I'm connected!  sorta... im getting about 7kb/s and im on 1.5Mbit DSL...

So my question to you is twofold.  
1) How can I restore the Madwifi drivers that came packaged with Ubuntu.   I.E. What package are they in?

2) What on earth happened to my connection speed?

Sorry for being so longwinded and thanks for any help you can send my way.

IMO, I think the Mad-wifi drivers are crap, what card are you using?
I believe that when running kismet on a card, ie ath0, you are running that card in monitor mode, and can not view the net until you are done with kismet.  Usually in my experience, kismet reset the card back to managed mode, but that is not always the case, and from what it sounds like, not the case here.  
After turning off kismet have you tried....?
```
puter$ sudo iwconfig ath0 mode managed

```
Are you running kismet with sudo? 

dont mean to drill anyone, or suggest that you dont know anything, Im just trying to get an idea.  An Idea, I run two cards when using kismet, so that I can access the web while running kismet.

---

### Post by tturrisi on 2006-08-12
> **cantormath said:**
> I believe that when running kismet on a card, ie ath0, you are running that card in monitor mode, and can not view the net until you are done with kismet...An Idea, I run two cards when using kismet, so that I can access the web while running kismet.
That's what I do.  You cannot run a kismet server on a card AND be connected the network at the same time using one wifi adapter.  To do so requires 2 separate adapters.

---

### Post by xEternus on 2006-08-12
Hello,

thanks for the ideas.  Yes, im runing kismet from root, and i dont expect to be able to access the net while running it, but I would prefer that it work after kismet is closed.

thanks.

---

### Post by tturrisi on 2006-08-12
make sure you close out kismet by using the command shift+Q instead of just x'ing out the window.

---

### Post by xEternus on 2006-08-13
Yes, thats how I close it.  But if you reacall, my original question is how do I restore the original madwifi drivers that came with ubuntu?

---

### Post by tturrisi on 2006-08-13
if you backed them up you could just open nautilus as root and move 'em back in place of the new ones.

---

### Post by xEternus on 2006-08-13
And if I didn't back them up?[-o<

---

### Post by xEternus on 2006-08-13
Sorry, I forgot to answer one question above.  I'm using a Belkin BLKF5D7000 card.

---

### Post by tturrisi on 2006-08-15
I believe the madwifi-docs explain how to remove existing modules from the kernel & install the new ones.  Perhaps just remove them & proceed with desired modules.

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo#RemovingMadWifi](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo#RemovingMadWifi)

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

The Ubuntu madwifi modules can be installed by enabling the restricted sources in Synaptic and then installing the linux-restriced-modules for your kernel.  (re-install them if Synaptic shows them as already installed)

FYI, I just replaced Ununtu on my laptop with Debian Etch upgraded to Sid.  I installed the newest madwifi modules and my atheros cards work fine as does Kismet.  However, with these new madwifi modules the Kismet.conf source is now:

source=madwifi_ag,wifi0,madwifi

...and kismet works just fine & my cards don't get stuck in monitor mode.

...now if I can just get the kismet wav files to sound using alsa (aplay)

---

### Post by xEternus on 2006-08-15
Thank you.  That was exactaly the information I was looking for.

---

### Post by tturrisi on 2006-08-15
results?

---

### Post by tturrisi on 2006-08-17
more info re stuck in monitor mode:

Sometimes, when shutting down kismet using shift+Q, my atheros cards get stuck in monitor mode.  To quickly put the card back into managed mode (station) I use system/administration/networking & deactivate the card & then immediately reactivate it & I am again connected to the AP.

Kismet warns at closing that sometimes a card will get stuck in monitor mode so this small issue is expected.  But 99% of the time my atheros cards don't get stuck in mode monitor.

---

### Post by xEternus on 2006-08-17
> **tturrisi said:**
> results?I'm connected at full speed, and kisment pulls out of monitor mode on its own about 95% of the time.  I'll call this experment a success so far.

---

### Post by tturrisi on 2006-08-17
> **xEternus said:**
> I'm connected at full speed, and kisment pulls out of monitor mode on its own about 95% of the time.  I'll call this experment a success so far.
LOL, I'd no longer call it an experiment but rather a final release!

---

