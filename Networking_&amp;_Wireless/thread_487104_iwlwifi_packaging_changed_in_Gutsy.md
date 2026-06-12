---
title: "iwlwifi packaging changed in Gutsy?"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by KjetilK on 2007-06-28
I was about to compile a 2.6.22 kernel to see if that can fix some of  [issues](http://ubuntuforums.org/showthread.php?t=246074), and importantly the iwlwifi driver. 

I'm a bit baffled by the packaging though. 

In [Feisty](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=iwlwifi&searchmode=searchword&case=insensitive&version=feisty&arch=i386), there are iwlwifi.ko and stuff, but in [Gutsy](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=iwlwifi&searchmode=searchword&case=insensitive&version=gutsy&arch=i386) it seems only the microcode remains. 

The [driver howto](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=iwlwifi&searchmode=searchword&case=insensitive&version=gutsy&arch=i386) seems to imply there are things there beyond the microcode.

So, I was wondering where th e rest of this stuff went?

And since I'm compiling a kernel from source, where's the code in the linux-source packages? I can't find it at all in the linux-source.

---

### Post by KjetilK on 2007-08-08
Clicking on that gutsy link there now, it seems that the .ko files have made it in, but nothing in the headers yet. Anyone know the status?

---

