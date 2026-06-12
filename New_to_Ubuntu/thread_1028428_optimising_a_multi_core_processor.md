---
title: "optimising a multi core processor"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by stonecoldjha on 2009-01-02
is there a way to optimise my ubuntu installation to work better with multi core processors like my core2duo so as to maximise performance?also,i am curious to know what the difference between dual core,core2duo and quadcore really is?if dual core is about two cores,what about core2duo?

---

### Post by StOoZ on 2009-01-02
it think the kernel does that by default...

---

### Post by ibuclaw on 2009-01-02
[EDIT]
s/CPU/Cores/ :)
Don't know if its the lack of sleep, or because there is a [cloud of phosphorus gas above my house]("http://www.guardian.co.uk/uk/2009/jan/02/phosphorous-cloud-west-midlands"), but thanks for reminding me that Skripka

I think its:
[LIST]
[*]**Single Core** - 1 Cores
[*]**Dual Core** - 2 Cores
[*]**Core2Duo** - 2 x 2 Cores
[*]**Quad Core** - 4 Cores
[/LIST]

As for optimising, you'll probably find that there is nothing much you can do, as it is already optimised enough.

Though, there are some tricks here or there to help improve boot or app loading times using threaded loading and pre-caching.

Regards
Iain

---

### Post by Skripka on 2009-01-02
> **tinivole said:**
> I think its:
[LIST]
[*]**Single Core** - 1 CPU
[*]**Dual Core** - 2 CPUs
[*]**Core2Duo** - 2 x 2 CPUs
[*]**Quad Core** - 4 CPUs
[/LIST]

As for optimising, you'll probably find that there is nothing much you can do, as it is already optimised enough.

Though, there are some tricks here or there to help improve boot or app loading times using threaded loading and pre-caching.

Regards
Iain

Um, not so much:

The number of cores refers to the number of processing cores inside the CPU

A quad core has just that-4 processing cores inside the CPU
A dual core has two processing cores inside the CPU
A Core2duo also has 2 cores...this is Intel marketing for you.

CPUs are not to be confused with processing cores.  More cores allow for better multitasking, and speedier performance in CERTAIN tasks.  SOME tasks are best done on single-core CPUs.

VERY few programs are written to take advantage of multi-core CPUs.  Very few.  Namely high-end graphics and audio apps...and some nice games.  MOST software isn't multi-threaded (such as web browsers).

---

### Post by ushimitsudoki on 2009-01-02
Core2 is just a model line (like Pentium). Before that was the Core line.

[Wikipedia]("http://en.wikipedia.org/wiki/Intel_Core_2")
> The Core 2 brand was introduced on July 27, 2006,[3] comprising the Solo (single-core), Duo (dual-core), Quad (quad-core), and Extreme (dual- or quad-core CPUs for enthusiasts) branches, during 2007.[4] Intel Core 2 processors with vPro technology (designed for businesses) include the dual-core and quad-core branches.[5]

The only thing you need to do is make sure your kernel has SMP support. (If you are using the Ubuntu stock kernel it does)

If you like to check it, try *uname -a* and look for "SMP".

---

### Post by handydan918 on 2009-01-02
If you post the output of ```
cat /proc/cpuinfo
```it's easy to verify that your processors a seen correctly.

---

### Post by stonecoldjha on 2009-01-02
yeah,sure,here is the output

sonu@sonu-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz
stepping	: 2
cpu MHz		: 1200.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3992.34
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz
stepping	: 2
cpu MHz		: 1200.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3989.25
clflush size	: 64

sonu@sonu-desktop:~$

---

### Post by scorp123 on 2009-01-02
> **stonecoldjha said:**
> is there a way to optimise my ubuntu installation to work better with multi core processors like my core2duo so as to maximise performance? You again? Why do you keep asking such things? Is there anything that still makes you think you're having "bad" performance? 

The Linux kernel does all the optimising automagically for you. There is nothing to do here.

If you are by some strange reason thinking you have performance issues then it would be helpful if you opened a thread about that instead of asking the same questions again and again ;)

---

### Post by LowSky on 2009-01-02
> **scorp123 said:**
>  automagically 

lol the awesomeness of that word sends shivers down my spine

