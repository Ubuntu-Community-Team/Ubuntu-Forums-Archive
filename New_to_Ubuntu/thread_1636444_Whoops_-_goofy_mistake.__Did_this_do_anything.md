---
title: "Whoops - goofy mistake.  Did this do anything?"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by shortboard on 2010-12-03
Hello,

I'm a very new Ubuntu user and am currently running 10.0.4 on my recently acquired (and first) VPS.  After running through the initial setup per the instructions at Linode, I made a rather goofy mistake and am wondering if I may have broken or compromised anything.  Hoping one of you might be able to shed some light here.

Basically, I accidentally inserted a portion of my Terminal session right back into the same Terminal shortly after installing some more software by way of an inadvertent drag and drop when some text was selected in TextEdit.  For what it's worth, I had sudo right before this.

Fortunately most "commands" just returned errors, but one did not and it has caught my attention. i accidentally input the following:

> shortboard@mymachine:~$ ldconfig deferred processing now taking place 
 

the system responded with 

> 
/sbin/ldconfig.real: relative path `deferred' used to build cache


Looking at the man docs for ldconfig ([http://linux.die.net/man/8/ldconfig](http://linux.die.net/man/8/ldconfig)), I see that it created some links and cache to any libraries found in a directory that I guess would have been called 'deferred,' assuming one actually existed.  Given that this directory does not exist (to the best of my knowledge), is it safe to assume that the command didn't do anything in this instance?

Thanks!

---

### Post by kerry_s on 2010-12-03
i doubt it did anything really bad, from what you posted it's not as root so it's confined to your home directory.

---

