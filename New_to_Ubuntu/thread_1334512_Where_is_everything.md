---
title: "Where is everything?"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by Anybloodyid on 2009-11-22
Hi

I have the game JAG and want to add some new levels the instructions are to place them in 
**jag/data/levels/**.

But where do I find it?

Thanks

---

### Post by danill2008 on 2009-11-22
I presume you are using WINE? If so, goto your Home folder and press Ctrl + H. Then naviagte to .wine and continue forward to drive_c. After this you will be displayed with Program Files. Here you can goto jag/data/levels. Hope this is what you where searching for....

---

### Post by SuperSonic4 on 2009-11-22
```
sudo updatedb
locate jag/data
```

---

### Post by Anybloodyid on 2009-11-22
Danill
Thanks but you presumed wrong 

Supersonic
Thanks that found where it was,   is there somewhere that shows all these commands and what they do?

---

### Post by danill2008 on 2009-11-22
"Danill
Thanks but you presumed wrong"

Sorry, was not sure about jag (never played it before):)[ Here]("http://www.pixelbeat.org/cmdline.html") is a guide to some linux commands and if you want more, [here]("http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet") is. The last one is written by Jacob Peddicord, so credit goes to him;)[URL="http://fosswire.com/users/jacob/"]
[/URL]

---

### Post by Anybloodyid on 2009-11-22
Thanks for that will take a look at those.
I ave another problem when I try to move one file from my download folder to the JAG folder I get a message that reads
Error moving permission denied.
I right click on the folder> properties > permissions and it reads 
You are not the owner so you cannot change these permissions.
Bloody Cheek I am the owner!
How do I change the permissions >  owner user permissions create and delete files?

---

### Post by danill2008 on 2009-11-22
Navigate to the folder in terminal and type: "sudo chmod 777 xxxxxxxxx" where xxxxx is the location of the folder.

---

### Post by Anybloodyid on 2009-11-22
Thanks Danill Another terminal command for me to remember.

---

### Post by danill2008 on 2009-11-23
Your welcome;) [Here]("http://ss64.com/bash/chmod.html") is a link to more info on chmod

---

### Post by mbzn on 2009-11-23
Here is a book to read in your free time, it takes time to get through but is well worth it

[http://tldp.org/LDP/GNU-Linux-Tools-Summary/GNU-Linux-Tools-Summary.pdf](http://tldp.org/LDP/GNU-Linux-Tools-Summary/GNU-Linux-Tools-Summary.pdf)

---

### Post by 3rdalbum on 2009-11-23
*facepalm*

Anybloodyid, don't remember that command. Well... remember it, but don't use it like this.

Ubuntu's security system says that your normal user account is just a user account, it doesn't own the system. In order to modify anything outside your home directory, or do something system-wide, you need to elevate into the root account.

This is really easy. If you need to run a command as root, just put the word "sudo" in front of it. If you want to run a program as root, just put the word "gksudo" in front of it. For example:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
gksudo nautilus
```

Running "gksudo nautilus" is going to be the key for you here. It opens up a file browser as root, so you can copy the Jag files from your home directory to the system-wide location. The file browser runs as root, so anything you do or launch from this window will also be running as root. Everything else will still be your ordinary user account.

An even easier way of doing this is to install the "nautilus-gksu" package from Synaptic. The next time you log in, you will be able to right-click a file or folder and choose "Open as Administrator".

Don't change the permissions of root-owned folders just so you can copy files in - it just makes your system less secure and more prone to file corruption and breakage. Be safe - become root when you need to, and be the user account when you don't need to be root.

For more information, see the [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo") page.

---

