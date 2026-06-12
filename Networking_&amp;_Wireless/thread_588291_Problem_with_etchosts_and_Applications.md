---
title: "Problem with /etc/hosts and Applications"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by kenwong on 2007-10-23
I clean installed Xubuntu 7.10 to my laptop a few days ago.

I clicked around things on my computer, including the network setups.  This might have harmed the system.

After a restart and login, I now get exactly this error message:

"Could not look up internet address for (none). This will prevent Xfce from operating correctly. It may be possible to correct the problem by adding (none) to the file /etc/hosts on your system."

I did some searches and it seems to me that I need to edit the file /etc/hosts.

The problem is even worse now: I cannot launch anything from "Applications" including Terminal.

Would appreciate if anyone can help.

---

### Post by Agent86 on 2007-10-23
See if you can reboot into recovery mode (usually the 2nd choice from the GRUB boot menu). You'll be in text-only mode, but you should be able to login. Then enter the command
```
nano /etc/hosts
```If, for example, your machine has the name "mypc" then edit the file so that at least the following two lines are in it:
```
127.0.0.1 localhost
127.0.1.1 mypc
```It's OK if there are other lines in the file, as long as these two are at the beginning. If you haven't named your machine, just make up one that doesn't conflict with others on your network (if you're on one).

You might also look at your /etc/network/interfaces file```
nano /etc/network/interfaces
```to make sure that at least the following two lines are in it:```
auto lo
iface lo inet loopback
```These entries are needed to let your machine talk to itself effectively.

---

### Post by kenwong on 2007-10-23
Hi Agent86,

Thanks very much for your help.  I will try now.

But before that, I remember that I HAD a computer name before the disaster which has disappeared in the new sessions.

Should I still do what you told me to?

And, just curiosity, why could a few clicks harm the system?  I remember that I went into "Network", then under "Hosts", add something but then deleted them immediately.

Thank you again.

---

### Post by Agent86 on 2007-10-23
Just substitute whatever your computer name was for "mypc" in my example.

It's possible that you accidentally deleted an entry that was needed, since the Network tool rewrites your configuration files (including /etc/hosts ).

In Linux systems, it's important to remember that anytime you run a program that asks for administrative rights (asks for your password), you could potentially screw up your system configuration. The same goes for any program in the "Administration" or "System" section of your menu, even if it doesn't ask for your password - if you run one administrative program that asks for your password, the system won't ask for your password again for (I think) 15 minutes, even if you run a different administrative program.

And when you're in recovery mode, you are running as root, so it doesn't even ask for your password before letting you configure things. So be careful.

BTW, if you've never used nano to edit files before, you use your cursor (arrow) keys to move around the file, Ctrl-O to save the file (it defaults to saving the file under the same name, which is what you want in this case), and Ctrl-X to exit nano.

---

### Post by kenwong on 2007-10-24
Agent86,

Thank you.

But the error message is still there.  Before that, on the log-in page, at the right bottom corner, the name appears as "(none)" (without quotes).

I can now launch the applications.

And I noticed that, in the /etc/hostname file, there is nothing inside.

Any idea?

Thanks again.

---

### Post by kenwong on 2007-10-24
Hi Agent86,

Just have it resolved by adding my computer name (like xxxxxx-laptop) to the /etc/hostbname file.

Thanks for your help.

BTW, after trying Xubuntu on my machine (with PII 300MHz, 256M RAM), seems that the speed disappoints a bit.  This is especially the case for running Firefox - it is even slower than when I ran it on my Windows 98.  Is there any way to speed it up?

I don't know whether it matters.  I chose "gnash" when I was asked to install flash plugin.  Some websites are showing abnormally.  And I suspect whether it makes the Firefox slow.

But I cannot find a way to remove gnash.

Can you help again?  Thanks.

---

### Post by Agent86 on 2007-10-24
> **kenwong said:**
> BTW, after trying Xubuntu on my machine (with PII 300MHz, 256M RAM), seems that the speed disappoints a bit.  This is especially the case for running Firefox - it is even slower than when I ran it on my Windows 98.  Is there any way to speed it up?I'm running Xubuntu 7.04 on a Celeron 333, but my machine has 512M RAM which may be the difference. You might try Xubuntu 7.04 Feisty Fawn instead as some people have reported a slowdown when going from Feisty to Gutsy.> I don't know whether it matters.  I chose "gnash" when I was asked to install flash plugin.  Some websites are showing abnormally.  And I suspect whether it makes the Firefox slow.

But I cannot find a way to remove gnash.

Can you help again?  Thanks.You can get the non-free Flash plugin by enabling the restricted formats

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Firefox may be slow because of tight memory, gnash wouldn't slow it down except on Flash pages.

---

### Post by Agent86 on 2007-10-24
Whoops, forgot about removing gnash. Start up the Synaptic Package Manager, and search for "flash" in Name and Description. Look for the items described as "GPL Flash" as those are the ones that supply gnash.

---