stonecoldjha what is running slow, that you think need adjusting.
Ubuntu is so light wieght it will run on computers with as little as 1GHZ processor and less then 512 RAM. If you think there is a perfomance hit, then look toward the slowest part of any computer and its the hard drive. Buy a WD raptor or go to SSDs for more perfomance.

Any processor out now is by far powerfull enough to run ubuntu without any issue

---

### Post by stonecoldjha on 2009-01-02
well,thanks,you recognized me.i don't know why but i love ubuntu so much that i want it to be faster and faster,so i am in a pursuit of speed.comments like mac is faster put me off.also,since i know that this site is a perfect place to know more about ubuntu,linux and computers,i like asking questions and becoming more and more knowledgeable in the process.
btw,i wanted to know if the open source community is even working to have better performance with ubuntu?
and,i am obsessed about ubuntu.

---

### Post by ibuclaw on 2009-01-02
Multiple CPUs can infact be used to [optimise power saving]("http://lesswatts.org/"), and although 95% of all apps are optimised for one core only, it is possible to do what you can here or there:

**Startup**
```
sudo gedit /etc/init.d/rc
```
find the line: CONCURRENCY=none
And change it to
```
CONCURRENCY=shell
```

**Firefox**
There is an option in the firefox browser about:config called **network.http.pipelining** that /can/ speed up firefox if turned on and your cores support its use.
Also, **network.http.pipelining.maxrequests** to be turned up to about 6.


**IRQs**
Interrupt requests by default, only go to the one core. But (and this is mostly for powersaving sake) you can split the requests with a handy little daemon tool
```
sudo apt-get install irqbalance
```
Info about it found here: [http://irqbalance.org/](http://irqbalance.org/)

There are plenty of fruitful choices after a quick search.
Though it is the knowing which ones will be best that is the most difficult decision.

Regards
Iain

---

### Post by ibuclaw on 2009-01-02
> **stonecoldjha said:**
> well,thanks,you recognized me.i don't know why but i love ubuntu so much that i want it to be faster and faster,so i am in a pursuit of speed.comments like mac is faster put me off.also,since i know that this site is a perfect place to know more about ubuntu,linux and computers,i like asking questions and becoming more and more knowledgeable in the process.
btw,i wanted to know if the open source community is even working to have better performance with ubuntu?
and,i am obsessed about ubuntu.

Speed is in the eye of the beholder...

Never use yourself as a benchmark for whether or not one OS is quicker than another. As you may be just fooling yourself...

There was actually a similar discussion on SSE2/SSE3 optimising a few days ago, I think [this post here]("http://guide.ubuntuforums.org/showpost.php?p=6456105&postcount=26") pretty much clarifies everything about speed and ubuntu.

---

### Post by stonecoldjha on 2009-01-02
i have seen graphic effects of ubuntu on a damn good computer with a 512MB nvidia card(Geforce 8600 GT),4 gigs of RAM and 2.66 GHz core2duo processor,but they are not as good the graphics on a macbook with somewhat lower specs.for,instance look at this,its not that smooth ,is it?

---

### Post by egalvan on 2009-01-02
> **scorp123 said:**
> You again? Why do you keep asking such things? Is there anything that still makes you think you're having "bad" performance? 

The Linux kernel does all the optimising automagically for you. There is nothing to do here.

If you are by some strange reason thinking you have performance issues then it would be helpful if you opened a thread about that instead of asking the same questions again and again ;)

the Hardy Desktop kernel **does not** have PAE enabled, therefore maxes out at 4 gig.

the Hardy Server kernel **does** have PAE enabled, therefore maxes out much higher... 
I only have 8gig, so I don't have experience with more.

So, no, the kernel does not always optimize.

And having "good" performance is not the same as "max" performance..

Tweaking Linux is good sport, and a learning experience.

ErnestG

---

### Post by ibuclaw on 2009-01-02
> **stonecoldjha said:**
> i have seen graphic effects of ubuntu on a damn good computer with a 512MB nvidia card(Geforce 8600 GT),4 gigs of RAM and 2.66 GHz core2duo processor,but they are not as good the graphics on a macbook with somewhat lower specs.for,instance look at this,its not that smooth ,is it?

What you may want to look at then is your Compiz and NVIDIA settings :)

```
sudo apt-get install nvidia-settings compizconfig-settings-manager
```

Then go into:
**System->Preferences->Advanced Desktop Effects**

