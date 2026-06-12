---
title: "cat file on network"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by tdapower on 2011-02-14
[SIZE=4]Can I use the cat command to read a text file on a shared folder of another networked computer?

cat smb://<file name with location>

I can  use gedit to open the same file,
 
gedit smb://<file name with location>

but in cat there is an error message appeared "No such file or directory"[/SIZE]

---

### Post by freak42 on 2011-02-14
I guess you have to mount the smb drive into your linux filesystem tree before you're able to use programs that are not protocol aware such as cat.

hth

---

### Post by tdapower on 2011-02-14
you are correct, but how the gedit works and cat doesn't?

---

### Post by Morbius1 on 2011-02-14
You know, just when you've deluded yourself into thinking you've finally mastered this samba thing someone like you posts something like this.

I had no idea that gedit could do that. It wouldn't even had occurred to me to try.

I have no actual explanation for this but I can tell you this.
> gedit smb://<file name with location>Does two things:
It automatically mounts the remote share at:
> /home/your-user-name/.gvfs/share-name on server-name/and then it opens the file-name in gedit.

Who knew that would happen?

I'm guessing that gedit is "smb" protocol aware and cat is not. Once the remote share is actually mounted though you can use cat:
```
cat /home/your-user-name/.gvfs/"share-name on server-name"/file-name
```

---

