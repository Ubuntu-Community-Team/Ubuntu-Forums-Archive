---
title: "Sharing from Edgy to OS X 10.4 puzzle -- multi-OS environment"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by Irixmark on 2007-01-24
I have Edgy and W2K installed as a dual boot system and want to share the home directory and the printer on the Ubuntu box using Samba, but I cannot get OS X to connect to it. After spending hours on it, I think it's an Ubuntu issue.

I get the following results:

1. A Windows XP laptop can read and write the home folder on Ubuntu and print.
My Powerbook running OS X 10.4 can do neither of the two. Both GUI and samba terminal complain that the password or username is not correct.

So, Samba is running fine on the Ubuntu server. The user is set up properly, otherwise the Windows laptop couldn't connect.

2. Booting the server into W2K, OS X and the Windows laptop can connect, print, and read and write.

So it's not a hardware problem.

3. [COLOR="Red"]Desperately[/COLOR], I install Suse 10.1 instead of Ubuntu and set up Samba. I don't like Suse. :-| 

Now OS X connects fine, reads and writes the home folder, and prints as well. It's not the old "Tiger broke my samba" issue that Mac users have complained about.

Reinstalling Ubuntu, I still have the same problem. Password encryption is also on in my smb.conf file. So I suspect that there's something about Samba in Ubuntu (at least Edgy) that doesn't work with OS X Tiger. 

There are a dozen or so threads out there referring to similar OS X to Ubuntu problems, but none of them have a working solution.

Does anybody have an idea? Or a suggestion for an alternative to SMB? :confused:

---

### Post by mrgrapefruit on 2007-01-24
you could be dangerous and get an NFS share going. Or AFP. Or FTP. Sorry for not being able to help with the samba issue, I've never used it, as I've only got macs and *nix machines

good luck

[EDIT:]for FTP style antics, [http://www.ubuntuforums.org/showthread.php?t=218630&highlight=zeroconf](http://www.ubuntuforums.org/showthread.php?t=218630&highlight=zeroconf) talks you through it

---

### Post by Irixmark on 2007-01-25
Good call, thanks. I've given up on SMB in OS X, but NFS turns out to be much faster anyway.

If anyone knows of a thread or site that explains how to configure the user/security for NFS with OS X... right now I've got it set up with all_squash, but I have no idea what that really means.

---

