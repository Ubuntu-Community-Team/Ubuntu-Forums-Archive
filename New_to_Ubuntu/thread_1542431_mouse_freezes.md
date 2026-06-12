---
title: "mouse freezes"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by ExoTek on 2010-07-30
Hello there people.

I have a very ennoying problem: my darn mouse (USB) freezes just about anytime it pleases!

I'm using Ubuntu 10.4, I keep it updated and I have a pretty normal pc (no laptop, bluetoot thigny etc)

Of course, I already tried to search the forum for such a problem and (hopefully) the answer to this problem but every time I try this I end up with gazillions pages and for what I check (and please don't think that I check only a few!) but the troubles that I see aren't like mine... 

Some have both their keyboard and mouse that freezes, in my case its just the mouse (my keyboard isn't USB).

Others just have to unplug and re-plug the mouse, I tried this (in the same outlet and others) but it did nothing.

Some were saying that, using the terminal and "sudo modprob -r usbhid" then "sudo modprob usbhid" would do it. But again that doesn't work for me!

Yet others are talking about changing something in the grub (yea! great! but I'm stuck with the ever user friendly "grub2" :( )

I could go on but I think you get the idea.

Oh, and also I had the same problem with ver. 9.04 of Ubuntu. (that's how long I'v been trying to find a solution on my own without having to come ennoying anybody with my problem)

At some point I thought that the problem was my mouse (some cheap thing bought at wallmart for 12 bucks!) but it works perfectly with windoze! (when I have to restart my pc, I just reboot windoze and then keep working for hours without any problems)

From my point of view, the only thing left to do is to locate a high set tree branch, get a short rope and ... ;)

---

### Post by davidmohammed on 2010-07-30
... before you try the rope trick - have you tried another mouse?  Maybe the mouse you are using is "windows only".

---

### Post by gandaran on 2010-07-30
> Oh, and also I had the same problem with ver. 9.04 of Ubuntu. (that's how long I'v been trying to find a solution on my own without having to come ennoying anybody with my problem)
did older versions of ubuntu like 8.04 work well?
what is the brand and model of video card?

---

### Post by ExoTek on 2010-07-30
Is there such a thing?

I will most certainly try that. I was thinking about buying a new mouse anyway (not USB this time...)

Could take a few days before I do so (go to the store etc...) but I'll keep you informed, thanks for answering. :)

I only recently started with linux, my first "love" was 9.04. Right before grub2 became default. (I had to read 'almost' the whole manual, a few tutorials just to get my system to dual boot and then, all proud of myself I click the "install upgrades" button and BANG! Grub2 is the new sherif in town! Read 'almost' the whole manual, search for and find only one tutorial ... anyway, that's another story.)

The video card? I'm surprised by that question! (which probably tells you much about my computer skills) anyways, the card is "nVidia" something. I'll have to check...

Ok, the card is: ASUS EN7600GT PCI EXPRESS 256MB DDR3

---

### Post by gandaran on 2010-07-31
> The video card? I'm surprised by that question! (which probably tells you much about my computer skills) anyways, the card is "nVidia" something. I'll have to check...

Ok, the card is: ASUS EN7600GT PCI EXPRESS 256MB DDR3
surprised? you problem is certainly due to hardware and it could be any, on this computer I used to dual boot windows and ubuntu, on the ubuntu side I have random mouse freezes while on the windows side the freezes came after striking a keyboard key! it took me many years to figure out and fix the problem, it was the video card.
Then I bought a new laptop that only worked with ubuntu 8.04, 9.04 or higher would freeze, this one I easily fixed just by updating BIOS!
did you install the nvidia driver from system » administration » hardware driver, if not try it.

---

### Post by teachop on 2010-07-31
Have a similar issue.  Sometimes the mouse and keyboard go out.  Actually the whole USB hub goes out.  Unplugging the hub brings it back.

I look in dmesg and there is no activity from the USB death, but there is when I unplug and reconnect it.  It is mostly random, but have had this happen more than once when starting a download.

Didn't start for me until Lucid, and I find no solution anywhere.  Tried replacing the hub, no help.

---

### Post by ExoTek on 2010-08-01
To answer gandaran, yes I got the proprietor driver for my card, thanks. 
To answer teashop, I have found 'many' threads where people had that kind of trouble where they could just unplug and replug but for some reason, it didn't work for me.

Anyways, I didn't change my mouse cause I was told (by one guy only though) that a non-usb mouse HAS to be non-laser ( you know the type with a ball that is a real magnet for dust and dirt and that needs to be washed and pampered dayly ;) ), but seeing me going away with my rope to the tall tree with a high branch, that guy (my brother actualy) gave me some adapter to plug my usb mouse in the "non-usb" plug. So far everything seems to go well but only time can tell.

Now I'll try to trigger the 'freeze' ... I don't know how though...

Oh yea... In my original post I say that it never happens with windoze... Not entirely acurate... I remembered it happening but for some reason it is so rare! (rare enough to not remember about it) I would say maybe 1% or 2% of the time. So it really is likely that the problem be hardware...

Anyways, I'll wait one or two days to see if it freezes again or not.

Thanks you guys for trying to help.

---

### Post by gandaran on 2010-08-02
> Oh yea... In my original post I say that it never happens with windoze... Not entirely acurate... I remembered it happening but for some reason it is so rare! (rare enough to not remember about it) I would say maybe 1% or 2% of the time. So it really is likely that the problem be hardware...
ExoTek
pay close attention to this, check if the freezes happen on Ubuntu after you use Windows for some time.
just after the computer freezes try rebooting 3 or 4 times without any freeze (use short sessions for this), use Ubuntu only say for one week without booting Windows, check then if the freezes stop.
report back.

---

### Post by ExoTek on 2010-10-26
Hello there,

I'm sorry for taking such a long time to reply.

I've been using Ubuntu only for about a week now (a little more than that actually) and I don't think it changed anything, it still freeze about any when.

In my effort to find a pattern (just paying more attention) I noticed that it seems to append more when I watch videos but -> ONLY ON THE WEB <- not local (video files on my hard drive). But whenever I end up on Youtube and such, BANG! (well, not realy 'BANG' but it just seems to be more likely)

Also, I had found once some post where it was indicated to set 'I don't remember what' in the BIOS setting and that had tremendously reduced the problem (didn't solved it though :() but some time after, something went wrong and I got a msg to reset the BIOS settings and now I just can't find the post where it said what to turn off in the BIOS... Maybe some buddy knows.

Thanks for the help, bye for now.

---

### Post by docmojo on 2011-05-09
Hi guys, I am a novice in these technical issues...

But faced this mouse freeze prob for a few days... Just struck me that, I had installed ClamAV prior to this glitch... So removed it from the system, and the problem seems to have disappeared... 

Do you'll have it installed too?

---

### Post by tealex on 2012-01-09
i have the same problem 
mouse suddenly freezes 
and in /var/log/messages 
USB disconnect, address XX

me help reinstall compiz

```

sudo apt-get purge compiz*
cd $HOME && rm -rf .compiz/ .config/compiz/

```

---

