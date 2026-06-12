---
title: "Remote access"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by Joreus on 2011-08-13
Where to begin... I have no idea how to do this and it's probably WAY over my head technically speaking.

I'm currently running Ubuntu 10.04. I'm looking for a way for me to swap files between desktops at home. This computer is Lucid and the other is Windows 7.

What I'm looking for is the ability for me to interact (move files, install programs etc) with the Win 7 machine from my Lucid machine and vice versa.

Example: I'm writing a document on my machine. I need to go to the other room and want to send my document there and have it open and ready to be continued with.

Secondly, is there any way for me to have music playing on my Lucid machine and have it stream to the other computers in my home?

I know this is asking a lot and the technical details are probably staggering, but is it possible? If possible, how is it done? Are there any guides or tips you would recommend? Would it be easier if I were running 11.04 instead?

---

### Post by papibe on 2011-08-13
If you have Windows 7 Ultimate, I would recommend using NFS. You probably don't, so your best option is to use [Samba]("https://help.ubuntu.com/community/Samba") to share files.

The easiest way is to:
[INDENT]Right click on the folder you want to share.
Select Share Folder.
Install Samba (maybe called Windows network support, or SMB).
[/INDENT]
After that you'll have the option "Sharing Options" if you right click the folder. There you choose the name and the permitions (read write for all).

You can see more details and pics [here]("http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/").

After that you'll be able to browse your Ubuntu directory on your Windows machine.

Good Luck!

---

### Post by papibe on 2011-08-13
> **Joreus said:**
> Secondly, is there any way for me to have music playing on my Lucid machine and have it stream to the other computers in my home?
Yes, but it doesn't make much sense. Usually you stream media to devices that have limited playing capabilities (like game consoles for example). Since the other device is a computer, you just share the music folder, and then in the other machine you just open the file and play it.

Hope it helps,
Regards.

---

