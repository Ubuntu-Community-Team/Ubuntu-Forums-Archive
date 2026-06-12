---
title: "Tried to install Ubuntu and now I'm stuck at a Grub prompt"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by esdf on 2010-04-14
I was considering switching from XP to Ubuntu. I put the Ubuntu cd in and followed the installation through, trying to set Ubuntu up on a separate partition so I can dual boot while testing both out. I left the computer while it was installing, came back and apparently the installation had failed for some unknown reason and it booted into the Ubuntu Live. 

When I restart the computer now, I get a grub prompt and can't boot into either Ubuntu or Windows. I've already spent countless hours trying to research my problem and figure out what went wrong, but got nowhere. I just tried an XP repair to get Ubuntu off the computer but after repairing XP it just goes back to the grub prompt on restart. What do I do next?

This was all the more frustrating because I wanted to switch from XP to Ubuntu for more ease of use, but it has only caused me a bigger headache than I've ever experienced with XP. 

Did I do something wrong or what? I'd still like to give Ubuntu another shot seeing all the praise it gets but I don't want to go through all this again. 

Thank you in advance for any advice or comments.

---

### Post by shuttleworthwannabe on 2010-04-14
I think your best bet is to repair the MBR using the XP disc, then retry installing Ubuntu. Couple of things to note:
1. Check your Live CD is not corrupted; if possible reburn at slow speed
2. Backup, backup, backup your data--and oh ya, backup again.
3. It takes about 20 min to install, so just grab a cupacofee and watch the installtion process; i have had this experience before, and it had to do with a badly burned CD.

Hope you come right.
S

---

### Post by elliotn on 2010-04-14
jst put a xp cd and go to cmd mode then type fix mbr. The ja grab a cup of coffee or a bottle of beer and watch the installation

---

### Post by esdf on 2010-04-14
Thanks for the replies, I'll try it right now.

---

### Post by philinux on 2010-04-14
its always best to check the md5sum of the iso and when you boot the live cd choose Check CD for defects

---

### Post by esdf on 2010-04-14
Thanks to the help here I got grub off my computer and XP works fine. I tried installing Ubuntu again, left the computer, and when I came back there was just the yellow Ubuntu wallpaper and nothing else. I had to push the button on the computer to get it to restart and then it booted back into XP. 

I did the error check on the Ubuntu cd, but no problems were found. When I run the partition manager on the cd it shows that both XP and Ubuntu are on the computer. I don't know how to get Ubuntu completely off, or how to get Ubuntu to work (which is what I'd like). It's just one frustration after another to install this. Any ideas on what to do now?

---

### Post by SBFree on 2010-04-14
If you CD is ok it may be worth to check your hardware. Try running MemTest over night, check for cooling problems, try a different HD or checks on the drive. Installs that hang are often hardware or power problems.

---

### Post by oldfred on 2010-04-15
Does the liveCD run without any issues. 

And why after the first failure did you not watch it to see if it crashes and gives some indication of why. 

If you are using manual install to reinstall to the existing partitions, it does not have to move any data, and the install is very quick.

---

### Post by esdf on 2010-04-15
I tried reinstalling to the existing partition but that's when I just got the frozen screen. What I'm thinking now is deleting the Ubuntu partition. But when I use the Ubuntu partition manager and delete the Ubuntu partition it gives me an error that there's no boot partition or something like that. What do I do about that?

---

