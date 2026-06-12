---
title: "can't get restricted extras for 9.10"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by jfloydb on 2009-10-29
I'm wanting to watch YouTube, play mp3, play mpg4 video, and the like. I've just upgraded to 9.10. I believe that I need the restricted extras, but they seem to be unavailable ("not available in current data"). What do I need to do? 

trying to download/install from the flash site didn't work...

---

### Post by SunnyRabbiera on 2009-10-29
Hmm, perhaps the servers are being overloaded.

---

### Post by jfloydb on 2009-10-29
I can wait for the servers, I suppose. But am I correct in thinking that I need the restricted extras?

---

### Post by Sef on 2009-10-29
> I can wait for the servers, I suppose. But am I correct in thinking that I need the restricted extras?


If you want the restricted extras software, it is the best way to install software, so better to wait.

---

### Post by dj-toonz on 2009-10-29
> **Sef said:**
> If you want the restricted extras software, it is the best way to install software, so better to wait.

I can second that, I'm getting time outs with the Karmic repos, when I try to even get the same thing & medibuntu servers for karmic seem down aswell so I'm myself going to wait till over the weekend to get mine, I've still got jaunty on both systems fully updated so I can watch what I need in that till then

---

### Post by llamabr on 2009-10-30
All those sites are mirrored.  If you're getting time outs from the main site, consider using an alternative.

---

### Post by jfloydb on 2009-10-30
I got the extras...

---

### Post by myolbug on 2009-10-30
How do I get the extras?

---

### Post by barbz127 on 2009-10-30
> **myolbug said:**
> How do I get the extras?

Search for extra in the add/remove software or the software center.

You will get k/x/ubuntu restricted extras - install it.

---

### Post by nakama85 on 2009-10-30
> **jfloydb said:**
> I'm wanting to watch YouTube, play mp3, play mpg4 video, and the like. I've just upgraded to 9.10. I believe that I need the restricted extras, but they seem to be unavailable ("not available in current data"). What do I need to do? 

trying to download/install from the flash site didn't work...

this may be posted in here already but going to terminal and running ```
sudo apt-get update
``` worked for me. once that was complete "not available in current data" went away and I was able to install restricted extras

---

### Post by skotu on 2010-05-01
I ran ```
sudo apt-get update
``` (which on other threads has fixed the problem for many people) but that didn't fix the problem for me.

I got it fixed after reading this thread. [http://ubuntuforums.org/showthread.php?p=9158262#post9158262](http://ubuntuforums.org/showthread.php?p=9158262#post9158262)

I went to **System > Administration > Software Sources **and the Community-maintained Open Source Software (universe) repository was not selected. I selected this along with the rest of them and changed the server to somewhere closer to my location.

Then I was able to install software.

---

