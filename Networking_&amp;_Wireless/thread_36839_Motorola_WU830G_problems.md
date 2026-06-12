---
title: "Motorola WU830G problems"
date: 2005-05-24
forum: Networking &amp; Wireless
---

### Post by radiohead on 2005-05-24
Hey guys,

I have been running Ubuntu for about 2-3 months. During that time I was connect to a CAT-5 wire and my ethernet card was automatically found and everything. It worked great.

Well, I decided to move my comp to my room and just didn't have internet at all for a while. Then me and my dad got the Motorola WU830G since it was like 20 bucks. I ran on Windows XP after that for about two weeks. Now, I am really missing my command-line IRC clients. So, I installed Ubuntu about an hour ago. 

I got NdisWrapper and unzipped it to my desktop. I cd to it and follow the installation instructions on 

ndiswrapper.sourceforge.net/wiki/index.php?Installation.

It does the make distclean just fine but when I sudo make, I get an error.

```

Cannot find kernel sources in /lib/modules/2.6.10-5-386/build;

```

I am not sure if that 386 in there is what kind of comp I have or what because i do not have a 386. I have an i686 or something like that.

In the instructions, it says nothing about the errors that you could get or how to fix them. I am not sure if this is an error I can do away with or one that i should look at.

Any help is greatly appreciated.

---

### Post by anders.ostling on 2005-05-25
you will get the .386 package even if you have a 686 (at least that is what I got with my Mobile P4 ...). Does not really matter for what you are trying to do. 

You need to install the source package for your kernel. Use synaptic to search for "linux" packages and select the source package (for .386). That should do it.

Anders

---

