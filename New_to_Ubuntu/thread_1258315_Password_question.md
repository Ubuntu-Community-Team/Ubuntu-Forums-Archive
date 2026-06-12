---
title: "Password question"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by louval on 2009-09-04
[LEFT]I have Ubuntu 9.04 installed. When I look at the File System in the File Browser I see that at least two of the folders have a symbol with an X in it. If I try to open it I am told that I do not have permission to access the folder. However, I am the only user on the machine and would think that I would be the Administrator on it as well. 

Can anyone help me with figuring out why I cannot access the folders and what to do so that I can access them.

Thanks
[/LEFT]

---

### Post by |Porsche on 2009-09-04
Do you have root privileges?

If so type

```
sudo nautilus
```

You should be able to access those folders with that session of nautilus.

---

### Post by gordintoronto on 2009-09-04
> **louval said:**
> [LEFT]I have Ubuntu 9.04 installed. When I look at the File System in the File Browser I see that at least two of the folders have a symbol with an X in it. If I try to open it I am told that I do not have permission to access the folder. However, I am the only user on the machine and would think that I would be the Administrator on it as well. 

Can anyone help me with figuring out why I cannot access the folders and what to do so that I can access them.

Thanks
[/LEFT]

In Linux, it's called "root," and the sole user does not have root privileges.  This means when your browser's security is overcome by a rogue site, that site can not quietly install malware.  Instead, it must ask you for the root password, which should make you suspicious.

---

### Post by Vrekk on 2009-09-04
If there are in your home directoy you can (re)gain ownership of the files with ```
sudo chown -R *username:username* *folderhere*
```

---

### Post by Paqman on 2009-09-04
> **louval said:**
> 
Can anyone help me with figuring out why I cannot access the folders and what to do so that I can access them.


Those are system folders, so you don't really need to access them. Part of the reason Linux is more secure than some other OSes is that we have a built-in system of permissions. Every file has a set of rules that govern who can read, modify or run it.

By default you have permission to do anything to files within your home folder. Everything else if off limits. You CAN take on raised privileges if you need them by giving the system your password, but this should only be done when it's actually required.

---

### Post by mikewhatever on 2009-09-04
Do yourself a favor, don't follow the suggestions in post #2, #4. In case you absolutely need to access system folders :confused:, use **gksudo nautilus**.

---

### Post by louval on 2009-09-04
Thanks to all. I tried using the Chown command but the response to that was permission denied. I may not know what I am doing but I got no where with a Nautilus session.

Based on what GordinToronto said about the Root  directory I'll won't try. The other one is lost+found. Is that something I should have access to?

Thanks again.

---

### Post by |Porsche on 2009-09-04
> **mikewhatever said:**
> Do yourself a favor, don't follow the suggestions in post #2, #4. In case you absolutely need to access system folders :confused:, use **gksudo nautilus**.

How is that different?

---

### Post by Ms_Angel_D on 2009-09-04
As an afterthought here's some useful info to helping you understand the linux file system

