---
title: "I got the dreaded Checking Battery State..."
date: 2010-04-14
forum: New to Ubuntu
---

### Post by agar_agar on 2010-04-14
After installing 9.10. Computer didn't turn off while upgrading, neither it was interrupted. I rebooted then and the message appears, I did Ctrl+alt+f2 and logged in.
I get 
Last login: Tue Apr 13 23:01:23 CDT 210 on tty1
apt-config: error while loading shared libraries: /lib/tls/i686/cmov/libm.so.6: invalid ELF header
apt-config: error while loading shared libraries: /lib/tls/i686/cmov/libm.so.6: invalid ELF header
apt-config: error while loading shared libraries: /lib/tls/i686/cmov/libm.so.6: invalid ELF header
Linux ac1410-sa 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686

I'm running a  1.4 GHz Intel Core 2 SU3500 Processor on an Acer netbook with Intel 4500 Media Accelerator.
Now what?

---

### Post by Jon Monreal on 2010-04-14
You might want to consider trying "sudo apt-get install -f" to repair any possibly broken packages. If you should try this, be watchful of which packages it wants to remove, so you don't end up with a rare case like [this]("http://ubuntuforums.org/showthread.php?t=944095").

---

### Post by agar_agar on 2010-04-14
A reply! woot woot.

Sadly, the same message comes up after running the command "sudo apt-get install -f"
error while loading shared libraries: /lib/tls/i686/cmov/libm.so.6: invalid ELF header

What does it even mean and how can I get rid of it? 
Thank you for yur support.

---

### Post by Jon Monreal on 2010-04-15
Try typing the following, and post the output here:

ls -l /lib/tls/i686/cmov/libm.so.6

Edit: Also try:

sudo dpkg --configure -a

---

### Post by agar_agar on 2010-04-15
Output for "ls -l /lib/tls/i686/cmov/libm.so.6" follows:
lrwxrwxrwx 1 root root 14 2010-04-11 23:27 /lib/tls/i686/cmov/libm.so.6 -> libm-2.10.1.so

I've tried that other command as per another thread's advice but nothing happened. I'll wait for your kind help, I'm really blank about what's happening. : )

---

### Post by Jon Monreal on 2010-04-15
Okay, how about "ls -l /lib/tls/i686/cmov.libm-2.10.1.so"?

With everything piling up here the way it is, it might be better to simply reinstall if you have a good enough internet connection.

---

### Post by agar_agar on 2010-04-15
It just says
ls: cannot access /lib/tls/i686/cmov.libm-2.10.1.so: No such file or directory.

So I think it's a full reinstall, then. ufff
Thanks Jon M. By the way what do you mean with "if you have a good enough internet conn."? I'd reinstall from the live CD. Is there a better way?

---

### Post by Jon Monreal on 2010-04-15
That's it, the file that the original file links to is not present!

Try typing "sudo apt-get install --reinstall libc6-i686". With any luck that should fix this problem, at least.

What I meant about the good internet connection was more the updates you would have to do afterwards. The LiveCD is the best option.

It's no problem (although [testimonials]("https://wiki.ubuntu.com/Jon%20Monreal") on the wiki are appreciated).

---

### Post by agar_agar on 2010-04-15
If I put that command between quotes it returns something about python, but essentially the same very first message:

/usr/bin/python: error while loading shared libraries: /lib/tls/i686/cmov/libm.so.6: invalid ELF header

:( If there's no more resources I'll reinstall. This time I'll wipe the disk clean, so there's no problem with past installations. Is that recommended?

---

### Post by Jon Monreal on 2010-04-15
Sorry, don't type the quotes, just what's inside: sudo apt-get install --reinstall libc6-i686

---

### Post by agar_agar on 2010-04-15
oops! sorry I didn't check in for a long time. So the error message is the same with or without quotes. But I noted that when I type with quotes some python reference comes up too. I guess I thought that'd be useful. Ok, reinstalling now. Thanks so much.

---

### Post by Jon Monreal on 2010-04-15
Well, there was one last thing you could have tried: using the Live CD to replace the missing file.

Simply reinstalling is probably for the best, though, because there could be other problems as well.

If you need more help, please don't hesitate to post.

---

