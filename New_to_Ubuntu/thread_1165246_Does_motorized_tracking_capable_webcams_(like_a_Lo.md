---
title: "Does motorized tracking capable webcams (like a Logitech Orbit/Sphere) work in Linux?"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by diablo75 on 2009-05-20
I've been looking over the [UVC drivers compatibility lists]("http://linux-uvc.berlios.de/") and see green check boxes next to the Logitech Orbit/Sphere webcams (which include a motorized base for mechanical motion tracking).  Someone I know purchased one of these cameras recently and while they are able to get video from the camera, they are unable to get any motion tracking to work and they wanted to know why (if the tracking is not supported in Linux) there would still be a green checkmark next to the camera in the list.

---

### Post by oneiota on 2009-08-12
I'm surprised this question is not commented on.  I also have the Logitech Sphere AF and would like to hear an answer.  

It would be useful to know if one can enable tracking.  Failing that even simple manual movement of the lens would help; from new it is stuck in an upward facing angle and jolly annoying to use without being able to adjust it downward.

---

### Post by Maheriano on 2009-08-12
[www.zoneminder.com](www.zoneminder.com)

---

### Post by diablo75 on 2009-08-13
Well outside of the forum I learned a lot about this question, so seeing it come back up, I'll share what I found out.

The drivers that are included with the linux kernel included with recent versions of Ubuntu DO support the ability of telling the camera to move, but that is only to say that if a piece of software WANTED to tell the camera what to do, it could.  In other words, the functionality is available to software, but has not yet been utilized by anything in the world of Linux (except for very difficult to understand text-based software that is a real trick to get working).

So for the time being, if you were a software developer and made something that was smart enough to detect and track motion AND actuate the camera, you could do it.  Unfortunately, nobody has yet (mostly).  I'm a Skype user myself, so I would have to wait for the Skype devs to develop support for such a feature.

In a Windows environment, the camera is still entirely dependant on the Logitech software.  It is separate from the IM software, and in a way, acts as an intermediary layer in between the camera and whatever IM you choose to use.  The IM itself doesn't tell the camera to move, nor does the camera (the internal hardware) tell itself to move.

Long story short, don't buy a motion "detecting" webcam for Linux and expect it to work the way you'd hope it to.

---

### Post by Maheriano on 2009-08-13
> **diablo75 said:**
> Well outside of the forum I learned a lot about this question, so seeing it come back up, I'll share what I found out.

The drivers that are included with the linux kernel included with recent versions of Ubuntu DO support the ability of telling the camera to move, but that is only to say that if a piece of software WANTED to tell the camera what to do, it could.  In other words, the functionality is available to software, but has not yet been utilized by anything in the world of Linux (except for very difficult to understand text-based software that is a real trick to get working).

So for the time being, if you were a software developer and made something that was smart enough to detect and track motion AND actuate the camera, you could do it.  Unfortunately, nobody has yet (mostly).  I'm a Skype user myself, so I would have to wait for the Skype devs to develop support for such a feature.

In a Windows environment, the camera is still entirely dependant on the Logitech software.  It is separate from the IM software, and in a way, acts as an intermediary layer in between the camera and whatever IM you choose to use.  The IM itself doesn't tell the camera to move, nor does the camera (the internal hardware) tell itself to move.

Long story short, don't buy a motion "detecting" webcam for Linux and expect it to work the way you'd hope it to.

I'll post this again for you: [www.zoneminder.com](www.zoneminder.com)

---

### Post by oneiota on 2009-08-13
Thanks Diablo, that all makes sense.  It is reasonable that Skype doesn't make use of the tracking ability and I don't mind that.  What I would like to be able to do is simply lower the essentially fixed position of the lens so that it sits in a better place.

Thanks also Maheriano.  It is almost tempting to download ZoneMinder (surveillance software) simply to appreciate an example application that uses this camera's capability.

---

