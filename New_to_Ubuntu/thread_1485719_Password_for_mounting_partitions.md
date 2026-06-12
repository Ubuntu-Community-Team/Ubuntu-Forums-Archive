---
title: "Password for mounting partitions"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Blutkoete on 2010-05-17
Hello!

The problem: When I wanted to mount other partitions with Ubuntu, it asks me for my password. If I open a different partition  (e.g. the Windows parition) in Lubuntu, it doesn't. That's kind of annoying as I don't want people to be able to delete my C:\Windows or /bin/ folders (not that people want to do that, but it's also a protection against too-fast typing in the terminal by myself).

I was wondering whether that is because I allowed auto-login on Lubuntu, but I can't try that out because I can't figure out where to change back to password-required-login in Lubuntu.

I checked fstab already whether those partitions are mounted by default on startup, but they aren't.

I'm running Windows 7 (for DVDs and minor compatibility issues), Ubuntu 10.04 as the main productive operating system and Lubuntu 10.04 (stable beta) as kind of a guest account and for surfing & general relaxation (it boots and shuts off so incredible fast and windows just pop up the moment you click the icon).

As kind of a guest account, it's the GRUB default, and while both Windows and Ubuntu require a password for log-on, Lubuntu doesn't (as I specified during the installation).

Thank you very much,

Blutkoete

---

### Post by Nesaskewatch on 2010-05-17
Go to system>admin>users and groups.  You can change permissions there.  Also, I don't think it will allow *any* changes like you mention without a password.

---

### Post by Blutkoete on 2010-05-18
Thank you!

But it's kind of strange: If I believe what those settings tell me, I shouldn't be able to connect to a LAN or WLAN (which I am) and the system should ask me for my password each time I log on, but it doesn't.

Is there maybe a permission text file somewhere which I can look into from the console?

---

### Post by mastablasta on 2010-05-18
> **Blutkoete said:**
> Hello!
That's kind of annoying as I don't want people to be able to delete my C:\Windows or /bin/ folders (not that people want to do that, but it's also a protection against too-fast typing in the terminal by myself).

 
I don't think the password protects against that. I mean, afterall they can always boot from liveCD and delete it. Also if they were really devious they could just reset your password i believe.

---

### Post by CharlesA on 2010-05-18
> **mastablasta said:**
> I don't think the password protects against that. I mean, afterall they can always boot from liveCD and delete it. Also if they were really devious they could just reset your password i believe.

The password prompt is probably just the system asking for superuser privileges so that it can mount that file system. I haven't run into that before, unfortunately.

---

### Post by Blutkoete on 2010-05-18
They shouldn't be able to boot a LiveCD because they need my BIOS password for that :).

Of course, there are always ways to breach my Noob security, but it protects against accidents, which is my main goal.

It's probably only the system asking for the SUDO password, I just don't understand why mounting asks for the password in Ubuntu, but not in (my) Lubuntu.

Maybe I'll just play around a little, can't destroy much if I have to reinstall my small Lubuntu partition later.

---

### Post by ScottinSoCal on 2010-05-18
> **Blutkoete said:**
> I was wondering whether that is because I allowed auto-login on Lubuntu, but I can't try that out because I can't figure out where to change back to password-required-login in Lubuntu.

I just checked, and this is right for 10.04, but IIRC it's also correct for 9.10: go into System:Administration:Users and Groups. The user profile there has a setting for whether to ask for a password at log on or not.

Edited for up my grammar to fix, so sense this post made. It's early, and I haven't had my coffee.

---

### Post by Blutkoete on 2010-05-18
Good morning, Scott :).

Thank you for your help.

Nesaskewatch also suggested to look there, but it says "Ask for password" already. Maybe Lubuntu has a special way to handle this.

I'm thinking about reinstalling Lubuntu, not telling it during installation to not ask for a password (double-negative, whoa) and look what happens.

---

