---
title: "can't see hdd on karmic install"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by DarinB on 2010-03-03
I have a laptop with a / on a 52gb hdd and a /home on a separate internal hdd with 200gb   yes this lap top has two internal HDDs.
karmic manual disc partitioner does not see the 52gb disk to make the / 
I was able to reformat the / and reinstall hardy on it 
i was recommended to delete the os on the / hdd 
the manual partitioner on karmic still does not see it. 
I had him clear the /boot flag and try again still can't see it. 
what is going on and all i want is a clean install of karmic with a separate /home hdd,,,,that is how i have my system and it worked great first time.

---

### Post by quixote on 2010-03-04
I wonder if it might be worth booting with a liveCD, making sure that 52GB drive is not mounted, and checking it with e2fsck or fsck?  If it has some bad blocks right at the beginning, maybe that's what is confusing parted.  (I know, it's a long shot.)

---

### Post by DarinB on 2010-03-05
that is really a good idea!!!!
but it has been reformatted and hardy heron was reinstalled on it, 
i had him wipe out the entire hdd unallocated then reformat it. 
now he was able to put re format again linuxMint 5 on it and it runs well. but i am sure he will want to go to LM 9 LTS or lucid LTS. I thought maybe he should install windows xp on it since it will really wipe out everything then do a dual boot with LM 9...not sure what to tell him since. he already made the comment that i keep in switching OSs on him, kind of a worrisome since his xp was blue screen and would not re install with out going to blue screen. 
ahhh the stress of computing!!! such fun huh? I think the boot sector of that hdd is messed up or had hidden checked on the partition flag and LM 8 or Ubuntu Karmic could not see it. Don't know why any variation of hardy can see that drive though...confusing situation.

---

### Post by quixote on 2010-03-05
I'm not sure, but I believe different partition editors, and even different versions of parted itself, can have different sensitivities to what they consider bad blocks.  At least, it seems to happen rather often that one method doesn't see bad bits when another one does.  False positives are tedious, but false negatives are actually worse!  So I say go by the fussiest method :D. 

Likewise reformatting, depending on the package doing it, can mark off bad blocks and cure these problems sometimes.

I've been running Lucid in virtualization and it looks really nice.  Seems very stable and the newer versions of Firefox, Thunderbird, and OpenOff all look real good.  But I don't use it day in, day out yet, and that's always the real test.  I would have said, stay with the Hardy and then do a direct upgrade to Lucid as the next LTS, but it sounds like you've already put LM on there.  In any case, he doesn't need to reformat to run a filesystem check.  The bottom line is go with whatever works!

---

### Post by DarinB on 2010-03-05
thank you for your clarity. that is what i suggested but use LinuxMint 5 based on Hardy Heron. and then go to LinuxMint 9 that will be based on lucid. not biggie just has all the codexes for the newbies. 
i an concerned about the bad blocks. but maybe i will have him do a fschk of the live cd or change the mount times so it forces a fscheck.
it is an enigma but i am believing more and more there must be some bad block where the mbr was. i would have thought the reformatting would have taken care of the bad blocks. thanks again.
and he is happy as a pig in sh* that he has lm 5 running. 
i don't have to worry about it until next fall when lm 9 is out and seasoned.

---

