---
title: "Unable to watch flash video's on NASCAR.com"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by alienexplorers on 2009-03-08
I have been trying to watch flash video's on NASCAR.com and the video's don't play correctly.  The video's stutter and jump ahead missing much of the video's.  I have tried nonfree flash and adobe flash.  Any help would be appreciated.

---

### Post by robenroute on 2009-03-08
Hi there,

I've just tried a few videos on nascar.com and all seems fine to me. I'm using Ibex, FF and the non-free flash plug-in.

---

### Post by cooney on 2009-03-08
Hershey, PA.  Wow.  Do they still have the steet lights that look like Hershey Kisses.  They were so cool.

To 'try' to answer your question.  I have to assume that your processor speed is 450 mHz.  Despite your running an nVidia video card,  I believe that your cpu is just way to slow.  I'm open to correction if wrong, but when I was doing the very same thing with a 1.1gHz + nVidia (Fedora/Ubuntu) I experienced stutters but, probably not as erratic as yours.  Now that I'm running a 3.x Pentium, gigs 'o ram, blah, blah, blah;  it's pretty smooth but, I'll get an occasional hic-cup (stutter) now and then.

Other sites (you-tube, cbs.com, etc...) seem to be a lot smoother than Turner's nascar.com.

I know you don't want to here this and I'm sorry that I can't wave my magic wand and make the stutters go away but, tis what it is my friend.  I'm pretty sure they're streaming those vids so you "can't" copy and save them.  If that's the case then it just amplifies your problem.

One last time.  I am very open to being totally wrong regarding this no-solution post and would welcome a solution that anybody may have unearthed as the OP is asking for.

go 88

---

### Post by cooney on 2009-03-08
[I]Hi there,

I've just tried a few videos on nascar.com and all seems fine to me. I'm using Ibex, FF and the non-free flash plug-in.[/I]

What cpu, speed, ram, vid card?

Inquiring minds want to know.

---

### Post by Marshal0505 on 2009-03-08
> **cooney said:**
> 

I know you don't want to here this and I'm sorry that I can't wave my magic wand and make the stutters go away but, tis what it is my friend.  I'm pretty sure they're streaming those vids so you "can't" copy and save them.  If that's the case then it just amplifies your problem.
...


Ok I don't have a real solution but the flash videos are getting cached by your browser.So go to your /tmp directory and you can save your vid under another name and watch it without stutter.

---

### Post by kelvin spratt on 2009-03-08
I think a lot of the problem is the site its self.
If you tube plays ok he should not have a problem,
I just tried the site and there was negligible buffering meaning your overtaking the feed so then it stutters.

---

### Post by cooney on 2009-03-08
> **Marshal0505 said:**
> Ok I don't have a real solution but the flash videos are getting cached by your browser.So go to your /tmp directory and you can save your vid under another name and watch it without stutter.

I just tried your suggestion and you're right.  They're not streamed and work as you say.  To be frank, With a 3.+ gig cpu, I rarely see a stutter.  But watching it via the cache (/home/YOUR-USER_NAME/.mozilla/firefox/po34vlme(YOUR_FUNKY_NUMBER-NOT_MINE).default/Cache) is the fastest.

What's your specs?

I really think the OP just doesn't have enough horsepower.  Don't mean to be a pita.  Just trying to get to the root as quickly as possible.

---

### Post by robenroute on 2009-03-08
> **cooney said:**
> [I]Hi there,

I've just tried a few videos on nascar.com and all seems fine to me. I'm using Ibex, FF and the non-free flash plug-in.[/I]

What cpu, speed, ram, vid card?

Inquiring minds want to know.

Running an HP laptop (6710b): integrated Intel X3100 graphics, CPU is C2D 7500, 2 GB RAM

---

### Post by cooney on 2009-03-08
> **robenroute said:**
> Running an HP laptop (6710b): integrated Intel X3100 graphics, CPU is C2D 7500, 2 GB RAM

Proves my point.  Your CPU is 2 gig. alienexplorers, the OP of this thread, cpu is 450 meg.  I really believe that's his problem.

Sorry alienexplorers.

Ya'all make some mighty fine chocolate there in Hershey, PA though.

You may have better results if you pause the video once it starts playing, then once it's fully downloaded, resume playback.  If it still stutters then follow Marshal0505's advice and play it from FFs cache.  If that don't work then time to find something faster

go 88

---

