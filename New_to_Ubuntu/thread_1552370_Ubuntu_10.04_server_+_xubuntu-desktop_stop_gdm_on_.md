---
title: "Ubuntu 10.04 server + xubuntu-desktop stop gdm on start"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by eDRoaCH on 2010-08-13
Setting up a low-power server in virtualbox for a project I am working on. I can get around a command line somewhat, but sometimes just want a gui out of laziness. So I installed Ubuntu 10.04 server then did apt-get install xbuntu-desktop

Now I boot directly into xfce, which is not what I want. I want to be able to start AND stop x at any time.

So- I've tried removing gdm (I realize it should be like xdm or something but cant figure out which one it actually is) from all the runlevels to no effect, and remember ubuntu changed (in 9 I believe?) and now does something funky in terms of managing startup stuff, which I never learned. so...

1. how do i prevent xfce from booting on startup, but so it still works when I type startx?

2. how can I stop an x session and go back to the command line?

Help appreciated!

---

### Post by lukeiamyourfather on 2010-08-13
Ctrl + Alt + Backspace will kill a GNOME sessions, I think it works with Xfce too. Not sure about how to prevent it from starting up. Would like to know that myself.

---

### Post by eDRoaCH on 2010-08-14
No ideas? I see this is a fairly common one on the boards but no one has seemed to solve it since around Ubuntu 8.

as I said I removed gdm from the rc.d with no effect...

---

### Post by Kamzi on 2011-10-22
Posting to an old thread but didn't find newer one. Is there any solution to this? I would like to prevent my server from starting x and start it manually when it is needed.

---

### Post by manco1911 on 2012-04-09
I'm having this exact same situation.. 
hope someone jumps in with an answer, i will try a bit on a virtual machine and see what i can do.. 

if i find anything ill post it here.

---

