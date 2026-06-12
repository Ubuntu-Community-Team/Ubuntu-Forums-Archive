---
title: "Resuming from hibernation messes the screen up at login"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Ima2k on 2011-05-02
I'm running a netbook with 11.4 on it and whenever I come back from hibernating (closing the lid/turning back on) the screen goes all black except the top left which is like a 8"x2" bar with messed up colors like the gfx card has fried(which it hasn't, just saying) and the only thing I can do is a hard restart.

It's all purple and stuff.

I'm running a dual core atom 1.5ghz with 2gb ram, intel gma 3150, 2gb dedicated to the swap*.

*The swap, I'm pretty sure is working, I have a 2gb logical partition for it, and system monitor shows 2gb of swap,although its always at 0% use / I've never used it much.

---

### Post by Steve H on 2011-05-02
Which graphics drivers are you using? Is it the proprietary or OS drivers?

---

### Post by Ima2k on 2011-05-02
> **Steve H said:**
> Which graphics drivers are you using? Is it the proprietary or OS drivers?


Thanks for the reply. I have not changed them, so OS drivers.

---

### Post by Ima2k on 2011-05-03
Sorry, but bump. 

I'm still getting this.

---

### Post by Steve H on 2011-05-03
> **Ima2k said:**
> Thanks for the reply. I have not changed them, so OS drivers.

You need to supply more info. 

Is it ATI or Nvidia? 

Which version of Ubuntu?

Have you checked the logs? What do they say?

---

### Post by treasonvoice on 2011-05-03
I have a fairly silly question. Are you running Wubi? Or do you have a separate dedicated partition for ubuntu?

---

### Post by Ima2k on 2011-05-03
> **Steve H said:**
> You need to supply more info. 

Is it ATI or Nvidia? 

Which version of Ubuntu?

Have you checked the logs? What do they say?


Sorry, I did mention in the first post. 11.4 and Intel GMA 3150.

And I do not know how to check logs.


> **treasonvoice said:**
> I have a fairly silly question. Are you running Wubi? Or do you have a separate dedicated partition for ubuntu?

Dual booted with Windows, dedicated partition for Ubuntu.

---

### Post by Steve H on 2011-05-03
Might be worth looking [here]("https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/745304"). It looks like a bug and a fix has been released.

Hope that helps.

---

### Post by Ima2k on 2011-05-03
> **Steve H said:**
> Might be worth looking [here]("https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/745304"). It looks like a bug and a fix has been released.

Hope that helps.


Alright thanks, what do I do now? just wait until it shows in the update manager?

Thanks.

---

### Post by EGamerHDK on 2011-05-03
I had this problem and it was a problem with the video card drivers apparently. I just searched "Add" and "Additional Drivers" came up. Selected it, and it gave me a choice between two drivers. I switched and it did the trick.

---

### Post by Steve H on 2011-05-03
> **Ima2k said:**
> Alright thanks, what do I do now? just wait until it shows in the update manager?

Thanks.

You could either try the suggestion from EGamer or wait for the next update, as stated in the bug report 

> Seth Forshee wrote on 2011-04-27:	 #15
The fix is currently sitting in the queue for the next stable kernel release and should be included in an update shortly after the natty release.

---

### Post by drmrgd on 2011-05-03
> **EGamerHDK said:**
> I had this problem and it was a problem with the video card drivers apparently. I just searched "Add" and "Additional Drivers" came up. Selected it, and it gave me a choice between two drivers. I switched and it did the trick.

I'll second this.  After my Natty install with an Nvidia GeForce 6800 I was getting all kinds of rendering problems after resuming from hibernation (or suspension). I couldn't even see the login box - it was just a large blob of graphical noise. Changing drivers "mostly" fixed the problem.  Now it only occurs occasionally, and when it does happen, all I have to do is mouse over the bad spot and it re-renders perfectly again.  

Try changing up the drivers to see if that fixes it.

---

### Post by EGamerHDK on 2011-05-03
> **drmrgd said:**
> I'll second this.  After my Natty install with an Nvidia GeForce 6800 I was getting all kinds of rendering problems after resuming from hibernation (or suspension). I couldn't even see the login box - it was just a large blob of graphical noise. Changing drivers "mostly" fixed the problem.  Now it only occurs occasionally, and when it does happen, all I have to do is mouse over the bad spot and it re-renders perfectly again.  

Try changing up the drivers to see if that fixes it.

Exactly what happens to me.  NVIDIA Quadro FX 770M...

---

### Post by micheledm on 2011-05-03
Same here. Dell XPS 1330M with Nvidia 8400M.

---

