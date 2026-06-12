---
title: "Mark thread as [AVOID]?"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by Mariane on 2009-10-23
Is there a way to mark threads as [AVOID] or something when following the instructions there can lead to disastrous results? 

I am CERTAIN the advice I received was well intentioned, it's just that it did no work for me. I don't want to complain about the person who gave me this advice, I want to thank him for at least trying to help. 

Mariane

---

### Post by coolbrook on 2009-10-23
For your own purpose or for others?  You can subscribe to the thread as a reminder of the author/participants.

---

### Post by kansasnoob on 2009-10-23
> **Mariane said:**
> Is there a way to mark threads as [AVOID] or something when following the instructions there can lead to disastrous results? 

I am CERTAIN the advice I received was well intentioned, it's just that it did no work for me. I don't want to complain about the person who gave me this advice, I want to thank him for at least trying to help. 

Mariane

Personally I'd click on report. The moderators can decide whether it's (a)well intentioned but just wrong, (b)downright malicious, or (c)something else.

In my experience the mods are level headed and fair minded about such things. I've made mistakes myself and it's good to know when I have.

---

### Post by Mariane on 2009-10-23
For other people. I'm certain I won't make the same mistake again (though I'll certainly make others). My computer ended up in the repair shop so this is one I'll remember :P .

I don't want to report the poster even though I'm sure the moderators are good people, it just sounds so unfriendly. 

Mariane

---

### Post by tahitiwibble on 2009-10-23
Would you like to let us know what happened so that we can avoid the same catastrophe?

---

### Post by kansasnoob on 2009-10-23
> **tahitiwibble said:**
> Would you like to let us know what happened so that we can avoid the same catastrophe?

+1! At least show us.

---

### Post by CharlesA on 2009-10-23
I am curious as well.

---

### Post by QIII on 2009-10-23
If this is a reference to your problems with VirtualBox (I looked through your posts), the failure may or may not be due to that.

People use VirtualBox all the time without problems.

I wouldn't be so hasty as to fall into the "Post Hoc Ergo Propter Hoc" fallacy and conclude that either VirtualBox or anyone's help in correcting the issue was at fault for the issues you encountered just because the issue happened after the something else occurred.

Either of those may have been at fault.  But those are only two of a number of possibilities and the problem may have been caused by any or a combination of them.  Assuming it to be one of those is a Faulty Causation Fallacy known as the Fallacy of Reduction.

Eh ... sorry.

Science guy here.

---

### Post by Mariane on 2009-10-23
I could not boot from the hard disk but I could boot from Ubuntu CD and (apparently) still access my files. 

I was advised to hit "Escape" during boot to access grub and to use it to check the disk. It returned errors then suggested I typed fsck without -a or -p parameter. I did. More error messages and the only option to the questions was "yes". Type 'y' for "yes" or just sit there looking at the computer. I was asked to do this over and over again, eventually I got fed up and tried to reboot. 

It didn't boot from the hard disk. It booted from the Ubuntu CD but I couldn't access my files anymore. Fsck that. So back to the shop, luckily it is still well under the guarantee. 

As far as I can understand you, Q3, yes, I don't know whether the advice was bad or anything, so I don't want to report this guy. I just want to tell people to be careful if they find themselves in the same situation. 

Mariane

---

### Post by CharlesA on 2009-10-23
Ah, I thought it might be the VirtualBox thing. Sucks that something happened to the drive, but it didn't necessarily mean that it was caused by VBox. Since it's a laptop, it could have had a hardware malfunction even if it's only 2 weeks old.

At least you were able to return it for service. :-)

If it was the poster that said to enter GRUB to try different kernels, that would have not causes the drive to "eat it."

---

### Post by bkratz on 2009-10-23
> **Mariane said:**
> I could not boot from the hard disk but I could boot from Ubuntu CD and (apparently) still access my files. 

I was advised to hit "Escape" during boot to access grub and to use it to check the disk. It returned errors then suggested I typed fsck without -a or -p parameter. I did. More error messages and the only option to the questions was "yes". Type 'y' for "yes" or just sit there looking at the computer. I was asked to do this over and over again, eventually I got fed up and tried to reboot. 

It didn't boot from the hard disk. It booted from the Ubuntu CD but I couldn't access my files anymore. Fsck that. So back to the shop, luckily it is still well under the guarantee. 

As far as I can understand you, Q3, yes, I don't know whether the advice was bad or anything, so I don't want to report this guy. I just want to tell people to be careful if they find themselves in the same situation. 

Mariane




All this person did was to ask you to try an older kernel version--he said nothing about checking for errors simply to report back what you found.

