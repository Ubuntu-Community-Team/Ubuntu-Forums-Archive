---
title: "GPG Error, how to fix?"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by MalphasWats on 2009-09-27
I'm learning fast, but I've got a bit stuck with something.

When I try to update, I get the following error:
```
W: GPG error: http://gb.archive.ubuntu.com jaunty Release: 
The following signatures were invalid: BADSIG 40976EAF437D05B5 
Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

I googled and thought I'd found a solution here:
[http://ubuntuforums.org/showthread.php?t=438313](http://ubuntuforums.org/showthread.php?t=438313)

but it's for a different archive, so where do I find the keys for my version?

I tried browsing to the url in the error, poked around and found a few .gpg files, which I tried feeding into apt-key add but it just said that there was no valid OpenPGP data found.

What should I do to fix this?

Thanks
-Malphas

---

### Post by sandyd on 2009-09-27
> **MalphasWats said:**
> I'm learning fast, but I've got a bit stuck with something.

When I try to update, I get the following error:
```
W: GPG error: http://gb.archive.ubuntu.com jaunty Release: 
The following signatures were invalid: BADSIG 40976EAF437D05B5 
Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```I googled and thought I'd found a solution here:
[http://ubuntuforums.org/showthread.php?t=438313](http://ubuntuforums.org/showthread.php?t=438313)

but it's for a different archive, so where do I find the keys for my version?

I tried browsing to the url in the error, poked around and found a few .gpg files, which I tried feeding into apt-key add but it just said that there was no valid OpenPGP data found.

What should I do to fix this?


Thanks
-Malphas

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 40976EAF437D05B5

---

### Post by MalphasWats on 2009-09-28
Thank you Carlee,

  I ran that and it said it had imported the key successfully but I still get the same error when I run apt-get update

Any ideas?

Thank you
-Malph

---

### Post by MelDJ on 2009-09-29
get the gpg key of the software source and follow the steps shown in this video: [http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)
hope it helps

---

### Post by MalphasWats on 2009-10-05
Thanks for the reply MelDJ. I've only just had a chance to watch through the video. I can follow the steps but I have no idea where to find the key that I need to fix this problem, I tried browsing [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) but there are lots of files that suggest they have key information so I'm not sure which one I need or how to work it out. I even tried importing the one I found here: [http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)
exactly like it shows in the video, but nothing happened at all and I still get the error when I apt-get update.

It's a bit frustrating - I know it doesn't *really* matter but I really hate getting error messages that I can't fix.

Thanks for your help so far
-Malphas

---

