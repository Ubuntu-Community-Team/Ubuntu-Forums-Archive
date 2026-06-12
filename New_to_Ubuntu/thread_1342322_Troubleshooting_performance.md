---
title: "Troubleshooting performance"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by alhenderson on 2009-11-30
Hello All,

Just joined the forum, hope someone can give me some pointers..  I have just installed Ubuntu on my Dell Inspiron 8200 laptop having put up with Windows running like a dog.  I don't use the laptop for very much - Firefox and Thunderbird are the main apps I run.  However, the performance is not what I hoped for, which leads me to believe I might have a hardware problem of some sort.

I have the CPU graph showing on the task bar and it is constantly between 75-100% with me just running Firefox.  Sometimes web pages are almost impossible to use (facebook being a prime example) - typing a sentence can take ages.  When the system is like this, I have looked at the process list on the system monitor and the only process taking up any serious CPU is the gnome system monitor.

Can anyone help me with any troubleshooting tips that might help me get to the bottom of this.  I know the laptop's not the best (Pentium 4, 1.6Ghz, 749M RAM) but I would have thought that a bit of web browsing and email should not stress it too much..

My fan is almost constantly running (in fact one of the two isn't working), but the CPU temp monitor doesn't suggest a problem.

Sorry to ramble on a bit, trying to put down any useful information..

Thanks for any hints,
Al.

---

### Post by mörgæs on 2009-11-30
Here is what is worth knowing of Firefox:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

If Flash is slowing down Firefox, I would suggest Flashblock.

Your hardware should not be the problem. Ubuntu can run well with far less horsepower.

---

### Post by Geoff918 on 2009-11-30
What version of Ubuntu are you using? What version of Firefox are you using?

I seem to remember a rash of these complaints some time ago. By the time you get that information, I should be able to find a thread marked [SOLVED] for you.

Here are some useful bits of info:

From command line interface (CLI) -- Applications - Accessories - Terminal

uname -a

(please paste output)

and of course the old Help - About from within Firefox

---

### Post by alhenderson on 2009-12-01
Thanks for the tips guys - should have mentioned at the time, I am using XUbuntu 9.0.4 and whatever version of Firefox comes with that.  I don't have the laptop to hand at the office so will check later.

I'll also check out that Firefox link and do the uname thing.  Maybe I should also be trying a different browser?  Firefox does seem to be very memory intensive when I run it at work..

Thanks,
Al.

---

### Post by mörgæs on 2009-12-01
Yes, you could give Opera a try.

---

### Post by alhenderson on 2009-12-01
> **mörgæs said:**
> Yes, you could give Opera a try.

Funnily enough, I was just reading the thread about how good Opera 10 was and considering that.  Thanks :-)

Al.

---

### Post by cascade9 on 2009-12-01
> **alhenderson said:**
> I have the CPU graph showing on the task bar and it is constantly between 75-100% with me just running Firefox.  Sometimes web pages are almost impossible to use (facebook being a prime example) - typing a sentence can take ages.  When the system is like this, I have looked at the process list on the system monitor and the only process taking up any serious CPU is the gnome system monitor.

Can anyone help me with any troubleshooting tips that might help me get to the bottom of this.  I know the laptop's not the best (Pentium 4, 1.6Ghz, 749M RAM) but I would have thought that a bit of web browsing and email should not stress it too much.. 

Gnome system monitor uses wayyy to much CPU. Try command line-> top. Its lighter. 

I sometimes use a computer with less hardware muscle than that for web browsing, etc. and had no real problems (well, OK, if I opened to many tabs it would run awful, but that was more the limited RAM.....384MB isnt enough) 

> **alhenderson said:**
> My fan is almost constantly running (in fact one of the two isn't working), but the CPU temp monitor doesn't suggest a problem. 

Its possible that your CPU is thermally throttling. That would make it run very badly. I'd try to get your fan fixed if you can.

---

### Post by 3rdalbum on 2009-12-01
If you have an Intel-based graphics chipset, then it's possible that part of your problem is the low-performance Intel graphics drivers in 9.04. The problem has been solved in 9.10, and didn't exist in 8.10.

But before upgrading your distribution, run the "top" command and see what's using your CPU so much.

---

### Post by cascade9 on 2009-12-01
I'm pretty sure that the Dell Inspiron 8200 1.6 has a Geforce 2 Go. 

But its worth checking that out.

---

### Post by alhenderson on 2009-12-01
Thanks for all the messages guys!  Firstly, running Firefox 3.0.8.

Output from uname:

Linux dowthorpe 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Having switched off the gnome CPU monitor and used 'top' I can see that the two processes competing for the most usage are 'update-apt-xapi' and 'Xorg' - the former seeming to be the worst behaving one.

I have a GeForce2 Go graphics card.

So, question is, what's 'update-apt-xapi'?  I read something about it being an update manager of some sort, but for what?  

Thanks for any thoughts,

Al.

PS - is it possible to output the top command to a text file?  I thought you could use '|' but i got a bash command not found error..

---

### Post by alhenderson on 2009-12-04
I've installed Opera 10.10 and the system performance hasn't really changed.  Using 'top' I can see that Xorg is taking up anywhere up to 30% CPU when I'm not doing anything.  Is this normal?

Al.

---

