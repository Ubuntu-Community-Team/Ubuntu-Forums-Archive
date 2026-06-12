---
title: "So, what's this &quot;remote desktop&quot; thing? How does it work?"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by Eoghanalbar on 2010-04-10
I understand that I can use my ubuntu computer over the internet from another computer. That's pretty wild, man! So I've got a couple broad, general questions to ask, because I'm not sure how to start, and I can't find any sort of "beginner's guide to using remote desktop" that explains these basic things.

So.

1) How do you set it up so you can do that?

[Are there different options, programs, whatever? Is there anything I should really know to make sure it's really secure (or are there certain things I should avoid doing while using it)? etc]

2)And what's possible with it? 

[That is, can I use my home desktop from just any other ubuntu computer connected to the internet? I guess other linux computers should be easy too, right? Is it difficult or impossible to do with other OS's? How about using a live CD? Does my home computer have to be awake, or can I do it even if it's in suspended mode or whatever? etc etc]

Thanks a lot for being patient and kind enough to explain this basic stuff to a newbie!

~Owen

---

### Post by spiky001 on 2010-04-10
have a read here see if this helps
[http://ubuntuforums.org/showthread.php?t=1339252](http://ubuntuforums.org/showthread.php?t=1339252)

---

### Post by HermanAB on 2010-04-10
The 'Remote Desktop' feature of Ubuntu is a disguised VNC, which is notorious for its insecurity.  So, in short, it is best avoided.  Unless you are a masochist and actually *wants* to get your machine hacked...

The best way to access your machine over the internet is with SSH and unfortunately Ubuntu doesn't install that by default.  You need to install the ssh-server package and forward port 22/TCP in your router.

---

### Post by norm7446 on 2010-04-10
Remote Desktop, one of the first thing I uninstall. Ten foot barge pole always springs to mind when anyone asks me about remote desktop.

---

