---
title: "Wrong architecture?"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by lockalidiot on 2010-02-10
Hi all.

I just installed Ubuntu 9.10 for my desktop. I've been pleased with it in general, but with some programs that I try to install I get an error message saying: > Error: Wrong architecture 'i386'

What does this mean, and what should I do?

Thanks all!

---

### Post by patchwork on 2010-02-10
You probably have 64 bit (i386_64) Ubuntu, and are trying to install 32 bit (i386) software.  
Before you kill yourself trying to make that work, does the software you want to install come in a 64 bit flavor?

---

### Post by snowpine on 2010-02-10
> **lockalidiot said:**
> Hi all.

I just installed Ubuntu 9.10 for my desktop. I've been pleased with it in general, but with some programs that I try to install I get an error message saying: 

What does this mean, and what should I do?

Thanks all!

It means you are not installing software using Ubuntu's built in packaging tools. The Software Center, Add/Remove Programs, Synaptic Package Manager, and various terminal commands (apt-get or aptitude) should automatically install the correct version for your architecture. Maybe you are trying to download random stuff off the internet? (not recommended)

---

### Post by mwcrowley on 2010-02-10
What are you doing to install these programs?  Are you using Synaptic or Add/Remove, or are you downloading them from a website and trying to install them?

---

### Post by Psumi on 2010-02-10
I would suggest using **dpkg -i <package> --force-architecture**... but it may harm your installation.

---

### Post by mwcrowley on 2010-02-10
> **Psumi said:**
> I would suggest using **dpkg -i <package> --force-architecture**... but it may harm your installation.

No disrespect, but I would not recommend this.  If you're not sure why you are getting the original error message, you are not yet up to cleaning up the mess this might cause.
Cheers.

---

### Post by audiomick on 2010-02-10
> **mwcrowley said:**
> No disrespect, but I would not recommend this.  If you're not sure why you are getting the original error message, you are not yet up to cleaning up the mess this might cause.
Cheers.
+1 for this.

---

### Post by lockalidiot on 2010-02-10
First, thank you all for answers!

Yes, I'm running 64-bit. Yes, I'm trying to download these programs from internet sites, like trying to get Avast! for anti-virus, etc.. I wasn't able to find a decent anti-virus program from the Software Center.

---

### Post by patchwork on 2010-02-10
clamtk is a nice little antivirus software in the repositories.....

---

### Post by snowpine on 2010-02-10
> **lockalidiot said:**
> First, thank you all for answers!

Yes, I'm running 64-bit. Yes, I'm trying to download these programs from internet sites, like trying to get Avast! for anti-virus, etc.. I wasn't able to find a decent anti-virus program from the Software Center.

Downloading random software from internet sites is the "Windows Way" of doing things. Worrying about viruses is also the Windows Way. :)

The Ubuntu developers have created a huge repository of tested and trusted software that you can safely install using the package manager. This repository includes antivirus; I know that clamav is very popular.

---

### Post by Dan_Dranath999 on 2010-02-10
clamtk is nice, but i like Avast! more

---

### Post by atomizer on 2010-02-10
You do know that anti-virus on linux is for protecting windows users?

(so you don't send an infected file to them?)

---

### Post by wojox on 2010-02-10
What's the reason for an anti-virus? [Linuxvirus]("https://help.ubuntu.com/community/Linuxvirus")

---

### Post by lockalidiot on 2010-02-10
Suppose I got a bit too comfortable with the Vista... Everyday learning more.. Thank you all!

---

