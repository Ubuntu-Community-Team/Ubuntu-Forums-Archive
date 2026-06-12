---
title: "&quot;Unable to open session&quot; at login..."
date: 2011-06-10
forum: New to Ubuntu
---

### Post by Timbothecat on 2011-06-10
Hi Guys.
My son has Ubuntu 10.4 on his computer and when he tries to login he gets the message "Unable to open session" and then goes back to the login screen.
He recently had an issue where an update caused his computer to crash and then it couldn't find the init file to reboot, but this is different (obviously).
Is there something that I can do to fix this (like use a live cd to fix up files etc) or do I need to to a clean install? -which I'll do using 11.04- and just move on.
Also, when I use a live disc I can get to his folders, but I can't remove anything as the live disc doesn't have the correct permissions. Is there a way I can use the live disc to get his data off so that I can do the re-install if that's what's needed?
Thanks in advance for your help.
Have a good one,
Tim.

---

### Post by jtarin on 2011-06-10
To access the files using the Live CD I would suggest the [CHROOT method]("https://help.ubuntu.com/community/Grub2#ChRoot"). Skip steps 8,9 and 10. They are only for reinstalling grub.After you enter step 7 you should be able to access the files then.

---

### Post by jtarin on 2011-06-10
Your login problem might be overcome by adding a new user from the commandline and using that to login.[Look here for direction.]("http://nixcraft.com/getting-started-tutorials/3293-create-new-user-account-ubuntu-linux-command-line.html")

---

### Post by Timbothecat on 2011-06-10
> **jtarin said:**
> Your login problem might be overcome by adding a new user from the commandline and using that to login.[Look here for direction.]("http://nixcraft.com/getting-started-tutorials/3293-create-new-user-account-ubuntu-linux-command-line.html")
Hi jtarin, thanks for the replies.
I've managed to get all of the permissions stuff sorted out and I'm backing up the HDD as we speak. As for setting up a new user, I'm a little confused. Is there some way I can use that to fix the problem or is it a permanent solution?
At any rate, I think I'm just going to install 11.04 after I've got all of the data off it.
Thanks again for your help.
Tim.

---

