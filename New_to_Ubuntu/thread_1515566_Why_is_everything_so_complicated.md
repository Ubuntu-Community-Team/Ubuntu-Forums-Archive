---
title: "Why is everything so complicated?"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Martin Sullivan on 2010-06-22
Newbie here, terminal will not accept password! cannot type in password!

---

### Post by philinux on 2010-06-22
> **Martin Sullivan said:**
> Newbie here, terminal will not accept password! cannot type in password!

It doesn't appear as *** etc. Just type it and press enter.

---

### Post by ThesaurusRex on 2010-06-22
When typing passwords, you're text is "hidden." Simply type your password and press return (or enter).

---

### Post by Rubi1200 on 2010-06-22
Silly question, but are you sure you typed it correctly and that CAPS lock was off?

Did you try changing the password to something else in System > Preferences > About Me > Change Password ?

See also here:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

The above is intended if other measures don't work (see posts above)

---

### Post by Mark Phelps on 2010-06-22
> **Martin Sullivan said:**
> Newbie here, terminal will not accept password! cannot type in password!

It's not necessarily "complicated" -- but it is different.

The more you stay in the Ubuntu world, the more you will find little differences from MS Windows.

If you're OK with making the needed adjustments, you will become amazed over the variety and extent of stuff you will be able to do.

But ... if you're expecting Ubuntu to be nearly identical to MS Windows, I'm afraid you're going to be sorely disappointed.

---

### Post by Martin Sullivan on 2010-06-22
Thank you!  Simple enough but still cannot get Linksys wireless adapter to connect to server?

---

### Post by Martin Sullivan on 2010-06-22
Thanks but have been told that typing does not show when entering password!

---

### Post by Martin Sullivan on 2010-06-22
Check!  I've already deduced that.  It just seems counterintuitive!

---

### Post by Martin Sullivan on 2010-06-22
Thanks Rex!

---

### Post by Martin Sullivan on 2010-06-22
> **philinux said:**
> It doesn't appear as *** etc. Just type it and press enter.
 
Thanks!

---

### Post by QIII on 2010-06-22
Counter-intuitive only when you expect Windows to inform your intuition.

One of the things that may take some time is divorcing yourself from the expectation of Windows-ness.

It really does become more intuitive - when your expectation is Linux-ness.

It's like learning a new language.  It can be frustrating at first because the new language is not "intuitive" to you because it is not like English.  Eventually, the new language exposes its intuitiveness.

---

### Post by Martin Sullivan on 2010-06-22
> **QIII said:**
> Counter-intuitive only when you expect Windows to inform your intuition.
 
One of the things that may take some time is divorcing yourself from the expectation of Windows-ness.
 
It really does become more intuitive - when your expectation is Linux-ness.
 
It's like learning a new language. It can be frustrating at first because the new language is not "intuitive" to you because it is not like English. Eventually, the new language exposes its intuitiveness.
 
Nicely stated and I have assumed Windowness, I'll have to switch gears!

---

### Post by QIII on 2010-06-22
It takes some time.  Don't get frustrated.  I started out with Unix and had to get "used to" Windows way back in the day.

Linux was a homecoming for me.

---

### Post by Martin Sullivan on 2010-06-22
> **QIII said:**
> It takes some time. Don't get frustrated. I started out with Unix and had to get "used to" Windows way back in the day.
 
Linux was a homecoming for me.
 
From my viewpoint it appears that most of the Linux help comes from the internet and I am frustrated by the fact that I cannot figure out how to even connect to the net!  I've tried the "use hidden connection' and am able to connect to the router but there it stops!  I've been trying for several days to access the internet but am about to give it up as a bad job.  Any suggestions??

---

### Post by QIII on 2010-06-22
I certainly understand how the inability to get online might be a bit of a roadblock!

Could you give us some information about your router, how you have it  set up and more detail of what you have done to get on to the web?

Are you connected directly to the router or are you going through a home network and accessing it through Windows ICS?

Can you get online while using the LiveCD in a Live session?

Is your router set to accept only specified MAC/IPs?  Are you trying to  use a wireless connection?  If so, what is the brand and model number of  your wireless card?

Is your installation "inside" Windows (Wubi), or stand alone?


(Sorry for all the questions.  Just trying to get enough info to be helpful.)

Just looked back through the thread and I see that you are using a Linksys wireless adapter -- what is the model?

---

### Post by ibuclaw on 2010-06-22
> **Martin Sullivan said:**
> Newbie here, terminal will not accept password! cannot type in password!

There is a sane way out you know. ;)

In a terminal:
```
sudo visudo
```
You may be asked which editor to choose, just select the one suggested as easiest (nano).

In the file, look for the line
```
Defaults        env_reset
```
and add "pwfeedback" on the end of the line, so it now looks like.
```
Defaults        env_reset, pwfeedback
```

Then save and run:
```
sudo -K
```
to reset the lock, and try sudo again on something.
```
sudo apt-get update
```
You should now see stars '*' being printed out as you type your password. :)

Regards

---

### Post by aysiu on 2010-06-22
> **QIII said:**
> Counter-intuitive only when you expect Windows to inform your intuition.

One of the things that may take some time is divorcing yourself from the expectation of Windows-ness.

It really does become more intuitive - when your expectation is Linux-ness.

It's like learning a new language.  It can be frustrating at first because the new language is not "intuitive" to you because it is not like English.  Eventually, the new language exposes its intuitiveness.
It actually has very little to do with Windows and Linux.

This is an inconsistency in the interface that really just has to do with what terminal veterans are used to (and not wanting to change that to avoid confusion in new users).

The terminal has no feedback, but the GUI does. It's inconsistent. And the GUI has it *in Linux*, not just Windows. The Mac terminal also offers to no visual feedback, but the Mac GUI does offer visual feedback.

More details here:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by QIII on 2010-06-22
Hmmmm...

Inconsistency?  I suppose.

Maybe I *have *been doing this too long.  To this old fart it just seems normal.  I think it was that way in my Unix days when GUI was a characteristic of chewing gum.   I'm pretty sure it's still that way in the terminal in Solaris and FreeBSD.  I'll have to check for sure when I get home.

Ah, well.  Maybe that's why is seems right to me.

Of course, I'm a relative newcomer.  I've been at this about 35 years.  Since dates in 64 bit Unix and Linux don't stop abruptly in 2038 like they do in 32 bit systems, 35 years out of 290 billion years is a pretty small fraction.  ;)

---

