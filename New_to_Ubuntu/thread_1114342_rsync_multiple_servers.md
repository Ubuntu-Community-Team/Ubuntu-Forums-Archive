---
title: "rsync multiple servers"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by edpatterson on 2009-04-02
> Finally, its unlikely that you actually need to upgrade rsync. Its quite a mature bit of software and I doubt that much gets changed to it. Its more likely that the rsync commands aren't correct. Try asking for help with that instead.
OK, here goes

I followed the how-to from here [http://www.howtoforge.com/forums/forumdisplay.php?f=2](http://www.howtoforge.com/forums/forumdisplay.php?f=2) and it worked just fine. Then I attempted to add another server by generating a key pair for it, copying it to the master server and adding the public key to the authorized_keys file.

When I tried to sync to the second server I got a 'smartcards not supported' message (I do not have any smart cards) then a prompt for the password. I put in the password and it bombed out.

I then tried to sync the original server. I got the smartcard error, entered the password and the files synced.

I am at a loss. I have one server that has new files copied to it during the day. I then need to copy those files out to 14 other servers.

Any help appreciated.
Ed

---

### Post by lavinog on 2009-04-17
can you post the command you were using to rsync?
Can you ssh to those servers without using a password?

---

