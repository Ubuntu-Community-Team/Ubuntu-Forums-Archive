---
title: "Programs Not Starting"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by pemur1 on 2010-03-08
I've tried to search for this, but I just can't find anything that fits my particular problem.

I came home from work and wanted to listen to some music. I clicked on Rhythmbox, but it wouldn't open. I then tried Banshee, and it wouldn't open. I'd get the "Starting Rhythmbox (or Banshee)" dialogue in the bottom panel, but after a few seconds it goes away. I'm not exactly sure what's causing this. I even restarted, but the programs still wouldn't open. Any assistance is greatly appreciated.

---

### Post by Endomancer on 2010-03-08
I wish I knew what causes this too, although Rythmbox works fine for me, a lot of games I install from the software centre do this to me.

But in the case of Rythmbox when you try opening it pay attention to the right side of the top panel, mine opens there but often doesn't open into the main screen area

---

### Post by pemur1 on 2010-03-08
> **Endomancer said:**
> I wish I knew what causes this too, although Rythmbox works fine for me, a lot of games I install from the software centre do this to me.

But in the case of Rythmbox when you try opening it pay attention to the right side of the top panel, mine opens there but often doesn't open into the main screen area

I kept an eye on the top panel also, but it didn't come up.

---

### Post by pemur1 on 2010-03-08
Another strange problem.

I attempted to open the Ubuntu Software Center, but it also won't open. I'm kind of perplexed now.

---

### Post by Endomancer on 2010-03-08
Unfortunately thats all I can think of, I posted my question on the games not loading back in December, and am still waiting for a response. I hope you have better luck

---

### Post by JerichoKru on 2010-03-08
> **pemur1 said:**
> I've tried to search for this, but I just can't find anything that fits my particular problem.

I came home from work and wanted to listen to some music. I clicked on Rhythmbox, but it wouldn't open. I then tried Banshee, and it wouldn't open. I'd get the "Starting Rhythmbox (or Banshee)" dialogue in the bottom panel, but after a few seconds it goes away. I'm not exactly sure what's causing this. I even restarted, but the programs still wouldn't open. Any assistance is greatly appreciated.

Open the terminal and try running a program there.

For example:

```
banshee
```

and post the output.  I don't know what the ubuntu software center executable is called...since I'm on Xubuntu, which has the old version of it.

---

### Post by exavoid on 2010-03-08
What Version of Ubuntu are you running?

Regards

---

### Post by pemur1 on 2010-03-08
> **JerichoKru said:**
> Open the terminal and try running a program there.

For example:

```
banshee
```

and post the output.  I don't know what the ubuntu software center executable is called...since I'm on Xubuntu, which has the old version of it.

I get this when trying Rhythmbox:

```
Error re-scanning registry , child terminated by signal
```

I don't get a thing with Banshee.

---

### Post by pemur1 on 2010-03-08
> **exavoid said:**
> what version of ubuntu are you running?

Regards

Ubuntu 9.10

---

### Post by rbc on 2010-03-08
Google came up with this:
[http://ubuntuforums.org/showthread.php?t=1331010](http://ubuntuforums.org/showthread.php?t=1331010)

Scroll down to Radio89's post. It's #8 in the list

---

### Post by rjdaggett on 2010-03-08
If you don't have a video driver with 3D accel, games will not start. They start then fail. This happened to me (ATi) untill you install a 3d driver. type this in a term "man apt-get" learn to fix the package maybe, but if its a game the video drivers doing it.

---

### Post by Endomancer on 2010-03-09
Thanx rjdaggett

I'll have to look a bit further into that, I already tried the ATI binary X.Org driver in the software centre and found it was a glutton on cpu usage, so I been using the driver on [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch) which is lighter on the cpu, but I guess it doesn't do 3d

---

### Post by pemur1 on 2010-03-09
> **rbc said:**
> Google came up with this:
[http://ubuntuforums.org/showthread.php?t=1331010](http://ubuntuforums.org/showthread.php?t=1331010)

Scroll down to Radio89's post. It's #8 in the list

That seemed to do the trick.

Thanks so much for your assistance, rbc.

---

