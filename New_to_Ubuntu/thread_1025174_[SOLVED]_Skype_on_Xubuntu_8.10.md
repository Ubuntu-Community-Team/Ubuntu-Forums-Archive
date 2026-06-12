---
title: "[SOLVED] Skype on Xubuntu 8.10?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by LNB on 2008-12-29
Hi Everyone, I'm trying to install Skype onto my new Xubuntu 8.10 box, but it does not seem to be cooperating.

The Skype site seems to have packages for Ubuntu 8.04, but not for Xubunto 8.10.

Here is the link:

[_http://www.skype.com/download/skype/linux/choose/_]("http://www.skype.com/download/skype/linux/choose/")

Does this mean that Skype is not compatible with Xubuntu 8.10?

Thank you!

---

### Post by haldean on 2008-12-29
Skype is probably just a little late on updating their version numbers. Linux has never really been their focus :( The 8.04 packages will work fine on 8.10, and most packages will work no matter which flavor of Ubuntu you're using (Xubuntu, Ubuntu, Kubuntu, etc.)

Download the package, double click and it should install just fine! I'm running Skype on my Ubuntu 8.10 laptop right now.

---

### Post by LNB on 2008-12-29
Thanks for your quick response.  I downloaded the file onto my desktop and double clicked on it.  The Package Installer initiates, but an error message comes up that states:

> Error: Wrong architechture 'i386' 

May I get your assistance on what this means / how to get to the next step?

Thank you.

---

### Post by WASHAD on 2008-12-29
The fact that you are using Xubuntu makes me wonder if you meet the minimum requirements. I think that I remember Skype requiring a 1Ghz processor. 

SteveJ

---

### Post by Sef on 2008-12-29
> Error: Wrong architechture 'i386' 			 		

Are you running an Xubuntu 64-bit?   If you are not sure then, open the Terminal (Applications > Accessories > Terminal) and type or paste in this code:

```
uname -a
```

Paste the results here.

---

### Post by LNB on 2008-12-29
Thank you.  Here are the results:

```
Linux ubuntu 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

```

I have a Dell which is pretty old... Am I running 64 bit?

---

### Post by LNB on 2008-12-29
Also, on:

> The fact that you are using Xubuntu makes me wonder if you meet the minimum requirements. I think that I remember Skype requiring a 1Ghz processor.

SteveJ

I have a pretty old Dell, but it is running on an Intel Pentium 4 2.8Ghz x2 (HT), with 2.5 Gb of RAM.  I take it that my computer meets the min requirements?

Thank you.

---

### Post by Sef on 2008-12-29
> I have a Dell which is pretty old... Am I running 64 bit?Yes, you are.  You can install Skype on a 64-bit system. [s]I'll give you the link when I find it.[/s]  [Skype on 64-bit]("https://help.ubuntu.com/community/Skype") is here, scroll down a bit.

---

### Post by tanresa on 2008-12-29
I also have the same problem. Could you help me too? Here's my result:

Linux mohawk 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

I don't know if what applies to LNB applies to me as well. Thanks for any help.

---

### Post by LNB on 2008-12-29
Success!  Thank you very much guys.  I got Skype installed and it started up.  Will work on setting it up so that I can make calls, but that will be for another day.  

Again, thanks for your help.

---

### Post by tanresa on 2008-12-29
Nevermind! Success for me too. Thanks.

---

### Post by JGFuller on 2009-01-01
Thanks also to the forum contributors - the recommended solution worked for determining the type of processor, and the location of the proper Skype download.

:popcorn:

---

