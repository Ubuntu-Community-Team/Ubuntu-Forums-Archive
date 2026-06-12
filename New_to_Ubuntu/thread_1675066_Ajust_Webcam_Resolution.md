---
title: "Ajust Webcam Resolution"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by derp88 on 2011-01-24
I am rather stuck on this one. I've googled it and maybe I'm just using bad search terms. I am looking for a way to adjust the resolution for the my webcam. It's rather course and grainy looking. Is there any way I can improve the resolution of the webcam? Any advice or suggestion will be greatly appreciated. :confused:
 
Ubuntu 10.10 is what I am using. not sure what other info to provide.

---

### Post by ubudog on 2011-01-25
Installing Cheese Webcam Booth may help you.  Also, have you tried turning a small nob on the webcam itself?

To install Cheese...

```
sudo apt-get install cheese
```

(run that in a terminal)

That should do it.  Good luck!

---

### Post by derp88 on 2011-01-26
> **ubudog said:**
> Installing Cheese Webcam Booth may help you.  Also, have you tried turning a small nob on the webcam itself?

To install Cheese...

```
sudo apt-get install cheese
```

(run that in a terminal)

That should do it.  Good luck!

I will install cheese webcam booth and see if it helps. As far as any button or nob on my cam there isn't one on my desktop nor my laptop. Laptop is a VAIO, and the desktop cam is a Hercules, this is made to run on linux. I don't know if this will help any for additional advice. I will keep this post up to date. Thank you for your advice :)

---

### Post by LowSky on 2011-01-26
there is an app called video4linux control panel (aka v4l2ucp) if you want more adjustablity.

---

### Post by ubudog on 2011-01-27
> **lowsky said:**
> there is an app called video4linux control panel (aka v4l2ucp) if you want more adjustablity.

+1

---

### Post by derp88 on 2011-02-06
I installed cheese webcam booth, with no luck in improving my webcam resolution. Any other suggestions anyone? :confused:

---

### Post by beew on 2011-02-07
> **derp88 said:**
> I installed cheese webcam booth, with no luck in improving my webcam resolution. Any other suggestions anyone? :confused:

Open Cheese and go to Edit > Preference where there is a box to adjust the webcam resolution.

---

### Post by derp88 on 2011-02-07
I installed v4l2ucp (video for linux control panel) with no luck there's to way for me to increase the resolution (pixels) it's very grainy and pixelated.any other suggestions any one? :sad:

---

### Post by derp88 on 2011-02-07
I did adjust cheese box, but it had no affect on cam resolution when on skype or say chat rooms that use flash for video. Sorry should have given this information earlier, my bad. I've been googling, but have found much yet....

---

### Post by beew on 2011-02-07
The skype resolution appears to depend on your internet connection even just for the video test. This is rather strange but I notice there is a huge difference in resolution  depending on whether I have a good internet connection when  I do the video test.

---

### Post by relativecalm on 2011-04-12
Hmm it seems that Flash has a bug (or incompatibility :P).
I wonder how Flash actually chooses the resolution. And I also wonder if we could fool it somehow. Make it see some other minimum available resolution (if that is what it chooses by default)?

---

