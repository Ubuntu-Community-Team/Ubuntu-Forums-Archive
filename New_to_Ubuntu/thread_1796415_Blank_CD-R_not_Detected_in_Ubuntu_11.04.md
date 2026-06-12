---
title: "Blank CD-R not Detected in Ubuntu 11.04"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by courage1919 on 2011-07-03
Whenever I right click ubuntu-10.04.2-desktop-i386.iso, then 'Write to Disc...", it says "Please replace the disc with a supported CD or DVD." when a blank CD-R is in the disc tray. What's wrong?

---

### Post by wolfen69 on 2011-07-03
Have you tried a burning program such as Brasero or K3B?

---

### Post by courage1919 on 2011-07-03
Brasero doesn't recognizes it. Though, I haven't tried K3B.

---

### Post by wolfen69 on 2011-07-03
Do you have another brand of discs you can try?

---

### Post by courage1919 on 2011-07-03
Yeah, but they're DVD-R and they don't work with my Ubuntu computer. I just tried K3B and it too said that there was no disc in the tray when a blank CD-R was in it.

---

### Post by wolfen69 on 2011-07-03
When was the last time the cd drive worked?

---

### Post by courage1919 on 2011-07-03
When I installed Ubuntu 11.04 with a live CD.

---

### Post by psusi on 2011-07-03
Are you sure it is actually blank?  Try another one maybe?  Can it read a standard CD-ROM disc?

---

### Post by wolfen69 on 2011-07-03
Boot to the live cd again and see if it works.

---

### Post by courage1919 on 2011-07-04
> **psusi said:**
> Are you sure it is actually blank?  Try another one maybe?  Can it read a standard CD-ROM disc?
Yes, it is. I've tried my other blank CD's and they are not recognized either. Does it count if it reads a CD album that I have as a CD-ROM disc in your last question?


> **wolfen69 said:**
> Boot to the live cd again and see if it works.
I did so many times. No luck.

---

### Post by jtarin on 2011-07-04
I've had various successes with CD-R and DVD-R in windows and Ubuntu. It depends on the brand sometimes too. I normally use CDRW and DVDRW as they always work.

---

### Post by amjjawad on 2011-07-04
Have exactly the same problem and couldn't manage to fix it as of now.

CD-R can be detected.
DVD-R and DVD+R can NOT be detected.

No matter what Software I use, it has nothing to do with this. 
I changed my Drive but still nothing.

My blank CDs/DVDs are Imation.

When a non-blank DVD is inserted, it works (Ubuntu detects it). However, a blank one can't be detected.

So far, the issue only with Blank DVDs. Blank CDs are detected after I changed my Drive.

So, you're not alone :)

P.S.
This is Ubuntu 10.04.2

---

### Post by amjjawad on 2011-07-04
> **courage1919 said:**
> I did so many times. No luck.

Do you mean that you could not boot your machine from your LiveCD?

When you insert any other CD/DVD which is NOT blank, is it readable?
or detectable?

---

### Post by mcduck on 2011-07-04
If you can't even boot with th live-CD, even though you previously were able to do that, then it's not a software/OS problem but an actual hardware issue. Check that the drive's cables are properly connected. If you hear the drive at least trying to read th disc, then you could try using a cleaning disc. IF it doesn't even try, then it's most likely broken and you'll just have to replace it with a new one.

---

### Post by courage1919 on 2011-07-04
> **amjjawad said:**
> Do you mean that you could not boot your machine from your LiveCD?

When you insert any other CD/DVD which is NOT blank, is it readable?
or detectable?
I could boot it from Live CD as the same as you said in your first post in this thread. Basically, any blank CD-R that has something in it (Ubuntu 10.04 live CD, Gparted, etc.) can be detected. BUT, if it's a for sure blank CD-R with NOTHING in it, and I want to burn it with some .iso file, it WON'T be detected. It's really strange. I too checked my drivers and there was no problems.


> **mcduck said:**
> If you can't even boot with th live-CD, even though you previously were able to do that, then it's not a software/OS problem but an actual hardware issue. Check that the drive's cables are properly connected. If you hear the drive at least trying to read th disc, then you could try using a cleaning disc. IF it doesn't even try, then it's most likely broken and you'll just have to replace it with a new one.
But then why does it detect a blank CD-R with something in it and doesn't detect a blank CD-R without anything in it?

---

### Post by amjjawad on 2011-07-04
> **courage1919 said:**
> I could boot it from Live CD as the same as you said in your first post in this thread. Basically, any blank CD-R that has something in it (Ubuntu 10.04 live CD, Gparted, etc.) can be detected. BUT, if it's a for sure blank CD-R with NOTHING in it, and I want to burn it with some .iso file, it WON'T be detected. It's really strange. I too checked my drivers and there was no problems.


Then it should NOT be a Hardware issue, it must be something that we are not aware of. I'm not sure how to fix that but hope someone could tell us.

Before I changed my CD/DVD Writer Driver, even CD-R could NOT be detected. Now, only DVD-R and DVD+R. I'm talking about BLANK CDs/DVDs with no data at all. Totally blank.
Weird!

---

### Post by mcduck on 2011-07-04
> **courage1919 said:**
> I could boot it from Live CD as the same as you said in your first post in this thread. Basically, any blank CD-R that has something in it (Ubuntu 10.04 live CD, Gparted, etc.) can be detected. BUT, if it's a for sure blank CD-R with NOTHING in it, and I want to burn it with some .iso file, it WON'T be detected. It's really strange. I too checked my drivers and there was no problems.



But then why does it detect a blank CD-R with something in it and doesn't detect a blank CD-R without anything in it?

