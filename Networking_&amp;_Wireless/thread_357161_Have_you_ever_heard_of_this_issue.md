---
title: "Have you ever heard of this issue?"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by milton1 on 2007-02-09
My network administrator is attempting to convince me that the mere presence of a linux computer on the network could cause the entire network of computers to go down. To me, this sounds like absolute nonsense. Has anyone EVER heard of ANYTHING that could show this kind of result, or is my administrator being paranoid and ignorant?

---

### Post by cookie200 on 2007-02-09
Did you asked him exactly how it would cause a network to go down?  Sounds like someone just talking without thinking.

Granted a machine that is hacked could bring a network down.

---

### Post by milton1 on 2007-02-09
I had that same thought, that the machine had been hacked. Still that isn't a linux specific issue.

---

### Post by kebes on 2007-02-09
This sounds absolutely ridiculous to me. There are literally thousands of organizations around the world that run mixed networks--Windows, Linux, Mac OS, BSD, etc. I work at one. All of these universities and companies seem to manage, so what's the problem at this network?

It sounds almost like this admin just doesn't want to deal with Linux (he's afraid of things of things he doesn't understand?), and is using this as a convenient excuse. He's probably hoping you'll just drop it.

It's up to you if you want to pursue this, but I'm aware of no legitimate reason why a Linux computer cannot exist on any properly-configured network. Ask for specific details so that you can research the issue. Chances are he won't be able to provide any.

---

### Post by milton1 on 2007-02-12
New information:

Supposedly the machine in question was a linux server set up on a sub-network within the existing LAN, and the network traffic was being misdirected to this (or by this) machine.

OK, so this does not seem quite as impossible to me, but it still sounds like there was something seriously wrong with the network setup.

---

### Post by mips on 2007-02-12
> **milton1 said:**
> 
OK, so this does not seem quite as impossible to me, but it still sounds like there was something seriously wrong with the network setup.

Just about any device can cause network problems if configured by an egit.

Once had a case where some egit configured a equipment management device that gathers data to use the same ip address as the router/default gateway. Every second packet on that network got misdirected. To further complicate things the device was at a remote location connected via bridging off the local  lan.

Another word of advice if using linux is to make sure you got the box locked down security wise and if  on a corporate non-private network that you actually have permission to connect it to the network. Someone I know had the bad fortune of a having a linux box compromised and it was used to carry attacks out with. He never got the ok to install the box and he was very close to being fired, saved by devine intervention from his boss.

---

### Post by koenn on 2007-02-12
If the network admin is telling you that the whole network is gonna go down to moment you plug in an Linux machine, he's lying, or ignorant. No question about it. 

However, this:
> Another word of advice if using linux is to make sure you got the box locked down security wise and if on a corporate non-private network that you actually have permission to connect it to the network.
makes sense. 

From the nedwork admin's perspective : supposedly he has his network well organised, and all computers on it wel configured and secured, possibly by remote / centralised addmin tools such as , say, Microsoft Active Directory Group Policy Objects (GPO). 
Now, a Linux machine would be a loose canon : it can not be configured by these GPO's - and the network admin has no control over it  nor does he know how it is setup or what it can do. He has to trust you to
1- know what your doing and secure that linux machine so it can't be used as a trojan or a backdoor into the network
2- not use that Linux machine to go around doing nasty things - he can not stop you from doing that the way he can with windows users. 

If I was that network admin, i'd think twice as well ...

---

### Post by mips on 2007-02-13
> **koenn said:**
> If the network admin is telling you that the whole network is gonna go down to moment you plug in an Linux machine, he's lying, or ignorant. No question about it.

He is exaggerating, it could cause problems though.


> **koenn said:**
> 
If I was that network admin, i'd think twice as well ...

Another option would be to give him root access. In some places this is a given, our security section had root access to anything on the network.

---

### Post by milton1 on 2007-09-04
UPDATE! Today, one of the folks who told me last year that we could not run linux on our network because it could destabalize it, asked me if we could discuss adding more linux computers to our system, especially as we seem to be having particular difficulty with vista. Vista has been banned from our network! One word: Karma.

---

