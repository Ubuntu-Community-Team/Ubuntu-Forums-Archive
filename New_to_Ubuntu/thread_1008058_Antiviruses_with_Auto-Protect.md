---
title: "Antiviruses with Auto-Protect?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Grimhound on 2008-12-11
Are there any decent anti-virus programs for Ubuntu with auto-protect and live-scanning capabilities?

And before people get on me about it: I like to keep my computer free of viruses and malware of any type regardless of whether it affects the OS directly or can affect others by negligence on my part. I prefer to keep my defenses up.

---

### Post by Michael.Godawski on 2008-12-11
Have a look at clamav:

[http://www.clamav.net/about/](http://www.clamav.net/about/)

---

### Post by JoshuaRL on 2008-12-11
Well, to be honest I haven't used them much.  Although I have used F-prot once with Puppy Linux to clean a friend's Windows drive.  Not sure about live scanning and autoprotect though.

Might try ClamAV too.

---

### Post by scorp123 on 2008-12-11
> **Grimhound said:**
> I like to keep my computer free of viruses and malware of any type regardless of whether it affects the OS directly or can affect others by negligence on my part.  And what about negligence on their part? If other people use an inferior OS that is susceptible to virus and malware attacks then it is _their_ responsibility to keep their system clean, not your's ... IMHO. You use Linux now. Congratulations. Now lean back, relax and enjoy all those freed-up CPU and I/O cycles you can use for other things instead of having to scan for viruses all the time ... ):P

---

### Post by Paqman on 2008-12-11
Your best antivirus software comes preinstalled, and works against viruses 100% of the time. It's called the Linux kernel :)

Add-on antivirus software for Linux desktops really only give peace of mind. So if that's important to you, then go for it. However, Linux antivirus apps like ClamAV just aren't as good as the best native Windows ones, so the best way to protect a Windows box is still to install a good antivirus suite locally onto it.

---

### Post by Grimhound on 2008-12-11
> **scorp123 said:**
> And what about negligence on their part? If other people use an inferior OS that is susceptible to virus and malware attacks then it is _their_ responsibility to keep their system clean, not your's ... IMHO. You use Linux now. Congratulations. Now lean back, relax and enjoy all those freed-up CPU and I/O cycles you can use for other things instead of having to scan for viruses all the time ... ):P

Just to be honest. If cloud computing actually takes off, and I pray it doesn't, all operating systems will end up in the same situation regardless of construction. It's better to have a weapon and not need it than to be defenseless.

Also, people being smug about the supposed protections of an OS is what makes people want to start making absurdly vile virii for it. I mean, look at OS X.

---

### Post by Michael.Godawski on 2008-12-11
> If cloud computing actually takes off, and I pray it doesn't, all operating systems will end up in the same situation regardless of construction.

Why do you think the construction of a system is not important and has nohing to do with its security? ( I am really curious no flame bait intended )

The Linux environment does have a stronger security because of the restricted handling of privileges and rights. A possible attacker-malware cannot gain root privileges and cause havoc.

---

### Post by scorp123 on 2008-12-11
> **Grimhound said:**
> all operating systems will end up in the same situation regardless of construction.  Well maybe you say such things because you are a newcomer ... but above statement simply isn't true. There are galaxies of technical differences in between that would easily show why Microsoft's design is inferior (e.g. a web browser in the OS core and which runs in kernel context??? WTF?) and why your scenario is highly unlikely to happen.

> **Grimhound said:**
>  It's better to have a weapon and not need it than to be defenseless.  Well, if that's the case and if your wish is "to have a weapon" then please read, learn and adapt. Your Windows thinking will get you nowhere. To use your "weapon" analogy: Cavalry used to be a weapon once. It was good. It was perfect for stopping foot soldiers. If there was one thing infantry was afraid of then it was becoming prey to cavalry attacks. ... But then someone invented armoured vehicles. And on the end of the line of that development stand modern main battle tanks. We agree that a cavalry charge against a main battle tank is pretty useless, yes?

That's exactly what you are doing here. You are using cavalry tactics against a completely different target.

Just forget about virus scanners, OK? They are not a threat here. Just as cavalry would be no threat whatsoever against a main battle tank.

You said you want to "be armed and ready". Fine then. I suggest you read about OpenSSH, about running services (Web, FTP, SSH), about firewalls that keeps unwanted IP addresses and the people behind them away. And then I suggest you read about manipulated install packages and why it is a very good idea to only install software from the official repos (which reside on servers that are well protected) and never ever from other sources which are not trustworthy.

These are the threats we might be facing here. You want to be "armed and ready". That's fine ... for as long as you choose the right weapon.

Your current choice however is based on ancient knowledge which has little to no value here. Viruses don't exist here. But human hackers do. They are a real threat everyone opening up a network service (Web, FTP, SSH, Mail ...) should be aware of. Viruses? They are no threat here whatsoever.

> **Grimhound said:**
>  I mean, look at OS X. The same trick could also be used against Linux users :D

That's precisely why we oldtimers brainwash you newcomers to only install software from trustworthy sources!! ):P

But as you will agree with me: manipulated packages are not exactly the same thing as a computer virus (which I'd define as autonomous small program that automatically infects other binaries and spreads over a computer and over a network in due time .... )

No virus scanner can protect you against manipulated packages. Only your intelligence and cautiousness can :)

---

### Post by JoshuaRL on 2008-12-11
> **Grimhound said:**
> Just to be honest. If cloud computing actually takes off, and I pray it doesn't, all operating systems will end up in the same situation regardless of construction. It's better to have a weapon and not need it than to be defenseless.

Also, people being smug about the supposed protections of an OS is what makes people want to start making absurdly vile virii for it. I mean, look at OS X.

I have to take a small bit of respectful exception to this.

First of all, cloud computing works best with *Nix as the OS.  Windows can never compete with the speed and uptime here.  So when I think of living in the cloud, I think of wider (albiet not as well advertised) adoption of Linux.  And there's a difference between a loaded magnum sitting in a quiet drawer with a trigger lock, and a Terminator bot on full alert patroling your yard and yelling at you every time something gets close.  AV with real-time protection falls firmly in the latter category.

And to be honest, Linux isn't safe because no one has thought to crack it.  The old "security by obscurity" claim is false.  If Linux was just waiting around for a blackhat to attack, then all of the servers with Linux on them would be insecure too.  And that's where the real power and money is, not on botnets or phishing scams.  But Linux is built secure, and kept up to date like it was a religion.

As far as OSX goes, that is where self-assuredness came back to bite them.  If I remember right, the last Pwn-2-Own contest where OSX lost was because of a flash vulnerability that Apple just didn't feel was important to update out of.  That is the main flaw of OSX right now, a lot of OSS that isn't properly updated.  But it is of note to realize that there haven't been any widescale attacks on OSX.  Just not enough vulnerabilities there to matter for crackers.

Sorry for the book.

---

### Post by scorp123 on 2008-12-11
> **JoshuaRL said:**
>  But Linux is built secure, and kept up to date like it was a religion.  Amen! O:)

---

