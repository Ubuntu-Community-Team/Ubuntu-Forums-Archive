---
title: "R-T kernel"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by 7G Operator on 2010-06-01
Anyone know when a wonderful zero (ish;) latency real-time kernel is going to be released for 10.04? Had one for Karmic, (it had the name of some dude by it as i recall), and it was fandabydozy. Cheers

- Dan

---

### Post by collinp on 2010-06-01
Are you referring to this?

[http://packages.ubuntu.com/lucid/linux-image-2.6.31-10-rt](http://packages.ubuntu.com/lucid/linux-image-2.6.31-10-rt)

---

### Post by 7G Operator on 2010-06-01
Yes. Thats the one i was using with Karmic i believe. Is there an R-T kernel yet available specifically for Lucid? I was reading about it being under development a while back, wandered if there was any further news?

---

### Post by trulan on 2010-06-01
What news there is is here:
[http://ubuntuforums.org/showthread.php?t=1470264](http://ubuntuforums.org/showthread.php?t=1470264)
Basically, there is and there isn't.  You can use the kernel from Karmic (linked above) or you can use 2.6.33-rt from a ppa (or build it yourself if you want some adventure) but it's not exactly supported.  NVidia drivers and Broadcom drivers need patching for starters.  But, there it is if you want it.

---

### Post by NightwishFan on 2010-06-01
There is the "preempt" kernel designed for low latency servers, such as game servers. It could also be run on desktops I am sure. Then there is the "real time" kernel which is for time critical operations. Lucid should have both.

The one you are likely looking for is "preempt".

---

### Post by 7G Operator on 2010-06-01
Fair doos thanks for the responses. Do you have any experience using the RT31 or RT33 on Lucid Trulan? If so which would you recommend? I was using the 31 ingo molar on Karmic, seemed to work well. When you say kernel patches are you talking about the rtprio -99, memlock - unlimited (512MB in my case, don't believe in awarding total memory control to a program in case of crashes for better or for worse) - nice -19, changes? What exactly is the different between a R-T Kernel and a pre-emption kernel? To reduce latency to as close to zero as possible, surely they have the same principles right?
  Also the RT33 is still in prototype form right? Is there a place to see peoples experiences with these prototypal =P systems? I.e any bugs e.t.c? 

Cheers - Dan

---

### Post by trulan on 2010-06-01
I have used both 2.6.31-rt and 2.6.33-rt extensively.  And while I've expended a lot of time and effort in getting my system fully functional on 2.6.33-rt, I can't honestly say I've seen a whole lot of difference.  It's probably mostly that it seems cooler to have a newer kernel.

Changes like RTPRIO and NICE just give you permission to use the added features of the RT kernel.

Lowlatency is a less drastic version of full real time preemption.

When I referred to patching things, I meant hardware drivers, specifically for NVidia video cards and Broadcom wireless cards.  If you use the generic kernel, the low-latency kernel, or 2.6.31-rt, these drivers **should** install with no issues.  If you use 2.6.33-rt, these drivers **will not work** unless you manually change some code and build them yourself.  Not a huge deal, but it's a bit intimidating if you've never hand-edited any code before.

2.6.33-rt is not considered a prototype anymore, it just wasn't released in time to be included in Lucid, and so support for things like drivers will not be included in Lucid either.  I haven't experienced any operational bugs with either kernel, just broken drivers that need to be hand-edited and manually compiled.

---

### Post by 7G Operator on 2010-06-01
Cool. Cheers for the heads-up dude.
Basically though low latency and zero latency and real-time and pre-emption, now appear to be simply differing ways of saying as minimal latency as possible. And merely differing tags for the varying builds of kernel? I realise it seems to be more to do with priority of applications in that R-T would devote more compute cycles to audio processing than p0erhaps low latency, which would reserve cpu time for other programs as well? Am i wrong in thinking this is the only difference between low, zero, pre-empt e.t.c? If so i think to clarify this terminology, may be a wise step forward ;).

- Dan

---

### Post by NightwishFan on 2010-06-01
From what I know, as I said previously: Real Time is for time critical applications that would fail if they do not meet a specific deadline. Low Latency is something that is desired for certain workloads, but would not fail if a deadline is not met.

---

### Post by trulan on 2010-06-01
Right.  It all hinges on the word 'preemption' which is basically allowing a specific process (for example, time-critical audio, or industrial welding lasers) to be processed in exactly the time specified, rather than having to politely wait their turn like regular computer programs.  It may shed some light on this to realize that a server kernel allows even less preemption than a regular desktop kernel.

So there are four levels of preemption in the Linux kernel:
1. Server (almost no preemption)
2. Desktop (a little preemption)
3. Low latency (more preemption)
4. Real Time (full preemption)

---

### Post by 7G Operator on 2010-06-01
Would it not be best to set rtprio as 100 then? (assuming that is per cent value). Also when utilizing hyper-threading technology should this and can this be set over 100%? For instance when looking at the system monitor, (Single core, dual logical core Hyperthreaded) it sometimes registers over 100% and up to 200% (obviously). Should this be taken into consideration when setting rtprio setting?

---

### Post by 7G Operator on 2010-06-01
rtprio  executes *command*  with a real-time priority, or changes the real-time priority of currently executing process *pid*. Real-time priorities range from zero (highest) to 127 (lowest). Real-time processes are not subject to priority degradation, and are all of greater (scheduling) importance than non-real-time  processes. See [*rtprio*(2)]("http://docs.hp.com/en/B2355-90693/rtprio.2.html") for more details.
If -t  is specified instead of a real-time *priority*, rtprio  executes *command*  with a timeshare (non-real-time) priority, or changes the currently executing process *pid*  from a possibly real-time priority to a timeshare priority. The former is useful to spawn a timeshare priority command from a real-time priority shell.
If -t  is not specified, *command*  is not scheduled, or *pid*'s real-time priority is not changed, if the user is not a member of a group having PRIV_RTPRIO  access and is not the user with appropriate privileges. When changing the real-time priority of a currently executing process, the effective user ID of the calling process must be the user with appropriate privileges, or the real or effective user ID must match the real or saved user ID of the process to be modified.
**RETURN VALUE**

rtprio  returns exit status 0 if *command*  is successfully scheduled or if *pid*'s real-time priority is successfully changed, 1 if *command*  is not executable or *pid*  does not exist, and 2 if *command*  (*pid*) lacks real-time capability, or the invoker's effective user ID is not a user who has appropriate privileges, or the real or effective user or the real or effective user ID does not match the real or saved user ID of the process being changed.[B]
[/B]


Never mind about my first point, i recently found this bit of info, which seems to do nothing more than confuse me even further haha *sigh. So 0 is better than 127? Why set rtprio at 99 then? 
****

---

### Post by 7G Operator on 2010-06-01
If a program was written that could assign rights to a program (virus) and then set the rtprio,to its maxium level, could this be a possible future security issue?, as in my understanding it would not allow any other service to interrupt the cpu so to speak?
   If this was implemented as part of a boot-up script perhaps this could lead to an undesirable outcome? I am no professional at such things (obviously haha) and im sure its already been discussed e.t.c, but reading such things, kinda does make you wonder i guess. If such a program manage to infiltrate Ram then it would surely spell game over for that computer? Haha maybe im being a bit pessimistic i guess. Perhaps someone more knowledgeable could enlighten me. Thanks for the temporary clarification by the way Trulan dude, haha i say so because it seems having tried to research it, i have but become more confused =P. 

Cheers - Dan

---

### Post by geoff123 on 2010-07-18
7G - 
I ran across this post looking for something else and thought I could add a little info to this thread.  I am also no "expert" on this, but I think the answer to your question "could this be a possible future security issue" is yes.  However, I view this as relatively low risk since the virus would have to be written to use the real-time capabilities and the person running the program would need the privileges of running real-time. Real-time use is not for the average desktop computer user that uses the web, it has no benefit and could have security issues you mention. That is one of several reasons it is not included in Ubuntu - I think the other being other third party video or wireless drivers are not always designed for this and can be harder to get working or have other problems.

I think most "desktop" users (such as me) that are using real-time capabilities are doing music/audio recording and have tweaked their computers for this purpose.  The real-time kernel allows me to make sure my sound card and midi inputs have the highest priority so that if I am playing some music on my keyboard it is captured with the greatest precision and accuracy and there is low latency from playing to capture to output.  It helps make sure that when I hit a note, it is captured within a millisecond all the time (not after 20 miliseconds where there will be a noticeable latency delay, and not over a range of 1 to 20 miliseconds, where the timing of the performance will be off), but always within 1 to 2 milliseconds.  

Of course there are other uses also for scientific and manufacturing equipment, anything where input and output of a specific piece of equipment or program are time critical - but I don't use that stuff.

Hope this helps. G

---

