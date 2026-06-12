---
title: "Why am I seeing the dots when putting in password in terminal?"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by Georgia boy on 2010-07-12
Quick question. Went into terminal to check this:gksudo gedit /etc/sane.d/dll.conf
Noticed the dots like what you get when logging in when booting. Thought that you're not supposed to see anything while in terminal. At least I've never seen anything before. When I pasted that command in terminal I got a login screen and when I signed in I saw the dots like normal. Supposed to be that way?

Tom

---

### Post by audiomick on 2010-07-12
I think this is ok.

You are right: when you use sudo, you don't see what you write when you enter your password.

gksudo or gksu are variations of sudo for starting graphical applications like gedit or nautilus. As far as I know they are interchangeable if not identical. When I use gksu, a password entry window appears in which I see the dots as I type.

---

### Post by Georgia boy on 2010-07-12
Thanks Michael. For a moment there I thought I had messed something up somehow. Just seemed odd seeing that when I've never seen anything while signing in with Terminal. Each time I used my password in Terminal I kept my fingers crossed that I didn't hit the wrong key. Been lucky so far. But when I did the gksudo gedit /etc/sane.d/dll.conf and saw the regular login screen you get when booting up I thought I has screwed something up. Never had done the gksudo before so I had never seen the login screen pop up in terminal. Always had a blank password sign in while keeping the fingers crossed.

I really appreciate the explanation. Now if I can get Simple Scan/Xscan working with my printer again I'll be real happy. Got six pages on the thread and still can't get them all to corporate with each other.

Thanks again.

Tom

---

### Post by audiomick on 2010-07-12
You're welcome.

sorry I can't help with the scanner. I haven't looked into that yet. I managed to buy one that is definitely not supported, so I am waiting for it to turn up in the supported hardware lists before I try.

---

