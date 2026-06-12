---
title: "would my 64-bit computer be better with ubuntu 64-bit or 32-bit?"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by hanzj on 2010-04-29
hello,
I have a 64-bit computer.
>   cat /proc/cpuinfo | grep model
model        : 47
model name    : AMD Athlon(tm) 64 Processor 3800+
The computer has 1 GB of ram.
The computer is year 2004 or a bit older.


Page 144 of the ["Getting Started with Ubuntu 10.04" manual]("http://www.vrac.iastate.edu/%7Egodbyk/screen/Getting%20Started%20with%20Ubuntu%2010.04.pdf") says 
 > 
Computers capable of running 64-bit software are able to process more information than computers running 32-bit software; however, 64-bit systems require more memory in order to do this. Nevertheless, these computers gain performance enhancements by running 64-bit software.

    Why choose one over another? Pay attention to the version you select in the following cases:

&#8227; If your computer is fairly old (made before 2007), then you may want to
  install the 32-bit version of Ubuntu. 
&#8227; If your computer has more than 4 GB of memory (RAM), then you may need
  to install the 64-bit version in order to use all the installed memory.


Based on the manual, my computer is "fairly old" and it's suggested I install 32-bit ubuntu. Should I?

Please try to answer three questions:

1. In my case, is it better to use Ubuntu 64-bit edition?
2. In my case, what are the disadvantages of using 64 bit ubuntu? 
3. In my case, what are the advantages?

If you answer my 3 questions, your comment would be more helpful for me than just a general "Go install 64 bit" or "Install 32 bit". Thank you.

---

### Post by computerguts on 2010-04-29
yes, make sure this is the case though before you install

---

### Post by QIII on 2010-04-29
Do you remember all those people who doggedly stuck to 16 bit OSs when 32 bit OSs became the norm?

If you have the hardware, use a 64 bit OS.

All the FUD about stuff not working is exactly that:  FUD.

---

### Post by Calash on 2010-04-29
Go 64bit.

Try the LiveCD first and make sure all your hardware works.  If you don't see any major issues go ahead and install it.  You will likely not even notice the difference.

---

### Post by arrrghhh on 2010-04-29
I'd say go 64-bit, it's becoming more and more compatible.  The real benefit comes in if you have more than 4GB of RAM - the 32-bit register is incapable of recognizing more RAM than that.  The benefits aren't *huge* (other than the RAM issue), but everything is going that way eventually.

---

### Post by hanzj on 2010-04-29
i've just updated my OP. I have only 1 GB of ram.

---

### Post by Calash on 2010-04-29
Ok then

> 1. Is it better to use Ubuntu 64-bit edition?

Yes.  It is where all computing is going.  We are fast approaching the end of life for 32bit.  Why stick with the past when you have the hardware and software available?


> 2. What are the disadvantages of using 64 bit ubuntu?

Few and far between.  As with the 16bit-32bit transition you may find hardware that is so old no drivers are available.  Advances such as PCI and PCI-e are making this much less of an issue than before.

You may run into some software problems.  Flash comes to mind, though the latest releases from Adobe are really addressing this fact.

The only other thing to not is to be aware you are running 64bit if you go outside of the repositories for your software.


> 3. What are the advantages?

Ability to address more memory
Faster processing of commands
Utilizing your hardware to the maximum ability
Transitioning before being forced

