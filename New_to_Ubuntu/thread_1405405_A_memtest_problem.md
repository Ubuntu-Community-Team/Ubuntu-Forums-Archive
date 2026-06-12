---
title: "A memtest problem?"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-02-12
I have a dual-boot WinXP / Ubuntu 9.10 desktop PC that developed a very odd problem last night.

Both OSs worked fine up to early evening, when I went out to play a game of poker. When I returned, I booted up XP and the screen display had a weird type of what I can best describe as static interference, which gradually got worse as my session progressed.

So I rebooted. But each screen, including the PC-specific splash screen that precedes grub, showed some variant of mucked up display. I tried booting Ubuntu, but that just failed horribly, with the monitor displaying a no signal message with a regularity of every few seconds.

I've tested the monitor connected to my laptop, and it works fine.

I've just tried booting the desktop again, and I'm getting the same problem, but this time from the grub options list, I ran memtest.

The output was:
```
error: too small lower memory (0x99100 > 0x98800)
```

I'm completely lost as to what the real problem might be, let alone how to solve it, so does anyone here have any ideas?

---

### Post by mhgsys on 2010-02-12
> **Roger Allott said:**
> 

The output was:
```
error: too small lower memory (0x99100 > 0x98800)
```

I'm completely lost as to what the real problem might be, let alone how to solve it, so does anyone here have any ideas?

Seems like bad ram , try another ram module.

Edit; uhmz, [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429)
We're talking asus bios here?

Makes me think it has something to do with the videocard instead.
I can understand why your lost now.

Try running memtest from a (older) live cd, see if the same error appears.

---

### Post by Roger Allott on 2010-02-12
> **mhgsys said:**
> Seems like bad ram , try another ram module.

You mean I've got to buy a new RAM thingy?

Do you have any idea why it would have suddenly gone pear-shaped, tits-up, etc.?

---

### Post by mhgsys on 2010-02-12
> **Roger Allott said:**
> You mean I've got to buy a new RAM thingy?

Do you have any idea why it would have suddenly gone pear-shaped, tits-up, etc.?

Well, That's the first thing I thought, but then I came googleing across the error Bug with asus.

 [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429)

 try running memtest from a (older) live cd, and see if the same error appears.

Maybe it has something to do with the videocard instead.



.
__________________

---

### Post by LowSky on 2010-02-12
I had  or have the exact same issue... not sure yet, still working on it.

I just udated the BIOS on my MSI 790FX-GD70, which ais a AMD AM3 board and the problem has not occured since. I will say its only been 2 days. Will keep you posted. I too thought it was my RAM, but I actually think its arelated to the video card.

---

### Post by Roger Allott on 2010-02-12
> **mhgsys said:**
> 
Edit; uhmz, [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=549429)
Where talking asus bios here?
Thanks for the link, but the machine is an HP Pavillion.


> **mhgsys said:**
> 
Makes me think it has something to do with the videocard instead.
I can understand why your lost now.

Try running memtest from a (older) live cd, see if the same error appears.
Good idea. I'm running memtest from Live CD right now. I didn't get the "too small lower memory" error, but what it's actually reporting is a bit of a mystery due to all the screen 'interference'!

---

### Post by Roger Allott on 2010-02-12
> **LowSky said:**
> I had  or have the exact same issue... not sure yet, still working on it.

I just udated the BIOS on my MSI 790FX-GD70, which ais a AMD AM3 board and the problem has not occured since. I will say its only been 2 days. Will keep you posted. I too thought it was my RAM, but I actually think its arelated to the video card.

How does one go about updating one's BIOS? And how do I find out what BIOS upgrade I need?

I hate to be paranoid about Microsoft, but could this problem be related to the updates they released this week for Windows, which apparently went quite 'deep' into the OS hierarchy?

---

### Post by QIII on 2010-02-12
By the way, memory modules do go Tango Uniform eventually...

---

### Post by QIII on 2010-02-12
> **Roger Allott said:**
> I hate to be paranoid about Microsoft, but could this problem be related to the updates they released this week for Windows, which apparently went quite 'deep' into the OS hierarchy?

Doubt it.  Sounds more like hardware.  Things sometimes just spout a whisp of smoke and choke themselves to death.

---

### Post by LowSky on 2010-02-12
> **Roger Allott said:**
> How does one go about updating one's BIOS? And how do I find out what BIOS upgrade I need?

I hate to be paranoid about Microsoft, but could this problem be related to the updates they released this week for Windows, which apparently went quite 'deep' into the OS hierarchy?

No I believe the issue to be driver related. I'm thinking it a Nvidia issue, but I'm not sure. by updating my computer BIOS might be a odd fix but it helped.

Updating BIOS is easy, all you need is the motherboard model, usually written on the motherboard. Go to the manufacturer website and download the nest BIOS. some PC can update BIOS using a boot CD or a flash drive, others have utility programs for Windows or need a 3.5" floppy.

---

### Post by QIII on 2010-02-12
Not sure, LowSky.  I don't think it's a driver issue.

He said "including the PC-specific splash screen that precedes grub".

That would be before the driver is even invoked by an OS.  If it is passing the POST, then it's either the BIOS or the hardware.

But, getting back to the Microsoft update question, I don't think even they would be so arrogant as to take it on themselves to muck with the BIOS.  Maybe I'm wrong.

---

### Post by mhgsys on 2010-02-12
Try re-plugging the video card.

Take it out, put it back in again ; 

Sometimes hardware slots do weird things. 

(or try another video card)

> 

