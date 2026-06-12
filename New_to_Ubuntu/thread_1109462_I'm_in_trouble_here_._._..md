---
title: "I'm in trouble here . . ."
date: 2009-03-28
forum: New to Ubuntu
---

### Post by photoikon on 2009-03-28
Any help appreciated.

I had a functioning Vista Ultimate SP1.

Made a little partition of 200 gig and a 4 gig Swap for Ubuntu.

Installed Ubuntu.  No Grub and Ubuntu wouldn't start, booted right into Vista every time.

Made some adjustments and finally got grub menu to pop up, and Ubuntu runs fine.  

Will not boot into Vista -- I get "NTLDR" not found

Then all of a sudden I get no grub again, boots right into Ubuntu, without even the CMOS screen ever popping up.

Got it to boot once into Vista Safe Mode, tried repairing the Vista install, and it tells me there's nothing wrong.

I'd like to just get out, get Vista back and put this on a standalone machine.  Need help getting my stuff back and accessible.  I'm sure it's just something pointing the wrong way, but am in over my head.

And the dual boot instructions looked so easy and straightforward!

Thanks 

m2

---

### Post by Paqman on 2009-03-28
> **photoikon said:**
> 
Made some adjustments

What exactly did you do?

---

### Post by photoikon on 2009-03-28
I did this:

sudo grub
root (hd1,0)
SETUP (hd1)
QUIT

That didn't work, so then I figured it wanted:

sudo grub
root (hd1,1)
SETUP (hd1)
QUIT

And that gave me the grub that had the Ubuntu in it that worked.  When I got out of Ubuntu and tried to select the Vista entry, that's when I got NTLDR not found

After that, I haven't had any control over anything that makes any difference, and why the grub loader quit showing up, I do not know.


Thanks
m2

PS.  I guess if I could get back to Vista, I'd try Easy BCE to try to get control, since it appears to be easier for an idiot to understand, but didn't know that at the time, since it appeared to be so simple.  I guess having so many different drives makes it complicated.

---

### Post by Paqman on 2009-03-28
> **photoikon said:**
> I did this:

sudo grub
root (hd1,0)
SETUP (hd1)
QUIT

That didn't work, so then I figured it wanted:

sudo grub
root (hd1,1)
SETUP (hd1)
QUIT


Ok. The way Grub works is like this:

hd1,0 = Second hard drive, first partition
hd1,1 = Second hard drive, second partition

It's a bit confusing, but bascially Grub starts numbering from 0.

So you've got two hard drives? Can you let us know where exactly you've got Vista and Ubuntu installed? Are these IDE or SATA drives, and if they're IDE, which have you set up as master?

---

### Post by photoikon on 2009-03-28
Here's the way it looks to me:

I have an old 500 gig drive that for some reason is drive 0 -- it doens't boot.

The second drive is the Vista boot drive and it has 759 gigs alloted to it.  On the same drive, I have the swap and the 200 gig partition for Ubuntu.

So I thought I did the right thing with the commands, since it was on hd1 and not hd0, which everything else on the web seems to automagically refer to and assume.

By the way, they're all SATA. The hd1 is master (I think) - how do I check that?  CMOS?  yikes

---

### Post by photoikon on 2009-03-29
Anyway, stayed up for as long as I could without my head hitting the desk.  No success.  

Got to thinking this morning . . . hmmmmmm.

About 6 mos ago had a problem with Vista and had to reload it.  It had originally been on the 500 gig drive, and I suspected as I talked with the "engineer" that he had left some stuff on it, but I had wanted to have Vista installed on the 1TB drive - and it appeared that is was, since that's where all the files were -- well, now it appears that "some" were not.  

So, I guess in guiding me through getting it up and running, he left some critical files on the 500 gig drive, the former boot drive, which I had been using, I thought, for storage only.

This morning, I unplugged the 500, booted with Vista CD and did repair on the 1TB.

Presto.  Back to normal.  Boots from there. No GRUB errors, NTLDR, etc.

Lesson is, if you have several drives, make sure you know where everything is, which sometimes is hard to do.

Now, since I have Vista booting, and I know it's only using the 1TB drive, (since I removed the 500 and formatted it) do I dare go back in and reinstall Ubuntu on a partition and try to dual boot?  Or should I just consider myself lucky not to have destroyed everything?

m2

---

