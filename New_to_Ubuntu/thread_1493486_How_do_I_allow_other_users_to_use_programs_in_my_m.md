---
title: "How do I allow other users to use programs in my main account?"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by sooperspook on 2010-05-25
I have Warcraft and other games installed under WINE on my main account.

I would like to let my son play these games on his own account.

However, I can't see any way to do this.

any help would be appreciated.

Thanks.

---

### Post by -humanaut- on 2010-05-25
You need to change the permissions on the file to allow "others" to read,write, and execute or create a group like "games" and give the permissions 777 to the files you want to allow. And include your sons user name in the group.

---

### Post by BoneKracker on 2010-05-26
> **-humanaut- said:**
> You need to change the permissions on the file to allow "others" to read,write, and execute or create a group like "games" and give the permissions 777 to the files you want to allow. And include your sons user name in the group.

_After you have created the group (e.g. "games"), you would change the group identifier on the files in question_ (in Nautilus or using the command 'chown' ("change owner").  To execute the command recursively on an entire directory and all its subdirectories, you add the option '-R' (refer to 'man chown').  For example, to make a folder called "games" in your home directory accessible to users who are members of the group "games", you would do:
```
chown -R :games ~/games
```
Now, having done that, exactly what access members of group "games" have is governed by the specific group permissions that are set for each file.  You change permissions with the command 'chmod' ("change mode", which can also be applied recursively).

Setting permissions to 777 makes all those files (including any that are executables) accessible to anyone and everyone.  That's generally a bad idea.  The only files you'll generally see with 777 permissions should be temporary files and symbolic links.  You shouldn't have to set 777 permissions for another user to be able to use files, unless it's somebody who does not have an account on the system (i.e., a remote user logged in anonymously).  If there is something Wine-specific I don't know about, somebody please correct me.

For security, you typically want to limit the write access you give others (e.g., mode 750 on directories, 640 on files, and 750 on executable files, which amounts to read-write access for you, read-only access for the group (so people can't accidentally uninstall your applications or delete your files, etc.), and no access for "others".  Something like that is probably set up as your default (automatically used when you create files -- see 'man umask').  If you take that more cautious approach, then you need to build from there, and specifically allow write access where group members should have it.

If you can't figure out what group members need write access to, then just _give the group the same privileges as owner_ (i.e. 770, 660, etc.)  That approach is probably quite suitable in this case.  If you look, you may find this is already the case (depending on the installation process and/or your umask).  If they are the same, then all you need to do is create the group (e.g. "games"), 'chown -R :games <the files>', and add your son to group 'games'.

---

