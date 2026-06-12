---
title: "Network Problems - Permissions"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by Ingla on 2007-06-17
Hello.

I'm trying to set up file transfer between two Linux machines. Computer 1 is running Ubuntu Dapper, and Computer 2 is running Xubuntu Edgy . I have never set up a Linux to Linux network, although I have working networks from Windows to Windows and from Linux to Windows (don't ask ... I have a bunch of hard drives with various OS's). Linux to Linux is proving to be a monster.

When I'm on Computer 1, which is generally where I want to be. I've been successful in bring over a file from Computer 2. The other direction doesn't work ... access denied (unfortunately I primarily need to transfer from Computer 1 to Computer 2).

Thinking that. possibly, I could succeed in bringing a file from Computer 1, while sitting on Computer 2, as I had the other way around, I proceeded to try. 

First problem was Xubuntu (Xfce) doesn't show Network Servers AT ALL. So, I followed the instruction at:

[http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu](http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu)

Unfortunately, I still can't do anything. Here's a list of issues I think I've identified.

1. On Computer 1, the shared folder is set to SMB while, on Computer 2 it is using NFS. The GUI control in Xfce refuses to change to SMB. It simply will not save the configuration and I don't know how to change that in the command line. SAMBA is installed and user account activated on both machines, as far as I can tell from Terminal output.

This has not prevented file transfers by pulling files from Computer 2 while sitting on Computer 1  ... as mentioned.

2. While working on Computer 2 and trying to pull over a file from Computer 1, I get permission denied notices.
The same thing happens when I try to send from Computer 1 to Computer 2. I think the problem is permissions for the shared folder on Computer 2.

The folder is simply /Network. It belongs to my user and my user group. Permissions for my user are read/write. For the group and others it is read only.

However, I cannot change the permissions. When I try chmod as my user, I get opreation not allowed. If I try as sudo or as root, I get cannot chmod permission denied. I haven't been using Linux so long that the phrase, "I've never seen anything like this" could be terribly meaningful, but how is it that NOBODY ... not the user, sudo or even root, can change permissions??!!??

Trying to change permissions in the GUI doesn't work either, even though I own the directory.

On Computer 1, the shared folder shows ownership "unknown" with read only privileges for everyone, but it still works.

Being totally ignorant in the Linux networking department, I can't say what the problem is, but it seems logical that if I can't give others (me, on my other computer) permission to write to the shared directory, it might be kind of hard to bring over a file.

Also, it seems that chmod should work on any Linux box, regardless of distro.

Can anyone help me figure out what I'm doing wrong?

---

### Post by scrooge_74 on 2007-06-17
Are you using NFS to share drives?  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#NFS_Server)

You probably will have to make a directory with permissions so you can move files around from one PC to the other, and then you move those files to the place you want them to finally be.

You can also make changes in the other machine by using ssh, you log into the other computer as the user you need to change permissions and then make the corrections you need.

---

