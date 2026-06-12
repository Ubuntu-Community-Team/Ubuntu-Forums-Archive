---
title: "Update verification error - public key is not available. What does it mean?"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by r3bol on 2009-03-01
Hi, When running my updates I get this error:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 248DD1EEBC8EBFE8

I'm not exactly sure what this is / how improtant this is.

Here is a reference in my sources.list:
deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main

Should I just delete it, or does it need to be fixed?

Thanks.

---

### Post by Elfy on 2009-03-01
ppa's have signatures now - you need to add the key

[https://help.launchpad.net/Packaging/PPA#Adding](https://help.launchpad.net/Packaging/PPA#Adding) a PPA's keys to your system

---

### Post by forger on 2009-03-01
Use this perl script: [http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by binbash on 2009-03-01
[http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html](http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html)

---

### Post by r3bol on 2009-03-01
[https://help.launchpad.net/Packaging/PPA#Adding](https://help.launchpad.net/Packaging/PPA#Adding)
:confused:
That sounds like something to do with development. I have no idea what its talking about :P

Anyway - I tried the perl script and...

perl launchpad-ppa-fix.pl
Can't locate IO/Socket/SSL.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at launchpad-ppa-fix.pl line 43.
BEGIN failed--compilation aborted at launchpad-ppa-fix.pl line 43.

Looks like I'm missing something to do with perl. What should I install (OMG i feel like such a retard)?:lolflag:

---

### Post by binbash on 2009-03-01
I updated the blog post.You need : 

sudo apt-get install libhtml-parser-perl libio-socket-ssl-perl

---

### Post by r3bol on 2009-03-01
All Done! :) No more error massages!

I would mark this as solved, but the option doesn't seem to appear in the Thread tools options list. 

Thanks for your help.

---

### Post by binbash on 2009-03-01
You are welcome and it is removed : )

---

### Post by forger on 2009-03-02
> **binbash said:**
> I updated the blog post.You need : 

sudo apt-get install libhtml-parser-perl libio-socket-ssl-perl

Binbash, I already explained it - **you post the OLD VERSION** - the version 1.4 has proxy support and more tweaks for everyone.

In the future [SIZE="5"]please use[/SIZE]:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by labinnsw on 2009-03-30
I just wasted the last hour trying to learn how to get a key. I don't know what key I am looking for and I don't know where to look for it.

If I knew that, I could follow the instructions from YouTube. I am getting the same message: 

"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 248DD1EEBC8EBFE8"

Do things really need to get this complicated?

---

### Post by Elfy on 2009-03-30
It's simple enough - the instructions are above and you have the key.

[https://help.launchpad.net/Packaging/PPA#Adding](https://help.launchpad.net/Packaging/PPA#Adding) the keys in the terminal

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 248DD1EEBC8EBFE8
```

---

### Post by labinnsw on 2009-03-30
Thanks, That's infinitely easier than what I just spent the last hour doing.

---

### Post by dirtyhabanero on 2011-04-21
Hope this thread ain't dead.

But forestpiskie spells it out in simple terms for me. I lack the knowledgeg of using keys and thought that I had to fetch one myself from somewhere else. 

At least this has shed some light on using PPA's. If I went along and added all the PPA's from [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas), I understand that I'd be able to always be 'up-to-date' with the developer and their softwares. Like the Arduino team! Is this the purpose of PPAs?

---

