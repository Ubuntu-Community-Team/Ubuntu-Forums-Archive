---
title: "64bit or 32bit"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Zintha on 2010-04-30
I know I know, "Not another one of these!"

However, I don't really understand the difference. Sure i've read wiki pages and other thread posts etc but they're either unclear or go way over my head on how they're useful.

So far, all I know is that 64bit doesn't work too well on older machines and 32bit doesn't read more than 3.2gb of RAM but I don't know anything past that (for sure anyway).

So, clear it up for me.

If 64bit > 32bit too (as in, "If you can use 64bit, use it" then my next question is:

How can I go from 32bit Ubuntu 10.04 to 64bit Ubuntu 10.04 and not lose all my precious delicious data?

---

### Post by tgm4883 on 2010-04-30
> **Zintha said:**
> I know I know, "Not another one of these!"

However, I don't really understand the difference. Sure i've read wiki pages and other thread posts etc but they're either unclear or go way over my head on how they're useful.

So far, all I know is that 64bit doesn't work too well on older machines and 32bit doesn't read more than 3.2gb of RAM but I don't know anything past that (for sure anyway).

So, clear it up for me.

If 64bit > 32bit too (as in, "If you can use 64bit, use it" then my next question is:

How can I go from 32bit Ubuntu 10.04 to 64bit Ubuntu 10.04 and not lose all my precious delicious data?

You have to reinstall. Backup your data (if you already have your data on another partition thats fine) then reinstall. Don't format the partition with your data on it.

---

### Post by Zintha on 2010-04-30
> **tgm4883 said:**
> You have to reinstall. Backup your data (if you already have your data on another partition thats fine) then reinstall. Don't format the partition with your data on it.
I figured. What I might do is install Lucid 64bit onto a new harddrive so I had 32 and 64bit around.

Which would be nice if 64bit had any issues etc.

Also, I heard that Ubuntu puts everything personalised into the Home folder, firstly is this true? Secondly, if it is, would it be plausible just to copy that as a backup.

Third, if the above is not true, whats a good program to backup/what files can I just copy+paste?

---

### Post by barney385 on 2010-04-30
Yep.

+1

---

### Post by howefield on 2010-04-30
> **Zintha said:**
> How can I go from 32bit Ubuntu 10.04 to 64bit Ubuntu 10.04 and not lose all my precious delicious data?

Back up your data, which should be a part of your routine in any event. Anyone who describes data as precious as well as delicious must keep more than one copy of it :)

A clean install would be required. This would be a good opportunity to install with a separate /home partition if you haven't already.

---

### Post by Zintha on 2010-04-30
edit : I'm asking questions I could now google.

My only remaining original ones that google didn't solve are:

1) Difference between 64bit and 32bit to a newbie user?
2) Should I use 64bit if I can?

---

### Post by Shark_AtK12 on 2010-04-30
1) 64 bit supports up to and more than 4 gigs of ram and processes/stores info using 64 bit registers. (Is able to do more per cycle)

2) If you can go 64bit. The support is a lot better now. If you just do everyday browsing, you probably wont notice the diff but if you do encoding or any other CPU intensive application, you will

---

### Post by pricetech on 2010-04-30
If you have the second hard drive and are planning to try 64 bit there, then that pretty much makes it a no brainer doesn't it ??  You always have the option of swapping back to the drive with 32 bit if it doesn't work out for you for whatever reason.

I've tested both on the same machine and 64 bit is noticeably faster.  The only thing that I use that doesn't work is flash and I can live without it / work around it.

---

### Post by srs5694 on 2010-04-30
> **Zintha said:**
> Also, I heard that Ubuntu puts everything personalised into the Home folder, firstly is this true? Secondly, if it is, would it be plausible just to copy that as a backup.

It's more-or-less true. Your mail queue goes in /var/mail (which is only relevant if you use a mail server on Ubuntu rather than or in addition to using POP or IMAP to retrieve your e-mail directly from your ISP), temporary files go in /tmp (but these are by definition unimportant between boots), some games store high scores elsewhere (not usually a big deal), and of course you could have something configured oddly on your own system.

Many people, myself included, recommend splitting off /home as a separate partition. Among other things, this practice makes some types of system upgrades easier, such as a 32-bit-to-64-bit upgrade, switching to another distribution, or re-installing fresh after some sort of system corruption has caused damage. If you're backing up /home as part of a 32-to-64 upgrade, I recommend splitting off /home when you do your new installation. In a year or two, this may save a lot of trouble.

> 1) Difference between 64bit and 32bit to a newbie user?

I wrote a [url=http://www.linux-mag.com/id/1699]piece on x86-64/AMD64 for Linux Magazine[/quote] several years ago. Although the details about specific CPU models and distributions are woefully out of date today, the basics of 32-bit vs. 64-bit -- and more importantly, x86 vs. x86-64/AMD64/EM64T -- are still relevant. In brief, you'll be better able to access more RAM and you'll see a modest (~10-15% on average) speed increase in CPU-intensive programs when using 64-bit software. OTOH, some programs aren't available in 64-bit form, or are substandard in that form. Today the most important example is Flash, which is still in alpha test in its 64-bit Linux incarnation.

> 2) Should I use 64bit if I can?

You'll probably be fine either way, but IMHO, 64-bit offers enough benefits that it's usually the better choice these days. These benefits aren't huge, though, and the drawbacks can be important for some people.

---

### Post by kill4killin on 2010-04-30
::EDIT::

So I seem to have gone off on a tangent, and it took me 15 minutes to write this response of doing research, oops... the only thing that you may find cumbersome is knowing the difference between 64bit and 32bit drivers and programs. Some programs are designed so that they work more efficiently in the 64bit environment if you have it available, others are just 32bit that use the 64bit libraries. Other than that, you'll notice not difference.

::ORIGINAL POST::

64bit will support memory amounts over 4GB 32bit will not, looks like you got that much. Some people will quote it as 3.5 or 3.75GB or whatever, but 32bit supports up to 4GB, the trick is that this limit includes the memory in the onboard and PCI/PCI/AGP devices as well. This takes up part of that 4GB limit and lowers how much you can see in the system when you load your OS. The same thing would theoretically occur with 64bit OSs as well, it just wouldn't be visible until you approach 16.3 exabyte limit (good luck).

To summarize it comes down to memory addressing ([wikipedia link]("http://en.wikipedia.org/wiki/Memory_address")). 64 bit has more and 32 bit has less

*I'm not expert on any of this, I actually thought until I researched into the topic for this response that 64bit was 128GB limit and I found the following two links fascinating and I'm posting them just for source reference.*

[http://en.wikipedia.org/wiki/Memory_address](http://en.wikipedia.org/wiki/Memory_address)
[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by Zintha on 2010-04-30
Absolutely fantasticly fast and good answers. Will mark as solved!

Already downloading Lucid 64bit and preparing myself to install onto secondary HDD.

Thank you!

---

