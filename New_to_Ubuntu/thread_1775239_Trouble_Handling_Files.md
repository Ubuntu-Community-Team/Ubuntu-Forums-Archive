---
title: "Trouble Handling Files"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by davec51 on 2011-06-04
Though I have been using Ubuntu for awhile, I still have not solved one problem -- how to add, delete and change files on a network. I keep getting the message that I do not have permission. When I try to log in as root, I keep getting told that I don't have the right password. I have created several users with administrative privileges, but that doesn't seem to make any difference.
I hope someone can give me simple instructions on how to create a root password or a user with true root privileges.
I can become root with "sudo su" in a terminal, but terminals are an awkward mystery to me.

---

### Post by corncob on 2011-06-04
Hit ALT F2.  When the command line opens type in
```
gksudo nautilus
```
This should open the file browser as root.

---

### Post by hakermania on 2011-06-04
davec51, you maybe dont know the actual difference.
If in a terminal you give
```
su
```
then it will ask for the root passwd, which isn't set at the beginning, and so you cannot log in as root using this way. The right way to do it is to give
```
sudo su
```
and type your login passwd. Then you give the command
```
passwd
```
to set the root passwd, the one that will be asked by the 'su' command, this means the normal root passwd.

So, I don't know a lot about why you get this network error message, but I hope you understood something about root and its passwds

---

### Post by davec51 on 2011-06-04
Thanks, Hakenman and Corncob, for you quick responses.
"gksudo nautilus" does give me control over the files on this HD, but I get the message that "Nautilus doesn't handle network files" when I try more.
The setting of the root password with "passwd" in sudo su worked. Now I have the ability to get into true root and do my dirty work. 
Thanks

---

### Post by critin on 2011-06-08
I've been searching for how to set a root password for months and finally found this.  It doesn't say if I make a new password and type it in the terminal after the command 'passwd' though.  Is the root password only stored in the terminal?  

I wish it was included at installation like the owner name and password are.  Or more convenient info.  sudo/su are mysteries to search for too.  They don't seem to be included in the 'Getting Started' pages at all.

Thanks for helping me understand.

---

### Post by wildmanne39 on 2011-06-08
> **critin said:**
> I've been searching for how to set a root password for months and finally found this.  It doesn't say if I make a new password and type it in the terminal after the command 'passwd' though.  Is the root password only stored in the terminal?  

I wish it was included at installation like the owner name and password are.  Or more convenient info.  sudo/su are mysteries to search for too.  They don't seem to be included in the 'Getting Started' pages at all.

Thanks for helping me understand.
Hi, these should help.
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by critin on 2011-06-08
Thank you!  I'll bookmark these to study.

---

### Post by wildmanne39 on 2011-06-09
> **critin said:**
> Thank you!  I'll bookmark these to study.
Hi, your welcome. If your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

