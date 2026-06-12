---
title: "chmod - mode of 'file.name' retained as 0755"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by aidanewen on 2010-10-11
OK, this is making me crazy. I can't seem to chmod a directory. 

```

user@host:/usr/share$ sudo chmod -Rv o+r openbravo-erp
mode of 'openbravo-erp' retained as 0755 (rwxr-xr-x)
user@host:/usr/share$

```I've tried ls -L to see if it's a symbolic link but it doesn't seem to be. I've no idea why I can't change the permissions. 

Can anyone help?

---

### Post by mike2357 on 2010-10-11
It looks like it's working, but chmod is telling you the permissions you want are already set, so there's no need to change.

"o+r" means give others read permission, and it appears they already have it.

What are you trying to do?  Maybe there's a piece I'm not seeing.

---

### Post by aidanewen on 2010-10-11
Sorry I made a typo above, the permissions on the directory are drwxr-xr-x.

(I've now corrected my original post...)

---

### Post by bodhi.zazen on 2010-10-11
> **aidanewen said:**
> Sorry I made a typo above, the permissions on the directory are drwxr-xr-x.

(I've now corrected my original post...)

What do you want the permissions to be ?

Since others already have r access, +r will do nothing.

You need to either 

chmod 750 (use numbers) or remove permissions you do not want

chmod o-x 

BUT permissions on directories are not the same as permissions on files

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by aidanewen on 2010-10-11
I want others to have read permission:

drwxr-xr-x***r*** rather than drwxr-xr-x

---

### Post by aidanewen on 2010-10-11
I'm trying to apply the change to all files and sub directories recursively (using the -R option).

---

### Post by The Cog on 2010-10-11
> **aidanewen said:**
> I want others to have read permission:

drwxr-xr-x***r*** rather than drwxr-xr-x

drwxr-xr-x does give everyone read permissions. It's a  directory and the user permissions are:
rwx : full permissions to owner
r-x : read and execute (enter the directory) to the group
r-x : read and execute (enter the directory) to the world

There cannot be another "r" after drwxr-xr-x because the description is already complete.

---

### Post by aidanewen on 2010-10-11
OK, I get it. Only files can have that r - not directories (where an x means they can be opened right?).

What about my recursive change of permissions. I want all the files in the directory readable by anyone, but I'm getting the following:

```

  user@host:/usr/share$ sudo chmod -Rv o+r openbravo-erp/


.....


  mode of `openbravo-erp/src/src/index.html' retained as 0755 (rwxr-xr-x)
  mode of `openbravo-erp/src/src/build.xml' retained as 0755 (rwxr-xr-x)
  mode of `openbravo-erp/src/src/ehcache.xml' retained as 0755 (rwxr-xr-x)
  mode of `openbravo-erp/src/src/buildAD.xml' retained as 0755 (rwxr-xr-x)
  user@host:/usr/share$ 
  

```It doesn't look like I've managed to change the permissions on my files either.

---

### Post by The Cog on 2010-10-11
But others already have read permissions. Look:
> mode of `openbravo-erp/src/src/index.html' retained as 0755 (rwxr-x[COLOR="Red"]**r-x**[/COLOR])
Other users permissions are **already** r-x (read, not write, execute). That's why the existing mode was retained. I don't think you really want executable XML files, but that's another issue.

---

### Post by aidanewen on 2010-10-11
OK, I think I'm starting to understand this properly - The hyphens don't separate users, groups and others, they represent missing permissions?

So if I did a chmod o-r on one of those xml files I'd get rwxr-x--x?

I think I get it.

Thanks loads for your help.

---

### Post by mike2357 on 2010-10-11
When you're ready to digest more, check this out:

[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by The Cog on 2010-10-11
> **aidanewen said:**
> OK, I think I'm starting to understand this properly - The hyphens don't separate users, groups and others, they represent missing permissions?

So if I did a chmod o-r on one of those xml files I'd get rwxr-x--x?

I think I get it.

Thanks loads for your help.

Absolutely - you got it.

If your users still get access denied when read the files, check every directory in the path down to to files, looking for a directory they don't have permissions to. I think they need both r and x on the directories.

---

### Post by sisco311 on 2010-10-11
> **The Cog said:**
> I think they need both r and x on the directories.

They need read and execute (a.k.a. search) permissions on the directory and execute permission on every ancestor directory.

Unix/Linux file & directory permissions are well explained here: [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

