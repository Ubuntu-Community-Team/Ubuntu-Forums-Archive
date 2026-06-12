---
title: "DVD wont play"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by xdarkday on 2010-01-14
I am running 9.10 on my macbook 1.1


Sometimes it will let me play a movie, sometimes it wont. When it doesnt, the dvd drive will act like its trying to read the dvd then spit it out.

I have not been able to find a way to get it working consistantly, and at this point I think anything I did to fix the problem was just coincidence to it working sometimes. Any help?

Also, under Places, it shows a 4.9 gb file system which may be a weird mounting issue (with no dvd in the laptop)

---

### Post by audiomick on 2010-01-14
do you still have OS.X on the box, and if you do, does the drive work properly?
It sounds to me like the drive is dying.

---

### Post by xdarkday on 2010-01-14
> **audiomick said:**
> do you still have OS.X on the box, and if you do, does the drive work properly?
It sounds to me like the drive is dying.

I dont, and I dont have a copy of OSX either. 

This **really** seems like a software issue to me. 

The DVD player will stop working right after I eject a disc. Meaning, if I eject the disc and try and put another one in right after, it wont play. However, when it does work, it works till I am done using it. 

After a few restarts, or some messing around it will play one disc. That is why I think its some kind of mounting issue. like it is not really unmounting, and it decides it wont play a disc.

So maybe a step by step.

Lets say its been a few days since Ive used the DVD drive. I put a movie in, and it will work perfectly. 

I eject the disc to watch another movie, the DVD drive will try to read it, then spit it back out.

This will happen EVERY time. This is the problem.

---

### Post by audiomick on 2010-01-14
> **xdarkday said:**
> Sometimes it will let me play a movie, sometimes it wont. When it doesnt, the dvd drive will act like its trying to read the dvd then spit it out.


This sound mechanical to me. If it were not mounting or something, I don't think the drive would react. Spitting it out indicates, in my experience,  that the drive doesn't think it is a valid media. If it is consistent, and the cd's are known to be good, then it could well be that the drive isn't managing to read them.

However, this is speculation at this distance. Wait and see if someone else has a different opinion.

---

### Post by xdarkday on 2010-01-14
> **audiomick said:**
> This sound mechanical to me. If it were not mounting or something, I don't think the drive would react. Spitting it out indicates, in my experience,  that the drive doesn't think it is a valid media. If it is consistent, and the cd's are known to be good, then it could well be that the drive isn't managing to read them.

However, this is speculation at this distance. Wait and see if someone else has a different opinion.

I really just do not believe that is what is happening. I dont want to say you're wrong, but just by what Ive expericance with this issue, it just doesn't seem like my first guess. Usually with disc read errors/drive going out, it will happen even after discs will start, and just be random untill the problem gets worse. My issue however is ore consistent to what I think is a mounting issue. 

It really seems like the same issue that is going on in this thread
[http://ubuntuforums.org/showthread.php?t=1328830](http://ubuntuforums.org/showthread.php?t=1328830)

It seems a bit of people are have similar issues.

---

### Post by llamabr on 2010-01-14
I would guess hardware issues, too.  Does it have any trouble mounting disks that are not dvd?

---

### Post by running_rabbit07 on 2010-01-14
If you have all of the codecs and such from the medibuntu repo, then it has to be hardware. If you haven't install all of the codecs and such, then that is what needs to be done.

---

### Post by llamabr on 2010-01-14
I tend to believe there's a problem with the hardware, too.  But I find it difficult to see how not having the codecs would cause the drive to spit out the disk.  It wouldn't play the media (if it's a dvd), but there's no reason not to let it physically sit in there.

---

### Post by running_rabbit07 on 2010-01-14
> **llamabr said:**
> I tend to believe there's a problem with the hardware, too.  But I find it difficult to see how not having the codecs would cause the drive to spit out the disk.  It wouldn't play the media (if it's a dvd), but there's no reason not to let it physically sit in there.

One of my machines used to spit out movie DVDs, it was fine with data DVDs.

---

### Post by xdarkday on 2010-01-14
> **llamabr said:**
> I tend to believe there's a problem with the hardware, too.  But I find it difficult to see how not having the codecs would cause the drive to spit out the disk.  It wouldn't play the media (if it's a dvd), but there's no reason not to let it physically sit in there.

I think the macbook drive might work different than a normal pc drive. I just put a normal CD in there and it was fine. Im not sure codecs are an issue since I am able to play dvds often. Just not one right after another.

---

### Post by audiomick on 2010-01-15
HI. I have already put in my 2 bob's worth, and don't want to start up again, but here are some more thoughts anyway;)

Please note that I do not wish to exclude the possibility of a software fault. Maybe that is your problem. All I want to do is offer you things to think about, to help you find out what is going on.

> **xdarkday said:**
> I think the macbook drive might work different than a normal pc drive.
Maybe, but I don't think they can be too different. I don't know how it is with DVD drives, but with CD drives there were effectively only two manufacturers, phillips and one other.

> **xdarkday said:**
>  I just put a normal CD in there and it was fine.
This would correspond well with the laser getting out of alignment or bearings getting loose and causing bad alignment. The "hole size" that the laser has to read is a lot bigger for a CD than for a DVD. This means that the drive can become a lot more imprecise and still read a CD than it can for a DVD. Example: my old laptop (toshiba, so good quality) could, in the end, not read DVD's at all, not burn CD's at all, read most, but not all, cd's. In windows the same as in Ubuntu.


 > **xdarkday said:**
> Im not sure codecs are an issue since I am able to play dvds often.
If you can play DVD's at all, then the codecs are there.

> **xdarkday said:**
>  Just not one right after another.
I gather that is absolutely consistent, i.e. when you have played a DVD, you can never play another one immediately after. What happens if you let the computer sit for a half an hour or so without doing anything with it and then try again? 

Here's the logic: Something might be getting warm with use and inducing a malfunction. The indexing on a DVD is always on a specific part of the disc. The drive can just manage to read this for the first DVD, but not anymore for the second.

---

### Post by xdarkday on 2010-01-15
> **audiomick said:**
>  What happens if you let the computer sit for a half an hour or so without doing anything with it and then try again? 


the same problem. it wont play.

I just want to say thank you for your help!:popcorn:

---

### Post by audiomick on 2010-01-15
If you reboot immediately and try again, does it work?
What about just log off and back on?

If one of those helps, it would be an indication of a software problem.

It just occurs to me, how are you ejecting the DVD's, and which player are you using. That won't tell me much, but might mean something to someone else who reads this.

---

