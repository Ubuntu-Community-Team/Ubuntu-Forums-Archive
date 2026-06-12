---
title: "Having trouble with Ubuntu"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Visvalor on 2011-02-22
I keep having to reinstall Ubuntu. 

I've reinstalled Ubuntu at least 12 times in the past week. It's getting rather tedious. 

My question is, is it common for Ubuntu to go down after installing software? Everything was out of the software center. And I haven't installed things that might have caused problems a second time. 

I'm using 64-bit Ubuntu
Sys specs are;
Quad Core Phenom
4gb ram
1tb Sata HD (western Digital)
2tb Sata HD (western Digital)
80gb IDE HD (Recently installed to avoid the crashes with the 2 Sata drives (both brand new)
XFX Geforce 8200 motherboard 

I keep finding new ways to crash the system and the resolutions are always to either edit the xorg config or the main.1st (or some file like it) 

This is rather tedious :P

---

### Post by whatthefunk on 2011-02-22
It shouldnt crash after installing.  How are you installing software?  Through the command line or through a package manager?

---

### Post by Kixtosh on 2011-02-22
He states that he is installing software from the software center utility. I don't thing I've ever managed to crash Ubuntu, BTW, so even once a week would seem strange to me, never mind several times in the same week!

---

### Post by DougieFresh4U on 2011-02-22
What are you trying to do when it crashes?

---

### Post by Visvalor on 2011-02-22
Different things. I'll do a bunch of installs and when I reboot it comes up with a different error each time.

I've installed 

Gimp
MySql
PHP
Apache
Battle of Wesnoth?
Glest
A devel of Mysql and Zlib
Amarok
And assorted automatic updates

I've cut everything out individually and after a reboot or 3, it goes to some sort of error. Usually telling me it's dropping to root (I forget the exact error), or just idling with a black screen and a blinking cursor, or the worst one just kept spamming something about the DMA bad file or something.

All and all I think my big problem is a hard drive with bad sectors. So I've installed it this last time on an 80gb HD to see what happens instead of my 1 or 2tb

---

### Post by Visvalor on 2011-02-22
Oh and Filezilla

---

### Post by asmoore82 on 2011-02-23
Sounds like good signs of failing hardware &#8212; especially a hard drive.

I would run memtest from the boot menu or a LiveCD.
And I would boot a LiveCD and test the hard drive(s) with `badblocks`
```
sudo badblocks -sv /dev/sda
sudo badblocks -sv /dev/sdb
```

I don't buy into the whole "a few re-allocated sectors are OK" bit.
If the drive can handle sector errors internally that's fine and dandy, but
if any errors at all are showing through to the OS layer, I replace the drive.

If the drive is still under warranty I've never had any trouble getting
a free replacement either &#8212; they're just gonna refurb and resell.
I also wouldn't hesitate at all to use a refurb drive myself. *Reliable*
drives are just an illusion created by "survival of the fittest."

---

### Post by mastablasta on 2011-02-23
> **Visvalor said:**
> And assorted automatic updates
Did you maybe install it via Wubi inside windows?
 
 > 
All and all I think my big problem is a hard drive with bad sectors. 
 
hmm WD 1 and 2 TB drivers. are they propperly aligned (you have to align them before putting any files there)? Not sure if alignment is done automaticly in linux. it's sure not in WinXP.

---

### Post by mnerobi15 on 2011-02-23
Right click computer go to manage select Disk Management and right click  the Parton it is on then click format when it is finished right click  the vista parton and select extend go to the max amount of MB it will  let you and then it will be back to normal.

---

### Post by Visvalor on 2011-02-23
Definitely the hard drive. I installed on an old IDE 80gb, and it's yet to crash :P

---

### Post by Kixtosh on 2011-02-23
There is software that is available to help diagnose and repair hard drives. I use SpinRite from Gibson Research, which costs $90, I think. In fact, I was even able to use it to get Windows to boot up on a laptop that had been dropped, damaging the hard drive so that all I got after the BIOS splash was a blue screen with various cryptic fault messages. It was also making some strange noises. After running SpinRite a few times (it corrects more errors, if possible, when run more than once), I was able to copy off any files that weren't backed up before replacing the damaged drive.

In your case, if you haven't dropped the drive, you would be able to determine if SpinRite finds problems or not, and if it can fix them.

I now use it to check my hard drives from time to time, and if I could touch wood, I would claim that I have never had a hard drive fail yet, other than the one that got dropped in the laptop ... but since I can't (touch wood), I won't (claim any such thing). 

[http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)

P.S. You can probably mark the thread as [SOLVED] now. I think it's in the "Thread Tools", in red letters, at the top of the page.

---

### Post by Hakunka-Matata on 2011-02-23
[http://wdc.custhelp.com/app/answers/detail/a_id/5655]("http://wdc.custhelp.com/app/answers/detail/a_id/5655")

Tells you how to align/partition WDX0EARS drives, interesting

---

### Post by asmoore82 on 2011-02-23
> **Kixtosh said:**
> There is software that is available to help diagnose and repair hard drives. I use SpinRite from Gibson Research, which costs $90, I think.

Nonsense, nothing that Linux-based tools can't do perfectly well for free.
No software can "repair" hard drives that are physically damaged or failing.

---

### Post by Kixtosh on 2011-02-23
> **asmoore82 said:**
> Nonsense, nothing that Linux-based tools can't do perfectly well for free.
No software can "repair" hard drives that are physically damaged or failing.Nothing beats first hand experience in my opinion, and I have that, so it's anything but nonsense. Do some research for yourself.

I shall merely repeat that I dropped my laptop. It would no longer boot. After using the SpinRite software, which runs right after BIOS and before the O.S. boots, I was able to boot Windows normally long enough to simply copy the files I needed. In fact, these same files, I had tried to copy by installing the drive in an external enclosure, but all I got was cyclic redundancy check errors. That should give you a clear indication of how serious the damage was. 

In any case, your comment is certainly less than ... ahem ... diplomatic, shall we say (or helpful for that matter) ... and you seem to have no experience with the product in question. It might have been more polite had you simply stated something such as "with due respect for your personal experience, fellow forum member, which I certainly cannot explain, I just don't believe that what you suggest is possible".

Because of your intent to rashly discredit my suggestion, the OP may well overlook a valid avenue of investigation. It certainly sounds as though the damage to his hard drive is not as severe as the damage I was dealing with.

---

### Post by mastablasta on 2011-02-24
> **Kixtosh said:**
> The Linux tools you describe operate from within the operating system, so they would never have even got started in my case.
 

 
i am gonna jump in and say that Linux can boot from CD or USB and therefore any tools in the system could boot a computer eventhough there is no hard disk (or damaged hard disk) in it.

---

### Post by Kixtosh on 2011-02-24
> **mastablasta said:**
> i am gonna jump in and say that Linux can boot from CD or USB and therefore any tools in the system could boot a computer even though there is no hard disk (or damaged hard disk) in it.That's a good point, that I should have thought of myself.

To further the discussion for Visvalor and his issues (if he wants to pursue them, that is), can anyone point to a good breakdown of hard drive evaluation and/or rescue utilities available with Linux? Maybe there's a good thread on the topic somewhere.

---

### Post by asmoore82 on 2011-02-24
> **Kixtosh said:**
> After using the SpinRite software, which runs right after BIOS and before the O.S. boots
Scientifically, *anything* that runs after BIOS is merely some form of OS.

> **Kixtosh said:**
> The Linux tools you describe operate from within the operating system, so they would never have even got started in my case.
Absolute hogwash! Straight from SpinRite's Wikipedia entry:
> **Wikipedia]Open Source Unix-based alternatives include dd_rescue and dd_rhelp, which work together, or GNU ddrescue.
…
These programs are more complicated to use than SpinRite, although GNU ddrescue is fairly easy to use with default options, and can easily be downloaded and compiled on Linux-based Live CDs such as Knoppix. It can also be used with SystemRescueCD.[/quote]

[QUOTE=Kixtosh said:**
> To further the discussion for Visvalor and his issues (if he wants to pursue them, that is), can anyone point to a good breakdown of hard drive evaluation and/or rescue utilities available with Linux? Maybe there's a good thread on the topic somewhere.
Visvalor never, ever mentioned anything about needing to rescue data from
these drives. Which is why I was further taken aback by your suggestion of
mysterious, expensive, closed, proprietary software that claims to do the
impossible. Further reading on Wikipedia explains that SpinRite persistently
reads data from damaged sectors, takes a best guess at what the data is
supposed to be, and then writes that data back to other areas on the
very same disk. Trying to write back *“rescued”* data to a known bad
disk is a deeply flawed algorithm, plain and simple.

The only thing to do with failing or damaged drives is get your
data off of them immediately and replace them.

---

### Post by Kixtosh on 2011-02-24
I don't understand your excessively aggressive attitude, especially concerning something with which you have no first hand knowledge ... unless you are just "baiting". In any case, it's polluting the thread and is irrelevant. ...

---

### Post by guilleme on 2011-02-24
Please, everyone, let's all calm things down, and let everyone to have their own opinions. I think that we all prefer different software for different reasons, and all algorithms and programs have their weak points and design flaws, (they also have strong points, and remarkable features) and even so they mostly work pretty well. 
I personally don't have the money to buy expensive software, but I'm quite very sure I would do it if I needed the software or I just had more money. Paid software tends to be at least equivalent or little better than free software, or at least more usable (windows being a notable exception:)), but for most users, free software will normally do.
I think that the alternative for Visvalor would be to try the free alternatives, and see if they work. If they do, go no further, if they don't, try SpinRite. 
Visvalor, a small question, did you add any *fancy* repositories for installing software?
And, are the live CD's running ok?

---

### Post by asmoore82 on 2011-02-25
I'm just trying to spread the knowledge from a great deal of experience...

It is these statements that are dismissive and rude:
> **Kixtosh said:**
> Nothing beats first hand experience in my opinion, and I have that, so it's anything but nonsense. **Do some research for yourself.**
> **Kixtosh said:**
> **especially concerning something with which you have no first hand knowledge** ...
Professional computer repair is *only* the career field that
I've been in my entire adult life, thanks for asking.
I've never ran across any drive that I couldn't get the data off of,
short of drives that were DOA or making grinding noises,
including some data that had been purposely deleted.

> **guilleme said:**
> Paid software tends to be at least equivalent or little better than free software
:shock:#-o[-X Untruer things have *never been* said.
[http://blogs.msdn.com/b/volkerw/archive/2008/01/16/stay-at-home-server.aspx](http://blogs.msdn.com/b/volkerw/archive/2008/01/16/stay-at-home-server.aspx)

You also seem to be confused about free software &#8212; it has nothing to do
with price; Free software is about freedom and liberty, not price.
[http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

---

### Post by Kixtosh on 2011-02-25
> **asmoore82 said:**
> ... I've never ran across any drive that I couldn't get the data off of,
short of drives that were DOA or making grinding noises, ...That's my point. I DID get data off a drive that WAS making grinding noises. I even got the O.S. to boot (more out of curiosity than anything else).

In any case, for those of us who have not spent their entire adult life in computer repair, and do not have your knowledge of the topic, we have to resort to the tools that we can get for free, or a reasonable fee. SpinRite is one of those tools in my opinion (for both data recovery or hard drive diagnosis and maintenance in general). You disagree, possibly because you have other and better tools at your disposal, but you haven't shared any of those yet.

Perhaps had I known you then, I would have sent you the drive instead and asked you to rescue my data that was not included in my backups, but could you have helped me for $90 or less (with a 30 day full refund policy in case of failure)?

---