For more go to [http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by quadproc on 2010-04-29
> **hanzj said:**
> 
1. In my case, is it better to use Ubuntu 64-bit edition?
2. In my case, what are the disadvantages of using 64 bit ubuntu? 
3. In my case, what are the advantages?

Almost all desktop and laptop software now is capable of running on 64 bit processors so the older 32 bit SW will be relegated to legacy status as time passes.  Life will likely be much easier on the 64 bit path.

quadproc

---

### Post by KdotJ on 2010-04-29
64bit for sure. If your processor can do it, then thats the best option

---

### Post by barney385 on 2010-04-29
I've been using amd64 since Hardy came out.

It is working great/better with Lucid Lynx.

:smile:

---

### Post by Spiritof76 on 2010-04-29
> **hanzj said:**
> hello,
I have a 64-bit computer.
The computer has 1 GB of ram.
The computer is year 2004 or a bit older.



Please try to answer three questions:

1. In my case, is it better to use Ubuntu 64-bit edition?
2. In my case, what are the disadvantages of using 64 bit ubuntu? 
3. In my case, what are the advantages?

If you answer my 3 questions, your comment would be more helpful for me than just a general "Go install 64 bit" or "Install 32 bit". Thank you.

I guess I'll be the sole Luddite but I can't understand any benefit for you to upgrade. You have a 6 year old machine with only one gig of memory. So I don't under stand where you would benefit from going to 64 bit.  I haven't seen a lot of data supporting the claims that 64 bit bit is considerably faster. Nor has there been much claims that there is a lot of software that runs better in 64 bit.  I do no for certain that folks have had problems with 64 bit because some software doesn't work at all with it, and some other 64 bit version is buggy.  Some hardware drivers don't like 64 bit either.  

All that being said if you have a good reason to install 64 bit go ahead and do it.  It doesn't look to m e though though there is really any benefit for you, but there are some potential landmines.  Why put yourself through it if there isn't any reason to?

---

### Post by kelvin spratt on 2010-04-29
64bt is certainly worth it.

---

### Post by anewguy on 2010-04-29
> **QIII said:**
> Do you remember all those people who doggedly stuck to 16 bit OSs when 32 bit OSs became the norm?

If you have the hardware, use a 64 bit OS.

All the FUD about stuff not working is exactly that:  FUD.

Not necessarily - I have a 64-bit processor and tried the 64-bit version of 9.10 quite a while ago.  At that time at least, several things could not be made to work, and the word on the forum was "not currently with 64-bit" and "for that functionality you will need to use the 32-bit version".  Just what those things were I couldn't tell you now.  All I know is the problems I had were enough to make me go back and install the 32-bit version instead.  Sure, it doesn't take full advantage of the processor(s), but I also haven't had the problems as I did with 64-bit back then.  Is it possible that whatever those things were have been made to work now?  Sure - I don't know.  I just know it's not worth the hassle for me, even on a new install like I'll be doing with 10.01.  Not all negative remarks about 64-bit are FUD.

Just my experience - not arguing, just my experience.

Dave ;)

---

### Post by cascade9 on 2010-04-30
> **Spiritof76 said:**
> I guess I'll be the sole Luddite but I can't understand any benefit for you to upgrade. You have a 6 year old machine with only one gig of memory. So I don't under stand where you would benefit from going to 64 bit.  I haven't seen a lot of data supporting the claims that 64 bit bit is considerably faster. Nor has there been much claims that there is a lot of software that runs better in 64 bit.  

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

5-15% everywhere, and a LOT faster than that on some tasks (audio and video endoing in particular). 

That test was with 9.04, if anything, 64bit has pulled away even further now (no benchmarks to back that up now though). 

> **Spiritof76 said:**
> I do no for certain that folks have had problems with 64 bit because some software doesn't work at all with it, and some other 64 bit version is buggy.  Some hardware drivers don't like 64 bit either.  

Used to be a much bigger problem than it is now...sure, you can still find people who have had issues with newer 64bit versions *nods at anewguy above* but its becoming more and more rare. A lot of the peoplewho did have issues tried it back in 05 or 06, and then procedded to anounce that '64bit sucks' '64bit isnt any faster' (it wasnt faster in 06) etc when things have chnaged a lot in just a few years....

I've never had any issues with 64bit since I've been running it full time (at least a year now)

> **Spiritof76 said:**
> 
All that being said if you have a good reason to install 64 bit go ahead and do it.  It doesn't look to m e though though there is really any benefit for you, but there are some potential landmines.  Why put yourself through it if there isn't any reason to?

Its free, if you dont have a miserly d/l quota, its worth trying IMO.

---

### Post by swoll1980 on 2010-04-30
My 64 bit install works great.

---

### Post by jvc26 on 2010-04-30
Use 64bit, I've used it since somewhere around Dapper, and it works well (more recently than then!).

J

---

### Post by VeeDubb on 2010-04-30
> **QIII said:**
> All the FUD about stuff not working is exactly that:  FUD.

I agree with you 100%, today.  Before we had 64bit flash and 64bit java, it was legitimate, but these days, there's just no reason to cripple your CPU with a 32bit OS.


> **hanzj said:**
> i've just updated my OP. I have only 1 GB of ram.

Dude, buy more RAM.  It's worth it.  Really really worth it.

---

### Post by 3rdalbum on 2010-04-30
Normally I'd say "Go for 64-bit", but for a gigabyte of RAM you should stick with 32-bit in order to maximise use of your memory.

If you can put another 1 gig stick of RAM in that computer, go 64-bit.

---

### Post by Calash on 2010-04-30
> **3rdalbum said:**
> Normally I'd say "Go for 64-bit", but for a gigabyte of RAM you should stick with 32-bit in order to maximise use of your memory.

If you can put another 1 gig stick of RAM in that computer, go 64-bit.

That is a good point that I did not think of, though the Wiki I linked to probably has information on it.

64bit applications take more memory than their 32bit counterparts.  While not much per app it can add up a bit.

Add that to the downside list


Good catch, thanks :)

---

### Post by Ric_NYC on 2010-04-30
I will try the 64-bit version.
I tried it before and I had some things that didn't work (I don't remember what was it)... then I went back to the 32-bit version.

I hope this time it works well.

---

