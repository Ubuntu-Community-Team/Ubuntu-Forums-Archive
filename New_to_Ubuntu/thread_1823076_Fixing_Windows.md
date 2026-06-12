---
title: "Fixing Windows"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by (Nes) on 2011-08-11
My computer is having a "SMART" error on the HD, yes, yes I know imminent failure, but no way to turn the damn thing off so I can FIX the problem... trying to outsmart themselves... 
It's an HP with the "BIOHD-8" issue, I can't seem to find anyway to actually fix this problem at all. Everyone just says "buy a new one", well that's not really fixing it!! :-({|=

Anyway.

I need to do SOMETHING to my HD from Ubuntu (running off an external drive right now) so that I can access my most recent _important_ documents/pictures, pull them off the HD then take it out back and beat the living crap out of it...

When I try to access right now I'm getting the 

> 
ErrorError mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.So what do I need to do to accomplish my goal? 

I'm brand new to Ubuntu but this is just amazing, wish I'd switched years ago!! What I would call 'moderate' computer skills, so I can follow directions :D

I can NOT boot up windows. 

Thanks.

---

### Post by Gone fishing on 2011-08-11
If you are getting smart errors the drive is failing.

I would download parted magic a live distro with lots of tools for dealing with disks  etc. 

I think you could mount the ntfs partition possibly using the force option then get the data off and copied to something else quick. If that fails the I think using the dd command copy the data to another disk maybe what you need to do.

---

### Post by (Nes) on 2011-08-15
Finally got things ready on the external, I'm ready to get into the main HD of the computer. I've got GParted booted up and told it to run a check and I get this:

> 
Error (5): Opening (drive) as NTFS failed: input/output error NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE! ...



Yeah, I can't START windows, that's why I'm trying to get into from Linux *headdesk*
I'd like to try the 'soft' method a little more before I just hack into the damn thing - any ideas? :S

---

### Post by Mark Phelps on 2011-08-16
Unfortunately, there is no Linux substitute for Windows CHKDSK -- and as long as it is failing, Linux will refuse to mount it.

If you have access to a Windows PC, you should Google for, download and burn Hiren's Boot Disk.  It comes with a host of filesystem utilities.  You might be able to use one of them to fix the filesystem on the drive.

---

### Post by (Nes) on 2011-08-25
Was a good suggestion, but no go.

Forced mount is going to work either...

Guess I'm copying :S. I really don't want to, it's only a few select folders I need off there I'm going to be deleting the rest anyway (completely caught the ubuntu bug!!)

---

### Post by Jerry N on 2011-08-25
No sweat - just get those important files from your backup.  You do have the important files backed up, don't you?

Jerry

---

### Post by sandyd on 2011-08-25
attach external/internal HD

Run ddrescue, or DD with 1kb bitsize.

DD/ddrescue will allow you to clone the drive onto the new external/internal HD. The drives don't have to be the same size, as long as the destination is larger then the source.

p.s. The new external/internal HD will be wiped out, and all the **original** data will be gone; replaced by the data from your failing HD.

p.p.s. Go take a day off while its running. It will take all day....

Smiles,

---

### Post by (Nes) on 2011-08-26
Jer the _important _stuff is backed up, but it's more recent art work that I'm going to loose - nothing I can't live with out. 

Sand that's the plan! :S 
I could use the external drive I'm running off now, but that's my backup, and I'm obv. going to have a to buy a new HD anyway so I'm just going to wait to do that. What to choose, what to choose... :-k


And thanks for all the help guys!! It's very much appreciated! I'm a total Linux convert (should have done it years ago), this system is amazing, I'll have to offer some spare time to pay back soon as I get this beast up and running properly :).

---

### Post by (Nes) on 2011-09-09
How I fixed it:

I don't know why I couldn't get it to work at first, but I swapped my external and internal HDD (the internal being the one that was not working) then I was able to run Hiren's boot disk :).

I ran the mini windows xp, was able to get in and run a disk check (with fixing enabled) on the broken drive, it took HOURS, but I gained access to my files!! That HDD still can't be booted up, but you can plug it in & have access to all the files/etc.

Now I just have to figure out how to partition my new drive, set up Ubuntu on it & off I gooooooo....!!

Thanks for all the advice guys! ):P

---

