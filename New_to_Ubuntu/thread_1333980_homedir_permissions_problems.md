---
title: "homedir permissions problems"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by LeDechaine on 2009-11-22
Ok, first, let me explain.

I do NOT have an home partition, or an home directory in my "/" partition.
Instead, i'm using a symlink to a directory which is in my data partition (drive).

Everything worked well, since, well, my data hard drive just died.
Luckily I had backups. So, **"no problem"**, I use an Ubuntu Live CD, put my home folder into another data partition, deleted the symlink and created another symlink to this other directory, and then reboot.

But now, at the login prompt, I get an error telling the permissions are wrong. Oops.

I'm supposed to make my homedir readable/writeable/whatever by me and only by me, ok. HOW the F*CK am I supposed to do this if I CAN'T LOGIN WITH MY OWN DAMN USERNAME and can only use my UBUNTU LIVE CD!!!

After many attempts to do "the right thing", without different results, i'm pissed off, and I use **chmod -R 777 homedir** (and the symlink).

Rebooting again, there's the same error saying that, **for security reasons, a file in my homedir is locked.**

Oh, what a brillant idea! The system is so much secure now, so much that I CAN'T EVEN USE MY FREAKING OPERATING SYSTEM ANYMORE!

Maybe using **chattr +i homedir** is the perfect way to be SECURE now?!!!


Now what, I have to reinstall my whole damn Ubuntu system only because the operating system is so much scrapped to the core that it can't realize that for it to work, a user must LOG IN???

Guess what, i'm looking for a quick fix, and if I don't get one, smashing my box with a freaking sledgehammer will do.
I just can't stand having linux headaches anymore searching for codes and cheats and hacking the matrix just to do daily basic things that are SUPPOSED to just WORK in a CORRECT operating system.

---

### Post by amingv on 2009-11-22
First things first, please tone down your posting. This is no good way to get help.
It's understandable you're frustrated but we're not your screambags, neither do we want to guess what you'll do if you don't find a quick fix.

Also you have a rather, err..., peculiar set up. Nothing too strange about the system behaving peculiarly.

Now, I believe you may be able to fix this from the recovery console. Follow the steps [here]("http://www.psychocats.net/ubuntu/resetpassword") up to where you choose the "Drop to root shell prompt" option. Notice that if you're on Karmic, you'll use the Shift key instead of Esc.

When you get there, cd to where your home folder/partition/whatever is and use these commands:
```
chown -R <yourusername>:<yourusername> *
chmod 644 -R *
```

Of course, replace <yourusername> with your actual username.

If you encounter any other problems (either with this or with any of the basic stuff that "should work"), please instead of hacking the matrix ask here nicely. I'm sure you'll get some answers and help.

---

### Post by LeDechaine on 2009-11-22
Well, it worked. Except that **chmod 644 -R** did nothing, I had to **chmod 777 -R** to receive the same error about the locked file, BUT i've been able to log in.

Thanks!

---

