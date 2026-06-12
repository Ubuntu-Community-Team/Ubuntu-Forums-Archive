---
title: "fstab cockup - please help"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by Slimboyfat on 2008-01-17
Hello to everybody – this is my virgin post

I hope it's in the right section

I’m a complete newbie to all of this and am finding  the hands on approach to Linux great, but very challenging (haven’t had to think like this since I tried writing adventure games on a Dragon32 and that was 30 years ago – whatever happened to Scott Adams?)

I’m running Ubuntu 7.10 on an Asus Eee and have been trying to mount a NAS drive (Iomega home network)

I found various helpful threads on the subject here and got as far as creating a folder in media called nasdrive and using the following:

sudo mount -t smbfs //192.168.1.7/PUBLIC /media/nasdrive

This worked fine and I was feeling very pleased with myself

However, I then went on to try and auto-mount on startup and used the following:

sudo vim /etc/fstab
add the following line:
//192.168.0.3/your_path /media/netdrive smbfs

Trouble is, I don’t know what I’m doing really, just copying and pasting sudo commands – pretty stupid of me, I should have quit while I was ahead.

I appear to have created a swap file and buggered things up a bit – the system feels very slow and the internet connection has slowed up for some reason.  The mount to the NAS drops in and out too.  If I run sudo vim /etc/fstab I get the following:

E325: ATTENTION
Found a swap file by the name "/etc/.fstab.swp"
          owned by: root   dated: Wed Jan 16 16:09:32 2008
         file name: /etc/fstab
          modified: YES
         user name: root   host name: ubuntu
        process ID: 5584
While opening file "/etc/fstab"
             dated: Wed Jan  9 10:30:48 2008

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/fstab"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/.fstab.swp"
    to avoid this message.
"/etc/fstab" 7L, 333C

So, my questions:

1.	What does ‘your_path’ mean in this context
2.	How do I and should delete the swap file – step by step
3.	How do I add a line to fstab and what should it be – step by step
4.	Have I caused any other problems elsewhere?

I would be really grateful for any help you can give me

regards

Slimboy...

---

