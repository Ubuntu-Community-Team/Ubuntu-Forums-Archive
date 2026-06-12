---
title: "ntfs-config error"
date: 2014-06-17
forum: Networking &amp; Wireless
---

### Post by ken0069 on 2014-06-17
Installed ntfs-config on this new install of 14.04 and whenever I try to run it from the GUI I get this error?  So I did a "reinstallation" and still got the same error?

>    	 	 	 	   No authentication proram founds
 ntfs-config need to be run as root, but I can't find a graphical authentication program.
 You should install gksu or kdesu.
 Alternately, you can run ntfs-config from the terminal su or sudo.

I am able to run it from terminal but want to know why it won't run from the GUI?

Thanks,

Ken

---

### Post by yancek on 2014-06-17
Have you tried the suggestion in the error message?

> You should install gksu or kdesu.

---

### Post by Bucky Ball on 2014-06-17
You also need ntfs-3g installed and then you need to:

```
gksudo ntfs-config
```

... but you shouldn't need to run it from a terminal. It should be in your Settings menu as 'NTFS Configuration Tool' or something like it.

---

### Post by ken0069 on 2014-06-18
FYI, when I say GUI that means (Graphic User Interface) and that I've gone to System>Administration>NTFS Configuration Tool to try to open it.

I've got two computers that are very near the same and both are running Ubuntu 14.04.  The other one has NTFS-Config installed and it works fine from the GUI, ie, System>Administration>NTFS Configuration Tool?  No errors.  This one though gives me this error every time I try to use it that way.  

And as I said above I am able to run it from terminal using sudo ntfs-config as the command.

RE: gksudo?  I've been using Ubuntu for a few years (since v9.04) and I've never used anything but sudo in the past, so this begs the question of why is gksudo or kdesu needed now?  Isn't that used in Fedora or Suse?

Thanks

Ken

---

### Post by Bucky Ball on 2014-06-18
Should always use gksudo to open a GUI as root. 

> You should never use sudo to start graphical apps as root, because some files from your home directory may become owned by root.

From here:

[http://linuxg.net/sudo-vs-gksudo-what-are-sudo-and-gksudo-and-when-to-use-them/](http://linuxg.net/sudo-vs-gksudo-what-are-sudo-and-gksudo-and-when-to-use-them/)

There are very good reasons to use gksudo rather than sudo. No, it is not exclusively a Fedora or Suse thing. It is a Linux thing.

We learn something every day ... ;)

---

### Post by ken0069 on 2014-06-19
Thanks for the info but I've got even more problems with samba, ie, it's installed but can't open it via >System>Administrator>Samba.  Click on that and nothing happens, not even an error message??  Can't open it in terminal either?  I was able to copy the smb conf file from my other computer then edit it and get my Windows drives to show up on my network though but neither Samba nor ntfs config are working like they are suppose to.  

And it seems it may be an issue like you described in your last post, ie, root may have taken over some files and I'm not able to open them.  

On another note, I loaded Mint 17 on a spare IDE drive today and I'm thinking about going back to that OS since the Mate desktop seems to work well and it's more stable now than when I left it a few years ago.  Everything is working OK with Mint so far and I may just go ahead and clone it to this SSD with Ubuntu I'm having problems with as I'm getting tired of fooling with it.  

Thanks for your help,

Ken

---

### Post by Bucky Ball on 2014-06-19
Please post a new thread regarding your Samba woes. They have nothing to do with the title or topic of this thread and it will only confuse things. If we stick to and can resolve the NTFS-config issue then perhaps Samba will fix itself. Thanks.

Be aware that Mint is not supported in the main support forums here.

---

### Post by ken0069 on 2014-06-20
Samba and ntfs-config problems are no more!  I spent the better part of 3 days this week fooling with that thing so today I finally got p&%$@# enough that I cloned mint17 over it and moved on.  I actually got a chance to watch some baseball today.

Re: Mint Support, from what I remember a few years back, there's a pretty good support forum for Mint so all is not lost.  After all, once everything is configured and working correctly I probably won't need any help.  I'm not one to mess around with Linux unless something is wrong.  

Ennywho, thanks for your help!! :wink: 

Ken

PS, I do still have two systems with Ubuntu on them.

---

### Post by Bucky Ball on 2014-06-20
All good. Please mark thread as solved to help others (Thread Tools, top right of page). Thanks and good luck.

PS: Yes, Mint has an active community and forum.

---

