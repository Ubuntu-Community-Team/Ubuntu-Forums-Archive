---
title: "Wubi or VirualBox?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by tread29 on 2009-03-25
Which is better for running the ubuntu environment virtually on XP, Wubi or VirtualBox?

---

### Post by binbash on 2009-03-25
Wubi is better in my opinion

---

### Post by Simian Man on 2009-03-25
Use Virtualbox to decide if you like it.  Once you have decided if you want to install it, do a regular installation.  Wubi isn't really very good.

---

### Post by tread29 on 2009-03-25
> **binbash said:**
> Wubi is better in my opinion

Why? Ease of install? Can you tweak setting like in virtualbox?

---

### Post by Stormx on 2009-03-25
Wubi isn't a virtual machine. Virtualbox is.

Go with Wubi. If you like it, install it normally.

---

### Post by binbash on 2009-03-25
Not because of easy install.You can't use most things at virtualbox like compiz etc.

---

### Post by Simian Man on 2009-03-25
Wubi simulates a hard disk with an NTFS file, andNTFS doesn't really handle large files well.  A proper installation will give more speed and stability.

---

### Post by tread29 on 2009-03-25
> **Stormx said:**
> Wubi isn't a virtual machine. Virtualbox is.

Go with Wubi. If you like it, install it normally.

I've been using Ubuntu at home for about 3 year now. I already know I like it. I just wand to run it virtually on my work laptop and just found out about Wubi. I've used Virtualbox in the past and didn't have any complaints.

---

### Post by stoogiebuncho on 2009-03-25
If you want to run it virtually then use virtualbox.  Wubi is not the same as virtualization and will change your windows bootloader (which, if it's your work lappy, might make your IT guys frustrated with you).

(I think Wubi's pretty good, actually, but it's not virtualization.)

---

### Post by tread29 on 2009-03-25
> **stoogiebuncho said:**
> If you want to run it virtually then use virtualbox.  Wubi is not the same as virtualization and will change your windows bootloader (which, if it's your work lappy, might make your IT guys frustrated with you).

(I think Wubi's pretty good, actually, but it's not virtualization.)

Good to know. Thanks! I think I'll be sticking with Virtualbox.

---

### Post by raydeen on 2009-03-25
The only real downside I've seen to Wubi is that once you're in it, you can't access your Windows files if you need to. With dual-boot and VirtualBox (to an extent) you can access files on your Windows/OS X partition if you need to. On my Windows laptop, I can just open up the Windows partition and grab stuff. On OS X, I have FTP turned on for the MacBook and just FTP from the VBox Ubuntu into my MacBook partition. A little convoluted but it works. :)

---

### Post by thehouseofho on 2009-03-25
> **raydeen said:**
> The only real downside I've seen to Wubi is that once you're in it, you can't access your Windows files if you need to. With dual-boot and VirtualBox (to an extent) you can access files on your Windows/OS X partition if you need to. On my Windows laptop, I can just open up the Windows partition and grab stuff. On OS X, I have FTP turned on for the MacBook and just FTP from the VBox Ubuntu into my MacBook partition. A little convoluted but it works. :)

You can access your Windows files easily with wubi.  Your entire Windows installation is located in /host.  Once you're in /host, you're in C:\ in Windows.

---

### Post by parc-sys on 2009-03-25
Personally, Virtualbox seems the best, and easiest to work with.  I've just finished installing an XP, Vista, Win7, Server 03 and Server 08 setup with VirtualBox, and no problems here.

---

### Post by starcannon on 2009-03-25
Wubi is the best option, if you want to trial a Dual Boot situation that can be "undone" through the MS Windows add/remove software utility.

Virtual Box is the best option if you require Ubuntu to be available on your MS Windows desktop, again giving you easily removability if you decide its not for you.

So, either way is excellent, it just depends on "how" you want to access Ubuntu, not really a matter of which is better, just which is best for your needs.

GL and have fun.

---

### Post by nosman240 on 2009-03-25
i personally prefer Wubi. I first tried Ubuntu out in a virtual environment, but there were some speed problems on occasion and i didn't always like having an OS open within a window (i guess that's just a personal thing). It really depends on what your needs are i think, because depending on the situation it could be better running it in VirtualBox or not

another thing i do like is that if i ever get tired of Ubuntu (fat chance) i can just go into windows and click uninstall, and poof! its all gone :)

---

