---
title: "Linux system Error Logs"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by sleepwalka26 on 2011-03-21
*Forgive me if this is already posted somewhere, and if so if someone could post a URL or direct me in a direction to solve my problem.* 

Having said that, My install of xUbuntu has found a few "hiccups" things were running smoothly then recently, the system "blacks out" to what I can describe as a terminal shell with some wording, then resets to the gui login screen. I would like to fix this rather than do a complete install of xUbuntu again. so what I'm looking for is if there is somewhere within my system that logs errors or something of that sort that will help to describe what exactly is going on, if there is a script or something that is causing this "reboot" cycle. 

This might be a no brainer to some but these "hiccups" seem to have begun once I installed VirtualBox, I don't know why that would or could cause a problem but some may/will know more than I.

---

### Post by deconstrained on 2011-03-21
It could be anything, really. A good place to start would be grepping through /var/log for memory-related errors. But before you even do that, double-check that you have enabled virtualization (this is a CPU option that can only be configured through the BIOS menu).

---

### Post by JKyleOKC on 2011-03-21
It's not necessary to enable the virtualization setting in BIOS in order to use VirtualBox successfully; in fact, in some cases enabling it actually slows down the VM. In addition, if you are installing Windows guests, do NOT change that BIOS setting after creating the Windows VMs. They are created differently when the setting is enabled, and enabling it after they are created will result in non-working VMs. I learned that the hard way. Fortunately, wiping out my "saved" snapshot, returning the setting to disabled, and then re-starting the VM saved my VM and its data -- but don't count on being that lucky!

---

### Post by sleepwalka26 on 2011-03-21
Any particular grep search term to use? ```
grep -r -i memory | /var/log
``` or something more or less specific?

---

### Post by sleepwalka26 on 2011-03-22
bump

---

### Post by sleepwalka26 on 2011-03-30
bump?

---

