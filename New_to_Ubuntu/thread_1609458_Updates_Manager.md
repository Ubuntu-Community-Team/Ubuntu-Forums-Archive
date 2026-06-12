---
title: "Updates Manager"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by theTemest on 2010-10-30
I understand the need to update systems to ensure security and optimal performance between hardware and software. That said, I find the Update Manager a convenient way to stay on top things. While this is good, I am a little tired of having recommended updates (DAILY) of Firefox and the Linux kernel when my desktop environment works quite well. 
I installed the updates to these two shortly after installing Ubuntu about a month ago only to be persisted with the entire system freezing to the point that I blew out Ubuntu and started over. After reading forums and searching online it appears that freezing is more common with Linux than I was lead to believe. My question is this: Is there any way to have the system remember my options to NOT accept the Firefox and Linux kernel updates? Because they are automatically checked I run the risk of installing updates that I don't want. As I said, right now Ubuntu 10.10 is working very well and I just don not wish to update, recommended or not.

---

### Post by Old_Man_Unix on 2010-10-30
> **theTemest said:**
> ... My question is this: Is there any way to have the system remember my options to NOT accept the Firefox and Linux kernel updates? Because they are automatically checked I run the risk of installing updates that I don't want. 

Well, they are automatically *checked*, but they aren't automatically *installed*.    

You always have the opportunity to *choose* which updates you want with the check-box in the Update Manager.

You can also defer the whole installation if you want to, and make your choices, if any, later on. 

I don't understand how this poses a risk when you can so easily choose what you want to do.

---

### Post by snowpine on 2010-10-30
If you update with 'sudo apt-get dist-upgrade' you will get kernel updates. If you update with 'sudo apt-get upgrade' you will not.

You can also always boot into the older kernel from the GRUB boot menu, if you feel a new kernel is causing problems for you.

I can't recommend ignoring Firefox updates. They are important to your security.

---

### Post by theTemest on 2010-10-31
Thanks for the timely replies.
Good points but having to uncheck any update I don't want every 24 hours could lead to an inadvertent install that I don't want [which is what happened to me]. There's no excuse for using care, but I was just wondering if I was missing something that the system remembers my previous choices. 
From your experience, would you guess the kernel or Firefox update to be causing the system to become so buggy?

---

### Post by jrev on 2010-10-31
If you don't want system freeze, why don't you stay on a previous version of Ubuntu, more stable and more secure ?

---

### Post by Elfy on 2010-10-31
You can lock versions in synaptic - highlight a package - Package Tab - Lock version.

Whether that is something you want to do for kernels or firefox I would leave to you.

You can also stop the update checking daily - Synaptic - Settings - Repositories - Update tab - change the frequency.

---

### Post by peculiar penguin on 2010-10-31
If you're getting daily updates (like literally every day) for the kernel and Firefox, something is broken (or you added a development PPA to your software sources or something). While sometimes there are multiple updates in short succession, that's usually only the case with security vulnerabilities or really bad bugs.

You can lock packages to their current version in Synaptic, but I'm not sure that's really a good idea for something as important as the kernel or as exposed the net as your browser.

Also I don't see how Firefox would freeze the entire system, it hasn't even managed to do that on Windows here :P

---

### Post by lotharmat on 2010-10-31
Isn't Ubuntu generally behind with firefox releases anyway??

---

### Post by theTemest on 2010-10-31
> **jrev said:**
> If you don't want system freeze, why don't you stay on a previous version of Ubuntu, more stable and more secure ?
I have 10.10 right now and it works perfectly. It is doing so with out the FF and kernel updates. 
I'll take your advice and stick with what I've got, secure or not. 
Thanks for your comment.
BTW...What is amazing about Ubuntu is how it identified my Windows network and the the ease with which I can connect. Windows doesn't even do it as easily with the same speed.

---

### Post by theTemest on 2010-10-31
> **forestpiskie said:**
> You can lock versions in synaptic - highlight a package - Package Tab - Lock version.

Whether that is something you want to do for kernels or firefox I would leave to you.

You can also stop the update checking daily - Synaptic - Settings - Repositories - Update tab - change the frequency.

PERFECT: I changed it to 1 week. Thank you!

---

### Post by theTemest on 2010-10-31
> **peculiar penguin said:**
> If you're getting daily updates (like literally every day) for the kernel and Firefox, something is broken (or you added a development PPA to your software sources or something). While sometimes there are multiple updates in short succession, that's usually only the case with security vulnerabilities or really bad bugs.

If you don't install a recommended update by unchecking it, in 24 hours the Update Manager will launch at startup and show these as recommended updates again. Every day at startup I am greeted with UM recommending 55MB of kernel and FF updates.

---

