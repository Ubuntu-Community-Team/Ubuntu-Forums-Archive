---
title: "why programs and their files are scattered everywhere"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by wencin on 2009-04-12
after looking for a while in the directory, i'm a little bit confused with the way linux putting files. seems that programs and their files are scattered everywhere (such as in '/bin' is the place for executables but the other part of the program just not there) . why would linux do this, rather than having it like windows (which put the whole program in the same directory)? i feel this is impractical and less user friendly (sorry).

---

### Post by Eisenwinter on 2009-04-12
Linux organizes everything by the "type of thing".

For example, library files are stored in /usr/lib, executables are stored in /usr/bin, etc.

---

### Post by Paddy Landau on 2009-04-12
> **wencin said:**
> i feel this is impractical and less user friendly (sorry).
I really wouldn't worry about it.

You don't ever need to know where programs go. They install themselves (through Synaptic Package Manager), and if you don't want a program any more, it uninstalls itself (again, through Synaptic Package Manager).

The only thing you do want to know, for backup purposes, is where your settings go. They almost always go in your own home directory. For example, settings for OpenOffice will go in
```
/home/wencin/.openoffice.org
```(assuming that *wencin* is your user name).

---

### Post by FreewheelinFrank on 2009-04-12
The Linux system seems to work OK, if not better than Windows.

Every tried installing a program in Windows and finding it doesn't work for a limited user?

Here's some information on the directory structure.

[http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)

