---
title: "Virtual Machine issue"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by BobJam on 2009-07-22
[B]I've posted this question on the xVM forum, where it is probably the most appropriate, but I thought maybe someone here would have a suggestion too.
[/B]
Host: Ubuntu 9.04

Guest:  Windows XP HE SP2

xVM Version:  3.0.2

I am a Linux/Ubuntu refugee from Windows.  But I'm still tethered to Windows (grub loader dual boot) because I do my on line banking with Quicken (and there is no Ubuntu version, nor is there any substitute that I can use for my on line banking).  Consequently, I installed xVM to run a Windows guest so that I could install Quicken and thus transition to Ubuntu completely, plus not have to tediously bounce back and forth between OS's.

I copied the Quicken install CD to a folder I can read with the Windows guest.

But when I try to execute the install.exe from that copied CD, I get the first few install screens and then it stops with an "Exit code 1619" message.

I Googled that message, and the nearest I could come up with was an MSI issue.  Am still reading up on that, but I don't think that is the problem.  I think the problem is that I can't install except from the physical CD.

I'd like to transition completely to Ubuntu, but unless I can resolve this issue, I will have to remain tethered to the Windows OS partition.


Any solutions for the virtual machine?

---

### Post by cjv8888 on 2009-07-22
Never used xVM, but in VirtualBox, you can use a physical CD ,USB etc

---

### Post by kellemes on 2009-07-22
If you cannot access a physical disk from the guest you can always try working from an ISO made of the Quicken install-cd, the quest-os will see this as a physical disk.
Hope this works..

---

### Post by BobJam on 2009-07-22
Hey cjv8888,

I'm using the wrong terminology.  Is not xVM, is VirtualBox.

So in VirtualBox, just how would I configure it to use a physical CD?

I see the USB configuration manipulation, but all I see on the DVD/CD stuff is .iso, not a physical drive.  Would it be the mount setting?  What am I missing?

A screenshot would help.

TIA

---

### Post by BobJam on 2009-07-22
OK . . . I got it to work.

Apparently, the "secret" is/was to allow Ubuntu to read the CD first, rather than go to VirtualBox and insert the CD from there (I did in fact mount the machine CD drive, but at first that didn't seem to solve the problem either because I was still getting the message that the CD was "corrupt or unreadable").

I discovered this "secret" when I 'sperimented by running a VM in Windows, where I had XP as host and also XP as guest.  I mounted the CD drive and it read it just fine.

So from that I deduced that it was an Ubuntu issue, but I couldn't figure out what it was.

As it happened, I left the CD in the drive, so that when I booted into Ubuntu, it read it right away.  Figuring that I'd mess around with it some more, I started up the VM, which was still configured to read the CD drive, but I still didn't have a clue about what was going on.

I saw that the CD title showed, so I ran the executable, and . . . WOW, was I a happy camper!

So, mods, you can mark this thread solved.

---

### Post by kellemes on 2009-07-22
> **BobJam said:**
> 
So, mods, you can mark this thread solved.

I think you can do this yourself from the "thread tools" menu.

---

### Post by BobJam on 2009-07-22
> **kellemes said:**
> I think you can do this yourself from the "thread tools" menu.I don't see it in the drop down?

---

### Post by kellemes on 2009-07-22
> **BobJam said:**
> I don't see it in the drop down?

Yes, I guess they removed it..
According to [this thread]("http://ubuntuforums.org/showthread.php?t=1166975") you can simply reply to the thread and edit the title like so.. "[Solved]Re: mark post as solved"

Or you could just leave it :-)

---

### Post by BobJam on 2009-07-22
Marked solved.

Edit:  Hmmmmmm . . . reply just marks this particular post title as "Solved", not the whole thread . . . What am I missing (no big deal I guess, but would be good to know).

Edit #2:  Tried editing first post, but title does not come up as editable there.

---

### Post by LookTJ on 2009-07-22
> **BobJam said:**
> Marked solved.

Edit:  Hmmmmmm . . . reply just marks this particular post title as "Solved", not the whole thread . . . What am I missing (no big deal I guess, but would be good to know).

Edit #2:  Tried editing first post, but title does not come up as editable there.
You could click edit and then in the box there is "Go Advanced" after that, you can edit the title :)

Hope that helps

---

