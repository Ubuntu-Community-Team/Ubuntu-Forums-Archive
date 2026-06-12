---
title: "Problem: Try ubuntu without any changes to your compute"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by Cactus_gulch on 2010-03-07
I ran the check sum before burning the image. It matched.

Everything went alright until I tried &#8216;Try ubuntu without any changes to your computer&#8217;.

Nothings seems to happen. How long does it take for the system to start up?

Then I let it run for a couple of hours...still nothing.

I ran the option to check the disk..after some time it came back with no errors.

I just want to get my data off a 'dead' computer.

It's a Sony [[COLOR=blue][/COLOR]]("http://www.linuxquestions.org/questions/#")PCG-FX250

Any ideas?
Thanks

---

### Post by patchwork on 2010-03-07
A live cd typically takes a minute or two to load, not an hour!  With all the checksums matching, there has to be something else going on inside your computer.  What kind of issues were you facing?

---

### Post by cusinndzl on 2010-03-07
Try making the BIOS boot from the optical drive first.

---

### Post by MooPi on 2010-03-07
You can try the Safe Graphics Mode on the Live CD. If your computer is having hardware issues  trying to load the Live CD may not work.

---

### Post by Cactus_gulch on 2010-03-07
This computer has been having problems since I let my cousin have it. Then it just wouldn't boot to Windows. She needs some data off the drive.
I tried booting in Safe Mode since that is the screen that comes up. Nope.
Then the other options....nope.

So, I took it back and tried to do the Ubuntu thing.
That's where this thread picks up.

I just tried to boot to the LiveCD to try your suggestions...now it won't even power up. That happened first thing this morning, but I noticed my power strip wasn't on and had to try a couple of times after that. Figured I'd hit the button wrong or something.

I just tried several times...still nothing.
Thanks

---

### Post by Cactus_gulch on 2010-03-07
Phew..just tried it again. Booting to the Live CD.
No 'Safe Graphics Mode' on the LiveCD menu.
I will try the BIOS suggestion.

---

### Post by Cactus_gulch on 2010-03-07
Found 'Safe Graphics Mode'....nothing happens.
Looking for BIOS now....

---

### Post by patchwork on 2010-03-07
If you're making it that far your bios is already set-up to boot from cdrom...

---

### Post by Cactus_gulch on 2010-03-07
Got to the BIOS.
CD ROM is the first in the list
then removable devices
then hard drive

I didn't make any changes.

---

### Post by quinnten83 on 2010-03-07
I think your pc is hardware dead. 
IN that case no CD, live or otherwise will help.
If you need to get the data off, buy a 2,5" disk casing and access it from another computer.

---

### Post by Cactus_gulch on 2010-03-07
I tried booting again without the LiveCD to get more information for you.

When I select Safe Mode - or anything else, you can see it almost opening Windows. It's a small BSOD like window.

I took some pictures and will see if I captured what was written to the screen as it whizzed by.

---

### Post by paydaydaddy on 2010-03-07
I agree that it is probably a hardware issue. Can you run memtest from the live cd?

---

### Post by Cactus_gulch on 2010-03-07
> **quinnten83 said:**
> I think your pc is hardware dead. 
IN that case no CD, live or otherwise will help.
If you need to get the data off, buy a 2,5" disk casing and access it from another computer.

Dang it...
JFYI...
'multi(0) disk(0)rdisk(0)partition(1)\Windows\system32\drivers\xxxxx lots of them.
Then I can see the Windows XP logo zip by and the BSOD [small window] and behind it I captured: A problem has been detected and Windows has been shut down to prevent damage to your computer...............further down in the blue....***  STOP: 0x0000008....

I will have to research the 2.5 disk casing and figure out what that is all about.
Would it be just as inexpensive to get a local shop to do this?

I really don't want to pay to get her data off because she neglected to back anything up.
Thanks again

---

### Post by Cactus_gulch on 2010-03-07
mem test?
Apparently I can. It's running right now.
At the moment, it's at pass 11% and test 5%.
Below it it has some detail including the errors column with '0'

---

### Post by Cactus_gulch on 2010-03-07
Still going...still no errors.

I think I have the reason for it dying...my cousin reaks of those dryer sheets [Bounce, etc]. It makes me physically ill. Nope..no kidding...
Anyway, if it's so bad for me, why not my computer. She killed it with Bounce. ;)

---

### Post by Cactus_gulch on 2010-03-07
> **quinnten83 said:**
> I think your pc is hardware dead. 
IN that case no CD, live or otherwise will help.
If you need to get the data off, buy a 2,5" disk casing and access it from another computer.


Looked up the 2.5" casing...talk about cheap....
So, next I will figure out how to get at the hard drive.

Thanks so much.

The memtest is still running.
Does it wrap around?
It's back to pass 2% after completing the 100%.
There is a message at the bottom that the pass was complete with no errors and to press ESC to exit.

---

### Post by paydaydaddy on 2010-03-07
have you tried getting into recovery mode by hitting escape just after the initial post screen?

---

### Post by paydaydaddy on 2010-03-07
memtest runs a series of tests. I don't remember how many. I suggested it because memorty is a common culprit and easy to test and fix. Feel free to stop it and try other things at any time. You can always go back to it and I would expect that with the symptoms you are describing that if memory were at fault you would see errors right away.

---

### Post by candtalan on 2010-03-07
> **Cactus_gulch said:**
> I ran the check sum before burning the image. It matched.

Everything went alright until I tried ‘Try ubuntu without any changes to your computer’.

Nothings seems to happen. How long does it take for the system to start up?

The live cd does need ram to run in. 256MB or more, although you can intstall into less (using alternate cd)

With less than minimum ram, it will try to load and will be moving stuff at one byte at a time.....

More RAM will get back to normal load times. Maybe it has low ram size?

hth

---

### Post by Cactus_gulch on 2010-03-07
So, if I get the casing and plug it into my own computer will my Trend Internet Security stop any viruses that are on the hard drive from that laptop?
Can I plug it in then scan for viruses without worries that the virus will do something on its  own - if there are any?

Also,
I have a Qmemory 40BGB drive in one of those casings. 
Can't I just put the hard drive from the laptop into the QMemory casing? We don't have any stores within 50 miles or so that would carry the casing....hence Cactus Gulch.
Seems logical - to me, anyway.

Thanks

---

### Post by Cactus_gulch on 2010-03-07
> **paydaydaddy said:**
> have you tried getting into recovery mode by hitting escape just after the initial post screen?

Just tried it a few times at different places [Windows and Ubuntu]. 
Didn't see anything different. If recovery mode is where it asks if you want to go into 'Safe Mode', then yes. That's what it boots to.

---

### Post by Cactus_gulch on 2010-03-07
We got the hard drive into the QMemory casing.
There was a site on how to remove the hard drive from the laptop. Very helpful.

So, now we are scanning the drive before we grab her data.

Thanks everyone for your help.

---

### Post by paydaydaddy on 2010-03-07
Recovery mode will give you a list of kernels withe the option to select recovery. If you can get to that screen the system may be able to repair itself.

---

### Post by Cactus_gulch on 2010-03-07
Scanned the hard drive - 32 trojans.
Got the data she needed off and will scan the data again.
Then will clean up the drive and put it back.
Maybe it will boot normally.
If not I will try the recovery mode.

Thanks again.

---

