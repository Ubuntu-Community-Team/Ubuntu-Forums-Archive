---
title: "Remote Login from Mac to Ubuntu"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by Hingle_McCringleBerry on 2013-09-30
Hello, 

I am using Ubuntu for all my research work and I would like to login to my research machine from my Macbook. I use Ubuntu 12.04 LTS in my machine. My research involves a lot of OpenGL work so I would like a client that supports remote window opening support. (I mention this because last time I used Microsoft Remote Desktop Client to login to a Windows Machine and the OpenGL programs wont start). 

I know I have a couple of options at my kitty : 1. NX or 2. VNC client

My question is which one should I prefer seeing my needs as mentioned above?

---

### Post by 1clue on 2013-09-30
Disclaimer:  I don't know if it has OpenGL support, but have you tried X?

ssh -X remote.host
openGlApp <options>

I use a mac as a workstation almost every day, and I run X apps from remote Linux boxes on it all the time.  Not sure which ones might be opengl.

You should have XQuartz on the mac, but I'm not sure if it came with the Mac or if it came with one of the dev tools I use.  It starts automatically if you ssh -X <hostname> and then run a gui app.

---

### Post by Hingle_McCringleBerry on 2013-09-30
Hey. 

Thanks for the reply. I know my mac has X and I have used it to log into the linux servers in my school. But ssh -X doesnt start the GUI interface. It just starts the command line prompt. Is it because I don't have xQuartz on my Mac (latest version of OS) that whenever I use ssh I am greeted with a command line interface??

---

### Post by 1clue on 2013-09-30
Test it with ssh -X hostname, then start firefox 'sudo synaptic'.  The Mac should start XQuartz at that point, it's easy enough for a Mac user to do it.

:)

:D

Sorry.  I'm a mac user too.   :)

---

### Post by 1clue on 2013-09-30
Evidently the Mac is getting even with me.  Sorry about the double post.

:D

---

### Post by Hingle_McCringleBerry on 2013-09-30
:ks:ks:ks:ks:ks

---

### Post by 1clue on 2013-09-30
It's a little bit flaky sometimes.  If you ssh -X hostname, and then start the gui app right away, it should work fine.  If you quit that and start another gui app it doesn't always work.  If you let it sit for awhile (go get lunch) and then come back, it might not work.  Always works for me with a fresh ssh session.

The -X flag sets you up for X on the Linux box (or whatever the remote is, if you want to be general about it) and the actual launch of the app starts XQuartz.

---

