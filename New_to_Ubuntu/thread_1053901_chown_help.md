---
title: "chown help"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by untappedpilot2 on 2009-01-29
Somehow I made a few folders and they got changed to being owned by "root". What can I do to change the ownership of the main folder as well as all sub-folders?

---

### Post by rafaelsousa on 2009-01-29
```
sudo chown youruser yourfolder -R
```

The "-R" means it will be done recursively

For more help about this command try 

```
man chown
```

---

### Post by hyper_ch on 2009-01-29
what folders?

---

### Post by untappedpilot2 on 2009-01-30
> **rafaelsousa said:**
> ```
sudo chown youruser yourfolder -R
```

The "-R" means it will be done recursively



Thanks this did the trick. To get it to work I did..

```
sudo chown username /my/directory/* -R
```

--adding the /* on the end made it work. Some of the directories I needed to change were in my /home folder, and some file or other couldn't be edited even as root when I tried it without the /*

Anyway thanks again for your help.

---

### Post by lekifsirk on 2009-01-30
You guys are my heroes!  I have been stressing so hard because I did something yesterday that really messed up my computer and I was just getting ready to wipe the slate clean and re install.  Not a great way to spend my night.  I tried what you suggested here and it fixed my problem.
Thank you a million times.
-Kris:D

---

### Post by dmizer on 2009-01-30
Though your problem may have been fixed, it's never a good idea to simply change things with a wild card (*) and recursive (-R) switch. You can do just as much harm as good with such commands.

Permissions are in place for reasons. It's far more preferable to change permissions on a file or single directory level if you're having problems. With a bit more information like what hyper_ch was requesting, the command could have been made more precise and then there would have been far less potential for disaster.

---

