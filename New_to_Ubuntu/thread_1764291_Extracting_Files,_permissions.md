---
title: "Extracting Files, permissions"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by Weighty Ghost on 2011-05-21
While tying to extract a tar.gz file to my /opt directory I get a prompt saying I do not have permission.

Is there a way to do this without buggering with that god-damned "terminal"?

I can extract to my desktop ok, but I don't have permission to extract to the /opt directory.

I'm trying to get XAMPP going but the first step is to extract the archive to the aforementioned directory.

---

### Post by ubudog on 2011-05-21
You can do this without using the terminal by pressing ALT+F2.

Enter the following in ALT-F2:
```
gksu cp file.tgz /opt
```
(replacing "file.tgz" with the file you want to extract.  If the file is on your Desktop, you would want to replace file.tgz with Desktop/file.tgz.)

Then, to access that directory and extract it:
ALT-F2 then
```
gksu nautilus /opt
```

You can then double click on the file, and extract it.

Hope that helps.

---

### Post by Weighty Ghost on 2011-05-21
Update:

The archive extracted ok on my desktop, but I can't c&p, nor drag and drop the files to the opt directory, -again for want of "permission".

Thanks for any help. 
There are some threads that go into how to do this by way of the god-damned terminal. I'm sure I'll be able to do this, but if it is possible to change the security settings universally in Ubuntu, so I don't have to go through the GDT every time I need to move a file I would appreciate the insight.

Thanks,

---

### Post by Weighty Ghost on 2011-05-21
Man you guys are fast...,

Thanks ubudog, I did'nt see your post before I posted an update. I'll try that. 

Thanks, and have great weekend,

Edit: For any newbs doing a search and finding this thread you have to append ubudogs code with the command "sudo" ie;
"sudo gksu nautilus /opt" otherwise you get more permissions problems.

---

### Post by AlphaLexman on 2011-05-21
> **Weighty Ghost said:**
> Edit: For any newbs doing a search and finding this thread you have to append ubudogs code with the command "sudo" ie;
"sudo gksu nautilus /opt" otherwise you get more permissions problems.
Actually that is **NOT** good advice at all. You do not need to sudo gksu (redundant).

---

### Post by audiomick on 2011-05-21
+1 that. "Sudo" and "gksu" are effectively the same thing. The pertinent difference is that "gksu" is specifically for starting graphical applications with root privileges.


Ubudog's advice should work, as far as I can tell. It might be easier just to start an instance on Nautilus with root privileges without aiming to do some of the work on the way, as this advice does.

To do this:

Open a god damned terminal

type
```
gksu nautilus
```

type your password, the one you use to log in, when asked. You will not see what you are typing.

An instance of Nautilus, the file manager, will open which has root privileges. Here, you will be able to copy to /opt and do whatever else you want. You will also be able to delete important system files without being asked if you really want to do this, so be careful.

You are having permission problem with copying to /opt because it belongs to root. There are very good reasons for this; don't be annoyed about it. This is related to why Linux is a basically very secure system.

One more thing: it is not good manners to start two threads on the same subject, even if you are stressed out.
[http://ubuntuforums.org/showthread.php?t=1764357](http://ubuntuforums.org/showthread.php?t=1764357)

---

### Post by Weighty Ghost on 2011-05-21
Hmmm,

I tried the second code as is and still got the permission problems. When I searched another thread a poster appended sudo to the code and it worked just fine (for both of us), perhaps I mistyped.

And thanks, launching the file manager as root frees up all privileges, thats actually the info I was looking for (helpful warning appreciated, re; system files) 

Thanks again Mick,

---

### Post by audiomick on 2011-05-21
No worries. ;)

---

### Post by AlphaLexman on 2011-05-21
**NOTE:** There exists a difference between being the 'root user' and a user having 'root privileges'.
See [RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by audiomick on 2011-05-21
Very nice link. Thanks, I hadn't seen that before.

---

