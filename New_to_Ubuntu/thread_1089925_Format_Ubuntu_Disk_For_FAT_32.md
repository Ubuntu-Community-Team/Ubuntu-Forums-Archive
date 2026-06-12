---
title: "Format Ubuntu Disk For FAT 32"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by MiltR on 2009-03-07
I reformated an entire hard disk that had Ubuntu 8.04 on it to FAT 32 using Gnome Partition Editor so that I could put it in a Windows Me computer. But Ubuntu still recognizes the disk and Windows doesn't.

Can someone please tell me how to get the disk set so that Windows will recognize it.

Thanks,
Milt

---

### Post by mhh91 on 2009-03-07
try formatting it using windows,if you have access to windows on another computer :)

---

### Post by thtrgremlin on 2009-03-07
Are you sure you reformatted it to fat32 and not just change the partition type? Why not let Windows format the partition?

And not to flame, but Windows ME? ANYTHING else would be better; like Windows 98, or 2000, preferable XP?

---

### Post by xpod on 2009-03-07
Theres a "manage flags" option in gparted,try checking the box in there for "boot".I`m sure i`ve had to set that flag when formatting with gparted and installing Windows for people.
Then again you might just have to use fdisk for ME....that`ll give you a few hours to kill if nothing else;)

---

### Post by ivanvajar on 2009-03-07
Just format HDD during Windows installation. Windows ME? Why, for crying out loud?

---

### Post by MiltR on 2009-03-07
I would like to reply to all of you who were kind enough to comment on my question. But first, a brief explanation. I recently burned a Ubuntu "live' disk. I ran it a few times and find it interesting.

I decided to see how it works compared to WinME on my "old" spare office machine. So I put together a machine out of three old "junkers" I had. 

The fastest one has a 500 Meg. Pentium III. Two of them had the same model WD ten Gig. hard drives.  And each had a 128 Meg RAM. Now I've got 384 Meg. So, I've got a machine to run Windows ME and Ubuntu for comparison.

I now want to put Ubuntu on a better machine. One with a faster processor and more RAM. But I want to keep the "mule" for test purposes. So, I wanted to get Ubuntu drive back to ms dos. But I couldn't access it in either ms dos or Windows because Ubuntu reformated DEV/SDB when I installed it from the "live" disk. My Windows couldn't see it.

Thtrgremlin, I've used Windows 95, 95 update, 98, 98 update and ME. In my judgement, they're all derivitive of 95 and ME has a few features I like, such as System Restore. And the ME runs well enough for checking e-mail, typing word doc's. and some graphing in Excel. That's all I need it for up in my home office.
And I have a much better machine for other uses.

And finally, Thtrgremlin and Xpod I thank you both. You were correct. I made the FAT 32 partition, but I didn't set the flag for FAT 32. DUMB! I have got it formated properly now.Thanks for pointing out my problem.

Milt

---

### Post by ivanvajar on 2009-03-07
:-) I'm sorry if I insulted you. I am a very experienced Windows user and I found Win98 ver 4.1 and Win2000Professional good and stable systems even for 364MHz Celeron II computers with 64 MB of RAM, so, what's the big deal? All these folks here are friends trying to help. Be grateful for that. Best wishes!

---

### Post by MiltR on 2009-03-07
ivanvajar.

No insult taken. I just thought I'd explain why I did what I did. This is my first week with Ubuntu. So I imagine I'll be here with more questions for a while.

See 'ya,
Milt

---

