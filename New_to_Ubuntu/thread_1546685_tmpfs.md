---
title: "tmpfs ?"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by cioo on 2010-08-05
Newbie on Ubuntu just going through the security list making sure all the right stuff is installed (firewalls etc.).  One of the things I wanted to do was have stricter defaults with dev/shm.  

I read that one should type in:
tmpfs     /dev/shm     tmpfs     defaults,ro     0     0

into the terminal.

Well, when I did that, I got the following message:


No command 'tmpfs' found, did you mean:
 Command 'mtpfs' from package 'mtpfs' (universe)
tmpfs: command not found

What am I doing wrong?

---

### Post by renkinjutsu on 2010-08-05
That line should actually be put into your /etc/fstab file. That is the file that permanently saves the configurations of all your filesystems. The [COLOR="Red"]ro[/COLOR] option is to make the filesystem [COLOR="Red"]read-only[/COLOR] which is a bad idea for /dev/shm as it's a standard UNIX thing and applications may need to write to it and use it as fast storage (pulseaudio for example)

---

### Post by cioo on 2010-08-07
Your advice may be sound about what should be read only.  I was following the standard Ubuntu help security advice about dev/shm but the  instructions about what to type in the terminal did not work for me and hence my post.  As I am a beginner with Ubuntu, can somebody please explain what I type into the terminal to achieve this?

I am not used to using the terminal, so keep it very simple.  (Imagine you are trying to explain it to your computer-illiterate grandma)    :-)

thanks

---

### Post by Ozymandias_117 on 2010-08-07
> **cioo said:**
> Your advice may be sound about what should be read only.  I was following the standard Ubuntu help security advice about dev/shm but the  instructions about what to type in the terminal did not work for me and hence my post.  As I am a beginner with Ubuntu, can somebody please explain what I type into the terminal to achieve this?

I am not used to using the terminal, so keep it very simple.  (Imagine you are trying to explain it to your computer-illiterate grandma)    :-)

thanks

You will need to type ```
gksudo gedit /etc/fstab
``` if you want a GUI for modifying your fstab (You would then add that line to the end and save)

Or if you'd rather a terminal text editor, type ```
sudo nano /etc/fstab
```

---

