---
title: "Skype sound stopped?"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by metallicamike on 2009-04-06
I was on Skype one day (as I am everyday :P) and i changed the volume on something and then all sounds quit working. Then after about a week it finally said 'Problem with audio playback' in the call window. and no matter what i try i cant get it to work again. it just kind of randomly quit. anyone know what the problem is? PS. i dont remember what I turned down but im pretty sure i turned it back on.

Thanks!:popcorn:

---

### Post by ionFreeman on 2009-04-06
I didn't change any sound settings, but I don't know that I've ever used this computer for Skype, and I probably haven't without a headset. But, I'm getting that same 'Problem with Audio Playback' message. Audio playback generally works great. It's just Skype.

---

### Post by metallicamike on 2009-04-06
thats because you need to configure it first. anyway bump.

---

### Post by metallicamike on 2009-04-06
If it helps all of my hardware is intel integrated

---

### Post by laffinet on 2009-04-06
> **ionFreeman said:**
> I'm getting that same 'Problem with Audio Playback' message. Audio playback generally works great. It's just Skype.

I had this problem the other day, too. All I did was go into configuration, sound. Played the test sound, did a test call, everything was fine afterwards. Seems to be a bug.

Might work for you guys too.

---

### Post by demarshall on 2009-04-08
I cannot get audio to work in Skype even though it was working yesterday. The only thing that has changed is that a new kernel was installed. I wonder if that is the problem. I did a reinstall of Skype using Synaptic but that hasn't helped. Does anybody have any ideas what to try next?

---

### Post by demarshall on 2009-04-09
I solved the problem by setting repositories in Synaptic to allow for pre-released updates to be installed and then having Synaptic update all files. I then restarted my system and had sound. When I started Skype I still had a problem with sound but went into audio devices and set Sound Out on Sound Devices to Pulse.

I hope this helps other people.

---

### Post by demarshall on 2009-04-11
Well, I guess the problem isn't over. I had to restart my computer today because I had no sound. Does anybody else have any ideas?

---

### Post by _Purple_ on 2009-04-11
I had the same problem after upgrading to intrepid and managed to fix it by following [these steps](http://ubuntuforums.org/showthread.php?t=843012) in the quick start guide.

---

### Post by demarshall on 2009-04-12
Thanks _Purple_. I had already installed the packages listed there but need to do what follows that.

---

### Post by Jazzy_Jeff on 2009-04-12
I had some issues before. I have since uninstalled pulse audio and just use alsamixer and every thing works fine. Just tried my skype to be sure.

---

### Post by _Purple_ on 2009-04-12
> **demarshall said:**
> Thanks _Purple_. I had already installed the packages listed there but need to do what follows that.

Did you change the audio settings in skype?

---

### Post by Jacdeb6009 on 2009-04-13
Hi there,

Not a solution to anyone's problem specifically, but some interesting experiences and observations.

I run Hardy and Intrepid.

In Hardy Skype worked perfectly, no "fiddling" until Friday, when after a number of updates, Skype started complaining about a playback error.  This I atrributed to the updates (the updates caused a number of other problems and eventually I reverted to the previous kernel).

Anyway, after some investigation, I think that I have found the real culprit.  I run Sun xVM with Windows (don't ask...) and until Thursday or Friday I had not figured out how to get the sound to work (doh...).  Skype works fine, until xVM is running (more accurately, Windows is running) at which point it "steals" Pulse Audio and locks out Skype.  Shut down xVM and Skype works.  The solution was simple, since I don't need sound in xVM, I turned it off and now Skype works perfectly all the time.  I doubt that xVM is your problem, but you may want to look for something else that is "stealing" the Pulse Audio and locking it up.  Whether this is actually xVM or Skype which "misbehaves" is not clear to me and someone with more understanding can probably answer this.

As for Intrepid, it's neat, but I could only get Skype (and the recorder) to work by removing Pulse Audo completley and reinstalling ALSA (there are a number of threads that explain how to do this).  After doing this, getting Skype to work was simple and only required tweaking a couple of the settings to get it 100%.

Don't know that this helps you, but it may give you something to think about.

Hope you get it working!!

---

