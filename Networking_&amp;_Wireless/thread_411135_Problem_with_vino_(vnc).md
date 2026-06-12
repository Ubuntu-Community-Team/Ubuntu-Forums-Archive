---
title: "Problem with vino (vnc)"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by SiCk949 on 2007-04-16
Hi all.
I have a problem with vino (remote desktop). I configure it with the ui and I try to connect to my ubuntu 7.04 from windows xp sp2 with ultravnc viewer.
When I connect, the image seems to be blocked, but the rest works great! (i see the mouse, keyboard, etc working in the monitor's ubuntu  pc). I think that its a encoding problem, explain:

Inversal operation (I can connect with xvnc4viewer to ultravnc server on windows) but the system first try with zrle and later select hextile and all works great. First time the system didn't change it auto. so also with ultravnc server in windows I had the problem described before , but when I used hextile image works great... so i think that i can solve it configuring vino with hextile but i don't know how to make that.

I appreciate any help!! many thanks!!!


Edit: I also realise that also could be a network problem, cause the "green box" of the ultravnc right corner didn't bright, same on another connections.
I also tried tightvnc viewer windows with the same result...
PD: I connect writting the ip number and port.

---

### Post by SiCk949 on 2007-04-16
Well, the problem is with beryl!!! Using metacity all works fine, I'm reading a few post about vnc+beryl

---

### Post by azthomas on 2007-04-18
> **SiCk949 said:**
> Well, the problem is with beryl!!! Using metacity all works fine, I'm reading a few post about vnc+beryl

Is bery installed on Feisty by default?

---

### Post by snappynuts on 2007-04-18
I am having a similar problem.  I'm just using the default VNC host in ubuntu (I'm new to ubunto btw)... and when connecting from an XP workstation, the authentication seems to work fine, but nothing displays on the XP machine.  I do have Beryl running too.

---

### Post by SiCk949 on 2007-04-18
> **azthomas said:**
> Is bery installed on Feisty by default?

No, its compiz, you have a easy way for active it via admin panels (3d effects desktop, activate or not).

And the problem is solved if you use metacity, dont know how to make it run with beryl or compiz.

---

### Post by Virtual DarKness on 2007-04-30
Hello,
I think I've found a solution.. and I wrote a small [howto]("http://ubuntuforums.org/showthread.php?t=421272"). I hope it helps.

bye,
Giovanni.

p.s.
you have to turn off vino in order to have x11vnc works.

---