Click **General Options** and go to **Display Settings** Tab
And change **Texture Filter** from "Good" to **Best**

Go back and under **Effects**, enabling the **Bicubic Filter** should help unchop up the output a bit also.

And you can find similar things in NVIDIA X Server Settings too:
```
gksudo nvidia-settings
```
Under **OpenGL Settings** you can set **Image Settings** to **High Quality**.
Under **Antialiasing Settings** you can **Override Application Settings** for both Anti-Aliasing and Anisotropic Filtering and set them to a reasonable level. (Effects may not take action until you restart X).

etc, etc...

But please bare in mind that all your tweaking may have a knock-on effect in CPU usage too.

Regards
Iain

---

### Post by sdennie on 2009-01-02
> **egalvan said:**
> the Hardy Desktop kernel **does not** have PAE enabled, therefore maxes out at 4 gig.

the Hardy Server kernel **does** have PAE enabled, therefore maxes out much higher... 
I only have 8gig, so I don't have experience with more.


You are confusing performance with features.  PAE is a feature.  In fact, PAE actually has a performance penalty in some cases (though, it's not generally noticeable).

---

### Post by scorp123 on 2009-01-02
> **stonecoldjha said:**
> i want it to be faster and faster Try this then ...

[http://ubuntuforums.org/showpost.php?p=6419914&postcount=9](http://ubuntuforums.org/showpost.php?p=6419914&postcount=9)

A modern Quad-Core system already is very fast, so I am not sure you will notice any effect. But that's something you could try without risking too much (e.g. the side-effects are not drastic and it's easy to undo these small changes in case they don't help).

Happy tweaking ;)

---

### Post by egalvan on 2009-01-02
> **tinivole said:**
> Multiple CPUs :

**Startup**
```
sudo gedit /etc/init.d/rc
```
find the line: CONCURRENCY=none
And change it to
```
CONCURRENCY=shell
```

Could you explain what this change will do?

> 
There are plenty of fruitful choices after a quick search.
Though it is the **knowing which ones will be best **that is the most difficult decision.

Regards
Iain

Yes, it's just that reason that so many of us come to forums such as this...
many times we can find the information, but need help in applying it..

thanks
ErnestG

---

### Post by scorp123 on 2009-01-02
> **LowSky said:**
> lol the awesomeness of that word sends shivers down my spine  The word "automagically" is used several times in the kernel sources since at least the mid-90's. ;)

---

### Post by scorp123 on 2009-01-02
> **egalvan said:**
> So, no, the kernel does not always optimize. It does. You're mixing apples and oranges. Sorry to say so.

> **egalvan said:**
>  Tweaking Linux is good sport, and a learning experience. See the link I posted above. There is a few things you could tweak as far as responsiveness is concerned, if really this is what bothers you.

---

### Post by Skripka on 2009-01-02
> **egalvan said:**
> Could you explain what this change will do?


It allows your *buntu, at boot, to execute multiple operations in parallel, instead of one at a time.  How much you gain as a result varies with your hardware.

---

### Post by scorp123 on 2009-01-02
> **Skripka said:**
> It allows your *buntu, at boot, to execute multiple operations in parallel A small word of warning here ... the stuff doesn't work too well in my case, e.g. services that are dependent on each other are now started in parallel instead of one after the other ... booting is faster yes, but in my case some of my hardware (e.g. WiFi) stops working correctly.

So if anyone uses the hint above ... check if everything is working! And makes notes of what you changed ... just in case you have to undo those changes again ;)

---

### Post by bradthewanderer on 2009-01-02
You have issues :P

---

### Post by Skripka on 2009-01-02
> **scorp123 said:**
> A small word of warning here ... the stuff doesn't work too well in my case, e.g. services that are dependent on each other are now started in parallel instead of one after the other ... booting is faster yes, but in my case some of my hardware (e.g. WiFi) stops working correctly.

So if anyone uses the hint above ... check if everything is working! And makes notes of what you changed ... just in case you have to undo those changes again ;)

YMMV as they say.  There's sometimes a reason for defaults being minimal   ;)

---

