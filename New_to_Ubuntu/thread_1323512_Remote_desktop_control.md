---
title: "Remote desktop control"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by dndrich on 2009-11-11
Ubuntupals:

Looking for a simple way to control my brother's Karmic box from my Karmic box. His computer is connected to a router, then to the internet. Rather than set up some complicated ssh method, somebody at some point set up a set of scripts that could be used by both computers that would set this up. But a Google search, and I just can't find the link. Any thoughts here?

---

### Post by dndrich on 2009-11-11
Wow! I actually found something that worked exactly how I wanted it to.

Here is a link to a launchpad project for Ubuntu from the guy who appears to have written the remote desktop community documentation on the subject.

[http://pileofstuff.org/remote-help-assistant/](http://pileofstuff.org/remote-help-assistant/)

Basically, what I wanted to do was help my brother. He lives a few miles away. We are both using Karmic 64 bit. I downloaded the deb for the helper, and he downloaded the deb for the person being helped. Now each of us install the program, and it shows up under internet as remote help assistant. Basically what it does is set up the ssh parameters and the port forwarding for you, so any idiot can do it. You need to be on the phone with the other person to direct them initially, but this works just perfectly. Actually, we were on Skype, so we were talking via internet, but you get the picture. Anyway, I could control his desktop safely, and talk with him, and instruct him. Perfect. Anybody looking for a solution like this, this is it.

---

### Post by nhasian on 2009-11-12
two other ways:

you could go to System->Preferences->Remote Desktop and enable it on the host computer.  you will need to make sure port 5900 is forwarded in his router to be able connect.

alternatively if you are both using Empathy you could just right click on the contact as choose "Share my desktop"

---

### Post by dndrich on 2009-11-12
Didn't know the Empathy trick. I will have to try that!

---

### Post by Onesimus on 2009-11-12
> **nhasian said:**
> two other ways:

you could go to System->Preferences->Remote Desktop and enable it on the host computer.  you will need to make sure port 5900 is forwarded in his router to be able connect.


How do I check if port 5900 is forwarded in his router ?

How do I make it so, if it isn't ?

---

### Post by dndrich on 2009-11-12
The whole point of my post initially is to make configuration easy. That way knowing how to configure ssh, or your router, is made moot by using the remote helper program I suggested.

---

### Post by dndrich on 2009-11-12
OK, tried the Empathy trick. Wow! That really makes it easy. All you have to do is have a chat account, right click, share my desktop, and the other user can do just that. It works flawlessly. Now, that is the way to do that simply when trying to help somebody else. Fantastic. Great idea! I did not know that was available until that post. This community is amazing!

---

