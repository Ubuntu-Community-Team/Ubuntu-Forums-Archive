---
title: "Password Protected Recovery Mode"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-05-14
I have installed Startup-Manager from Synaptic. I am using Ubuntu 9.04. I went to security tab, checked "protect recovery mode" and set a password. I rebooted and selected "recovery mode". My question is: where and when will i see, maybe a dialog screen, asking me for the password that I set?

I was able to drop to a root shell without entering the password I set.

Thank you!

---

### Post by kanikilu on 2009-05-15
I haven't tried it myself, but here's one method:

[http://www.makeuseof.com/tag/how-to-password-protect-grub-entries-linux/](http://www.makeuseof.com/tag/how-to-password-protect-grub-entries-linux/)

---

### Post by NightwishFan on 2009-05-15
I would like to ask why is it so easy to access a root shell. I agree it is as easy as placing a CD in, however you can disable that from working. Do you have to manually disable the recovery mode?

---

### Post by Didius Falco on 2009-05-15
> **NightwishFan said:**
> I would like to ask why is it so easy to access a root shell. I agree it is as easy as placing a CD in, however you can disable that from working. Do you have to manually disable the recovery mode?

This Console Security Guide will tell you how to generate a password that must be used to boot into Recovery Mode:

[https://help.ubuntu.com/9.04/serverguide/C/console-security.html](https://help.ubuntu.com/9.04/serverguide/C/console-security.html)

That will make it harder for someone to casually get root access, so if your kid brother or someone is trying to hack into your PC, that should be enough to stop them.

But anyone that has physical access to your PC and is determined enough can get your data, full stop. They can just steal the whole PC, or just the hard drive and work on it at their leisure - including using a Live CD.

For more covert work, they can make an exact duplicate of the contents of your hard drive, replace your hard drive and you may never even know it happened.

Bottom line: If they have physical access, they can get whatever it contains.

Regards,

Didius

---

### Post by NightwishFan on 2009-05-15
I am aware of security on Linux. I just wondered why it is not password protected by default.

---

### Post by Didius Falco on 2009-05-15
> **NightwishFan said:**
> I am aware of security on Linux. I just wondered why it is not password protected by default.

In my opinion, it's because they've designed it to have all the security options available for those that may need them, but set it up for the average desktop user.

After all, Recovery Mode is often used to help people who've forgotten their password. Imagine their reaction when they come into the forum for help, and the first thing they are told is, "In order to recover your password, you'll need to know your Recovery Mode password."

Bye-bye new user...

Of course, you can tell them to use a Live CD, which makes the Grub password useless as a security measure

If your PC is in a public area with higher security needs, then by all means, put a password on Recovery Mode. Add one to the BIOS as well. Remove all the CD and Floppy drives and disable the USB ports. If you have data that has to be protected, use strong encryption and physical security measures.


But the average desktop user doesn't need or want all that.

All that does is add more roadblocks between the end-user and being able to actually use the PC.

I was in a thread a couple of weeks ago where a new home user had a four-year old daughter that wanted her own account who was looking for advice on creating her account,  setting account permissions and password issues.

When it was suggested that the account could be set up to log in automatically, someone said, "Wouldn't that be insecure?"

Now, I'm sure that person comes from a SysAdmin perspective, and security is an issue they have to keep in the forefront of their minds, but it made me laugh out loud.

I had a mental picture of a four year old in a trench coat and a fedora sneaking through the house to hack the PC. :D

No, it's all about physical access and striking a balance that is usable by the average computer user but still secure.

Again, just my own opinion on it. YMMV

Regards,

Didius

---

