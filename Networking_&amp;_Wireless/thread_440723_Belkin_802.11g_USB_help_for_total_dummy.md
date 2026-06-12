---
title: "Belkin 802.11g USB help for total dummy?"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by wbmercer on 2007-05-11
I don't know a single linux command.  I'm pretty good at pointing and clicking.  I was very proud of myself for successfully burning an ISO image of Linux Ubuntu 7.04, but it doesn't seem to recognize my wireless adapter.  If fixing that problem is tougher than pointing and clicking, I'm going to need absolutely step-by-step instructions.  "Install ndiswrapper" is not detailed enough for me.  If help exists at the level I need, getting internet access through Linux is all I need to break free of the MS Borg, I think.

My adapter is a Belkin 802.11g USB, Part #F5D7050ak v3000ak.

Can anyone get me connected?

Also, I don't understand the partitioning guide, so I need to see if this works from the live CD, before I really install it.  Then I'll need someone to walk me through the partitioning process so that my C drive with windows on it stays there and I just peel off 50GB of my now empty D drive to install Linux on.  But I can ask that or find the answer in a separate post if I get the wireless problem solved.

P.S.  Once I have the dual boot and internet working, I promise to buy Linux Ubuntu for Dummies to teach myself the rest of whatever I'm going to need in order to stay happy with Linux.  I just like the idea of being MS-free and don't have the money for a Mac.  Ultimately, though I don't want to spend all my free time tinkering with my PC to make it do things. I just want to surf the web, handle e-mail, blog, listen to music and watch an occasional video.  I think Linux can do that for me completely from a graphical, point and click interface, if I can just get set up.

---

### Post by chili555 on 2007-05-11
Welcome to the party! We having fun here and we're glad to have you join us!

