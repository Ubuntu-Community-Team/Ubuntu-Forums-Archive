---
title: "Installation major oops!"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by rs321 on 2011-06-19
Folks,

Installing 10.04 from a disk and just as I got to the part about partitioning a circuit breaker opened and shut it down.  I restarted the computer when I could and now I get to the point in start-up where there's a choice to boot from a CD and everything stops.  It doesn't "freeze", per se, because the cursor still flashes but that's as far as it goes.

Anybody have any suggestions short of formatting the disk that this newbie (pronounced "moron") can do?

Thanks,

-Randy

---

### Post by coffeecat on 2011-06-19
First - the circuit-breaker opened when you were at the partitioning stage of the installer, but had you committed any changes? If not, there would have been nothing written to the hard drive, and re-formatting it is unlikely to help. So I wonder if the sudden power down may have done something else.

Can you clarify what this choice to boot from CD is? Is this a BIOS menu? Is it the live CD menu?

---

### Post by rs321 on 2011-06-19
coffeecat,

Thanks for the reply.  Before I got to the partitioning stage I had to make a few choices, although I can't say specifically what they were.

I'm not sure I understand your questions; I slid the CD into the drive and rebooted, and when I got the option I selected to boot from the CD.  The CD is from Rankin's "Official ubuntu Server Book" which I got from the library.

With or without the CD in the drive the boot now goes only to the option of booting from a CD, goes to a blank line under that, and then sits there and blinks at me.  None of the "F" keys do anything up to and including that point, which is where I got the idea that my pooch has been screwed.  I suppose I could try it with the Windows installation CD (I have WinXP installed) and see where that goes but I'm leery of digging a deeper hole for myself so I'll hold off on that maneuver until wiser minds prevail.

-Randy (who will now go paint a fence with a vengeance and a brush until he calms down)

---

### Post by coffeecat on 2011-06-19
> **rs321 said:**
> I'm not sure I understand your questions; I slid the CD into the drive and rebooted, and when I got the option I selected to boot from the CD.  The CD is from Rankin's "Official ubuntu Server Book" which I got from the library.

With some BIOS's you can press a function key to get a BIOS booting menu, to choose which device to boot from. I was wondering if perhaps that is what you were doing because the "choice to boot from a CD" didn't sound like the regular Ubuntu CD. And it wasn't because you were using a disc from a book, as I can now see! :) My guess is that the Rankin disc is starting properly, perhaps offering you the choice to boot from it or the HD, and stalling when you choose boot from CD. Whether that's a problem that's developed with the CD or part of your hardware is another matter and I agree about trying another bootable disc.

If you're nervous about using the Windows XP disc (you should be ok, so long as you abandon it before doing anything) you could download the Ubuntu CD ISO from here:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Choose 10.04 rather than 11.04 if that is what you want, and then burn the ISO to disc as described here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

That will give you the live desktop version rather than the server version which your book title suggests you may have been trying to install. But at least it gives you a bootable CD which is safe to try.

---

### Post by rs321 on 2011-06-19
coffeecat,

What I did was reinstall WinXP, which wasn't too bad because I did that yesterday, too, then began reinstalling ubuntu.  Looks as though it's not going to work because ubuntu gave me a message that one of the files on the CD is corrupt and I should delete the installation and start anew.  Trouble with that is I don't have a clue as to how I should delete it as that isn't an option so far as I can find.

Guess it's time to do some searching here for how to do it, which scares me just a tad because if I can't figure it out I take the hard drive back to the computer shop and have them format it again then have them burn what's on my USB stick onto a disk.  (I have plenty of disk burners on my computer but I don't have the drivers.)

Thanks again for your efforts.

-Randy

---

### Post by coffeecat on 2011-06-19
If the message is that a file on the CD is corrupt then that sounds like a problem with the cover CD that came with the book. You don't need to do anything with the hard drive. The half-completed Ubuntu installation won't be usable but all you have to do is to use a good Ubuntu installation CD, re-format the partition with the incomplete Ubuntu install and start again. It's all quite recoverable, but not from the book CD which sounds as though it could be a faulty one.

Have a look at the two links in my previous post. You can download an ISO from the first and use Windows to burn the ISO to make a bootable CD with instructions in the second. The free Infra Recorder described in that works very well.

Good luck!

---

