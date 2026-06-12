---
title: "running 32bit o/s in 64bit machine - is this worth changing"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by capnthommo on 2009-01-22
hi everybody
i just read the post from klemperal about system not seeing the full amount of memory.
i entered the commands suggested by jerome and i strongly suspect that i have a 32 bit o/s and a 64 bit processor.
would it be worth my while installing/upgrading to the 64 bit operating system, or is this likely to cause me problems?
If it's worthwhile can someone either guide me through it or point me at a good simple "how to"?
is it possible that my system (a toshiba equium a210 laptop 1 year old) is some kind of hybrid - 64bit processor and all the rest 32 bit.
oh yes, it runs fine at the moment but if it could run better then...
thanks loads for any help
nigel
):P

---

### Post by DFord425 on 2009-01-22
You can download a 64 bit version of Ubuntu. And install it the same way as you did the 32 bit version. 
And a 32 bit version of Ubuntu can run on a 64 bit process, not the other way around.
And if you have a laptop, i doubt there is more than 4 gigs of memory which is about the max a 32 bit processor can handle.

---

### Post by bwang on 2009-01-22
64 bit has some issues: there is no native 64-bit java plugin for Firefox, so it takes some work to install it. How much RAM do you have?

---

### Post by Therion on 2009-01-22
> **bwang said:**
> 64 bit has some issues: there is no native 64-bit java plugin for Firefox, so it takes some work to install it. How much RAM do you have?
The Flash and Java issues with 64-bit distros are long dead.  Install ubuntu-restricted-extras right outta the repo, and you're done.  I've been running a 64-bit distro since Feisty and the whole 64-bit distro thing has never once been an issue.  IMO, there's really no reason NOT to use a 64-bit distro if your proc supports it.

---

### Post by jerome1232 on 2009-01-22
I have to agree especially since now sun and adobe have come out with 64 bit versions of the java plugin and flash.

I'm going to recomend reading this sticky in the 64 bit forum
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by capnthommo on 2009-01-22
okay, thanks for the rapid responses.
forgive me, i am not really technically minded - i can build you a house though!
DFord425 - yes you are quite right - i have a 4 G machine.  i can download a 64bit ubuntu if i decide to go ahead with it. 
but i have decided that if i have to reinstall i might as well use the opportunity to clear previous installations from the disk, and probably repartition too so i would need to think about it first.
i only have ubuntu on the machine so would it be advisable to go for a 'use entire disk' partitioning?
bwang, the machine is 4 G with 160 G ram (is that right?  i am never certain what i am talking about when we get onto the subject of memory and ram)
If it's worth installing 64 bit (and yes, i have seen one or two posts talking about 64 bit issues) i would like to do so as simply as possible.  
If i went ahead is it possible to just upgrade as opposed to a complete fresh install because i would prefer not to lose the settings and other software apps i have had to add in order to get things like dvd and printer and 'real player' working properly.

thanks again for the replies
nigel

---

### Post by bwang on 2009-01-22
> **capnthommo said:**
> 
bwang, the machine is 4 G with 160 G ram (is that right?  i am never certain what i am talking about when we get onto the subject of memory and ram)


I think you mean 4 G ram and 160 G hard drive. If you have 4 GB of ram, you definitely should install 64-bit, as it will allow you to use all of your RAM.

---

### Post by capnthommo on 2009-01-22
okay thanks therion and jerome1232.  i was composing my reply when your responses came in.
i shall read the sticky.
can i intrude on your time a little further? 
this is the result of the code and responses

```
  nigel@nigel-laptop:~$ cat /proc/cpuinfo | grep lm
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch

```
```

nigel@nigel-laptop:~$ uname -m
i686

```

can you just tell me from this if i am right and 64 bit will run in my (i think) 64 bit machine?
thanks greatly
nigel

---

### Post by capnthommo on 2009-01-22
thanks bwang
i shall write this down and pin it to my wall - it just won't stay in my head.
and yes i think i will go ahead, just need to think about about how i will do it.  i would like to rationalise the whole setup so i end with the minimum number of partitions for an effective and safe system and with minimum disruption.  a job for tomorrow i think.
thanks again to everyone who helped me, and i shall call this one solved.  if i have any related problems (opportunities?) i shall open another thread
cheers again
nigel

---

