---
title: "Dropping  ALL system permissions temporarily"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by mistypotato on 2009-04-17
Hello,

At times I need to work on my server "OFF LINE" sometimes.

During that time when I am not physically connected to the Internet or any network for that matter, I would like to be able to freely work on any file or directory without have to constantly keep bowing to permissions entering and retyping usernames and passwords constantly.

With that in mind, is there a way to temporarily disable the system that controls system wide permissions so that working on it is easier?

Thanks

---

### Post by Alekz_ on 2009-04-17
You mean.. have Full Control under all files?!?

Use root account!

---

### Post by 3rdalbum on 2009-04-17
Two solutions: You can type "sudo su" at the terminal to turn it into a root shell, or you could boot up into/switch to single-user mode.

You can switch to single-user mode by typing this at the terminal:

```
sudo telinit 1
```

You can bring it back to a multi-user runlevel by typing this:

```
sudo telinit 5
```

I think this should bring X back up, but if it doesn't you can always type this:

```
sudo gdm
```

---

### Post by mlentink on 2009-04-17
> **Alekz_ said:**
> You mean.. have Full Control under all files?!?

Use root account!

Please do not do so.

First of all, it is possible to extend the grace time that the sudo system grants you before it asks for you password again. 
Secondly, you can grant yourself root priviliges so:```

sudo su
```

Just type exit when you're done. 
And remember there are consequences. Any file you create or modify will subsequently be owned by root...

---

### Post by Alekz_ on 2009-04-17
I don't know what's the problem of use root account! 

His working on his server, so I suppose his know what his doing! I don't like to SUDO everytime I have to do some administrative task on my servers (I don't use Linux Servers, they're Solaris)!

And also, the commando sudo su give you the same privileges of the root account! :)

Just my point...

Alekz_

---

### Post by Ticketoride on 2009-04-17
1. File Manager ... any Shortcut ... right-click --> Properties, under "Comand" enter ---> **gksudo nautilus**
This gets the File Manager permanent "Root" Privileges browsing Files & Folders.

In Nautilus, also go to ---> View ... and select to "Show hidden Files".

2. Then go to: > System > Administration > Login Window. Click the 'Security' tab and then tick 'Allow local system administrator login'. You'll login as "Root" permanently.

3. Auto-login ---> [http://www.watchingthenet.com/how-to-enable-automati-logon-in-ubuntu-or-kubuntu.html](http://www.watchingthenet.com/how-to-enable-automati-logon-in-ubuntu-or-kubuntu.html)

4. Buh-bye Password ---> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mlentink on 2009-04-17
You might want to read the forum rules, and also this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Alekz_ on 2009-04-17
> **mlentink said:**
> You might want to read the forum rules, and also this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Already read this...

Sorry, but am I wrong about tell somebody to use root account in this forum? If so, tell me! :) I won't do this anymore!

I know about "best practices" for security, but I also know that sometimes it doesn't help to do my work easier!

PS:
OK! I missed that from [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> Please do not suggest this to others unless you personally are available 24/7 to support the user if they have issues as a result of running a shell as root.

Sorry about it! :)


¬
Alekz_

---

### Post by eldragon on 2009-04-17
> **Alekz_ said:**
> Already read this...

Sorry, but am I wrong about tell somebody to use root account in this forum? If so, tell me! :) I won't do this anymore!

I know about "best practices" for security, but I also know that sometimes it doesn't help to do my work easier!

¬
Alekz_

apparently ubuntu is dumbing it down instead of educating...

---

### Post by Sef on 2009-04-17
>  Sorry, but am I wrong about tell somebody to use root account in this forum? If so, tell me! :smile: I won't do this anymore!

Do not do it.  You can get an infraction for telling someone to use root.

---

### Post by mlentink on 2009-04-17
> **Alekz_ said:**
> Already read this...

Sorry, but am I wrong about tell somebody to use root account in this forum? If so, tell me! :) I won't do this anymore!




From the forum rules:

> Tutorials explaining how to enable the root account for a graphical login or autologin will not be supported on the forums and will be moved to the Jail. Although we believe people should have the freedom to run their computers however they want, we also believe in supporting Ubuntu's security model. You can find or post information elsewhere on the internet regarding graphical Ubuntu root logins; such tutorials do not have to be hosted on the Ubuntu Forums.

Users posting such tutorials after this announcement will be given a warning or infraction at the discretion of the staff. 			 		

As you will have read in the article on Sudo, it is highly unlikely there would be something you could not perform within the sudo system, so using a root login is unneccessary.

You yourself are obviously free to do as you please

---

### Post by Alekz_ on 2009-04-17
> **mlentink said:**
> From the forum rules:



As you will have read in the article on Sudo, it is highly unlikely there would be something you could not perform within the sudo system, so using a root login is unneccessary.

You yourself are obviously free to do as you please

OK! Understood! As I said, sorry about it!! Won't happen anymore!

---

