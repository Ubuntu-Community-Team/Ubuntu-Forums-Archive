---
title: "Windows in VirtualBox"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-11-21
I have a laptop with windows in virtualbox, everything works fine except for the internet (while on wired or wireless). How can I fix this?

---

### Post by fahadsadah on 2009-11-21
Make sure the guest has a network card, bridged with the host's.

---

### Post by LunaticHiatus on 2009-11-21
how would I go about doing that?

---

### Post by WakkiTabakki on 2009-11-21
> **LunaticHiatus said:**
> how would I go about doing that?
Unless you need to use VPN from within Windows, the easiest type of network to setup is NAT.

Go into to network setting of your virtual machine and enable a network adapter (see the attached image).
Also, don't forget to install the guest additions...

/N

---

### Post by LunaticHiatus on 2009-11-21
ah, many thanks. Picture helps a lot.

---

### Post by LunaticHiatus on 2009-11-21
Its set up with NAT and guest additions are added, still wont get online. Could it be a driver issue?

---

### Post by camaron1 on 2009-11-21
Just an idea: I've got too windows running on a virtual machine only that I have disconnected windows access to internet on purpose. The reason is Windows (which is no that secure) will be totally protected from any crap coming from Internet and I can still browse the internet simultaneously with FF withing Ubuntu. I I want to install some program in windows I just downloaded on the shared folder and then install it in Windows.

As I said, just an idea.

---

### Post by louieb on 2009-11-21
Which version of VirtualBox PUEL from the Sun site or OSE from the repositories)? 

Reason I ask is I use the PUEL version on my laptop and desktop, After installing VBox building a machine, and installing XP pro in it. Did not do anything special - Internet just worked. 

What version of windows? What does devices - network adapters show? (is there a yellow triangle by it).  It probably won't show your real network adaptor - just the virtual one - set up by the VM - my VM shows a AMD network card in pci slot 2. -  In real life both have intel network adaptors.

---

### Post by WakkiTabakki on 2009-11-21
> **LunaticHiatus said:**
> Its set up with NAT and guest additions are added, still wont get online. Could it be a driver issue?

Hmm, this may seem like a quite silly stab in the dark, but... In windows, right-click the network icon on the desktop (or in the start menu) and choose Properties. Now you should see all the network adapters available. Right-click on the one that corresponds to the NAT-adapter (not sure how you'd identify it, but....) and make sure it is connected (if not, choose "Connect" ofcourse :) )

The other day, I changed from NAT to a bridged adapter to be able to get VPN to work from within Windows, and I couldn't get it to connect at all (kind of similar to what you experience). Turned out windows didn't automatically connect to a newly added network adapter, so I had no manually right-click the adapter and choose "connect". Not the best 2 hours I wasted digging through virtualbox documentation and network setup-stuff in Ubuntu, only to find out I hadn't "pushed the start button" in windows... doh...

EDIT: Oh right... I just assumed (for some reason) you're running WinXP, otherwise, the above may not appy...

Lets hope its that simple...
/N

---

