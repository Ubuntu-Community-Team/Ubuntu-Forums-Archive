---
title: "Wine - Security ExecutableBit"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Savio2010 on 2010-11-23
[SIZE=4]Hi Everybody,:D

I migrated from Windows to Ubuntu 10.10 a few weeks back and it didn't take me much time to learn it... There are so many applications and its FUN:P using it.

I installed many of my day to day applications with ease... I even installed wine '1.2.1-0ubuntu1 (wine)'... I needed it. All with the help of Ubuntu Software Center.

Now I am not able run any *.exe file it gives me a error

[COLOR=Red]The file '/media/D/MultiBootISOs-2.1.3.9.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.[/COLOR]

This is a security alert.
Now how to run this file?
What is the risk in installing wine? (Viruses, Worms, etc)
Is is necessary to install a AntiVirus because Wine is installed?

Help
Savio
[/SIZE]

---

### Post by blancoisgod on 2010-11-23
The risk is this:
Since most viruses target windows and their .exe files, you (could) get a virus.

If you trust the program, you will be fine. If you want to run this program, right click the .exe and hit properties. Once there, a window pops up then hit the tab labeled "permissions". On the bottom, you will se a check box for allowing the program to be executable. Make sure the box is checked, and exit.

And on a side note, ubuntu is way cooler than windows :)

---

### Post by SecretCode on 2010-11-23
See also this thread: [http://ubuntuforums.org/showthread.php?t=1441315](http://ubuntuforums.org/showthread.php?t=1441315)

---

### Post by Savio2010 on 2010-11-23
I can't enable the execute 'allow executing file as program'.... (The tick-mark disappears immediately)

The Permissions set like:
Owner access : Read and Write
Group            : None
Others           : None

I am not able to change any of these (even though I am the owner). Is there a alternate command line for this? If yes then please specify in detail because I am from a Windows background.

---

### Post by Savio2010 on 2010-11-26
I have got a alternative of this applications

Its better to run virtual box then wine

Thanks for all your help:D:D

---