How can you call a CD "blank" it it has something in it? :D

So the drive actually *does* detect any non-empty discs? Then it's a different case indeed.

Could you open a terminal and run "wodim -prcap" and post the output here? (the command will list the capabilities of your optical drive)

---

### Post by courage1919 on 2011-07-04
> **amjjawad said:**
> Then it should NOT be a Hardware issue, it must  be something that we are not aware of. I'm not sure how to fix that but  hope someone could tell us.

Before I changed my CD/DVD Writer Driver, even CD-R could NOT be  detected. Now, only DVD-R and DVD+R. I'm talking about BLANK CDs/DVDs  with no data at all. Totally blank.
Weird!
I'm glad it's not just me and thanks for sticking out, man. I'm using a Dell Optiplex 270, by the way.


> **mcduck said:**
> How can you call a CD "blank" it it has something in it? :D

So the drive actually *does* detect any non-empty discs? Then it's a different case indeed.

Could you open a terminal and run "wodim -prcap" and post the output here? (the command will list the capabilities of your optical drive)
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device was not specified. Trying to find an appropriate drive...
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SAMSUNG '
Identification : 'CD-ROM SC-148A  '
Revision       : 'B403'
Device seems to be: Generic mmc CD-ROM.
wodim: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.

---

### Post by amjjawad on 2011-07-04
I think it's:

```
wodim pregap

```

---

### Post by mcduck on 2011-07-04
> **courage1919 said:**
> I'm glad it's not just me and thanks for sticking out, man. I'm using a Dell Optiplex 270, by the way.



wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device was not specified. Trying to find an appropriate drive...
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SAMSUNG '
Identification : 'CD-ROM SC-148A  '
Revision       : 'B403'
Device seems to be: Generic mmc CD-ROM.
wodim: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.

Is the "Samsung SC-148A" correct manufacturer & model for the drive? If it is, it's not a CD writer, just a CD-ROM drive.

That would actually fit, as at least based on the manufacturer specs there are plenty of Optiplex 270 versions shipped with just a CD-ROM drive...

---

### Post by mcduck on 2011-07-04
> **amjjawad said:**
> I think it's:

```
wodim pregap

```

no, it definitely isn't.

"wodim" is the name of the program (used for writing CDs and DVDs from command line. And "-prcap" is the option used to list detected write capable drives and their specs.

[http://manpages.unixforum.co.uk/man-pages/linux/opensuse-10.2/1/wodim-man-page.html]("http://manpages.unixforum.co.uk/man-pages/linux/opensuse-10.2/1/wodim-man-page.html")

---

### Post by dFlyer on 2011-07-04
Are you sure this is a cd recorder and not just a cd player?

---

### Post by schily on 2011-07-04
> **amjjawad said:**
> Have exactly the same problem and couldn't manage to fix it as of now.

CD-R can be detected.
DVD-R and DVD+R can NOT be detected.

No matter what Software I use, it has nothing to do with this. 


It is most unlikely that you will have problem if you use recent original software.

Try to use the original cdrtools. There are no known problems with this software.

---

### Post by amjjawad on 2011-07-04
> **mcduck said:**
> no, it definitely isn't.

"wodim" is the name of the program (used for writing CDs and DVDs from command line. And "-prcap" is the option used to list detected write capable drives and their specs.

[http://manpages.unixforum.co.uk/man-pages/linux/opensuse-10.2/1/wodim-man-page.html](http://manpages.unixforum.co.uk/man-pages/linux/opensuse-10.2/1/wodim-man-page.html)

I don't know ... I posted the command you provided but it said there is no such command.
I guess it's clear now.

---

### Post by mcduck on 2011-07-04
> **amjjawad said:**
> I don't know ... I posted the command you provided but it said there is no such command.
I guess it's clear now.

If you are using a distribution other than Ubuntu or are running old enough release, you might have cdrtools instead of cdkit, and therefore no wodim (in that case you'll probably have cdrecord instead, and it should have similar option for checking drive capabilities). And of course if you are running something more custom than the normal Desktop setup you might not have either one installed.

Wodim is included by default on any recent Ubuntu desktop install.

Anyway, "wodim pregap" wouldn't make any sense, as options are almost always preceded by a dash, and obviously we aren't even trying to set a pre-gap but determine the drive specs instead. ;)

---

### Post by amjjawad on 2011-07-04
> **mcduck said:**
> If you are using a distribution other than Ubuntu or are running old enough release, you might have cdrtools instead of cdkit, and therefore no wodim (in that case you'll probably have cdrecord instead, and it should have similar option for checking drive capabilities). And of course if you are running something more custom than the normal Desktop setup you might not have either one installed.

It's Ubuntu 10.04.2 so maybe that's old enough? :)

> Wodim is included by default on any recent Ubuntu desktop install.

I guess it's 11.04.


> Anyway, "wodim pregap" wouldn't make any sense, as options are almost always preceded by a dash, and obviously we aren't even trying to set a pre-gap but determine the drive specs instead. ;)
Need some extra time to learn these stuff :)

Thanks :)

---

### Post by courage1919 on 2011-07-05
> **mcduck said:**
> Is the "Samsung SC-148A" correct manufacturer & model for the drive? If it is, it's not a CD writer, just a CD-ROM drive.
 
That would actually fit, as at least based on the manufacturer specs there are plenty of Optiplex 270 versions shipped with just a CD-ROM drive...
 I dunno. All I know is that this computer was at least ten years old.

---

### Post by wolfen69 on 2011-07-05
> **courage1919 said:**
> I dunno. All I know is that this computer was at least ten years old.

What does it say on the cd drive itself? If it's a burner, it will say "rewritable" on it.

---