[http://www.watchingthenet.com/ubuntu-video-guide-for-windows-users-understanding-the-linux-file-system-hierarchy.html](http://www.watchingthenet.com/ubuntu-video-guide-for-windows-users-understanding-the-linux-file-system-hierarchy.html)

---

### Post by louval on 2009-09-04
Should I have access to /home/lost+found?

When I try to go there I get permission denied?

---

### Post by halitech on 2009-09-04
> **louval said:**
> [LEFT]I have Ubuntu 9.04 installed. When I look at the File System in the File Browser I see that at least two of the folders have a symbol with an X in it. If I try to open it I am told that I do not have permission to access the folder. However, I am the only user on the machine and would think that I would be the Administrator on it as well. 

Can anyone help me with figuring out why I cannot access the folders and what to do so that I can access them.

Thanks
[/LEFT]

What are the folders in question that you are not able to access?

> **|Porsche said:**
> Do you have root privileges?

If so type

```
sudo nautilus
```

You should be able to access those folders with that session of nautilus.

> **mikewhatever said:**
> Do yourself a favor, don't follow the suggestions in post #2, #4. In case you absolutely need to access system folders :confused:, use **gksudo nautilus**.

> **|Porsche said:**
> How is that different?

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by halitech on 2009-09-04
> **louval said:**
> Should I have access to /home/lost+found?

When I try to go there I get permission denied?

no you should not

---

### Post by louval on 2009-09-04
Thanks I'll take a look at [http://www.watchingthenet.com/ubuntu...hierarchy.html]("http://www.watchingthenet.com/ubuntu-video-guide-for-windows-users-understanding-the-linux-file-system-hierarchy.html").

---

### Post by mikewhatever on 2009-09-04
> **louval said:**
> Should I have access to /home/lost+found?

When I try to go there I get permission denied?

Is it just curiosity or do you really think there is something there for you?

---

### Post by louval on 2009-09-04
Ok, thanks to all. It's very much appreciated.

Lou

---

### Post by louval on 2009-09-04
> **mikewhatever said:**
> Is it just curiosity or do you really think there is something there for you?

Curiosity, wanted to see what is in there. I am used to be able to poke around in any folder in Windows, so figured that would be the case here.

---

### Post by Paqman on 2009-09-04
> **|Porsche said:**
> How is that different?

Sudo is only used for command line stuff. For graphical apps you should use:

Gnome/XFCE either one of:
```
gksu
```
```
gksudo
```

KDE:
```
kdesu
```

---

### Post by Paqman on 2009-09-04
> **louval said:**
> Should I have access to /home/lost+found?


Nope, that's a special folder created by the filesystem for putting broken bits of files into. All going well, it won't even get used (and no, that doesn't mean you can delete it!)

---

### Post by Windows Nerd on 2009-09-04
> **louval said:**
> [LEFT]I have Ubuntu 9.04 installed. When I look at the File System in the File Browser I see that at least two of the folders have a symbol with an X in it. If I try to open it I am told that I do not have permission to access the folder. However, I am the only user on the machine and would think that I would be the Administrator on it as well. 

Can anyone help me with figuring out why I cannot access the folders and what to do so that I can access them.

Thanks
[/LEFT]


I take it you come from a Windows background. On Linux, there are 3 different types of users: root users, administrators, and normal users. Root is also called the super-user, he can do anything and everything, no questions asked. An Administrator is similar to a super-user in the respect that they can do (almost) everything that root can, but they must elevate their privileges by prefacing commands run with "sudo" and entering in their password. Administrators can also run programs with root privileges by starting them through terminal and prefacing the command with sudo, if it is a command line program, or gksudo if it a GUI based program. A normal user cannot do much on a Linux-based system, except for basic, everyday functions such as browsing the web. 

When you first install Ubuntu, or any Linux distro, you will commonly set up two accounts: an administrator account that you use on a daily basis, and a super-user, root. Ubuntu is an exception though, for security reasons, the Root account is disabled by default, and you do not set one up on install. This is because while on root, you can do _anything_. It is very easy to delete your whole filesystem by accident. This is why there are Administrator accounts that can elevate thier privlidges temporairily, which makes it more difficult to do things like delete your filesystem by accident. Whenever you are asked for a password for your administator account, you know it is somehting that could be potentially dangerous. Not being logged in as root all the time also helps when, like other users have mentioned on this thread, you run into a dodgy site, which attempts to install malware on your computer in the background, but must ask for your root password to do this. When you are asked for a root password just randomly, you know something is up. 

If you wish to log-in as root, (which I strongly do not recommend), you mist find out how to do so on your own, because discussing this is against forum policy.

You cannot acess these folders because they require root privlidges to view and edit (similar to the Read and Write permissions for folders in Windows.) If you wish to access them, run in terminal:

```
gksudo nautilus
```Note: replace "nautilus" with whatever file browser you use. In Ubuntu, this is the default file manager.

The files in those folders with X's on them are important system files, and require root permission to view for a reason. So be careful poking around those folders!

For more information, you can go [here]("http://www.freesoftwaremagazine.com/articles/users_in_ubuntu"). This provides some basic information on users similar to what I just covered, as well as how to add a basic user.

*Phew* that was a lot to type. I know as a new user, things can be confusing at first, but with some use of the system everyday, you will be a power-user in no time! I hope it helps, and you have a good time using Ubuntu! 

Scott

---

### Post by louval on 2009-09-04
> **Windows Nerd said:**
> I take it you come from a Windows background. 

*Phew* that was a lot to type. I know as a new user, things can be confusing at first, but with some use of the system everyday, you will be a power-user in no time! I hope it helps, and you have a good time using Ubuntu! 

Scott


Yes I come from a Windows background (as fairly new (but not young) programmer in VB6 and some C# by day). I almost always use Ubunto when not at work and definitely learning it slowly (did I say not young).

Thanks so much for all the information and help from everyone.

---

### Post by |Porsche on 2009-09-05
> **Paqman said:**
> Sudo is only used for command line stuff. For graphical apps you should use:

Gnome/XFCE either one of:
```
gksu
```
```
gksudo
```

KDE:
```
kdesu
```

Thanks! I read the man page on gksudo and it will actually decide for you between su or sudo. I have never used gksudo and never had a problem. Good to know!

---

