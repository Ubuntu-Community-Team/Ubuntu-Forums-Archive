---
title: "GPG error during apt-get update &amp;&amp; upgrade..."
date: 2009-09-29
forum: New to Ubuntu
---

### Post by adamogardner on 2009-09-29
So I typed in upgrade (I made an alias that comprises update && upgrade and so on)  and during the course of it I get this error:
"W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: You may want to run apt-get update to correct these problems"  
I manual entered sudo apt-get update and got the exact same error.  
My questions are 3; What is a PGP error,  Why is it happening, and how do I fix it.

---

### Post by grturner on 2009-09-29
GPG is a verification system. 

to add a gpg key, read this [http://ubuntuforums.org/showthread.php?t=299708](http://ubuntuforums.org/showthread.php?t=299708)

---

### Post by adamogardner on 2009-09-29
4th quesion: Does this apply to me?:
  
  Re: How to: install GPG keys
To add a gpg key (change KEY for the requested key)
$ gpg --keyserver subkeys.pgp.net --recv KEY
$ gpg --export --armor KEY | sudo apt-key add -

I don't want to type something I don't at least partially understand. 
 also Do I put something in after "add-" in the last line?

I tried sudo apt-key update, but recieved the same error.

---

### Post by Hospadar on 2009-09-29
that *is* how you add keys, but the instructions will differ slightly depending on who's repo the key is coming from.  It looks like you are getting some google software, so you probably need to get the key from them.

Also it's not really the end of the world if you don't have a key (some home-cooked repositories don't have keys).  They key is designed to prevent people from hijacking your connection and using your apt-get call to inject malicious software, but the likeliehood of that happening for some small repo is extremely tiny I would say.

---

### Post by adamogardner on 2009-09-29
thankyou

---

### Post by Zoot7 on 2009-09-29
> **adamogardner said:**
> So I typed in upgrade (I made an alias that comprises update && upgrade and so on)  and during the course of it I get this error:
"W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: You may want to run apt-get update to correct these problems"  
I manual entered sudo apt-get update and got the exact same error.  
My questions are 3; What is a PGP error,  Why is it happening, and how do I fix it.
```
gpg --keyserver subkeys.pgp.net --recv A040830F7FAC5991
gpg --export --armor A040830F7FAC5991 | sudo apt-key add
```
That should do it for you. :)

---

### Post by adamogardner on 2009-09-29
Nice,  cheers!

---

