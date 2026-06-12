---
title: "I need command line help, please!"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by cousinlucky on 2009-03-19
My Ubuntu 8.04 os keeps informing me that I have duplicate files within
/var/lib/apt/lists and I see that I do. My bigger problem is I do not know how to access the file in the terminal, as root, so that I can eliminate one of the duplicate files. Can someone, please, help me with this? Thanks!

---

### Post by batharoy on 2009-03-19
[COLOR="Red"]**Don't use this command, read below to find out why.**[/COLOR]
```
sudo nautilus
```
Opens the file browser with root status.

---

### Post by sahabcse on 2009-03-19
Hi

Type

#sudo gedit /var/lib/apt/lists

Then remove the entry and save

---

### Post by aeiah on 2009-03-19
sudo essentially stands for 'super user do'. it gives you temporary admin rights (or root privilage) to make system changes like the one you need to. if you open the file manager (nautilus) with sudo you can browse around and make changes as normal or you could use the terminal. if you use nautilus, make sure you close the window when you've done because you dont want to use root nautilus for general use.

---

### Post by batharoy on 2009-03-19
> **sahabcse said:**
> Hi

Type

#sudo gedit /var/lib/apt/lists

Then remove the entry and save

It's a directory, gedit wont work.

> **aeiah said:**
> sudo essentially stands for 'super user do'. it gives you temporary admin rights (or root privilage) to make system changes like the one you need to. if you open the file manager (nautilus) with sudo you can browse around and make changes as normal or you could use the terminal. if you use nautilus, make sure you close the window when you've done because you dont want to use root nautilus for general use.

Good point, also things you "delete" or "send to trash" wont go to your user trash so be careful what you delete.

---

### Post by billgoldberg on 2009-03-19
> **batharoy said:**
> ```
sudo nautilus
```
Opens the file browser with root status.


Always, always use gksudo when opening nautilus as super user.

--

In a terminal "cd" to the directory, issue the "ls" command and us "sudo rm" to remove any duplicates.

---

### Post by mcduck on 2009-03-19
> **billgoldberg said:**
> Always, always use gksudo when opening nautilus as super user.

--

In a terminal "cd" to the directory, issue the "ls" command and us "sudo rm" to remove any duplicates.

+1.

Same applies to *all* graphical applications. Running GUI apps with "sudo" instead of "gksudo" might break things to the point that you are not able to log in any more..

"sudo" doesn't load root user's environment variables for graphical apps like gksudo does, this means that you are running the app as root, but using your normal user's home directory and configuration files. In some cases this will result in your normal user's files becoming owned by root.

Of course some apps work fine with sudo, at least most of te time, but it sure is easier and simpler to just use "gksudo" with all GUI apps and "sudo" with CLI apps than try to find out which ones work fine and which ones will break things.. ;)

---

### Post by Bearly Able on 2009-03-19
> **mcduck said:**
> +1.

Same applies to *all* graphical applications. Running GUI apps with "sudo" instead of "gksudo" might break things to the point that you are not able to log in any more..

"sudo" doesn't load root user's environment variables for graphical apps like gksudo does, this means that you are running the app as root, but using your normal user's home directory and configuration files. In some cases this will result in your normal user's files becoming owned by root.

Of course some apps work fine with sudo, at least most of te time, but it sure is easier and simpler to just use "gksudo" with all GUI apps and "sudo" with CLI apps than try to find out which ones work fine and which ones will break things.. ;)

Thanks, mcduck, you've just solved a completely different problem for me! :D  I realised I must have screwed things up by using sudo nautilus instead of gksudo nautilus when I read your explanation.  I've managed to fix it after a week of frustration.

---

### Post by stoogiebuncho on 2009-03-19
> **mcduck said:**
> +1.

Same applies to *all* graphical applications. Running GUI apps with "sudo" instead of "gksudo" might break things to the point that you are not able to log in any more..

"sudo" doesn't load root user's environment variables for graphical apps like gksudo does, this means that you are running the app as root, but using your normal user's home directory and configuration files. In some cases this will result in your normal user's files becoming owned by root.

Of course some apps work fine with sudo, at least most of te time, but it sure is easier and simpler to just use "gksudo" with all GUI apps and "sudo" with CLI apps than try to find out which ones work fine and which ones will break things.. ;)

Not to hijack, but does this mean that you should use gksudo even when opening files in gedit from the terminal?
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Yellow Pasque on 2009-03-19
> **stoogiebuncho said:**
> Not to hijack, but does this mean that you should use gksudo even when opening files in gedit from the terminal?
```
sudo gedit /etc/X11/xorg.conf
```

Yes, gedit is a graphical application. If you need root permissions with gedit, use gksudo.

---

### Post by cousinlucky on 2009-03-19
Gentlemen I really appreciate all of these helpful posts but I'm completely confused as to what I should now be doing.

I am guessing that I am to use gksudo nautilus - is that correct?

---

### Post by odanawt on 2009-03-19
You are correct sir! Or, at least, that is what I have gathered so far.

---

### Post by cousinlucky on 2009-03-19
Well I got rid of the extra file and learned a very valuable lesson. I got a terminal WARNING however! What does it mean?

** (nautilus:24758): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///

(nautilus:24758): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:24758): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown
cousinlucky@cousinlucky-desktop:~$

---

