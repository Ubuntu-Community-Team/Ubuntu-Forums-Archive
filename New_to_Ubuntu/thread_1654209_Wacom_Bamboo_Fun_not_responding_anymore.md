---
title: "Wacom Bamboo Fun not responding anymore"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by Loek on 2010-12-28
Hi All,

First of all thank you for creating, updating and distributing Ubuntu. I enjoy it everyday.

This morning I started my Maverick Server with a GNOME desktop and the Wacom tablet does not respond anymore. I have some xwacomsetup at startup applications and they are still there and enabled. Yesterday there was a recommended upgrade. I use a server instead of a desktop for my programming activities, for who I also need database servers and the like.

The wacom is important to me to prevent me from getting RSI.

Is it true that the recommended upgrade from the 27th of december did change any settings influencing the Wacom tablet? And if that is, what can I do about it?
I tried looking for the programs upgraded yesterday, but I do not know where to look. In the history of the synaptic package manager I found only the information about the programs I installed myself and there was no history overview in the update manager.

It is today my birthday - ok I share it with some millions, still -  a solution would be a great present. :D

Thanks in advance,


Loek

---

### Post by Favux on 2010-12-28
Hi Loek,

Welcome to Ubuntu forums!

Did the upgrade include a kernel upgrade?

Did you compile a wacom.ko to get the Bamboo Fun working, because it is one of the new Pen & Touch models?

If so the new kernel came with a new modules directory that contains the default wacom.ko (linuxwacom 0.8.4-4) that doesn't work for your Bamboo.  You would need to recompile linuxwacom 0.8.8-10 to get a working wacom.ko and copy it into place into the new modules directory.  See the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

Hope this helps.

---

### Post by Loek on 2010-12-28
Hi Favux,


Thank you very much for the reply and all the work you are doing to get the tablets straight.

Just looked in the boot directory and the kernel version I have is 2.6.35-24-server. That is installed at 02 december, but there seems to be a new initrd.img, which is dated indeed at 27 december.

I will check this out tomorrow. It looks very promising what you say.

I actually quite regularly use ubuntu as a greeting, therefor

ubuntu,

Loek

---

### Post by Loek on 2010-12-29
Hi Favux,


Thank you. It is working now again.

I only needed to execute the copying of the files and the command depmod -a. 
I wish I could now set the status of this thread to 'solved' in order to let people look in such a thread for such a problem and finding the answer.

Great work,

Loek

---

### Post by Favux on 2010-12-29
Good.  So you were right and it wasn't a complete kernel update.

If you go to your first post you'll see Thread Tools at the top on the right.  The last selection in there is Mark as Solved.

---

