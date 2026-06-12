---
title: "Brasero DOES NOT WORK"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by itsols on 2010-06-28
Sorry if this seems like a duplicate. But this problem persists and I really could take some advice.

I have Ubuntu 10.4 LTS, with ALL updates in place.

I tried burning a wav file as an audio CD. Brasero reported everything as normal. The CD was ejected after completion.

But when I re-insert the CD, I find it BLANK!

Either I'm missing something or there's a flaw in the program.

Really like to get this working.
Appreciate your views.

---

### Post by dineshs on 2010-06-28
Did you try k3b ?

---

### Post by radddi on 2010-06-28
Brasero really hasn't worked properly for quite some time and I too find it frustrating... So I use gnomebaker in stead and it works flawlessly. Plus, you don't need to install extra KDE stuff/libs.

```
sudo apt-get install gnomebaker
```

.:CheerS:.

---

### Post by philinux on 2010-06-28
> **itsols said:**
> Sorry if this seems like a duplicate. But this problem persists and I really could take some advice.

I have Ubuntu 10.4 LTS, with ALL updates in place.

I tried burning a wav file as an audio CD. Brasero reported everything as normal. The CD was ejected after completion.

But when I re-insert the CD, I find it BLANK!

Either I'm missing something or there's a flaw in the program.

Really like to get this working.
Appreciate your views.

Please report this as a bug. Open a terminal.

```
ubuntu-bug brasero
```

---

### Post by itsols on 2010-06-28
Many thanks for everyone's thoughts!

I've also filed a bug report on this.

Cheers!

---

### Post by crackpotfox on 2010-06-28
> **radddi said:**
> Brasero really hasn't worked properly for quite some time and I too find it frustrating... So I use gnomebaker in stead and it works flawlessly. Plus, you don't need to install extra KDE stuff/libs.

```
sudo apt-get install gnomebaker
```.:CheerS:.


is it ok to uninstall Brasero since it is an original program (isn't it)

i just don't want to mess up my ubuntu... i already messed up windows

---

### Post by itsols on 2010-06-28
Talk about messing up :)

I actually did... Hmmm... I did not, the upgrade did, when I moved from 8.04 to 10.04.

Anyway it's good to have my work back.

About removing Brasero, I don't think it'll cause any issues. There are always others that can be used in its place. But in my case I'm low on resources and I need to manage with what I have. Since my laptop is a dual boot with Windows The hard disk is rather limited. So I must get what I have to work.

And if I can have my gnomebaker doing the job, I don't see why I should cling on to Brasero.

The only reasons (IMHO) you should stick to a program is if:
1. You get support
2. You like it.

---

### Post by SoFl W on 2010-06-28
Did it write *anything* to disc?  Sometimes you can see the burn on the disc but it is a bad burn.  Is there a "simulate" option in Brasero?

---

### Post by itsols on 2010-06-28
No, there was no simulate. In fact I chose the option to write direct to CD instead of via the HDD.

Was there anything written? No, the disk is blank. Even shows blank on Windows. Also looked for burn indications on the surface of the CD. Nothing there.

This is surely something to do with Brasero.

I know it worked before. I even burnt the 10.04 ISO without a problem. But then I don't recall if that was on Brasero.

I honestly think this upgrade had a few issues.

But I'm glad I can continue to work on it. Most of my work is on development of LAMP apps and I'm kind of getting used to C# on Mono. So I hardly use too many other features. Perhaps time will tell :)

Cheers!

---

### Post by RetchingRabbit on 2010-06-28
Well, I burned 10.4 on 9.10 and it worked fine. 
The issue you describe could easily be a hardware issue. It in no way "surely" is a brasero bug.

---

### Post by Linuxforall on 2010-06-28
Brasero has bug with particular brand of drives so it could be firmware issue, with my SONY Optiarc, all the features work fine but with my LG-Hitachi, it throws a fit.

---

### Post by bodhi.zazen on 2010-06-29
I have tried a lot of Linux CD/DVD burners and nothing beats K3b .

Go ahead and file a bug report and I hope it is fixed soon, in the mean time, consider k3b ...

---

### Post by itsols on 2010-06-29
Thanks for your thought but I know a hardware issue when I see one. Maybe you missed a point in one of the posts above. Looks at this:

1. I CAN burn any CD with Windows.
2. I burnt CDs using Ubuntu 8.04
3. With 10.04, I burnt an ISO (not sure if I used Brasero)

The only issue is that I can't burn the WAV file into an audio CD.

Now this is certainly not a hardware issue :)

---

### Post by itsols on 2010-06-29
Thank you bodhi.zazen. Going by my old records of memory, I recall you giving me some good advice in the past. So I'll definitely consider k3b although I don't know what it is like :)

A bug report has already been filed. And in response to another reply I received earlier in this thread, I've also installed gnomebaker. But I'm yet to try it. If that works, I'll probably stick to it. Otherwise I'll have no option but to go for your k3b alternative.

Thank you!

---

### Post by itsols on 2010-06-29
GnomeBaker it is!

I just tried using GnomeBaker with the SAME CD (that failed to have anything on it with Barsero) and it worked like a breeze!

I must say though, that the interface on Brasero was more 'humane'. But I think GnomeBaker served the purpose for now and I'll have to stick to it until such time that Brasero is back with its fixes.

Happy Computing!

---

### Post by Linuxforall on 2010-06-29
Brasero uses wodim and thats the interface for hardware, its a hardware/software issue because with Karmic I had no such issue, however with Lucid Brasero became selective, works brilliantly with SONY, erratic with LG, both are one month old DVD Writers. They both work fine with K3b in Kubuntu.

Gnomebaker works for both drives here under Lucid. This wodim/Brasero bug is also affecting Fedora and there are plenty of posts related to this issue.

---

### Post by Jakiejake on 2010-06-29
> **crackpotfox said:**
> is it ok to uninstall Brasero since it is an original program (isn't it)

i just don't want to mess up my ubuntu... i already messed up windows

Gnome Baker Is Great
But I still like Brasero (When It Works!)
And you won't mess anything up!
Run this to remove it
> apt-get remove brasero

---

### Post by cheapie on 2010-06-29
> **bodhi.zazen said:**
> I have tried a lot of Linux CD/DVD burners and nothing beats K3b.

Nothing beats the splash screen of older versions of K3B either.

[img]http://k3b.plainblack.com/uploads/MT/fK/MTfKD9QmNDpA6wY60vrLVA/splash.jpg[/img]

---

### Post by Jakiejake on 2010-06-29
> **cheapie said:**
> Nothing beats the splash screen of older versions of K3B either.

[img]http://k3b.plainblack.com/uploads/MT/fK/MTfKD9QmNDpA6wY60vrLVA/splash.jpg[/img]

Awesome!

---

### Post by rbo83 on 2010-10-21
Only one caution : If you use rythmbox for music, it uses brasero for disc burning...

---

