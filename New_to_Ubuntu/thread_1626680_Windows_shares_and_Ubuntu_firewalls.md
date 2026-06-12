---
title: "Windows shares and Ubuntu firewalls"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by John Peschken on 2010-11-20
I am having all sorts of trouble trying to get a firewall configured to allow file sharing between my wife's XP machine and my Ubuntu 10.10 with a firewall installed.  I can make it work until I start a firewall on my machine.  I'm close.  I can get it sometimes to work one direction and not the other.  

I have tried to use Firestarter, UFW, Firewall builder, and KMyFirewall from the Ubuntu repositories.  I can't seem to get it configured quite right.  

All I want to do is have a directory on each machine that is fully accessible from the other.  I need a concise explanation of how to do that.

---

### Post by acrazyplayer on 2010-11-20
I agree that Ubuntu should have a option somewhere to help set up network sharing in a easy way. I have never tried to do so, so I dont know exactly what to do but I do know that Ubuntu needs certain programs installed for XP to "see" it. I'm pretty sure you need "samba" but then again I could be wrong. Good luck

---

### Post by Hippytaff on 2010-11-20
With Firestarter you can set a whitelist, but I guess this is only useful with static ip's

---

### Post by John Peschken on 2010-11-20
> **acrazyplayer said:**
> Ubuntu needs certain programs installed for XP to "see" it. I'm pretty sure you need "samba" but then again I could be wrong. Good luck

I have managed to get the file sharing working just fine,  It's when I turn on the firewall that things quit working.  Even though I think I am flipping all the right firewall switches for "SMB" incoming and outgoing it still does not seem to work.  Apparently I'm missing something, but I can't see what it is.

---

### Post by John Peschken on 2010-11-20
> **Hippytaff said:**
> With Firestarter you can set a whitelist, but I guess this is only useful with static ip's
Static ip's are kind of a problem as the other machine is on DHCP.  I could probably change that, but I'd rather not.  The Ubuntu docs you linked to basically just pointed to the Firestarter docs which I have studied plenty already.  They tell you how to enable certain types of traffic.  I follow those instructions to enable SMB (I think that's what I need) but it still doesn't work. You can do it by port numbers, but I have no idea what the right answer is for that.   Besides, I have outgoing set to "permissive", so why can't I see the Windows computer at all?  I read the docs, but it's just not behaving the way it seems to me that it should.  Probably something I am missing, but what?  I am stumped.  I know it's the firewall, because it works perfectly when I turn that off.

---

