---
title: "DeVeDe conversion while browsing w/ Firefox: Interrupted Processes"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by rocuan on 2010-07-17
Howdy!
First, let me just say these forums have saved me endless hours of ](*,)
so thank y'all in advance =D>

This is a general processing question but is specific to the slick little program DeVeDe I am sure most of you are familiar with.

I am converting an .avi to VIDEO_TS on a single-core laptop with 2gb of RAM.
Conversion obviously takes a while, an hour or more, but doesn't really eat up much processing power. 
So, it seems to me that it running other programs concurrently shouldn't affect the quality of the DeVeDe output.

I have a rudimentary understanding of process scheduling in Linux and will rip a quote from O'reilly's *Understanding the Linux Kernel*:
> In Linux, process priority is dynamic. The scheduler keeps track of what  processes are doing and adjusts their priorities periodically; 
in this  way, processes that have been denied the use of the CPU for a long time  interval are boosted by dynamically increasing their priority.  
Correspondingly, processes running for a long time are penalized by  decreasing their priority.
So,
if I watching YouTube videos and converting .avi's at the same time, the two will be trading off use of the processor, and, 
while possibly lengthening the conversion time, shouldn't affect the final result of DeVeDe's work. Right?
-or-
if Firefox dominates the CPU at a critical time, the conversion could be interrupted/compromised, degrading the final result . Right?

Have converted countless vids over the years on both *nix and M$ and never really reached a concrete conclusion on this.
I have had conversions end up choppy & out of sync but could be caused by something completely unrelated.
I just don't know.
Would love to hear your opinions/results/answers.

---

### Post by diablo75 on 2010-07-17
No matter how many apps you have running on your laptop, your video conversion output will be exactly the same every time.  The CPU is simply having to multi-task between separate applications, which is great because you wouldn't want programs to get stuck behind other processes that are hogging all the attention of the CPU.  I kind of think of the CPU like I think about the customer service counter at a department store... except there's no line for people to stand in; more of a mob that, more or less, get to talk to the CPU almost simultaneously (might be more like the floor of the NY Stock Exchange, but without the yelling).  In the end, all the customers walk out with the results they were expected to obtain.  Because at the very basic level of things, we're talking about math problems being solved, and if you ask the CPU to compute the same problem twice or more, you're going to get the same answer every time.

Continuing the analogy, take a look at this customer here we'll call Mr. DeVeDe.  This guy just showed up with 15 shopping carts filled with stacks of printed data which combined make up the original video file you are wanting to convert.  He will proceed to instruct the CPU (customer service rep) to begin crunching a LOT of math problems, per the parameters of the user preferences and the encoders selected.  The output the CPU gives back is always going to be the same, no matter how many other customers are gathered around the CPU asking for their own math problems to be solved for them.

The only thing that is going to affect your final output quality more than anything else are the explicit quality settings you should customize before converting.  Bitrate is probably the simplest of these settings and easiest to understand.  The more bits you have to describe a few frames of video and the audio to go with it, the more detailed your video quality will be.  Fewer bits, and you'll get crummy, highly compressed video.  The term compression in this context means video/audio that has had some of the not-so-noticeable details smoothed over in an effort to reduce the amount of 1's and 0's it takes to "describe" the video/audio in question.  Hence the opposite of compressed video: "Lossless" video, which means pixel for pixel accuracy without the little visual tricks used to make our eyes think no detail has been lost... and usually an extremely large file (like 20 to 50 MB per SECOND).

---

### Post by rocuan on 2010-07-18
Thank you for confirming my hopes of lossless multi-tasking and for the great analogy.

---

