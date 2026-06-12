---
title: "can't exit ssh session on win client if browsing samba share"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by anitract on 2008-02-16
I have an Ubuntu fileserver hosting a couple of shares through samba to a Windows XP client using an ssh tunnel, like so: [http://www.blisstonia.com/eolson/notes/smboverssh.php](http://www.blisstonia.com/eolson/notes/smboverssh.php).

Everything works great except for a small annoyance: once I establish my SSH session using Putty, I cannot sucessfully issue an EXIT command to end my Putty session. It will say logging out, but never finish.

Well, actually that is not entirely true.  I can Exit the session successfully every time if I do not browse to my samba shares.  Once I access them, the problem occurs.

My Questions:
1. What could cause this behavior?
2. Is there a command I can run on my Ubuntu server to see what SSH sessions are currently active/alive, or who is logged into my server from a certain address?

---

### Post by anitract on 2008-02-16
Did some more digging on this.
who (or) w   commands give me the info I need.

Regardless of whether or not the session on the client exits sucessfully, the session on my linux box appears to be done.

If I do a who -d, regardless of how the session ended, I see the dead process listed.  who -u no longer shows the session active either.

Question on who -d......these dead processes get cleaned up every so often by the looks of things...what is doing that?

---

### Post by The Cog on 2008-02-16
I think it's because SSH is (in this case) performing two different functions simultaneously. Firstly it is carrying a shell login session, and secondly it is carrying a tunnelled TCP connection (carrying SMB). SSH will exit when both sessions have ended, not before. Logging out of the terminal session won't forcefully terminate the SMB tunnel just as closing the SMB tunnel won't interrupt the terminal login.

---

### Post by anitract on 2008-02-17
Interesting....so I guess the question is, is there a way to end the tunnel before ending the terminal session?  Actually, why wouldn't Putty just do it this way by default?

---

### Post by The Cog on 2008-02-18
Close putty?

---

### Post by anitract on 2008-02-19
Closing Putty isn't totally "clean" though is it....I mean, does it leave any dead sessions or anything like that on the server?

---

### Post by dmizer on 2008-02-19
no ... this would be client side.

---

