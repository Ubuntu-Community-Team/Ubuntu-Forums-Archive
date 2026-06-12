---
title: "Memtest address vs. BadRAM address"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Marturion on 2011-02-17
Bad news: I have a few bytes of bad memory.

Good news: BadRAM is now included in Ubuntu (i'm running 10.10)

Bad news: There currently seems to be a bug in Memtest+ (4.10 and 4.20) when choosing "BadRAM patterns" as your error reporting mode. 

So my question is this...

The GRUB_BADRAM parameter in Grub2's configuration (/etc/default/grub) seems to expect a format of "0x00000000" for the bad memory address to be excluded. Memtest is giving me a "failed address" of "0000b609f90"

How should I enter that address into the GRUB_BADRAM parameter?

0x0000b609f90? 0x0b609f90? Or am I way off?

My guess is that for someone more familiar the syntax of memory addresses, this is a no brainier. Which might explain why I've had a hard time finding an answer with all of my googling.

Thanks in advance for any help!

---

### Post by fabricator4 on 2011-02-17
Neither I think.  It seems to require a memory address / mask pair as given by the memtest86+.

I haven't done it but there's some information [here]("http://www.gnu.org/software/grub/manual/html_node/badram.html").

You should probably remove the offending stick of memory and clean the socket and the contacts on stick then re-insert (careful of static, use a strap etc) and then run memtest86+ several times from cold to hot.  If the memory addresses come up bad in the same location every time, then you can use this address/mask information in badram.

Chris

---

### Post by Marturion on 2011-02-17
> **fabricator4 said:**
> Neither I think.  It seems to require a memory address / mask pair as given by the memtest86+.

I haven't done it but there's some information [here]("http://www.gnu.org/software/grub/manual/html_node/badram.html").

You should probably remove the offending stick of memory and clean the socket and the contacts on stick then re-insert (careful of static, use a strap etc) and then run memtest86+ several times from cold to hot.  If the memory addresses come up bad in the location every time, then you can use this address/mask information in badram.

Chris

Thanks for the response Chris, unfortunately the ram in question is integrated into the motherboard (laptop).

In my searching, I've run into the same grub documentation link you posted, but I'm afraid I still don't quite understand what information from Memtest+ I should enter as the memory address / mask pair.

For example, the information I have from Memtest+ is
Failing address: 0000b609d50
Good: fffffbff
Bad: ffff7bff
ERR Bits: 00008000

How should I (or can I?) translate that into the GRUB_BADRAM parameter located in /etc/default/grub ?

---

### Post by sydbat on 2011-02-17
> **Marturion said:**
> unfortunately the ram in question is integrated into the motherboard (laptop).There should be a service port door to install more RAM on the bottom of your laptop. This is where you will find your existing RAM and be able to R & R it.

What make / model is your laptop? Googleing it should bring up a manual that will show you how to do it.

---

### Post by Marturion on 2011-02-17
> **sydbat said:**
> There should be a service port door to install more RAM on the bottom of your laptop. This is where you will find your existing RAM and be able to R & R it.

What make / model is your laptop? Googleing it should bring up a manual that will show you how to do it.

It's a Toshiba Satellite A70

Yes, there is service door and an extra socket to include more RAM, but there is also integrated RAM on this particular model and unfortunately that's where the bad memory exists.

Thanks anyway though!

---

### Post by sydbat on 2011-02-17
> **Marturion said:**
> It's a Toshiba Satellite A70

Yes, there is service door and an extra socket to include more RAM, but there is also integrated RAM on this particular model and unfortunately that's where the bad memory exists.

Thanks anyway though!Dude, that sucks. I do not know if you could even disable integrated RAM. Maybe a BIOS setting? Of course, you would have to have other RAM installed first.

---

### Post by Marturion on 2011-02-17
> **sydbat said:**
> Dude, that sucks. I do not know if you could even disable integrated RAM. Maybe a BIOS setting? Of course, you would have to have other RAM installed first.

Yeah, not with this BIOS. That's one reason why Ubuntu is such a great option for this laptop - it'll keep it out of a landfill.

But first I need to learn how to properly place the information I got from Memtest+ into the "GRUB_BADRAM" parameter in /etc/default/grub ;)

---

### Post by hansolo4949 on 2011-02-17
Did you look in the ram door and see if there were any sticks if ram in there? I have NEVER heard of motherboards with integrated ram before, except for ones with integrated graphics, and even then, that is just ram fir the graphics card.....strange.

---

### Post by Marturion on 2011-02-17
> **hansolo4949 said:**
> Did you look in the ram door and see if there were any sticks if ram in there? I have NEVER heard of motherboards with integrated ram before, except for ones with integrated graphics, and even then, that is just ram fir the graphics card.....strange.


