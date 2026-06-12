---
title: "Ubuntu Software Centre painfully slow?"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by RobMcL on 2010-04-05
I'm running ubuntu 9.10 on my computer (installed with wubi), and I have a problem. The ubuntu software centre is ***painfully*** slow. I've been trying to install the ubuntu restricted extras for the past hour and its only at 19%. My internet connection is fine, and my computers good. It worked fine in a virtual machine I was running. My question is why is it so slow?

---

### Post by Paqman on 2010-04-05
Could be a problem with the server you're getting your downloads from. Go to System > Admin > Software Sources and change the download server, you can get it to automatically scan for the fastest server for you if you want.

It could also be your ISP throttling certain types of traffic. Not much you can do about that.

---

### Post by ELD on 2010-04-05
To test try downloading a regular file in firefox to compare the speed, then you can see if it software centre or your internet.

---

### Post by J V on 2010-04-05
Thats why no-one uses the software center, synaptic kicks its ***.

---

### Post by ELD on 2010-04-05
> **J V said:**
> Thats why no-one uses the software center, synaptic kicks its ***.

I find it a lot nicer to use actually and i use it 90% of the time now.

You also realise that synaptic would use the same server, so it would have the same issue right?

---

### Post by Phil Hansen on 2010-04-05
> **Paqman said:**
> you can get it to automatically scan for the fastest server for you if you want.

Thanks for that tip. Now using a server in Holland as opposed to South Africa. Faster and no error messages when reloading like I used to get with the SA server.
Phil

---

### Post by Paqman on 2010-04-05
> **J V said:**
> Thats why no-one uses the software center, synaptic kicks its ***.

They're just different front ends for the same system. People use whichever interface they prefer, but they both work exactly the same.

**Phil**: no problem, glad you're sorted. You can mark the thread as "solved" using the "thread tools" at the top.

---

### Post by Phil Hansen on 2010-04-05
> **Paqman said:**
> **Phil**: no problem, glad you're sorted. You can mark the thread as "solved" using the "thread tools" at the top.
Paqman: I was not the OP so cannot - Just wanted to say thanks

---

### Post by Phil Hansen on 2010-04-05
> **Paqman said:**
> **Phil**: no problem, glad you're sorted. You can mark the thread as "solved" using the "thread tools" at the top.
Sorry sent twice

---

### Post by Paqman on 2010-04-05
> **Phil Hansen said:**
> Paqman: I was not the OP so cannot - Just wanted to say thanks

Ah, my mistake ;)

---

### Post by RobMcL on 2010-04-05
Thanks for the help guys, but I think I may have found the problem myself (actually, ubuntu found it for me). I just installed ubuntu through wubi this morning, and getting all the updates was a bit flaky. Turns out, I hadn't finished upgrading. Once I finished the partial upgrade, it's downloading a lot better. Still not the fastest, but 10x better than before. 

I have a question though. Should I use the "Main Server", or "Server for United States". I'm in Canada, by the way.

EDIT: How do I changed the title to solved? It's only showing up in the thread.

---

### Post by Paqman on 2010-04-05
> **RobMcL said:**
> Once I finished the partial upgrade, it's downloading a lot better.

Did the machine offer you a "Partial Upgrade"? If so, that's bad. Reload your sources and try another update. Partial Upgrades can leave you with a very unstable system, but you shouldn't really be getting them on a stable release. Make sure those software sources are right up to date.

---

### Post by RobMcL on 2010-04-05
> **Paqman said:**
> Did the machine offer you a "Partial Upgrade"? If so, that's bad. Reload your sources and try another update. Partial Upgrades can leave you with a very unstable system, but you shouldn't really be getting them on a stable release. Make sure those software sources are right up to date.

I don't know, it seems to be working fine. I think I restarted when ubuntu was installing all the updates. What do you mean by unstable? And how do I make sure they're up to date? Again, thanks for all the help. :)

---

### Post by Paqman on 2010-04-05
> **RobMcL said:**
> I don't know, it seems to be working fine. I think I restarted when ubuntu was installing all the updates.

Ok, that's confused me a little. Did the machine actually ask you if you wanted to run a "Partial Upgrade", or do you mean that you just interrupted the update process. If it's the latter that's probably fine, the update process is surprisingly robust.

> What do you mean by unstable?

The package manager normally makes sure that all the right dependencies are installed for your software to work properly. A "Partial Upgrade" means that it hasn't been able to satisfy all the dependencies, it may end up in a situation when it can't upgrade things without removing others. If that thing that gets removed is something your system needs, then it'll break. Usually that's not catastrophic, but it might mean some important app or subsystem fails to work. Depending on what that is, it could be trivial or be really disruptive and annoying.


> 
And how do I make sure they're up to date? Again, thanks for all the help. :)

Open Update Manager and hit "Check". If you were offered a "Partial Upgrade", try checking every few hours until the server sorts its act out, or try a different server from System > Admin > Software Sources.

---

### Post by RobMcL on 2010-04-05
> **Paqman said:**
> Ok, that's confused me a little. Did the machine actually ask you if you wanted to run a "Partial Upgrade", or do you mean that you just interrupted the update process. If it's the latter that's probably fine, the update process is surprisingly robust. 

Yeah, I'm pretty sure I restarted when it was in the middle of updating.

---

### Post by Paqman on 2010-04-05
> **RobMcL said:**
> Yeah, I'm pretty sure I restarted when it was in the middle of updating.

Well, if it was still downloading then that won't have done any harm at all. If it had got to the installing bit it's a bit more dodgy, but at the most it would make one package fail to install.

---

