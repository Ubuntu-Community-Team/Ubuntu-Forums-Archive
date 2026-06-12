---
title: "WTA - How To Know if Someone Hacked our Cam ?"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by kemsud on 2010-12-28
Im noob in Ubuntu, i really dont know how system running on it.
im using Ubuntu 10.10 with acer travel mate 6292 

webcam : Crystal eye

Please explain to me.. how do we know if the web cam hacked by someone? 

1. is there a log recorded to see a history when the data in/out?
2. is it possible to remote web cam turn on without our notice and recorded the video?
3. or is it possible to turn on video in background without our notice and download/record our activity, exp : while we typing/see monitor?
4. How do we know it? or how do we track it the history?

is very important to me. Moderator and geek master help is very appreciate and welcome to give me a solution

Thanks :D

---

### Post by Wtower on 2010-12-28
The most possible way I can think of is if you someone with root access via ssh or from your immediate environment or even yourself without knowing installed something dodgy. Other than that i have never encountered something alike so far. So my advice: it is better off to be careful about who has access over the pc at the first place.

---

### Post by kemsud on 2010-12-28
> **Wtower said:**
> The most possible way I can think of is if you someone with root access via ssh or from your immediate environment or even yourself without knowing installed something dodgy. Other than that i have never encountered something alike so far. So my advice: it is better off to be careful about who has access over the pc at the first place.

im so sorry, but what is mean by immediate evironment? 

what is example by installed something dodgy? how do i know that package installer contain malware that can remote my cam?

is there any spesific thread to discuss the topic, since i think is very important to noob like me. Ubuntu is make me so addicted :D

---

### Post by QLee on 2010-12-28
[QUOTE=kemsud]... how do i know that package installer contain malware that can remote my cam?...[/QUOTE]

You don't have to worry about any software from the official Ubuntu repositories. It has been checked, verified and signed by an Ubuntu maintainer. The package manager checks that it is a true signed package. If you trust Ubuntu developers and maintainers, then you can feel safe with official packages. Personally, I trust them.

On the other hand, if you get packages from some unofficial place or let someone you can't trust have physical access to your computer, or allow remote connections, then who knows what might happen. A default install of Ubuntu is safe, after that it's up to you.


[Edit] I guess i might as well add this, if you are worried about your cam, you could tape a thick piece of cardboard over the lens.

---

### Post by Chrissd on 2010-12-28
Hi, there is something that you can install which shows a notification when the webcam is active. Unfortunately, I cannot for the life of me remember what it is called.

I'll get back to you if I find it again.

Edit: cameramonitor is what I was thinking of.
To install it you would use.
```

sudo aptitude install cameramonitor

```

---

### Post by sammiev on 2010-12-28
Most of the webcams have a light that only comes on when the camera is active. At least all the ones I have played with. :confused:

---

