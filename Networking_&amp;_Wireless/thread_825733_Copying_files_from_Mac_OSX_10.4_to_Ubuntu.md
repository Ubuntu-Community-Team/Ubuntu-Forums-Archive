---
title: "Copying files from Mac OSX 10.4 to Ubuntu"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by ajax010 on 2008-06-11
I have an Ubuntu machine running on my home network along with Windows and Mac machines.
I already back up files on the Windows XP machine to the Ubuntu machine without any problem.  I want to do the same with docs from the Mac.
I have set up the Ubuntu system so that I can see it (and a shared directory on it) on the Mac.  When I try to copy files to the Ubuntu machine from the Mac, it first asks me to authenticate (but will not apparently accept either the Mac id/pw or the Ubuntu one, and then it tells me I'm already connected to the resource.
When I'm on the Ubuntu machine, I can't see the Mac (as I can see the Windows machine shared drive) even though I have shared the Mac folder...
Help!  What Am I doing wrong?
Thanks

---

### Post by nixscripter on 2008-06-11
Apple uses their own form of file sharing. Unfortunately, I have not had a lot of luck with that, and the linux support is somewhat questionable.

The way I would see backing up a Mac is to create a backup script on the Mac, and run it. It requires a little bit of knowhow, but here are the general steps, assuming Mac OS X:

1. Create an account on the Ubuntu machine called 'backup', or some such thing. Like a daemon account (e.g what's used to run apache or cron), it should have no password, a shell of /bin/false, and a home directory of a folder for backup data.

2. On the Mac, use 'ssh-keygen' to create a public/private keypair. Send the public key over to the Ubuntu in the authorized keys file. This will allow you to log in as the 'backup' user without a password.

3. When you want to back up, use scp something like this:
```
 scp -BCr folder1 folder2 folder3 backup@**ubuntu.box.ip.here**:~
```

I know it's complicated, but as I said, Macs have their own file sharing. This is one UNIX/Linux method which happens to work on a Mac (since OS X is really modified FreeBSD).

If you would like more details, or can find a simpler solution, let me know.

---

### Post by Wangsta on 2010-07-17
Oh yes please! Could you go in more depth instruction-wise for me?

Especially about sending the public keys and stuff. Also how would I make this "backup daemon"? Like, how do I make it so it has "a shell of /bin/false"??

Thannnk yaaa!

---

