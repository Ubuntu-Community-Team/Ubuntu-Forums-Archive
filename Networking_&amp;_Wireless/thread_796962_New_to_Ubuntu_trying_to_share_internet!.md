---
title: "New to Ubuntu trying to share internet!"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by Micahphone on 2008-05-16
Hi everyone. I am new to Ubuntu. I got a laptop as a gift that is loaded with Ubuntu 7.10 the *Gutsy Gibbon*.

This is my ordeal. I have a desktop computer that is running XP Home that is connected via wireless. My new(to me) laptop has no wireless card and I don't feel like spending the money at the moment for one. So, I tried connecting using a cross-over cable to my desktop. No connection. The two computers don't even see each other.

I've ran network set up wizard. I've told it that my desktop is the main computer and all others connect through it. I've searched for 4 days trying to figure this out. I even did a few searches on this website for forum information. All I can find is info on how to connect with wireless. 

Here's a list of things I have done.

Cross-over cable.
Firewalls off to make sure they can see.
Network set up.

So beyond that I am lost.

If anyone can help me out that would be awesome!

Sorry for the question. I am sure this is something that is asked a lot. I am just failing in figuring out this crap right now.

 - Thanks!

---

### Post by rlcomstock3 on 2008-05-16
You will need to share the internet connection in your windows computer, then connect the ubuntu machine to it, I think it should work by default.  But I haven't done anything like that in windows for a long time, generally it is the other way around, share from linux.

---

### Post by Micahphone on 2008-05-16
> **rlcomstock3 said:**
> You will need to share the internet connection in your windows computer, then connect the ubuntu machine to it, I think it should work by default.  But I haven't done anything like that in windows for a long time, generally it is the other way around, share from linux.

Yeah I did that too. No dice.

I even tried bridging. 

Thanks for your time. I am going to give up on this for now. I'd like to give Ubuntu a chance later when I'm not pulling my hair out.:)

I'll just wait until I can get a wireless card.

Thanks again...

---

### Post by vyruss on 2008-05-16
> **Micahphone said:**
> Yeah I did that too. No dice.

I even tried bridging. 

Thanks for your time. I am going to give up on this for now. I'd like to give Ubuntu a chance later when I'm not pulling my hair out.:)

I'll just wait until I can get a wireless card.

Thanks again...

Well, windows is not particularly well suited for networking, usually people use linux for Internet sharing as it's much more flexible and reliable. However the basics are these:

You have to setup sharing on one PC by whatever means you have (I don't have windows and cannot help you there)

You have to have both machines (the one that's sharing its connection and the one that's the client) on the same network (e.g. **192.168.0.x** or **10.0.0.x** or whatever)

You have to set up the "client" so that its Default Gateway to the Internet is the "sharing" machine.

Basically if you can afford a wireless card it would save you time I think as you would not have to set up sharing at all.

---

