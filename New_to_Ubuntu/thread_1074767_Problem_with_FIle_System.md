---
title: "Problem with FIle System"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by jivabill on 2009-02-19
When I look at the files in File System I see that the folder "Lost + Found" is marked with a white X.  When I look at properties say that the file is unreadable.  Also it is empty it says.

How should I fix that?
thanks

---

### Post by pdtpatrick on 2009-02-19
what are you trying to accomplish with the Lost + Found folder?

---

### Post by jerome1232 on 2009-02-19
> **jivabill said:**
> When I look at the files in File System I see that the folder "Lost + Found" is marked with a white X.  When I look at properties say that the file is unreadable.  Also it is empty it says.

How should I fix that?
thanks

There's nothing to fix this is intentional.

The folder is only readable/writable/exectuable by root which is why your user is unable to view it's contents.

It's function is that if your file system was corrupted and fsck found some files that were "lost" it would put the file in lost+found for potential recovery.

```
sudo -i
[sudo] password for jeremy: 
ls -ld /lost+found/
drwx------ 2 root root 16384 2008-12-31 10:24 /lost+found/
```

drwx------ means only the owner of the folder can view it's contents, the owner is root.

---

### Post by jivabill on 2009-02-19
PDTPatrick
Hi, nice to meet you thank you for your reply to my problem.  I just saw the X on the Folder and thought something was wrong.  I see that there is another answer that explains what is going on.  Nevertheless thank you for your help.
bill

---

### Post by jivabill on 2009-02-19
Hi Jerome, thanks for looking into my problem report.

As you will see from my answer to PDTPatrick, I just saw the X on the folder and thought that meant something was wrong with the file.  Then when system said it was unreadable I thought perhaps it was corrupted.

So it sounds like IF I wanted to see the file I would have to use the Root File Browser.

But if nothing is wrong I don't need to do anything except being reassured :-).

Thanks for your help
bill

---