[http://ubuntuforums.org/showthread.php?t=1298471&highlight=Mariane](http://ubuntuforums.org/showthread.php?t=1298471&highlight=Mariane)

What exactly did he do wrong?

---

### Post by QIII on 2009-10-23
Lesson learned, of course:  fsck is a powerful and potentially dangerous thing, indeed.

I think that it might have been advisable to stop when you got that first "You may only answer Yes to this" question and jotted down the prompt.  Then you might have been able to get back on the forum and ask a question or two.

It is possible that you "fixed" something real good without realizing what was going on.

It is also possible that your disk simply went south.

I'm terribly sorry this happened, and I hope you can get it sorted out without too much cost.  

I'm a bit suspicious of the "oh, it has to go into the shop" response you got.  That's like the mechanic who tells you that you need $1000 worth of repair when you could have just tightened a widget with a crescent wrench you had in your garage.  Hopefully your warranty covers it...

There are ways to recover data with open source tools that might have been able to help at least get your important files back.  Then a wipe of the disk (using gparted and creating a monolithic NTFS partition, for instance) and use of the system restore disk you (ahem) should have made when you got the machine could have at least gotten you back to a reasonable starting point -- IF it came to that.

---

### Post by ikisham on 2009-10-23
Mariane, there's nothing to avoid there. You yourself said in the first post you phoned Dell and they said the HD had to be replaced. That's it.

---

### Post by Mariane on 2009-10-23
> **bkratz said:**
> 
What exactly did he do wrong?


Nothing. 

Something went very badly wrong but people here seem to have different ideas as to what caused it and I haven't a clue. 

One thing, though, what would be the point of asking here what I should answer to a question when the only option is to answer yes? In fact, what is the point of having the question there at all? 

Mariane

---

### Post by Dullstar on 2009-10-23
Hmm, maybe a system to allow the OP to mark a post as, "This advice did not work?"  Could be useful, I suppose.

---

### Post by CharlesA on 2009-10-23
TBH, if the only thing it allows is "yes" google the message and see what it means before answering "yes."

The point of asking here would be that you know what exactly the error/message means before answering yes to it.

---

### Post by Mariane on 2009-10-23
> **Dullstar said:**
> 
Hmm, maybe a system to allow the OP to mark a post as, "This advice did not work?"  Could be useful, I suppose.


Yes, or even telling about your own mistakes. I could write [AVOID] Answering yes when you don't understand the question ;) 

Mariane

---

### Post by Penguin Guy on 2009-10-23
> **QIII said:**
> I wouldn't be so hasty as to fall into the "Post Hoc Ergo Propter Hoc" fallacy and conclude that either VirtualBox or anyone's help in correcting the issue was at fault for the issues you encountered just because the issue happened after the something else occurred.

Either of those may have been at fault.  But those are only two of a number of possibilities and the problem may have been caused by any or a combination of them.  Assuming it to be one of those is a Faulty Causation Fallacy known as the Fallacy of Reduction.
I had to read through a few wiki pages before that made any sense to me.

As for original question: Couldn't you just add a tag: 'doesn't work', or something similar?

---

### Post by alphaniner on 2009-10-23
Did the prompt look like this:

```
Fix<y>?
```

Because if so, that just meant that yes was the default, ie. what fsck would do if you typed nothing and just hit enter.  I've used fdisk before and I know the seemingly endless string of 'Fix<y>?' can be daunting... but you had options other than forcing a reboot.

---

### Post by Mark Phelps on 2009-10-24
Mariane:

Sorry you got burned using the SuperGrubDisk -- but that's one of the downsides of Linux that is often not mentioned -- with a lot of power comes the potential for a lot of damage.

The same kind of potentials for serious damage exist in other Linux-based utility disks.  For example, using the GParted LiveCD, you can easily remove ALL partitions from your hard drive.  And, by simply interrupting a partition resizing/moving operation, you can trash your filesystem beyond recovery.

Best advice I can provide for the future in Linux is, if you see a message that makes you feel uncomfortable, exit the utility without making any changes, and post the message to these forums.

That way, you can get one of the "experts" to advise you regarding the specific message you got.

---

### Post by k3lt01 on 2009-10-24
> **QIII said:**
> Eh ... sorry.

Science guy here.We would never have guessed :P

> **QIII said:**
> Lesson learned, of course:  fsck is a powerful and potentially dangerous thing, indeed. When using the fsck command the user is told it can cause more issues. Unfortunately this seems like a case of desperation without understanding what could happen when using such commands.

Mariane, you are not the first nor the last who will do something like this. I think when asking for help on the forums it is important to do further reading when you come across a command that isn't discussed in your thread.

---

