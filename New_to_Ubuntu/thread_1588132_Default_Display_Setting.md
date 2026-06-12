---
title: "Default Display Setting"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by SEECo on 2010-10-04
I was running my ubuntu perfectly there was a very good theme, icon set etc. I wanted to install a splash screen in ubuntu lucid but then i realised it cant be. Then i tried to use startup-manager for this. And when i left that over there and went for0 some work my brother messed up withe the start up disk creator. And now when i try to reboot my computer it gave a strange screen instead of boot screen. Can anyone tell me to how to set the display things on the default.

---

### Post by jtarin on 2010-10-04
> **SEECo said:**
> And now when i try to reboot my computer it gave a strange screen instead of boot screen. Can anyone tell me to how to set the display things on the default.Can you describe this "strange screen"?

---

### Post by SEECo on 2010-10-09
How could i discribe it just there is a clue. When i press Ctrl+Alt+F1 it appears the same. If you know any thing just tell i will soon give you a pic of it

---

### Post by SEECo on 2010-10-11
Hey jtarin thanx for waiting here is the pic look at the top of my LCD,TFT. Hurry reply

---

### Post by jtarin on 2010-10-11
You could try to boot with the Live CD to correct.

---

### Post by radiosgalore on 2010-10-11
> **jtarin said:**
> You could try to boot with the Live CD to correct.

how would that work? you'd have to find out what was screwed with exactly then use command lines to correct. Tried sorting my own issue out via live CD and the file i need to remove - won't

---

### Post by jtarin on 2010-10-11
> **radiosgalore said:**
> how would that work? you'd have to find out what was screwed with exactly then use command lines to correct. Tried sorting my own issue out via live CD and the file i need to remove - won't
If you can boot into GRUB2 normally then use the "Recovery Mode" kernel to boot with and reconfigure your display.

---

### Post by SEECo on 2010-10-12
The grub2 screen doesn't appears because i do not have dual boot

---

### Post by jtarin on 2010-10-12
> **SEECo said:**
> The grub2 screen doesn't appears because i do not have dual bootTry pressing the "Esc" key at boot.

---

### Post by SEECo on 2010-10-17
If my computer starts when should I press the Esc button.

---

### Post by JKyleOKC on 2010-10-17
This is due to a bug in the start-up manager file; it inserts a command into one of grub2's files that puts the video into a crazy mode.

Several of us have reported the problem, which has been around for a couple of years (at least since version 9.04) but it's not getting any priority from the developers.

The bad command begins with "VGA=" followed by three decimal digits that may vary from one system to the next. At the moment I don't remember the bug number or exactly which file is involved but will look them up and add another message to this thread. To fix it all you have to do is remove that command from the file and then all will be well again; no need to re-install or anything so drastic!

---

### Post by JKyleOKC on 2010-10-17
The bug report is at [https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/495436](https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/495436) and tells the whole story.

Here's the cure, from my entry in the bug report: In my case the added code was VGA=771 and the effect was to convert the display font to unreadable garbage, not only for the text displayed during boot but for all virtual terminals using text mode. However the GUI on tty7 operated normally. Manually removing the VGA=771 from /etc/default/grub cured the problem.

To get to "tty7" just do your login as if you can read the screen, which should bring up the normal GUI. You can then open a terminal window and first make a backup by typing "cp /etc/default/grub grub.bak" in case anything goes wrong, then use "sudo nano /etc/default/grub" to open a text editor. Find the offending line, delete it, and save the file, next run "sudo update-grub" to rebuild grub's files, and restart. That ought to be all it takes!

---

### Post by SEECo on 2010-10-20
According to it is changed my vga but it still remains the same

---

### Post by JKyleOKC on 2010-10-20
After totally removing the "VGA=" and accompanying number, you have to run "sudo update-grub" and then restart the system before the change will take effect.

If the problem persists after that I have no idea what else to try...

---

