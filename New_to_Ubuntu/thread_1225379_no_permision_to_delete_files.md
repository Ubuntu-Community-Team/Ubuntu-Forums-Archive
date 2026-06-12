---
title: "no permision to delete files"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by danardel on 2009-07-28
Hi all! As I've just entered the linux world - successfully so far - I bumped into an issue: How can I remove the AVG85? I d'loaded on the desktop, then clicked on it, and installed it, but I couldn't run it. Many opinions on this forum say I don't need it. But I couldn't delete the files - apparently I don't have permision. But I am the installer... How do I do it? I tried to remove the whole AVG from the Add/Remove but it didn't find it...That's why I tried to delete file by file...

---

### Post by jocampo on 2009-07-28
> **danardel said:**
> Hi all! As I've just entered the linux world - successfully so far - I bumped into an issue: How can I remove the AVG85? I d'loaded on the desktop, then clicked on it, and installed it, but I couldn't run it. Many opinions on this forum say I don't need it. But I couldn't delete the files - apparently I don't have permision. But I am the installer... How do I do it? I tried to remove the whole AVG from the Add/Remove but it didn't find it...That's why I tried to delete file by file...

wait, you mean... uninstall the program or delete the icon? you can uninstall via synaptic if you used it to install it 1st ... you can also use this command

sudo apt-get purge [program name]

or

sudo apt-get remove [program name]

To delete a file on your own desktop, just right click and delete...

By the way, you don't need Antivirus Programs on Linux or defrag utilities ;-)

---

### Post by danardel on 2009-07-28
Re the need for AVR, I think I got a bit confused: according to this link [https://help.ubuntu.com/community/Antivirus/Avg](https://help.ubuntu.com/community/Antivirus/Avg) it's a YES, according to users' experience it's a NO...
So I chose the second. I tried to remove the program (going to Applications > Add/Remove) but it didn't work.
I'll try your way jocampo.
Thank you for the prompt reply!

---

### Post by llamabr on 2009-07-28
Once you put it on your desktop, what did you do?  Did you install something?  If you want to uninstall something you installed by hand, the answer is: it's a bit complicated.

If you just want it off of your desktop, go to a terminal

```
cd ~/Desktop
sudo rm AVwhatever
```

Note that that's two lines.

In the future, you'll want to add/remove programs in the way that you've described (with the add/remove option)

---

### Post by danardel on 2009-07-28
To jocampo:
It worked!
Thanks a lot!

To llamabr:
It didn't show in the Add/Remove, although the steps I did were:
- downloaded on the desktop
- clicked on the icon there, and installed it
- tried again, I got the message that it's been installed, do I need to re-install it?
- re-booted ubuntu, imagined that AVG will show up somewhere
- decided to delete the whole AVG (the files and directories where there though)

Now it's ok.
Thank you all for support!

---

### Post by wojox on 2009-07-28
You could also look for all occurrences by:

```
whereis avg
```

---

### Post by jocampo on 2009-07-28
> **danardel said:**
> To jocampo:
It worked!
Thanks a lot!

To llamabr:
It didn't show in the Add/Remove, although the steps I did were:
- downloaded on the desktop
- clicked on the icon there, and installed it
- tried again, I got the message that it's been installed, do I need to re-install it?
- re-booted ubuntu, imagined that AVG will show up somewhere
- decided to delete the whole AVG (the files and directories where there though)

Now it's ok.
Thank you all for support!

Great! glad it worked...

Just an additional explanation about AVG and viruses. Linux (and Ubuntu also, of course, 'cause is a distro) is not affected by Viruses, like in Windows. Technical documents and history says that since 1990s,  we have had about 50 viruses in total in Linux environments...so do the math, and you will find that probability to catch one is really slow.

Having said that, Linux is still vulnerable to malicious scripts and exploits. So, in order to avoid that, try to download software from well known sites or use official Canonical repositories.

Welcome to Ubuntu and Linux world! :-) ... I made the change about 3 months ago and won't turn back! :P

---

### Post by danardel on 2009-07-28
Thanks again for the advice!

---