Well, I guess [you have now]("http://www.crucial.com/store/listparts.aspx?model=Satellite%20A70%20Series"). :)

I've had the board out in order to clean and re-seat the heatsink (and apply fresh thermal grease). So, I can verify there's no other (easily) removable memory.

And though I do have some previous experience successfully soldering chips to a main-board, I really don't want to go that route in this case. ;)

---

### Post by Marturion on 2011-02-17
For now, I'm going to attempt using memmap based on the information

here:
[http://gquigs.blogspot.com/2009/01/bad-memory-howto.html](http://gquigs.blogspot.com/2009/01/bad-memory-howto.html)

and

here:
[http://ubuntuforums.org/showthread.php?t=1342957](http://ubuntuforums.org/showthread.php?t=1342957)

However, I would still be interested in the answer to my original question regarding Memtest+ and BadRAM if there's anyone who knows.

Thanks again everybody for your suggestions and friendly assistance.

---

### Post by fabricator4 on 2011-02-18
Aaaagh!  I tried googling things like badram, mask etc and the first thing it offered up was this self same thread.  You've got me curious so I shall keep looking, maybe for a manual for badram.  

Does memtest+ always give the same errors in the exact same locations?  This is important obviously, since if the failures are more random you can't hit a moving target.

Chris

---

### Post by fabricator4 on 2011-02-18
OK, got it, I think.  I went and had a look at the instructions for badram again.  That prompted me to start memtest and have a look.  Start memtest and press 'c' for configuration and then:

4 Error reporting mode
3 Badram patterns

Try that and see if it gives you useful information.

Chris

---

### Post by vanrein on 2011-02-18
Hello,

Following is the BadRAM documentation.  It usually comes as part of the kernel patch, but inclusion in something as mainstream as Ubuntu probably means that you haven't seen it yet.


Good luck,

Rick "BadRAM" van Rein

[http://rick.vanrein.org/linux/badram/](http://rick.vanrein.org/linux/badram/)

---

### Post by vanrein on 2011-02-18
The documentation for BadRAM is part of the kernel source, and from the sound of it is missing from the current Ubuntu release.  I'll attach the original documentation so you can download, read and use it.

Enjoy,

Rick "BadRAM" van Rein

[http://rick.vanrein.org/linux/badram](http://rick.vanrein.org/linux/badram)

---

### Post by fabricator4 on 2011-02-18
Thanks Rick,  That file on your website was going to be my next stop.  After sleep.  Hopefully Dan will be able to get some useful data out of memtest86+ and get this to work.  I really like the idea of being able to run Linux on an old laptop even though the fixed RAM is faulty.  Chalk one up for the good guys.

If badram.txt is included with 10.04 release it's awfully hard to find.  Another thing that's needed is a blow-by-blow instruction manual for people like Dan and myself who have never done this before.  Maybe there's one out there, but it also is not easy to find.

Hopefully Dan will be able to get some useful information from memtest86+ and figure out how to pass this to grub.

Chris.

---

### Post by Marturion on 2011-02-19
> **fabricator4 said:**
> OK, got it, I think.  I went and had a look at the instructions for badram again.  That prompted me to start memtest and have a look.  Start memtest and press 'c' for configuration and then:

4 Error reporting mode
3 Badram patterns

Try that and see if it gives you useful information.

Chris

Thanks Chris. Yes, I'm aware of the badram error reporting mode in memtest+, but have you actually gotten it to work when encountering an error? As I originally stated, there appears to be a bug in memtest+ so the badram patterns aren't displayed properly. In my case only a blank red bar show up when the error(s) are encountered (at least in two versions of memtest+ I tried - 4.10 and 4.20.)

That's why I am asking how to translate the default memtest+ report into a badram pattern that will work in the GRUB_BADRAM boot parameter (in /etc/default/grub). If I could just use the badram report already available in memtest+, this problem would have a much easier solution :)

> The documentation for BadRAM is part of the kernel source, and from the sound of it is missing from the current Ubuntu release. I'll attach the original documentation so you can download, read and use it.

Thanks Rick for BadRAM and for posting your badram.txt documentation here, I'll certainly look through that.

---

### Post by fabricator4 on 2011-02-19
Unfortunately (or fortunately for me!) I don't have any bad RAM to test this on.  

Maybe the data is right in front of you - the "Bad: ffff7bff" might be the mask you are looking for.  We might just be mislead about the statement that memtest86+ is going to present us with an addr:mask result.  If this is the case the "good" will be the compliment of the "bad" mask.  You only need the "bad" mask for badram:

```

Failing address: 0000b609d50
Good: fffffbff
Bad: ffff7bff
ERR Bits: 00008000

11111111111111111111101111111111 = Good
11111111111111110111101111111111 = Bad
00000000000000001000000000000000 = ERR bits

```

Umm, is ERR bits the part you need, the "mask". It's all I can see at the moment...

Rick? Anyone?


Chris

---

### Post by vanrein on 2011-02-23
There was a request for a more detailed explanation than the kernel readme.  This is a Linux Journal article that may help; note however that their layout shows 0<\#215>1234 instead of 0x1234.

[http://www.linuxjournal.com/article/4489](http://www.linuxjournal.com/article/4489)

Good luck,
Rick "BadRAM" van Rein

---

### Post by bobblanchett on 2011-10-23
The format of the badram part varies in length for x86 and x64 machines.

When you run memtest+ choose (c)onfigure then error formats then badram patterns
Then continue.

If memtest+ finds errors (and it may take hours or multiple runs)  it will spit out a badram kernel parm in 32 bit format:
badram=0xbaseaddress,0xmemorymask

If one is or more modules are badly affected you may have several address/mask pairs as the value of the badram key.

eg
 badram=0xdeadbeef,0xfffffffc

For x64 machines you must left pad the base address with 8 zeros and the mask with 8 f's.
as root, Edit /etc/default/grub then update-grub

Read badram.txt in the newer badram patches for details

Cheers,
Bob

> **Marturion said:**
> For now, I'm going to attempt using memmap based on the information

here:
[http://gquigs.blogspot.com/2009/01/bad-memory-howto.html](http://gquigs.blogspot.com/2009/01/bad-memory-howto.html)

and

here:
[http://ubuntuforums.org/showthread.php?t=1342957](http://ubuntuforums.org/showthread.php?t=1342957)

However, I would still be interested in the answer to my original question regarding Memtest+ and BadRAM if there's anyone who knows.

Thanks again everybody for your suggestions and friendly assistance.

---

### Post by Dreamer Fithp Apprentice on 2012-03-27
I'd love to know if OP ever got either of these approaches to work. For that matter has anyone figured how to get either to work for any Ubuntu? The text file the BADRAM gent attached was talking about LILO so it wasn't at all clear to me that it had any applicability to grub.

I got to this thread by using Ixquick/Google to try to find exactly what OP was asking for - how to get from memtest86 report nomenclature to BADRAM= nomenclature and I can't find anything on what I would have thought would be simple. It is hard to find any place where even the question is articulated clearly and I got no smell of an answer.

Is there any logical reason to prefer one approach over the other? I mean besides not being able to find any clear instructions on how to use one or both. I looks to me like in both cases this same fix will have to be done separately for each OS on the system. It would seem to me that the /etc/default/grub file containing the BADRAM= statement would have to be redone with any new installation but that the e approach might carry over if the new installation uses grub.

If there is any practical way to use either approach I sure would love to find clear instructions.

Edit added a few minutes later: I didn't notice this [http://ubuntuforums.org/showthread.php?t=1342957](http://ubuntuforums.org/showthread.php?t=1342957) , post # 2 before posting. It's a third approach. Post is 2 years old but the statement sisco is writing about is still there in /etc/default/grub with a pair of empty quotation marks waiting to be filled. So I filled it thus: 

GRUB_CMDLINE_LINUX="65M\$570M"

Following sisco311's instructions I did "sudo update-grub" and confirmed that a change had been made in /boot/grub/grub.cfg. I rebooted and haven't crashed. But since this doesn't take effect, assuming it works, until after I boot this OS, memtest can't test it. So how do I know if it worked?

---

### Post by keyz182 on 2012-03-29
I managed to get this all working rather, err, accidentally.

It seems memtest still doesn't show addresses properly in BadMem error reporting mode. That is, unless you mash the keyboard in frustration! There may be documented somewhere "Press x to display address" or something, but not that I saw.

Anyhoo, random mash of the keys (I think in the Arrows area) caused the badmem line to show up, copied it down, plonked it into /etc/defaults/grub and all is well.

I'm rather stretched for time at the mo, so I can't go poking around to see if it's a bug (and/or repeatable) unfortunately.

---

### Post by Dreamer Fithp Apprentice on 2012-03-30
Interesting. I assume you mean BADRAM. If you can recall anything else about just when in the sequence you pressed the random keys, like if you had just booted memtest or had you already started pressing some keys in the "menu" it might be helpful. I'll try some pressing some keys in the arrow vicinity next time. 

I'm still interested to know if anyone knows any reason one of these methods is to be prefered over another. The way it seems to me from reading some archived discussions is that the BADRAM function was redundant with less well known functions the kernel already had before kernel 3 but that it got incorporated anyway as an alternate syntax because a lot more people were familiar with it but that is half a guess.

And even more I'd love to know of some way to test the function of these statements to confirm that they are doing what I think they are doing.

---

