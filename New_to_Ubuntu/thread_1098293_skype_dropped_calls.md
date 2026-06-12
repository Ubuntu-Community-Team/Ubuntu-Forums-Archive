---
title: "skype dropped calls"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by chilimac02 on 2009-03-16
I'm trying to figure out if anyone else has had problems with skype 2.0 dropping calls after like 30sec.

Anyone have that issue or know how to fix it?

---

### Post by leonardo_neo on 2009-03-16
> **chilimac02 said:**
> I'm trying to figure out if anyone else has had problems with skype 2.0 dropping calls after like 30sec.

Anyone have that issue or know how to fix it?


I have been using Skype on Ubuntu, but never experienced problem like this......Does it happen every time you make call, or only sometimes??

---

### Post by PenguinsFan on 2009-03-16
I had alot of trouble using skype with my wireless card - Are you using wireless? If so, would it be possible to switch to a wired connection temporarily and try again? If it doesn't fail, that really narrows down the problem to your wireless adapter.

---

### Post by chilimac02 on 2009-03-17
thanks, I will try to use my wired connection next time and see if that solves the problem. If not, I'll just ask for more information :)

---

### Post by chilimac02 on 2009-03-17
yep, it was the wireless card. Now I just need to fix the audio lag that I'm having... :0

---

### Post by keithrennie on 2009-06-26
> **chilimac02 said:**
> I'm trying to figure out if anyone else has had problems with skype 2.0 dropping calls after like 30sec.

Anyone have that issue or know how to fix it?

Yes, I have the exactly the same problem, and it repeats reliably on all skype out calls (not sure on skype to skype yet.  Been using Skype on Ubuntu for years, never had it before in previous releases, only in Jaunty.  Funny thing is, the sound test works fine. Using HDA intel driver for sound out and ring, and my USB webcam for sound in because my headset mike stopped working.  I got rid of Pulseaudio which is a pain in the butt, has too many bugs and no advantages.

I'm using a wired connection, not wireless. I was beginning to suspect my internet service provider!

I will do some research on previous posts and will post if I find an answer.

---

### Post by superprash2003 on 2009-06-27
well you could connect this same machine to a different ISP and try , that would tell you if it is an ISP problem or not

---

### Post by nmaster on 2009-06-27
> **keithrennie said:**
> I got rid of Pulseaudio which is a pain in the butt, has too many bugs and no advantages.


i agree.  i started using esound instead of pulseaudio and skype works perfectly now.

---

### Post by PGScooter on 2009-06-27
I had the same problem. I installed skype-static-oss from the medibuntu repositories and it worked perfectly from there on out

---

