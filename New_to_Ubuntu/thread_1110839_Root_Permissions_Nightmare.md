---
title: "Root Permissions Nightmare"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by funkdified on 2009-03-30
I was trying to copy some files into the usr folder in root and tried to changed permissions to enable the copying. After running gksudo nautilus I changed the permissions of the root for 'groups' from 'root' to my username... then I thought I changed files/folders to 'write/access', but I think it might have just changed to access. 

Needless to say my system won't run. As soon as I made the changes I couldnt even open terminal likely because that requires the writing of some file. So I couldnt undo my mess.

When I tried to restart I get this error:

"GDM could not write to your authorization file"

Is there some way to access gksudo nautilus /root file manager from within the root shell prompt accessed in recovery mode?  Or is there something that I can type in the root shell prompt to restore the root read/write permissions?

---

### Post by |Porsche on 2009-03-30
post the results of ```
ls -al ~
```

---

### Post by funkdified on 2009-03-30
sorry, absolute newby here..  can you please tell me how to output the results to a file so that I can post them from within my other OS?

---

### Post by Eisenwinter on 2009-03-30
Can you boot into recovery mode?

If you can, then try changing the permissions, using chmod.

```
chmod 770 /
```

This will give you, and the root user, full permissions to the root filesystem.

Note that changing the permissions to allow read and write access to the root filesystem as a regular user, is dangerous, and not recommended.

I recommend that you change it back to root-only.

---

### Post by Temposs on 2009-03-30
> **funkdified said:**
> sorry, absolute newby here..  can you please tell me how to output the results to a file so that I can post them from within my other OS?

To do that:

```
ls -la ~ > newoutputfile.txt
```

---

### Post by funkdified on 2009-03-30
Hi guys, I actually created the output file and ran chmod 770 / but then when I went to restart a few things couldnt initialize including GNOME graphics and I was put to a command prompt form of Ubuntu... I think things got messed up pretty bad somehow.. so I just reinstalled ubuntu.. hopefully this time will go better...

---

### Post by drowner on 2009-03-30
It will be better.

Please note that you shouldn't have to change the permissions of a folder to write to it - with the sudo command you can get root privileges to write where you like

---

### Post by mvalviar on 2009-03-30
I'd suggest you never touch anything outside you home folder using nautilus with root permission. Its very easy to get into trouble. Just use sude cp or mv if you need to touch things requiring root privilege.

---

