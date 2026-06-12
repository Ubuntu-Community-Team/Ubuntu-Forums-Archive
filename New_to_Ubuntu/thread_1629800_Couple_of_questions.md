---
title: "Couple of questions"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by blacktrance on 2010-11-24
1. Is there a way to give myself permanent root privileges, so nothing would ever ask me for the password? It's as annoying as the Vista UAC.

2. Is there a GUI application for mounting CD images? Something like Daemon Tools.

---

### Post by bryncoles on 2010-11-24
in answer to 1) Yes, but it is considered unsafe from a security perspective, and it is against the forum code of conduct to tell you how to do it. 

Google should be able to tell you how though, if you really want.

---

### Post by Verbeck on 2010-11-24
1. try reading  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo). remember that it'll make your system insecure _(completely)_

2. right click the iso then select open with with other application, and select archive mounter from the list
or from the software center, get gmountiso

---

### Post by blacktrance on 2010-11-24
Thanks, but these answers are insufficient.

1. That tells me how to create a root user, not how to give myself permanent root privileges.

2. Unfortunately, gmountiso only works with .iso, and not with other CD images.

---

### Post by Wtower on 2010-11-24
I would agree with bryncoles, and I could argue that unlike with vista, in Linux the administrative tasks are more distinct and therefore less frequent. For instance, a lot of win programs wrongly require to be executed with administrative privileges. So personally I do not find the root password queries annoying.

For mounting iso images, there are plenty options in the Ubuntu Software Centre if you look for 'iso'. One I do use is AcetoneISO.

Regards

---

### Post by blacktrance on 2010-11-24
Every time I install something or update, it asks me for my password. It's rather annoying and I'd like it to stop. The Google results seem to all say something like "just use sudo", which is **not** what I want. I want to have full root privileges.

Acetoneiso seems to work, thanks.

---

### Post by Rubi1200 on 2010-11-24
The Ubuntu model of security is designed to protect your system.

Using sudo to elevate privileges for administrative tasks ensures the stability and security of your installation.

---

### Post by blacktrance on 2010-11-24
If it is at all possible to do, I want to know how to do it. Please don't coddle me.

---

### Post by QLee on 2010-11-24
[QUOTE=blacktrance]Thanks, but these answers are insufficient.[/QUOTE]
Perhaps insufficient in your vision but what you propose is a very bad idea. The aspect of Windows that you dislike, is Windows trying to become more secure, something we have had from the beginning and something to be preserved. There are very good reasons why helping you do what you ask in the forum is banned.

If you manage to find out how and do it, and if you are connected to the Internet, when your system becomes compromised, there is the potential for your "owned" system to become an attack platform that could threaten us all. Spam at the least. Why would any of us want to help you! Any one who is knowledgeable enough to run as root securely doesn't have to ask the question. I'm sorry if you don't like my frankness, but that's my opinion. Just learn how to run sudo for the few times you need elevated rights.

---

### Post by blacktrance on 2010-11-24
**I** keep my machine secure. I leave my OS to do what I want. Personally, I don't like the direction in which Windows has been going lately. I don't run random junk, and my system isn't going to be compromised. I frequently need sudo, and it's an annoyance. Do you want me to go back to the (somewhat) less safe Windows?

So just tell me how to do it, and no more "security" nonsense.

---

### Post by Verbeck on 2010-11-24
it has been a basic security measure in linux for ages (to require root privileges for system wide changes), because everything outside your home folder is owned by the user 'root'. enabling the root account is the only way to remove the prompt completely.

so please read [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)[B]
we [/B]**cannot help you to make your self root**

if you're unhappy about that, then are some options
1. google it
2. switch to another linux distribution which enables the root account by default
3. switch to windows

sorry i couldn't be of much help

---

### Post by blacktrance on 2010-11-24
So enabling the root account and logging in as root is the only way? There's no way to give me, the administrator, root privileges?

---

### Post by karthick87 on 2010-11-24
For mounting iso images download the nautilus script from the attachment and move it to **~/.gnome2/nautilus-script**.Now when you right click iso image you will find two new options mount and unmount.Click mount to mount your iso image and if you want to unmount right click the same iso image and click unmount.

---

### Post by Verbeck on 2010-11-24
there 'could' be... but according to the forum policy, we're not allowed to discuss it

---

### Post by ibizatunes on 2010-11-24
in the terminal run the commands 
sudo -i
you can get become root for that session (I strongly recommend you dont run as root all the time) otherwise all the extra security you have by not using windows is pretty much gone!

---

### Post by blacktrance on 2010-11-24
Phew, found out how to do it and did it. As with most things Linux, it was more difficult than it needed to be. But now I'm root, no thanks to you guys.

---

### Post by philinux on 2010-11-24
The guys did just fine.

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

Thread closed.

---

