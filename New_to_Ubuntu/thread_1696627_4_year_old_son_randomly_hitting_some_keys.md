---
title: "4 year old son randomly hitting some keys"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by Devilham on 2011-02-27
My kid just started randomly hitting my keyboard while still booting, now  when trying to boot I get sent to what appears to be the grub loader, and I need to pick an OS, but the one I would think that is my install doesn't boot any longer.  I am not sophisticated enough at this time to know how to repair the existing install, and a search of the forums came up with nothing, kind of baffling.  Any ideas?

---

### Post by grahammechanical on 2011-02-27
Even if you are not dual booting between two operating systems there is usually more than one kernel on the Grub menu. Even though you may not usually see it if you only have one OS.

Older kernels are still there, usually. There should also be a rescue boot option. Have you tried loading any of these? Where on these forums have you looked? I have seen some posts with similar problems. Although your's is the first post that put the responsibility on to a four year old child.

Regards.

---

### Post by Devilham on 2011-02-27
"Although your's is the first post that put the responsibility on to a four year old child."

Ouch!  I laughed out loud on that one, I don't blame the little guy, it is what it is....just was hoping there was a repair option somewhere, or a technique!  Don't sweat it though, as there was no real data on the machine I am just going to wipe it and re-install, only reason for this thread is that I was having some trouble with that as well (hanging at a certain point), but now am going to reformat the drive and try from there....thanks for the judging!!! (just kidding, I am assuming you were being snarky, lol!)

---

### Post by Devilham on 2011-02-27
Oh, and yes, I tried the older kernals as well, no dice for some reason, who knows what the little rapscallion commanded the damn thing to do!

---

### Post by jerenept on 2011-02-27
Did you try booting the recovery options as well as the normal ones?

---

### Post by Devilham on 2011-02-27
I see them there, but am not sure what to do with them, very new to the linux scene, so am not sure what to do from the command line that they seem to present

---

### Post by Hedgehog1 on 2011-02-27
***If the little 4 year old loves keyboards already, he may be a great programmer someday!***

If you opt to do a full re-install, that is easy if Linux is the only OS.  If this is a dual boot, it is a little harder.

As to the OS choices you see - they are really 'Linux kernel' choices, and the one at the top is the current one.

Each Kernel also offers the second 'recovery' version so if the new drivers of an update are locking the system, you can get in and fix things.

:KS

---

### Post by Devilham on 2011-02-28
I see, I think I have a bigger problem though, as it appears the hard drive has become flagged as locked.  I tried re-installing Ubuntu, and it would hang at a certain point,  so I ran Ubuntu from a USB stick, and tried to mount the drive, and am getting a message that it's locked.  I am going to try some utilities I have used in the past to to try and clear this up (partition magic, and a neat little app called suisse knife), but if anyone else has some insight, any info would be useful.

---

### Post by Hedgehog1 on 2011-02-28
We just saw this on another users system a few days ago.

Using gparted, go to the swap partition and right click on it and select 'swapoff'.

The liveCD is using the swap partition on the hard drive, keeping it locked.  I didn't know it could do this until this weekend (so much to learn!).

:KS

---

### Post by Devilham on 2011-02-28
That sounds like the deal, can't test it tonight but will tomorrow and will let you know how it works out....and thanks!  By the way, I managed a workaround (I had another HD, so I installed to there), but want to test this theory out none the less!!!!

---

### Post by Hedgehog1 on 2011-02-28
I believe that it will work for you.

Hey, for the keyboard loving 4 year old:  Do they offer C++ classes in kindergarten now?  If so, sign the little guy up!

***The Hedge***

:KS

---

### Post by Devilham on 2011-03-01
hmm, well that wasn't the case, but it was a very good theory.  Whatever happened (and at this point, I think I can now clear my boy of wrongdoing, I think this was actuall a coincidence of him hitting the keys, and the HD going **** up at the same time).  According to Gparted (I should have checked this in the first place), there are bad sectors on this disk, and the file system is corrupted....so nothing to it but to reformat it and see if it works...which was the plan anyways, thanks everyone for the help, as always, the Ubuntu community was really awesome.....even the guy who accused me of blaming my son :P  !!!!

---

### Post by Devilham on 2011-03-01
It's actually the reason I built the machine (for him to play with), as he is showing a great deal of interest in computers, so who am I not to indulge??

---

### Post by HereInOz on 2011-03-01
If there are bad sectors, it may be worth getting a new hard drive, rather than reformatting it.  

Bad sectors, like 4 year olds, have a tendency to grow and become even more troublesome as time goes on.

---

### Post by pricetech on 2011-03-01
If it's for your kid, may I suggest edubuntu ??  My 3 year old Granddaughter had fun sitting in grandpa's lap playing with the games.

---

### Post by Devilham on 2011-03-01
you may suggest, could you tell me a bit more about Edubuntu?  The little man loves to learn, and is very interested in computers, I would really like to nurture this

---

