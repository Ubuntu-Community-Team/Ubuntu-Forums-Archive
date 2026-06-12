---
title: "ATI drivers for x1050 , total mess"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by SandShark on 2011-01-17
I installed Ubuntu yesterday. I am still fighting with the terminal and basic stuff. Here's my problem. I started doing things too fast, installed packages too randomly and now am pretty stuck. I want to ask - how can I remove EVERY single driver and... whatsoever, so I can start from scratch, with my lovely x1050 (old, but still - mine :D ). I couldn't help noticing that every time I used the System -> Administration -> Hardware drivers I got absolutely nothing in there, despite installing a lot of stuff. Please, for the absolute noob, step by step - how to delete everything and install everything right. 
P.S. I'm in love with Ubuntu ^^ Great being here :)

---

### Post by davidmohammed on 2011-01-17
welcome aboard and the forums

given that you only installed yesterday, can I suggest it would be cleaner and easier to install from scratch again. 

Once you have done this, come back and I'm sure we can help you again.

---

### Post by SandShark on 2011-01-17
> **davidmohammed said:**
> welcome aboard and the forums

given that you only installed yesterday, can I suggest it would be cleaner and easier to install from scratch again. 

Once you have done this, come back and I'm sure we can help you again.

Right, question here as well. Since I'm installing Ubuntu from my windows, I have to ask - How many gigabytes should set to "Installation Size"?
[img]http://www.technobuzz.net/wp-content/uploads/2009/03/install-ubuntu-windows.png[/img]

P.S. Thanks for the warm welcome :)

---

### Post by davidmohammed on 2011-01-17
You either have a very small drive or a very full drive - suggest free up some space.

Question - why are you trying to install 8.04? - the current recommended versions are either 10.04 or 10.10.

Also, what are the specifications of your PC

RAM, Graphics card & Processor.

Depending on what the above, I'm sure we can advise you further.

---

### Post by SandShark on 2011-01-17
Oh, I'm sorry. That's a random screenshot to show you what I'm talking about (now I understand it wasn't necessary...)
I'm using the 10.04
Specifications:
Intel Celeron 2GHz
512 mb Ram
Sapphire Radeon x1050 256mb core clock 400 mhz

---

### Post by davidmohammed on 2011-01-17
OK,
  understand - you are installing ubuntu within windows.  I presume you did the same previously?  If so, first use windows Add/Remove programs to remove your previous installation.

Then reinstall ubuntu 10.04 - if you are just testing things, then 8 to 20 GB would be OK.  Once you are happy that everything is working, and that ubuntu is best for you, then I would recommend a dual boot installation.

---

### Post by SandShark on 2011-01-17
> **davidmohammed said:**
> OK,
  understand - you are installing ubuntu within windows.  I presume you did the same previously?  If so, first use windows Add/Remove programs to remove your previous installation.

Then reinstall ubuntu 10.04 - if you are just testing things, then 8 to 20 GB would be OK.  Once you are happy that everything is working, and that ubuntu is best for you, then I would recommend a dual boot installation.

Thank you VERY much :) I will reinstall ubuntu 10.04 and set it up to 20 GB, than will ask for help with the ATI drivers. 

Regards, SS

---

### Post by coffeecat on 2011-01-17
> **SandShark said:**
> my lovely x1050 (old, but still - mine :D ). I couldn't help noticing that every time I used the System -> Administration -> Hardware drivers I got absolutely nothing in there, despite installing a lot of stuff.

> **SandShark said:**
> Sapphire Radeon x1050 256mb core clock 400 mhz

> **SandShark said:**
> I will reinstall ubuntu 10.04 and set it up to 20 GB, than will ask for help with the ATI drivers.

Sorry, you're stuck with the default open source driver for that card. ATI withdrew support in their closed-source driver after February 2009:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

---