### Post by egalvan on 2009-01-02
> **vor said:**
> You are confusing performance with features.  PAE is a feature.  In fact, PAE actually has a performance penalty in some cases (though, it's not generally noticeable).

No, I'm not confused...

just countering the point about the kernel making automatic optimizations.

If I install 8gigs of RAM because I need it (big videos, for instance).
and the kernel only sees 4gigs, then that is not optimum.

A feature can increase ( or well decrease ) overall performance, it's true.

But what is worse, the performance hit of PAE, or the performance hit of swapping out RAM to the drive?

Which is what optimizing is all about...
finding the balance one needs.


And I may add, "fast" is not the same as "faster" :)

"fast" is subjective; everybody has their own definition.
What is fast to me, may seem slow to you.

"faster" is objective, it means "at a higher speed or rate than what it is running or moving now"  :)

ErnestG

---

### Post by ibuclaw on 2009-01-02
> **egalvan said:**
> No, I'm not confused...

just countering the point about the kernel making automatic optimizations.

If I install 8gigs of RAM because I need it (big videos, for instance).
and the kernel only sees 4gigs, then that is not optimum.

A feature can increase ( or well decrease ) overall performance, it's true.

But what is worse, the performance hit of PAE, or the performance hit of swapping out RAM to the drive?

Which is what optimizing is all about...
finding the balance one needs.


And I may add, "fast" is not the same as "faster" :)

"fast" is subjective; everybody has their own definition.
What is fast to me, may seem slow to you.

"faster" is objective, it means "at a higher speed or rate than what it is running or moving now"  :)

ErnestG

Ahh... but in order to achieve your goal, one must appropriately benchmark, before and after the change.

It is of no use saying it is faster if you think it... that is nothing more than just a placebo to your mind.
Placebo's will always wear off, one way or another.

Regards
Iain

---

### Post by scorp123 on 2009-01-02
> **egalvan said:**
> No, I'm not confused...  You are.

> **egalvan said:**
>  just countering the point about the kernel making automatic optimizations. It does as far as SMP is concerned, and that was OP's question and this is what I answered. As far as multiple CPU's and multiple cores are concerned, there is nothing to do, the kernel automagically decides things like CPU affinity, CPU loads, CPU task transaction, and things like that. On older Linux kernel releases way back in the 90's when SMP was still a new feature there were a few things you had to take care of manually .... but since kernel 2.4 and especially kernel 2.6 this stuff is totally irrelevant and obsolete. The kernel does SMP optimisation automatically. Period.

> **egalvan said:**
>  If I install 8gigs of RAM ...  This has nothing to do with OP's question regarding SMP. You are mixing apples and oranges.

---

### Post by egalvan on 2009-01-02
> **scorp123 said:**
> It does. You're mixing apples and oranges. Sorry to say so.


OK, I' mixing apples and oranges, and kumquats and kiwis..8-[

And let's assume you are correct, and the kernel "always optimizes".:neutral:

My computer has 8gigs of RAM, but the Desktop kernel only sees 4gigs of RAM.

Explain how seeing only half the RAM is considered "optimized":confused:


>  See the link I posted above. There is a few things you could tweak as far as responsiveness is concerned, if really this is what bothers you.

And why say we are "bothered", or that we think it is "bad"?

As I wrote in my previous post, sometimes we do this for "fun":D, or "just because we can", or "enjoyment":)
or for bragging rights...

I live in Texas, where everything is BIGGER and FASTER and TALLER, y'all! ):P

---

### Post by scorp123 on 2009-01-02
> **egalvan said:**
>  My computer has 8gigs of RAM, but the Desktop kernel only sees 4gigs of RAM.  Can you explain to me what your memory "problem" has to do with OP's question regarding SMP optimisation? ](*,) That's what we are talking about here. 

You are kidnapping this thread with your own issues instead of doing the right thing and either trying to help OP solve his problem or move away and open your own thread if you have problems of your own.

But just because I am in a good mood today, here is a few things you could try to resolve your memory "problem":
[http://ubuntuforums.org/showpost.php?p=6304828&postcount=4](http://ubuntuforums.org/showpost.php?p=6304828&postcount=4)

> **egalvan said:**
>  Explain how seeing only half the RAM is considered "optimized":confused:  I didn't say that. You are mixing apples and oranges. Please go back to Posting #1 and read it again. **[COLOR="Red"]We're talking about OP's Quad-Core CPU and his question on how to "optimise" _them_ (= the Quad-Core CPU's)[/COLOR]**.