[http://www.debianadmin.com/linux-directory-structure-overview.html](http://www.debianadmin.com/linux-directory-structure-overview.html)

[http://www.arsgeek.com/2006/09/01/linux-newbie-directory-structure/](http://www.arsgeek.com/2006/09/01/linux-newbie-directory-structure/)

---

### Post by Paqman on 2009-04-12
> **wencin said:**
> i feel this is impractical and less user friendly (sorry).

The good news is that on Linux you don't need to know where all the files are. So practicality doesn't come into it.

For example, on Windows you actually need to know the full path to the executable to launch it. On Linux you don't. The command to launch Firefox is just "firefox", for example. No path required.

We also use package managers. This means that the system has a good track of where every file associated with an app is located. When you uninstall it'll clean them all out. No messy registries that degrade over time, and no duplication of dependent files.

So yes, Linux does spread the files about, but from a users point of view it just doesn't matter. The Linux way of managing software is a hell of a lot easier and better than the Windows way.

---

### Post by CatKiller on 2009-04-12
> **wencin said:**
> i feel this is impractical and less user friendly (sorry).

It's incredibly practical. As Eisenwinter points out, files are organised by what they are, rather than what put them there. This means that you can have your files organised well, since filesystems are optimised for different things. Some are more efficient with lots of very small files. Some are really good if the files are very large. Some perform really well when the files' contents are changed often. With the UNIX way of doing things, you can use the strengths of all of these filesystems by using them functionally - mount one filesystem for /boot, another for /usr, /var/log, /var/mail and so on. It's very flexible.

You seem to have confused the Windows way of doing things with the DOS way of doing things. DOS used to put everything in one directory (although you could only have so many directories). Windows programs put a lot of things in one directory, a whole bunch of other things in another directory, and change system files all over the place without asking. When you remove the program, half of these files are not removed, and the system files are not changed back. There is no systematic way of seeing which program left which file behind.

The UNIX filesystem doesn't have to be "user-friendly," since any user that needs "user-friendliness" doesn't need to be messing around with files outside of their Home folder anyway. It is designed for flexibility and functionality. The package management system takes care of which files go where, and removes them when the program that put them there is removed. No user cleaning-up required.

EDIT: You might find [this description]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") of what each part typically  is for helpful. Note that any of these pieces could be on different partitions, or even on different computers, although it doesn't generally make that much sense to have /, /boot, /bin or /sbin on a different machine unless the local machine is only a thin client that has nothing on itself. Those are the file locations for files that let the local machine work on its own. Having /var or /home on different machines is relatively common for a proper multi-user network. The whole thing is **very** scalable.

---

### Post by Paddy Landau on 2009-04-12
To take it CatKiller's explanation a little further, remember that you can't really compare Linux with Windows. They have very different histories and philosophies.

Linux was designed from the bottom-up to be multi-user and secure and reliable. That's why so many web servers use Linux. The directory structure kind of reflects that structure.

---

### Post by PGScooter on 2009-04-12
> **Paqman said:**
> The good news is that on Linux you don't need to know where all the files are. So practicality doesn't come into it.


Although it's probably obvious to most of you guys, as a newbie myself, I find the command ```
type programname
``` very helpful. I think that it is very important to know where the program itself is, for example when Firefox for some reason doesn't know what to do with a pdf and asks you where it can find a program to open it with!

---

### Post by llamabr on 2009-04-12
> **PGScooter said:**
> I think that it is very important to know where the program itself is, for example when Firefox for some reason doesn't know what to do with a pdf and asks you where it can find a program to open it with!

For most applications like that, you'll find them in /usr/bin

fwiw, if you know what it's called, but can't locate it, you can do so with the 'which' command:

```
which xpdf
```

But I'm in agreement.  Usually you don't need to know where something is.  Your %PATH will include everywhere it may be.  So why does this make it less user friendly?

---

### Post by Paqman on 2009-04-12
> **PGScooter said:**
> for example when Firefox for some reason doesn't know what to do with a pdf and asks you where it can find a program to open it with!

I guess that's just about knowing what app you want. In the case of a .pdf you'd be looking for Evince.

---

### Post by Paddy Landau on 2009-04-12
> **Paqman said:**
> I guess that's just about knowing what app you want. In the case of a .pdf you'd be looking for Evince.

[LIST]
[*] Go to nautilus.
[*] Find the a file of the type that you want (e.g. for PDF, find any PDF file).
[*] Right-click the file and select Properties.
[*] Select the "Open With" tab.
[/LIST]
 You'll find a list of suitable programs, which may help.

---

### Post by Paddy Landau on 2009-04-12
In addition to the commands *which* and *type*, you can also use *whereis*.
```
whereis firefox
```

---

### Post by aktiwers on 2009-04-12
```
locate firefox
```

---

### Post by llamabr on 2009-04-12
> **aktiwers said:**
> ```
locate firefox
```

Locate is less useful, as it won't find anything installed recently (requires the database to be updated) and will return lots of false positives, i.e., everything with firefox in the name, including config files, libraries, etc.

'which' is best.

I'm still not sure why the file structure is not 'user friendly'.

---

### Post by 3rdalbum on 2009-04-12
Well, most of the time a program will install an executable into /usr/bin, some man pages into /usr/share/man, a launcher in /usr/share/applications/ and the rest into /usr/share/programname.

The program needs to be in /usr/bin in order to be in the $PATH (and easily launchable), the man pages need to be in that location to be indexed and found by *man*, and the .desktop files need to be in that directory to be found by your main menu. Everything else generally goes into the one directory where you can find it, if you want to find it for some unusual reason.

Some programs install shared libraries into /usr/lib, but once again that's where they need to be in order for the dynamic linker to find them. (and for other programs, that might use the same libraries, to find them).

---

### Post by CatKiller on 2009-04-12
> **llamabr said:**
> I'm still not sure why the file structure is not 'user friendly'.

"User friendly" is a really nebulous term that doesn't really have any independent meaning. A lot of people seem to confuse "friendliness" with "exactly the way Windows does things" which is merely familiarity, and isn't especially friendly to users at all, and given that Windows does many things a completely different way to the way everything else does things means that Windows is necessarily the "friendliest" for those users. Case-in-point; Microsoft deliberately chose \ as their filesystem separator because everyone else used / and they thought they might be accused of having made a UNIX knock-off.

"Friendliness" for users might be considered to be that which lets them do what they want to do, even if they have to actually learn how to do it. It's not like people come out of the womb knowing how to use Windows. By that definition, being able to have your files transparently allocated to different machines or different filesystems is very "friendly."

---

### Post by SeanBlader on 2009-04-15
There also seems to be a fair bit of code reuse in Linux, so if the Kernel, window manager, compositor, network, or any other component of the base OS uses some library code, then applications can later on make use of that library, decreasing the size and complexity of the system as a whole and making a more efficient use of resources. It's like recycling on a code level. 

One could argue that encapsulating your application entirely in one folder might seem useful for the user, it turns out to be really bad, because then that application has to use it's own code to do all the stuff it wants to to, but far worse it makes it a lot harder for the developer to be able to write software efficiently, or consistently with the intentions of the OS designers in mind.

If you want a good example, look at the interface for Windows, then for Windows Media Player, Internet Explorer, and for Office 2007. All of them are completely different different, despite the fact that they were written for the same OS, by the same company, for the same target audience. Separate folders make for design inconsistencies.

---

### Post by SunnyRabbiera on 2009-04-15
Really /usr/bin is like Program files in Windows, actually the linux directory structure makes more sense then windows...
I dare anyone to find their way in the windows directory, I find it even harder to manage then linux.

---

### Post by billgoldberg on 2009-04-15
It's pretty straight forward.

There is always the "whereis" program.

Do a 

```
whereis pidgin
```

for example.

---

### Post by 3rdalbum on 2009-04-15
To be honest, binary installers on Windows do put a heap of stuff all over your hard disk, but people assume that its folder in Program Files is all that there is to the program.

---

### Post by Arndt on 2009-04-15
> **3rdalbum said:**
> Well, most of the time a program will install an executable into /usr/bin, some man pages into /usr/share/man, a launcher in /usr/share/applications/ and the rest into /usr/share/programname.



Some programs, especially those meant to be run as server programs, also have system-wide configuration files (typically plain text) in /etc, and you may want to change them now and then. There is /etc/apache2/apache2.conf, for example.

---

### Post by Arndt on 2009-04-15
> **Paddy Landau said:**
> To take it CatKiller's explanation a little further, remember that you can't really compare Linux with Windows. They have very different histories and philosophies.

Linux was designed from the bottom-up to be multi-user and secure and reliable. That's why so many web servers use Linux. The directory structure kind of reflects that structure.

Well, the arrangement of configuration files, program files and data files into /etc, /bin, /var, etc. comes from the earliest versions of Unix, long before Linux. The .../share/... thing came with SunOS, I think (but I may be mistaken). I think the idea there was to separate the data on the local computer from the data which was available with NFS on the local network.

The reason for /bin and /usr/bin both existing was that the boot partition was quite small and only had room for essential file, in /bin. The rest were mounted from a different disk partition, on /usr. Ubuntu seems to keep the distinction but not mount them separately. Other Unixes have simply made a symbolic link between them.

---

### Post by markbuntu on 2009-04-15
Compared to windoze, the linux/unix filesystem is very orderly.

---

### Post by Paddy Landau on 2009-04-15
> **markbuntu said:**
> Compared to windoze, the linux/unix filesystem is very orderly.
Well, it actually doesn't matter. Until I saw this thread, I had no clue where Linux programs were stored, and I didn't care. I still don't care for that matter. I let Linux handle it.

Mostly, it's the same with Windows; I don't care where the programs are stored in Windows, except when viruses and other malware get in.

---

### Post by markbuntu on 2009-04-15
viruses...malware...another reason the linux filesystem is better.

---

