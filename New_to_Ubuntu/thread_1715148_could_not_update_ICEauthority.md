---
title: "could not update ICEauthority"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by MRRangel on 2011-03-26
Hello,

Newbee here.  I get the above error when logging in.  How can I fix.  Also, I was able to change the boot order in grub to windows first (it was at the bottom of the list) but when I logged back into ubuntu it changed back to a default of the first line.  How do I set it in stone to boot into windows first?  Thanks

---

### Post by Arijit_Kundu on 2011-03-26
did you update the grub?

---

### Post by MRRangel on 2011-03-26
Hello,

By update the grub do you mean through the update manager?  I was able to get the it to boot from the last choice and it worked fine.  But once I chose the ubuntu it started to default from that line.  I was not able to run the update manager until today.  Everything is being updated as we speak, so that may help???  Thanks

---

### Post by oldfred on 2011-03-26
Did you do something to /home. I have this in my notes on moving /home.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name.
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)

---