If you cared to read stuff before posting you might have grasped that until now!

---

### Post by egalvan on 2009-01-02
> **scorp123 said:**
> Can you explain to me what your** memory "problem"** has to do with OP's question regarding SMP optimisation? ](*,) That's what we are talking about here. 

**You are kidnapping this thread with your own issues** instead of doing the right thing and either trying to help OP solve his problem or move away and open your own thread if you have problems of your own.

But just because I am in a good mood today, here is a few things you could try to resolve your memory "problem":
[http://ubuntuforums.org/showpost.php?p=6304828&postcount=4](http://ubuntuforums.org/showpost.php?p=6304828&postcount=4)

 I didn't say that. You are mixing apples and oranges. Please go back to Posting #1 and read it again. **[COLOR="Red"]We're talking about OP's Quad-Core CPU and his question on how to "optimise" _them_ (= the Quad-Core CPU's)[/COLOR]**.

**If you cared to read stuff before posting you might have grasped that until now!**


First:
My "problem" started at post #8, where there appears to be a blanket statement regarding "optimizations"

*The Linux kernel does all the optimising automagically for you*

Perhaps you did not intend it to be a blanket statement, but only refer to SMP.
If so, my mistake.

My posts were intended to show the PAE situation as an *example* of how the kernel does not always optimize.


Second, I solved my "memory problem" long ago by using the Server kernel.

Third, my "issues" were with posts inside this thread.


Fourth, since you implied I did not read the Original Post,
note the the OP does not have a quad-core.

He stated he has a **Core2Duo**, which is a dual core .

**from Intel's Product Brief for the Core 2 Duo**:

[i]Features and Benefits of the Intel® **Core 2 Duo** Desktop Processor
Feature:
Dual-Core Processing

Benefit:
**Two independent processor cores in one physical package **run at the same frequency, and share up to 6 MB of
 L2 cache as well as up to a 1333 MHz3 Front Side Bus, for truly parallel computing.[/i]

---

### Post by scorp123 on 2009-01-02
> **egalvan said:**
> *The Linux kernel does all the optimising automagically for you*  You're quoting out of context. Read that posting again and which sentence I quoted there.

**Your inability to grasp that is most annoying. _End of discussion._**

---

### Post by sdennie on 2009-01-02
There is no need for this thread to become a flame fest.  Considering PAE a performance optimization if you have more than 3G of RAM might be valid. The benefits you gain from PAE in this case probably outweigh the inherent performance loss you get by enabling it.  But, the thread isn't about PAE.  It's about optimizing for a multi-core processor (doesn't matter how many cores) and so the assertion that the kernel is likely to do this for the user is absolutely true.  The suggestions for making userspace better utilize multiple cores are great but, the kernel is indeed already very smart about using more than 1 processor.

---

### Post by scorp123 on 2009-01-02
> **vor said:**
> But, the thread isn't about PAE.  It's about optimizing for a multi-core processor (doesn't matter how many cores) and so the assertion that the kernel is likely to do this for the user is absolutely true.  Exactly what I have been saying. Thank you.

As I see it OP's question was answered .... and therefore this thread could be closed, IMHO.

---

### Post by toallpointswest on 2009-04-21
> **tinivole said:**
> Multiple CPUs can infact be used to [optimise power saving]("http://lesswatts.org/"), and although 95% of all apps are optimised for one core only, it is possible to do what you can here or there:

**Startup**
```
sudo gedit /etc/init.d/rc
```
find the line: CONCURRENCY=none
And change it to
```
CONCURRENCY=shell
```

**Firefox**
There is an option in the firefox browser about:config called **network.http.pipelining** that /can/ speed up firefox if turned on and your cores support its use.
Also, **network.http.pipelining.maxrequests** to be turned up to about 6.


**IRQs**
Interrupt requests by default, only go to the one core. But (and this is mostly for powersaving sake) you can split the requests with a handy little daemon tool
```
sudo apt-get install irqbalance
```
Info about it found here: [http://irqbalance.org/](http://irqbalance.org/)

There are plenty of fruitful choices after a quick search.
Though it is the knowing which ones will be best that is the most difficult decision.

Regards
Iain

Irqbalance made a major improvement in the responsiveness of my Quad-core system. Thanks!

---