### Post by jerome1232 on 2009-01-22
Yup from that you have a dual core processor that is 64 bit (lm means Long Mode, if you have that flag your cpu is 64 bit.) You also currently have 32 bit Ubuntu installed.

---

### Post by ghetto2ivy on 2009-01-22
I disagree with the recommendations here. I run 64bit ubuntu on my desktop and its great -- nowhere near the issues of 64bit windows. No issues with Java or flash as mentioned. However, while ubuntu has all the repos ready with 64bit apps, the issue is that many third party apps you might get off the internet are only in 32bit.

That means that occasionally, you're going to need to download and compile apps from source yourself. Or if your luck the libs are ready and you can just run:
```
sudo apt-get install --force-architecture packagename
```

But either can be daunting for a new user. For example, the other day I had to compile google gadgets for linux -- yes I could have used screenlets, but wanted to try ggl. Its not impossibly difficult, but it makes ubuntu seem unnecessarily difficult. 

Furthermore, a 32 bit system can see 3.5 gigs of ram. But since it reads in bigger chunks, apps will take more memory, making it really a wash from that point of view.

Not worth the *possible* hassle for someone new to Linux.

---

### Post by egalvan on 2009-01-22
> **bwang said:**
> If you have 4 GB of ram, you definitely should install 64-bit, as it will allow you to use all of your RAM.

I have:

8GB of RAM,
AMD Athlon 64 X2,
running 8.04.1 32-bit,

and 'top' shows 8243008K.

( done as an experimental install to test RAM 'limits' )

ErnestG

---

### Post by notquitemichael on 2009-01-22
yup, deffinately 64bit. using ubuntu you'll hardly notice problems in packaging etc. i've used both 32bit and 64bit versions and aside from having to compile a psx emulator i've had no trouble.
also your machine is probably only using 4gb of ram (the limit of 32bit machines,) so you may get a speed increase (although i doubt anything is actually requiring that much ram from you!)

---

### Post by SunnyRabbiera on 2009-01-22
even so its your choice, there is nothing wrong with using the 32bit kernel.
Even with its 4GB limit its still good, as ubuntu doesn't need that much memory anyhow :D

---

### Post by egalvan on 2009-01-22
> **SunnyRabbiera said:**
> even so **its your choice**

Yep, choice is good...

>  there is nothing wrong with using [B][I]the 32bit kernel.
Even with its 4GB limit [/I][/B]its still good, as ubuntu doesn't need that much memory anyhow :D


But only the **default DESKTOP 32-bit kernel ** has a 4GB limit.

See post #12 above.

---

### Post by capnthommo on 2009-01-22
okay thanks folks.
i have just installed the 64 bit ubuntu using a whole disk install.  fingers crossed - so far so good - we shall see over the coming weeks.  one other benefit is that it has given me the opportunity to remove previous installs that i have wrecked and had to re install(i can't keep my fingers out).
thanks once more and goodnight - time for sleep now
nigel ):P

---

### Post by capnthommo on 2009-01-23
okay then, it seems to be holding so far.  i have now got my media things working as i like them (bbc iplayer, dvd, music etc)  and my files are looking better organised.  can't be sure but i think it is running a little better but maybe that's just me wanting it to.
mainly the partition is looking sensible now and things seem to run more rationally.
thanks for the help again
gefinitely call this one solved (at least so far)
cheers
nigel

---

### Post by hyper_ch on 2009-01-23
I have to ask: Is there a reason to still use 32bit?

---

### Post by leonardo_neo on 2009-01-23
> **Therion said:**
> The Flash and Java issues with 64-bit distros are long dead.  Install ubuntu-restricted-extras right outta the repo, and you're done.  I've been running a 64-bit distro since Feisty and the whole 64-bit distro thing has never once been an issue.  IMO, there's really no reason NOT to use a 64-bit distro if your proc supports it.

Thanks Therion for this information. Even I used to believe that 64 bit has some issues with java plugin. But with this information of your's, I am feeling light headed now :)

---

### Post by stchman on 2009-01-23
> **bwang said:**
> 64 bit has some issues: there is no native 64-bit java plugin for Firefox, so it takes some work to install it. How much RAM do you have?

You can use Icedtea instead of Sun Java.

---

### Post by Thelasko on 2009-01-23
> **hyper_ch said:**
> I have to ask: Is there a reason to still use 32bit?

Certain drivers (mostly printers) can have issues.  Maybe some really oddball software.  For most purposes, 64-bit is the way to go.

---

