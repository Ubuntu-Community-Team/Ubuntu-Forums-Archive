---
title: "Found drivers for Asus 138g (broadcom 4318)... but how?"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by Trebaruna on 2006-09-18
Just installed Ubuntu for the umpteenth time. Unfortunately, I seem to be unable to get my 4318 based wireless card running properly.

However, the ASUS site seems to have actual drivers for this monkey! yay! Well that's what I thought.

The driver is a source, so it needs compiling. Now I am very green when it comes to linux, but I started learning. Got the build essentials and all, but the readme included with the driver tells me there is a CROSS_COMPILE=<xxx> variable which needs to be set, something to do with gcc..?

I'm afraid I have no idea what that means, and I don't even know where to start looking. I threw the term cross_compile in google, but that seemed even more confusing!

If all else fails I'll try the ndiswrapper method again, but that thing installs, finds an unsecured network, connects and tells me something like bound 192.bla, renewal in 2472156290 seconds (I am not overdoing the seconds bit) and then sort of semi-hangs the system.

Pointers to the cross_compile reference, or to the ndiswrapper method, would be highly appreciated!

[ASUS linux driver]("http://dlsvr01.asus.com/pub/ASUS/wireless/WL-138g-v2/138gV2_Linux.zip")

---

### Post by nullmind on 2006-09-18
I have the Broadcom 4318 chipset and I use the bcm43xx-fwcutter solution (extracts firmware from the driver)

Where is the source that you are trying to compile and I'll have a look. I assume you read the INSTALL file that should be available or tried the vanilla of makes:

./configure
make
make install

Cheers,
Kris

---

### Post by Trebaruna on 2006-09-18
Thanks for your response, kris!

The driver -source- should be at the other end of the link in my original post.

Ehh yeah I tried make (the README tells me to make clean and then make), the other two seem to have little effect, which probably means I am using them wrongly.

After some more research it seems the cross_compile thing has to do with the build platform being different from the host platform. In my case of course both platforms are the same installation, so I have to look a little further into how it may be used and what can be specified.

A potentially important detail I forgot to mention, by the way, is that I am using the AMD64 ubuntu.

Just to stress once more, I am a total newbie in the Linux field. I am trying to research but it's difficult when I pretty much know nothing at all about some of the things I am looking for. Eventually I'll get there, but it's a long way to go.

---

### Post by Trebaruna on 2006-09-18
Ugh, what a beginners' mistake! After installing the kernel headers things went better.

However, it appears the driver does not appreciate 64 bit. Maybe advanced tweaking may solve the issue, but I'm not quite adept enough.
Either way, it seems it is a Broadcom native linux driver, so perhaps it could be useful in 32 bit..?

Anyhow, sorry to have opened a thread before *properly* researching.

---

### Post by nullmind on 2006-09-20
You should try the bcm43xx driver with the bcm43xx-fwcutter. My girlfriend has a dual-core AMD64 system (Turion) and uses that driver for her Broadcom chip. I use a 4318 but I'm on a Pentium M.

---

