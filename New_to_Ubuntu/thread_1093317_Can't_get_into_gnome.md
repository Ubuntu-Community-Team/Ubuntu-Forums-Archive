---
title: "Can't get into gnome"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by bell2jd on 2009-03-11
Hey everyone.  I'll preface this by saying that I have not done a particularly exhaustive search of the forums, but a quick search of the forums did not yield results, so I felt it was safe to start a new thread. If there is already a post that would fix my problem, please point me to it, and I will be eternally grateful. Also, I just installed Intrepid about 2 weeks ago, after using Windows my whole life, so I don't know very much at all about linux.

 Now, on to it. When I boot my computer, I get my boot menu just fine. I start 8.10, it goes to the first loading bar, then the second, then it goes to a black screen just like normal, and then from there, it just sits forever. It won't run the Gnome login screen. When I boot in recovery mode, I can do anything on the recovery menu except resume normal boot. I haven't actually *done* anything on the recovery menu because I was afraid I might damage something, but it gives me the option to do them.

If i go to the root shell prompt, it gives me my normal bash prompt, except as root instead of my username, so I'm fairly sure that I did something to gnome somehow, and not anything more critical than that. I at least know that all of my data is still there, because I can list it at the root shell prompt.

Any help that the community can give me will be greatly appreciated, and if there is other info that I should give, let me know.  Thanks in advance.

---

### Post by taurus on 2009-03-11
At the GRUB menu, highlight the kernel you want to boot and hit e for edit.  Then, scroll to the end of the kernel entry and remove both **quiet splash**.  Hit b to boot.  Now, you would see the text scrolling on the screen, telling you what process is running/starting.  See what is the last process started before it hangs.

---

### Post by bell2jd on 2009-03-11
thanks for the quick reply. 

when I go to the edit screen for a regular boot (not recovery mode) I can remove **quiet**, but there is no **splash** presumably that is not a problem, since you're telling me to get rid of it anyway. once I remove **quiet**, then boot, however, nothing changes. I get the same progress bars, and then the black screen. I understand what I should be seeing, but it doesn't come up. Aany other ways to get the same information?

---

### Post by taurus on 2009-03-11
Boot into recovery mode and post your /boot/grub/menu.lst.

```
cat /boot/grub/menu.lst
```
p.s.  You only have to post the first entry (title) since that is the one you use to boot your machine.

---

### Post by mhgsys on 2009-03-11
Does it really hang?

Have you tried getting in console by cntl+alt+f1 (f2 f3 et)
??

---

### Post by bell2jd on 2009-03-11
oh... i see what you meant. I was deleting the wrong quiet. There is quiet and splash.

When I did that, it displayed all the processes as they were starting, but it didn't get stuck anywhere. It just went through the whole thing, then took me right to the same black screen. Apparently, the problem is not happening when it boots, but after it finishes booting.

Oh, I just remembered some other stuff I probably should have put in the first post. Ooops.

1. The first time this happened was when I was restarting after I had just updated. Since then, it hasn't worked right.

2. A few days into having Linux I was reading Kier Thomas's Ubuntu kung Fu, and I didn't do one of the tips right, (it was setting a program to run with a keystroke combination) so I followed the instructions to fix it (delete the folders that contained the gnome settings). when I restarted, everything worked fine again, it just reset all of my gnome settings. This problem didn't start until several days later, so I don't think it's related, but it's probably worth mentioning.

---

### Post by bell2jd on 2009-03-11
> **mhgsys said:**
> Does it really hang?

Have you tried getting in console by cntl+alt+f1 (f2 f3 et)
??
I had tried opening a virtual console, and it wouldn't open.

---

### Post by mhgsys on 2009-03-11
Try starting in safe-graphics mode. press F4 at the menu and select safe-graphics mode

---

### Post by bell2jd on 2009-03-11
at the GRUB menu? because nothing happened there.

Also, after I have given it some more thought, I came up with what might be another solution, although an extreme one, and one I would like to avoid if possible. See, the only reason I didn't just reinstall Intrepid is because I have 30 GB of music that is not currently backed up anywhere. If I could back up that music, I would have no reason not to just reinstall. Like I said, drastic, but it should work. So, my questions are, 1. can you mount an external HD from the root shell in recovery mode? 1a.How would I do that? 2. how would I copy the music files onto it at the command line?

Thanks for the help from you two so far , by the way.

---

### Post by mhgsys on 2009-03-11
srry, only works in live cd.

try starting in recovery mode.

---

### Post by bell2jd on 2009-03-11
Recovery mode works, but I can't boot to the desktop with it, I get the same problem. I can do all the other things on the recovery menu though.

---

### Post by mhgsys on 2009-03-11
cool,

to get back on your question:
you can mount an hd in a recovery console to backup your data

try: mkdir /media/disk
(this will create a directory called disk)

then sudo mount /dev/sda (disk number) /media/disk

---

### Post by mhgsys on 2009-03-11
and now your in recovery mode: 
try 
sudo dpkg-reconfigure xserver-xorg

and try to restore X.
You can always edit /etc/X11/xorg.conf if any changes are needed.
and restart X with /etc/init.d/gdm restart

---

### Post by bell2jd on 2009-03-11
success.
dpkg-reconfigure xserver-xorg worked, and my computer is running fine again. thanks a lot.

---

