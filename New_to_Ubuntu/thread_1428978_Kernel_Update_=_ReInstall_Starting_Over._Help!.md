---
title: "Kernel Update = ReInstall? Starting Over. Help!"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by Michael Kaiser on 2010-03-13
I've posted in one thread and started another with no results. Since I'm still technically a Linux Newbie, I'm posting again in this section, hoping for some kind of help.

After the latest updates (including Kernel 2.6.31-20) I cannot boot into Ubuntu... in any Kernel. I have them back to 14, or 13. None will boot. After the splash screen I get the working/loading icon and that's all she wrote. I cannot figure out how to use the Live CD to do a system restore/recover, and Googling the problem has netted results that don't work for me.

Last time I tried to boot, though I got the same exact results, I noticed my Dropbox notification window pop up momentarily to tell me some files have changed. Now, that's odd! It seems to say that it may be merely that my desktop won't load. But, I don't know.

It seems that I'm going to have to reinstall Ubuntu 9.10 and start all over again, no?

Is there a way for me to recover my settings - namely the programs I use?

---

### Post by mikewhatever on 2010-03-13
You could look at the system logs from the live cd, especially at dmesg, or attach both dmesg and syslog to your next post. They are in /var/log on your Ubuntu partition.
To keep your settings, it's advisable to backup your home folder before reinstalling. Can be done from the live cd as well.

---

### Post by Michael Kaiser on 2010-03-13
Thanks for helping, Mike! I have a couple dumb questions, though:

> **mikewhatever said:**
> You could look at the system logs from the live cd, especially at dmesg, or attach both dmesg and syslog to your next post. They are in /var/log on your Ubuntu partition.

Do I get those logs through the Terminal (if so, how?), or by digging into the partition?

> To keep your settings, it's advisable to backup your home folder before reinstalling. Can be done from the live cd as well.

Would simply copying the folder to an external HD do the trick?

Thanks again.

---

### Post by sandyd on 2010-03-13
tell me. what video card do you have?
and have you installed drivers for it?

---

### Post by Michael Kaiser on 2010-03-13
> **carlee said:**
> tell me. what video card do you have?
and have you installed drivers for it?

Just the built-in Intel(R)82915G/GV/910GL Express Chipset Family.

Do you mean install driver in Ubuntu for it? No. Its always worked after installing updates.

---

### Post by mikewhatever on 2010-03-13
> **Michael Kaiser said:**
> Thanks for helping, Mike! I have a couple dumb questions, though:

Do I get those logs through the Terminal (if so, how?), or by digging into the partition?

Any way would do. You can just hit 'Manage Attachments' and then navigate to the log's location. Obviously, you need the Ubuntu partition mounted first.



> Would simply copying the folder to an external HD do the trick?


Yes, pretty much.

---

### Post by Michael Kaiser on 2010-03-13
> **mikewhatever said:**
> Yes, pretty much.

Ok. Another dumb question: How do I make sure the partition is mounted when using the Live Cd?

---

### Post by mikewhatever on 2010-03-13
You click on it in the left panel of the file browser. Another way is to mount manually. We can do that, if you post the outptut of <sudo fdisk -l> and specify the partition.

---

