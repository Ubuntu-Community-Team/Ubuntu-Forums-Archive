---
title: "lucid lynx and kernel 3.0.0-8"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by bootoot on 2011-09-06
Hi all

I upgraded my Ubuntu 10.04 to kernel 3.0.0-8 and i notice that HDAPS not working also temperature in conky not shown, other than that everything seems OK. any idea how to make it working?

Laptop: thinkpad x60s
system: ubuntu 10.04
previous kernel version: 2.6.32-33

thanks

---

### Post by Paqman on 2011-09-06
That kernel isn't available in that release of Ubuntu. Can you tell us how you upgraded it? Did you compile your own kernel, or did you grab one out of the repositories for the testing branch?

---

### Post by 2F4U on 2011-09-06
HDAPS on a ThinkPad needs a kernel module tp_smapi, which, as far as I know, is currently not precompiled for Ubuntu. I am using it in 11.04 in combination with TLP from this ppa

[https://launchpad.net/~linrunner/+archive/tlp/+packages]("https://launchpad.net/%7Elinrunner/+archive/tlp/+packages")

But there currently is no version for your kernel. You may wish to read through this link and see if you can get it running:

[http://www.thinkwiki.org/wiki/HDAPS](http://www.thinkwiki.org/wiki/HDAPS)

---

### Post by bootoot on 2011-09-06
@[Paqman]("http://ubuntuforums.org/member.php?u=228590"): i didn't compile it you can find it in synaptic package manager. ;)
@[2F4U]("http://ubuntuforums.org/member.php?u=1357554"): before i upgrade the kernel to version 3.0.0 HDAPS is working i installed it follow this guide [http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_Z61m](http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_Z61m), 
and i tried to update tp_smapi module but it said its already the lates version. will try TLP..

---

### Post by 2F4U on 2011-09-06
I forgot to mention that I also tried tp_smapi and hdaps with kernel 3.0 without luck. The problem is that currently there is no precompiled kernel module in the ppa I mentioned and I was too lazy to compile the necessary modules myself. I guess that if you want to use kernel 3.0 you have to compile the necessary software yourself.

---

### Post by bootoot on 2011-09-06
installed tlp still no luck.. try google also no result. btw before kernel 3.0 i was try kernel 2.6.35 and 2.6.38 and hdaps only work in 2.6.35.

---

### Post by Frogs Hair on 2011-09-06
Strange that the 3.0.0-8  kernel does not appear in the 11.04 synaptic package manager . Is this due to 10.04 being LTS ? Not that I want to install it , I'm just curious . If there were benefits it would have updated automatically

---

### Post by bootoot on 2011-09-06
maybe you right thats because lucid is LTS, cos in lucid can try various backported kernel (see post above), and for benefit i feel the performance improved but cant tell how big the difference is, maybe it just a placebo.

---

### Post by Brushstroke on 2011-09-07
As for your problem with your kernel, I have no clue. I just wanted to ask how you found this kernel in the Synaptic Package Manager in 10.04.3. It's not there for me. o_O

---

### Post by Paqman on 2011-09-07
> **bootoot said:**
> @[Paqman]("http://ubuntuforums.org/member.php?u=228590"): i didn't compile it you can find it in synaptic package manager. ;)


Not if you're using the official repos you can't:

[Lucid Main]("http://packages.ubuntu.com/search?keywords=linux-image&searchon=all&suite=lucid&section=all")
[Lucid Updates]("http://packages.ubuntu.com/search?keywords=linux-image&searchon=all&suite=lucid-updates&section=all")
[Lucid Backports]("http://packages.ubuntu.com/search?keywords=linux-image&searchon=all&suite=lucid-backports&section=all")

So you must have added an external source. Note that when you do this, the package will still show up in Synaptic.

---

### Post by bootoot on 2011-09-07
try add this source in system software source:

[http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main

---

### Post by Paqman on 2011-09-07
> **bootoot said:**
> try add this source in system software source:

[http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main

Well yes, that's a PPA. An external source. Thank you, we now know where you got it from.

That's a daily build PPA  for testing. The packages within it are possibly highly unstable. Stuff not working is to be expected. If you want them working, don't bother trying to troubleshoot a moving target like that, just install a stable kernel.

---

### Post by bootoot on 2011-09-07
thanks for the explanation, will revert back to previous kernel.

---

