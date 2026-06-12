---
title: "$Home/.dmrc and /.ICEauthority errors = endless logon loop"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2009-05-13
When I boot up, I receive a $Home/.dmrc error (full error message copied below), which, after hitting “ok,” and entering name/password (it was previously set to log in automatically), it returns an /.ICEauthority error (below) without building a desktop. After hitting “ok,” the screen blinks, and the .dmrc error reappears (along with a prompt for username). 

As it stands, it cycles between messages, never getting to a desktop — though I do have the boot options in the lower left corner. 

Possible sources of the problem: I started getting the .dmrc error first, but it let me boot to a desktop. I had been monkeying with permissions. While logged in, I’d copied a few hundred gig from a NAS to a Samba-shared directory, and was working with those files via other machines. Receiving permissions errors on those external machines, I logged in, browsed via Nautilus to their directory, and manually changed permissions via right clicking. Shortly after doing this I started receiving the .dmrc error at boot-up.  

Instead of smartly retracing/undoing the above, I found advice (here and elsewhere) that basically said to: 
sudo chmod 644 /home/Rhythmdvl/.dmrc
sudo chown Rhythmdvl /home/Rhythmdvl/.dmrc
sudo chmod -R 700 /home/Rhythmdvl
sudo chown -R Rhythmdvl /home/Rhythmdvl

It was after doing the above that I started receiving the .ICEauthority error, and the inability to boot to a desktop.

If it makes a difference to finding my way out of the woods, there is something working underneath it all — though I’m not at a desktop on the machine itself, from other machines in the network I can see/copy files in the Samba-shared directory. In addition, Webmin seems to log in and work fine. 

Any suggestions? 

Thanks, 

Rhythm 

The full text of the error messages:
> User’s $Home/.dmrc file is being ignored. This prevents the default session and language from being saved.
File should be owned by user and have 644 permissions. Users’ $home directory must be owned by user and not writable by other users.
> The Gnome session manager was unable to lock the file /home/Rhythmdvl/.ICEauthority. Please report this as a Gnome bug.
Sometimes this error may occur if the file’s directory is unwritable. You could try logging in via the failsafe session and ensuring that it is.

---

### Post by MontelEdwards on 2009-05-14
Well are login with root, or failsafe terminal?

---

### Post by drs305 on 2009-05-14
Your second chmod command could be overwriting your first. Try the commands in the order presented in this link (Go right to Step 3 if you don't want the background):
[http://ubuntuforums.org/showthread.php?p=6161267]("http://ubuntuforums.org/showthread.php?p=6161267")

or the wiki it spawned:
[https://help.ubuntu.com/community/dmrcErrors]("https://help.ubuntu.com/community/dmrcErrors#preview")

---

### Post by Rhythmdvl on 2009-05-15
Wow, thanks -- a great tutorial, thanks! The /.ICEauthority error never came back after fixing the .dmrc, even after multiple reboots to test (of course, we'll see what the morning brings :))

Oh, for other beginners out there:
When I got to the username prompt (i.e., between cycles), I used the menu in the lower left corner of the screen to change session. I chose Failsafe _T_erminal (Failsafe _G_nome didn't work). I then re-entered my username and password, and a small terminal window opened up in the lower right. It was identical to the normal terminal window I run from the desktop, but it doesn't have the menu bars (i.e., close, scroll, etc.) around it. From there I was able to enter the tutorial's command. Again, this is for those of us for whom this was the first time logging in to the Failsafe terminal -- I thought to add it here just to be pedantically complete. If I've made any errors, I hope someone will correct me. 

Again, thanks!


(Pardon my idiocy, but I could have swore there was a 'thanks' button and a way to mark threads as solved. Is that a different board? Am I blind?)

---

### Post by drs305 on 2009-05-15
> **Rhythmdvl said:**
> 
(Pardon my idiocy, but I could have swore there was a 'thanks' button and a way to mark threads as solved. Is that a different board? Am I blind?)

The 'Thanks' and 'Solved' buttons were moved during server upgrades. I believe the preferred method now is to add a 'Solved' tag. There is a link at the bottom right of the entire thread called "Edit tags". You can click on that and add "Solved" to the tag(s). 

In fact, anyone can add it, but I'll leave it for you if you wish to add the 'Solved' tag to this post.

P.S. The next time I log out I'll go through the steps you took to get to the terminal and incorporate them into the guides so other users will gain from your experience. Thanks for sharing that.

---

### Post by t0p on 2009-05-15
**Rhythmdvl:**  From your post I can see that you know this.  But the title of this thread still needs addressing, I think, even if it's just to educate the newbies.

So here goes.  With linux and other *nix-based Oses, you would not get an "endless **logon** loop".  You log *into* linux.  You might get an "endless log*in* loop".

</2 cents' worth>

---

### Post by Rhythmdvl on 2009-05-15
Tags 'n title updated! 

Thanks for the technical correction **t0p**. To be honest, until now I'd been using log in/login and log on/logon fairly synonymously without realizing there was a strong distinction. 

With attention, I can see how the two-word form is a verb while the single word suggests a noun representative of the credentials, but I'm not sure I understand the technical view of how in/on differ. Other than traditional usage (i.e., idiomatic), how do they differ contextually?

---

