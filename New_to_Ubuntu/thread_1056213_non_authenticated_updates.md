---
title: "non authenticated updates"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by mustard greens on 2009-01-31
what is the story with so many non-authenticated updates coming from the repositories lately, including updates to the kernel.  Ive been told by reliable sources that if my repositories are good then there is almost no risk, but I thought the idea was to feel 100% about updates from the repositories.  I have had multiple updates in the past couple days which were listed as non authenticated, some showing that they were important security updates.  could someone shed some light on this for me.

---

### Post by wolfen69 on 2009-01-31
if you added the medibuntu repositories without the GPG key, that could be the reason.

post the output of:```
cat /etc/apt/sources.list
```

---

### Post by jerome1232 on 2009-01-31
> **mustard greens said:**
> what is the story with so many non-authenticated updates coming from the repositories lately, including updates to the kernel.  Ive been told by reliable sources that if my repositories are good then there is almost no risk, but I thought the idea was to feel 100% about updates from the repositories.  I have had multiple updates in the past couple days which were listed as non authenticated, some showing that they were important security updates.  could someone shed some light on this for me.


pst I wouldn't install unauthenticated updates, that means they aren't signed, which means it's possible they aren't coming from where you think they are coming from. Or as the poster said before you just don't have the key for one of your repositories, in which case get the key, it's an important security feature.

---

### Post by mustard greens on 2009-01-31
the only repositories I have enabled (besides main universe and multiverse) are launchpad for open office and medibuntu.  under authentication, there is a listing for medibuntu packaging team, could that be the key, or do I need to find another key.

---

### Post by mustard greens on 2009-01-31
so I went out and found keys for medibuntu and launchpad and followed a tutorial on how to install them in command line. but I get this error

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: You may want to run apt-get update to correct these problems
 
when I run sudo apt-get I get the same message.

also, when I check the authentications through GUI it shows no change to the listed keys.
?

---

### Post by jerome1232 on 2009-01-31
Sounds like that's the key, assuming your using deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main for the open office repo, here's their public key, it's about halfway down. [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by mustard greens on 2009-01-31
thank you jerome, but does this explain the non-authenticated kernel header updates?

---

### Post by HermanAB on 2009-01-31
My policy is: Don't fix it if it ain't broke.  If a system is running properly, then an update cannot make it better.  Think about that.

Cheers,

Herman

---

### Post by jerome1232 on 2009-01-31
I don't know why an open office repo would contain kernel updates...

I have a pretty good argument for that HermanAB, usually a patch is coming in because something is broke, like it's fixing some privilege escalation flaw, or some way a worm can exploit a service. Perhaps fixes an exploit found by a proof of concept virus.

The only recent kernel updates I have were yesterday, I remember they were authenticated in my case.

```
Commit Log for Fri Jan 30 04:53:42 2009


Upgraded the following packages:
linux-headers-2.6.27-11 (2.6.27-11.26) to 2.6.27-11.27
linux-headers-2.6.27-11-generic (2.6.27-11.26) to 2.6.27-11.27
linux-image-2.6.27-11-generic (2.6.27-11.26) to 2.6.27-11.27
linux-libc-dev (2.6.27-11.26) to 2.6.27-11.27
linux-source-2.6.27 (2.6.27-11.26) to 2.6.27-11.27
lp-solve (5.5.0.10-10) to 5.5.0.13-3ubuntu1~intrepid1
```

---

### Post by mustard greens on 2009-01-31
yes the kernel updates were yesterday, not with the open office ones, but in my case they were definitely non-authenticated.  I seem to get many non-authenticated updates, and a friend who is a linux veteran of ten years told me that if my repositories are good (which he checked at the time) then his advice was to accept them.  he felt someone was forgetting to add the key upon posting them or something, but he doesnt use ubuntu or GUI so he wasnt as familiar with my setup and felt that ubuntu may be set to be overly cautious for the sake of us beginners.  any thoughts?

---

### Post by mustard greens on 2009-01-31
Im also curious, do we receive updates for all/any apps that come down the line, or just ones for apps installed on our system.  maybe what I really mean is do I need to be more selective about what updates I accept to avoid bloat, or should I accept all recommended updates because they are for apps I have installed.  thanks again for all your help.

---

### Post by jerome1232 on 2009-01-31
It only upgrades packages that are installed, while I agree it's probably no big deal I think people should be more cautious about this stuff.

This is me being slightly paranoid cautious but...

If a package isn't signed then there's no guarantee some malicious code hasn't been snuck into it. Your dns could be poisoned and your actually downloading off of bad guys repository instead, the use of keys for signing the files is the only way to prevent this stuff.

---

### Post by mustard greens on 2009-01-31
I suppose I will mark this solved since we found the key for the non auth packet this time, and in the case of future issue I will post again.  thanks to all for your help.

---

