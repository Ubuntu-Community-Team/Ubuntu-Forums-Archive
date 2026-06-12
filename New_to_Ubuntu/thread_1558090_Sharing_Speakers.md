---
title: "Sharing Speakers"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by MearnsRea on 2010-08-21
I have two systems running Ubuntu: A Desktop running Jaunty and a laptop running Lucid.  I want to find a way to take the audio stream from my laptop and play it on the desktop speakers.  I attempted to use PulseAudio to do this job, but my desktop always reports connection issues if I set it up for networking. I was thinking something along the lines of what follows:
-Share the desktop's /dev/audio file on my network
-Mount that network share on the laptop
-Direct sound to that mount point

It's just an idea, and it's probably flawed, but I'd rather have a quick-and-simple solution than a complex one.

I've been using Ubuntu for some time, and I can write basic BASH scripts.  However, I'm still somewhat in the dark when it comes to hardware configuration for Linux.

Thanks

---

### Post by earthpigg on 2010-08-21
there was a thread a while back that explained how to do exactly this over a network or the internet, without needing to plug any new/unusual audio cords into either computer.

the specifics where to pipe one computer's mic input into a different computer's audio output, as a surveillance thing while on vacation or whatever.

im going to see if i can find it.

---

### Post by earthpigg on 2010-08-21
found it. i thought it was so cool [i added the technique to wikipedia]("http://en.wikipedia.org/w/index.php?title=OpenSSH&oldid=326244716#Features") :P

here is the thread: [http://ubuntuforums.org/showthread.php?t=1328338](http://ubuntuforums.org/showthread.php?t=1328338)

---

### Post by earthpigg on 2010-08-21
i did an odd double-post-followed-by-edit thing, so im posting again to make sure MearnsRea sees the second post since i edited it to contain useful content and not a double post.

---