Thanks for the link, but the machine is an HP Pavillion.


 about that BUG and all; .... Some HP Pavillion seem to have the asus Bios....actually... lots of them seem to have asus motherboards/bios

[http://www.google.com/search?btnG=1&pws=0&q=HP+Pavillion+asus+Bios](http://www.google.com/search?btnG=1&pws=0&q=HP+Pavillion+asus+Bios)

---

### Post by Roger Allott on 2010-02-12
I'm 2.5 hours into the memtest and the 7 passes thus far have shown no errors. How many passes are generally recommended before I can escape to the next bit of checking, which I think is going to be to upgrade the bios?

---

### Post by audiomick on 2010-02-12
I think 7 passes should be enough. I haven't used memtest a lot, but one time when I had errors, they started showing up right from the start.

Bear in mind that flashing the BIOS nearly always voids any warranty that you might still have.

---

### Post by QIII on 2010-02-12
The "gradually getting worse" symptom is more indicative of hardware failure.  If you were to have a problem with your BIOS in terms of the assembly code, that would show up at the speed of light.  But the hardware that your BIOS operates in could gradually get worse as something heats up and finally poops out.

Keep eliminating possible hardware faults before you move on to the BIOS flash.

Open the case and blow out all the dust bunnies.

Carefully remove the video card and check it for blistered capacitors, scratched, cracked or raised traces, melted solder, etc.

Reseat the card and try again.

If that doesn't work, spend an hour doing the same thing on your motherboard.

Have you noticed if your processor has been running hot or anything like that?

---

### Post by Roger Allott on 2010-02-13
> **audiomick said:**
> I think 7 passes should be enough. I haven't used memtest a lot, but one time when I had errors, they started showing up right from the start.
I left it running overnight. It did 29 passes - no errors found.


> **audiomick said:**
> Bear in mind that flashing the BIOS nearly always voids any warranty that you might still have.
Well, other than running memtest, just about anything I do is going to void the warranty. In any event, it's a second-hand computer that I bought only a week ago. I think the original warranty ran out a long time ago.

---

### Post by Roger Allott on 2010-02-13
Would it be sensible to run a test utility such as [nVidia nTune]("http://www.nvidia.com/object/ntune_5.05.54.00.html") to find out whether it's my graphics card that's fuggered?

That tool is for Windows, but is the a Linux alternative?

---

### Post by Roger Allott on 2010-02-13
Well, I can't run the nTune thingy because now, when I boot WinXP, I'm just getting a black screen.

---

### Post by Roger Allott on 2010-02-13
And I've found [the file I need to upgrade my BIOS]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-54458-1&lc=en&dlc=&cc=us&lang=&os=228&product=3214121"), but it turns out to be a Windows .exe file, which is also a bit difficult to install when my WinXP just shows a black screen!

---

### Post by mhgsys on 2010-02-13
> **mhgsys said:**
> Try re-plugging the video card.

Take it out, put it back in again ; 

Sometimes hardware slots do weird things. 

(or try another video card)



 about that BUG and all; .... Some HP Pavillion seem to have the asus Bios....actually... lots of them seem to have asus motherboards/bios

[http://www.google.com/search?btnG=1&pws=0&q=HP+Pavillion+asus+Bios](http://www.google.com/search?btnG=1&pws=0&q=HP+Pavillion+asus+Bios)
> 
QIII  	
Re: A memtest problem?
The "gradually getting worse" symptom is more indicative of hardware failure. If you were to have a problem with your BIOS in terms of the assembly code, that would show up at the speed of light. But the hardware that your BIOS operates in could gradually get worse as something heats up and finally poops out.

Keep eliminating possible hardware faults before you move on to the BIOS flash.

Open the case and blow out all the dust bunnies.

Carefully remove the video card and check it for blistered capacitors, scratched, cracked or raised traces, melted solder, etc.

Reseat the card and try again.

If that doesn't work, spend an hour doing the same thing on your motherboard.

Have you noticed if your processor has been running hot or anything like that?

:rolleyes:

---

### Post by Roger Allott on 2010-02-16
Well, I've now done the removing the video card and brushing off the dust thing, and there's been no affect at all.

Something I noticed when I opened the case is that there are 2 RAM modules, which means I have to remove one of them to run memtest properly, and then swap them over and run it again.

My big problem is that whichever drongo designed the HP Pavillion doesn't seem to have thought that a user might ever want access to the memory cards, as they are completely inaccessible to anyone without treble-jointed wrists. I think the only way I can get to them is to remove the hard disk.

---

### Post by audiomick on 2010-02-16
> **Roger Allott said:**
> 
Something I noticed when I opened the case is that there are 2 RAM modules, which means I have to remove one of them to run memtest properly, and then swap them over and run it again.
.
I don't think that is quite true as such. I am sure the memtest looks at all the RAM that is there. If you are showing no errors, as you said you were, I think you can take it at face value. Only if you were seeing errors would you have to test the modules one at a time to isolate where the problem is.

I know what you mean about treble jointed wrists though...;)

---

### Post by mightyiam on 2012-02-10
> **audiomick said:**
> 
Bear in mind that flashing the BIOS nearly always voids any warranty that you might still have.

As far as I've come to understand in my 18 years of computer nerdiness [flasing BIOS doesn't void warranty]("https://encrypted.google.com/search?client=ubuntu&channel=fs&q=does+flashing+bios+void+warranty%3F&ie=utf-8&oe=utf-8").

---

### Post by oldos2er on 2012-02-10
Closed, necromancy.

---

