---
title: "wireless problems: SIOCGIFFLAGS error?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by MollFlounders on 2009-06-11
Hi folks, 
I just installed Ubuntu last night, really excited about it, but I'm having some problems with internet and hope someone will be able to help me out. I've been working through the documentation on the Ubuntu help site, and searching the forum for similar sounding problems all morning, but nothing I've tried so far has helped.  I'm an absolute beginner, so apologies in advance for dumb sounding phraseology!

I have installed Ubuntu version 6.06 LTS on my Gateway CX 2619 laptop, and am unable to get an internet connection. 

1) when I click on the Network connection icon at the top of the screen, I get this message: "SIOCGIFFLAGS error: No such device" 
2) Going through the  Network Settings box from System>Administrator doesn't help, as it says under Wireless connection that "The interface eth1 is active", but still no joy. Clicking on properties for this, I'm able to enter my Network name, but to enter the password for my wireless I only have a WEP key option, not a WPA option. I know to get internet on my eeepc I need it to be set to WPA, not WEP.
3) I've been working through all the documentation I can find in the guides on this site, and I *think* what I need to do is get the network manager gnome, so I can switch from WEP to WPA, right? I tried "sudo apt-get network-manager network-manager-gnome" but it didn't work: I got back "E: Invalid operation network-manager". Um, maybe because I am not connected to the internet on my laptop so can't get anything? this is my ill informed guess. (I'm writing this email on my eeepc, rather than my laptop - at least this is working!!)

any suggestions? Thanks in advance for you help and patience :)

Moll

---

### Post by TeoBigusGeekus on 2009-06-11
Why 6.06 and not 8.04, 8.10 or even 9.04?
The later the version the better the wireless support.

---

### Post by MollFlounders on 2009-06-11
long story to do with an emergency - short answer is that it was the version I had to hand on a cd last night

---

### Post by TeoBigusGeekus on 2009-06-11
Well, try to install wicd
OR
do a clean installation of a newer version and then install wicd.

---

### Post by MollFlounders on 2009-06-11
ok, I'm trying to do that following these instructions. 
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

but I get as far as "Go to Settings / Repositories..." and there is nothing I can see called "Third Party Software". I'm searching for WICD, but can't find that. Is there another way to do it?

as a really basic question, can I install things if I am not connected to the internet?

---

### Post by TeoBigusGeekus on 2009-06-11
> **MollFlounders said:**
> 
as a really basic question, can I install things if I am not connected to the internet?

Only if you get the installation files from another pc.

The thing is, even if you do that, i.e. find a .deb file or source code of wicd, you will probably have trouble with the dependencies (other pieces of software that wicd needs in order to function properly).
You must find the version of wicd for 6.06 - don't know where and I don't even know whether wicd existed back then.

---

