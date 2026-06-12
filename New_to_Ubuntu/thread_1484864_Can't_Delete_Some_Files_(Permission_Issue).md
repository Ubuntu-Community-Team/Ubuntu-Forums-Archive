---
title: "Can't Delete Some Files (Permission Issue)"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by SKhan on 2010-05-16
i want to delete some files from /usr/share/opera
but delete button simply doesn't work & "move to trash" is grayed out. i found out that this is because of permission restrictions.
so what should i do now to delete those files?

Note: i am familiar with ms windows ntfs advance permissions. but could not fully understand permissions under ubuntu.

here is the snapshot of permissions for the files i want to delete.

---

### Post by mjneil.81 on 2010-05-16
go to terminal (Applications>Accessories>Terminal type gksudo and type nautilus in the pop up window this opens nautilus (file browser) with root privileges. this should help. be careful when operating in this manner you can cause yourself problems, ensure you know the end result of modifying deleting files.

using chmod command in terminal will also allow you to change permissions.

---

### Post by ssj6akshat on 2010-05-16
1)Press Alt+F2
2)Type gksu nautilus
3)Enter your Password
4)Dont mess your system

---

### Post by 3rdalbum on 2010-05-16
> **SKhan said:**
> i want to delete some files from /usr/share/opera
but delete button simply doesn't work & "move to trash" is grayed out. i found out that this is because of permission restrictions.
so what should i do now to delete those files?


1. I don't think there's anything in /usr/share/opera that you should really be touching. If you wanted to remove bookmarks, cache etc you should be looking in the .opera folder in your Home Folder. (it's a hidden folder; press Control-H to view hidden folders).

2. If you know that you really want to remove a file from this directory, you need to open a file browser as the 'root' user and perform the action in there. You can do this by running the file browser as root, by pressing Alt-F2 and typing this:

```
gksudo nautilus
```

A handy shortcut for this is to install the "nautilus-gksu" package from Software Center or Synaptic. The next time you log in, you can right-click a file or folder and choose "Open as Administrator", which will open the file with the default program as root, or will open the folder in a root file browser.

> Note: i am familiar with ms windows ntfs advance permissions. but could not fully understand permissions under ubuntu.

It's the same concept, but most Windows users do it wrong :-) Each user has read/write access to their own home directory, but not to the rest of the system and not to other users' home directories. The only person who can modify the whole system is called 'root'.

In Ubuntu, you cannot log in as root. However the first user created can run programs as root, and those programs can perform the sorts of things that you would need to do. The mechanism for this is called 'sudo' for command-line programs, and 'gksudo' for graphical programs.

When we say "gksudo nautilus", you're opening the Nautilus file browser as root.

So why is this seperation between user and root actually done? It's done for security and stability reasons. A program run as your ordinary user cannot damage or infect your system, and it can't interfere with other users. You'd need to explicitly run it as root in order for it to be a danger to the system.

Windows XP and above can work in exactly the same way as Ubuntu in this regard, but most Windows users just log in as the administrator account. And they wonder why there's such a virus problem on Windows XP. Windows Vista and Seven are, by default, like Ubuntu in encouraging the seperation of user and administrator, and there's a corresponding decrease in virus attacks on those operating systems.

**Essentially all you need to know is this:**

a. Your home user can only write to its home directory and external storage. If you need to modify anything else, it needs to be done as root.
b. You can launch a program as root through the 'sudo' and 'gksudo' commands.

---

### Post by SKhan on 2010-05-16
**Thank you guys. Problem is solved.**


> **mjneil.81 said:**
> ensure you know the end result of modifying deleting files.
i perfectly know the end results.

> **ssj]Dont mess your system[/QUOTE]
sometimes it's necessary.  said:**
> 1. I don't think there's anything in /usr/share/opera that you should really be touching. If you wanted to remove bookmarks, cache etc you should be looking in the .opera folder in your Home Folder. (it's a hidden folder; press Control-H to view hidden folders).
/usr/share/opera contains default search.ini file. while .opera contains custom search.ini file.
if default file is not edited/deleted/renamed, then search drop-down in opera shows them in a merged way. and default search engines are shown at top of custom engines. this is something i dislike very much.
if default engines get synchronized online then it can result in default engines added to all my custom search files on all my computers.

---

### Post by SKhan on 2010-05-16
> **3rdalbum said:**
> It's the same concept, but most Windows users do it wrong  Each user has read/write access to their own home directory, but not to the rest of the system and not to other users' home directories. The only person who can modify the whole system is called 'root'.

In Ubuntu, you cannot log in as root. However the first user created can run programs as root, and those programs can perform the sorts of things that you would need to do. The mechanism for this is called 'sudo' for command-line programs, and 'gksudo' for graphical programs.

When we say "gksudo nautilus", you're opening the Nautilus file browser as root.

So why is this seperation between user and root actually done? It's done for security and stability reasons. A program run as your ordinary user cannot damage or infect your system, and it can't interfere with other users. You'd need to explicitly run it as root in order for it to be a danger to the system.

Windows XP and above can work in exactly the same way as Ubuntu in this regard, but most Windows users just log in as the administrator account. And they wonder why there's such a virus problem on Windows XP. Windows Vista and Seven are, by default, like Ubuntu in encouraging the seperation of user and administrator, and there's a corresponding decrease in virus attacks on those operating systems.

Essentially all you need to know is this:

a. Your home user can only write to its home directory and external storage. If you need to modify anything else, it needs to be done as root.
b. You can launch a program as root through the 'sudo' and 'gksudo' commands.
very nice and clear explaination. i liked it very much.

---

