---
title: "Uninstalled false repositories"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by guillem_tell on 2011-03-18
Hello everybody.

I'm using Ubuntu 10.10 in a quite new computer. I was trying to install new ATI drivers and I do not know exactly how I lost my previous configuration. Trying to return to the previous configuration I uninstalled some repositories, but not the right ones.

I am able to see the GRUB menu and select which kernel I want to execute, but after that monitor turns always in safe mode.

What should I do?

Thank you very much for your attention.

---

### Post by andrewthomas on 2011-03-18
Uninstall the proprietary drivers.

---

### Post by guillem_tell on 2011-03-18
Thank you for your answer.

The problem is that I do not know how to uninstall the drivers because the monitor goes to sleep, after the GRUB selection the monitor enters automatically in power safe mode.

By the way, I'll be able to be i front of the computer next monday, not right now.

---

### Post by guillem_tell on 2011-03-21
I'm still having the problem.
 
I should say that I uninstalled all graphics drivers, I think.
Can I restore the default drivers drom the cd or by command lines?
 
I would appreciate any help.
Thank you!

---

### Post by Arijit_Kundu on 2011-03-21
Here are some steps that might help you:

1. Reboot.
2. When the 'countdown' appears, press escape to enter the GRUB boot menu.
3. Select 'Recovery Mode' and press enter.

You will end up at a terminal prompt.

4. Type "dpkg-reconfigure -phigh xserver-xorg". You will see a series of questions about your display. Answer them conservatively! When you get to the "driver" question, select "nv", not "nvidia", just to be safe.

5. Type "reboot". This time, don't use recovery mode.

With any luck, you'll get to a graphical login this way. Let me know!


(from [here]("https://answers.launchpad.net/ubuntu/+question/15627"))

---

### Post by guillem_tell on 2011-03-22
Thank you very much, but finally I opted to reinstall everything again... not a constructive way, but I need to work further with the computer...
 
Anyways, Thank you!!

---