Plug in your Belkin and let's learn a command or two. Open a terminal *Applications -> Accessories -> Terminal* and type in:```
lspci -vv
``` See if there is an entry related to your wireless adapter. Try another command:```
lsusb
```Your adapter may be a Ralink RT73 chipset. If so, this: [http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73) is the best working solution. I know it looks daunting to a newbie, but it's simply a matter of following the steps and double-checking your work.

> I just want to surf the web, handle e-mail, blog, listen to music and watch an occasional video. I think Linux can do that for me completely from a graphical, point and click interface, if I can just get set up.Linux can do that and so much more, quite easily.

---

### Post by wbmercer on 2007-05-13
chili555, 

Thanks for your willingness to help my poor stupid self.  I entered the first command you suggested and saw a lot of my hardware, but didn't see the Belkin wireless adapter.

I then entered the second command and found this:

"bus 003 Device 003: ID 050d: 705a Belkin Components"  I wrote those and typed them here, so it's possible a space might be wrong somewhere in that line of my transcription.

So what does that result tell me?

Also, I looked at the instructions you linked to.  I don't know whether I have SMP or preempt, or how to find out.  The first command you had me  run did list "[Athlon64/Opteron] HyperTransport..."  Does that mean I have it?

I tried running the command it advises in that case and got this result:

"Couldn't find any package whose name or description matched "linux-386"

What does that mean and what do I do about it?  Do I just go on with the rest of the instructions?

Brad

---

### Post by chili555 on 2007-05-13
> So what does that result tell me?A search of Google/linux confirms this is an RT73 chipset.> I don't know whether I have SMP or preempt, or how to find out. Open a terminal and type:```
uname -a
```You will or will not see 'SMP' listed. You will not see preempt unless you called for it as a boot option.> Couldn't find any package whose name or description matched "linux-386I believe it's actually 'linux-image-386.' You should install that kernel and switch into it as described before you proceed. The process will not work correctly otherwise.

Are you still running the live CD? I believe the live CD runs a -386 kernel by default. If you run *uname -a* and do *not* see SMP, then you will be safe to proceed. 

Good luck and post back to let us know how you are getting along.

---

### Post by wbmercer on 2007-05-18
Okay, there's no SMP, so I guess I'm past that step.  The first step in the [http://ubuntuforums.org/showthread.p...highlight=rt73](http://ubuntuforums.org/showthread.p...highlight=rt73) howto says to download "rt73 USB nightly CVS tarball" but the only rt73 I see on the linked download page is "rt73 (USB) CVS hourly tarball: rt73-CVS".

Is that close enough?  If not, how do I find the nightly one instead of the hourly one?

I basically only have Saturdays to work on this, so at this rate it may take me a while to get online in Linux!  ;-)

I suspect my next question will be how to download the driver, since I won't be online.  I'll have to download it to my flash drive in Windows and then copy it from there to somewhere while I'm in Linux.

Brad

---

### Post by chili555 on 2007-05-18
I know the title on the page says 'hourly' but when you actually download it, it says 'daily.' That's the one you want.

> I'll have to download it to my flash drive in Windows and then copy it from there to somewhere while I'm in Linux.That's probably the best way.> I basically only have Saturdays to work on this, so at this rate it may take me a while to get online in Linux!Hurry! I'll be here to help you for several more hours.

This step:> sudo aptitude install build-essential linux-headers-`uname -r`can be accomplished from the install CD.

---

### Post by wbmercer on 2007-05-21
> **chili555 said:**
> I know the title on the page says 'hourly' but when you actually download it, it says 'daily.' That's the one you want.

Got it.

> That's probably the best way.Hurry! I'll be here to help you for several more hours.

Sorry, I took an unfortunate detour and am now even more screwed.

> This step:can be accomplished from the install CD.

This statement led me to wonder whether it was possible that some of the other steps cannot be accomplished from the install CD.  My initial idea was to try to completely solve the problem and get online through Linux from the CD, and only then try again to actually install Linux and go through the same steps again to permanently get me where I want to wind up.

The possibility that I might not be able to follow the steps all the way through from the CD, combined with the fact that all the steps take longer when operating from the CD just because the OS runs slower from the CD than when actually installed led me to the fateful decision to go ahead and install Linux Ubuntu 7.04 first and then get back to following the steps to get the wireless adapter working.

I think I correctly partitioned the hard drive.  I can still boot up in Windows and it shows the C drive where it is, and an empty D drive which is now 90GB instead of the previous 180GB (because I took the default partition suggestion in Linux to take half of the 180GB for Linux.  I can boot up in the second and third Linux options.  The second one says recovery and runs through a lot of stuff, says OK about all of them, and leaves me at a command line.  The third one says memtest something.  I let it run for 5.5 hours and it just keeps checking stuff and saying it's not finding any errors.  I stopped it at 5.5 hours, not knowing whether it just keeps repeating the same steps indefinitely or was still checking more stuff.

The first option, though, to actually boot up in Linux, that should bring me to the GUI I want, doesn't.  It starts booting up very slowly, finally asks for my username and password, then stays on a blank tan screen for maybe 15-30 minutes, then pops up a light blue square in the upper left quadrant of the screen with the rest remaining tan colored, and stays that way forever.

So, now I'm inclined to think I need to fix that and get the Linux installation working properly without losing Windows, before I get back to solving the wireless problem.  I installed Linux from this CD earlier with no problem except that I wiped out windows by taking the whole hard drive.  When I hit the adapter problem I then re-installed Windows allowing it to have the whole hard drive (divided into C and D).  That's where I was until I made this latest attempt at a dual-boot installation.

I'd really love to make this work and feel like I'd gained something from the whole experience, but it's getting discouraging.

Brad

---

### Post by chili555 on 2007-05-21
> I need to fix that and get the Linux installation working properly without losing WindowsI agree. You have a functioning dual-boot going with a display problem, probably, on the Ubuntu part. I suggest starting a new thread over in "Absolute Beginners" referring, perhaps, to 'Login leads to black screen.'

Memtest is a memory testing system. The idea is to be able to find if your memory (RAM) is at fault if you can't even boot to the operating system. > The second one says recovery and runs through a lot of stuff, says OK about all of them, and leaves me at a command line.This option loads the minimum system to simply get you running. So little is running that the window manager, Gnome or KDE, etc., is not running. It's perfect for troubleshooting. For example, you could log in and then issue a command:```
sudo less /var/log/messages
```The command *less* allows you to scroll slowly through the text with the arrow keys. See if there are any clues as to why Gnome didn't start.

---

