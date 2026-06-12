---
title: "Setting admin password"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by ndex477 on 2011-05-15
[SIZE=3]I just downloaded 11.04 a couple of days ago and I'm as green as a pine tree. Linux is a totally different world from Windows.

That said, can anyone tell me how to set my admin password? I read online to go to Terminal and type: "sudo psswd root" then I would be prompted to enter a new password, but my cursor in Terminal won't type any letters and I'm not getting a prompt for a new password.

Please help!

Thanks in advance.[/SIZE]

---

### Post by wildmanne39 on 2011-05-15
> **ndex477 said:**
> [SIZE=3]I just downloaded 11.04 a couple of days ago and I'm as green as a pine tree. Linux is a totally different world from Windows.

That said, can anyone tell me how to set my admin password? I read online to go to Terminal and type: "sudo psswd root" then I would be prompted to enter a new password, but my cursor in Terminal won't type any letters and I'm not getting a prompt for a new password.

Please help!

Thanks in advance.[/SIZE]
Hi, you should have set up the password when you installed ubuntu. You use it by typing sudo plus the command that you want to use, then it will wait for you to enter your password but that part is invisible you will not see it. I hope this helps.:D

---

### Post by Rocket2DMn on 2011-05-15
First, please use the default font size for making posts here - if you have trouble viewing the text, you should update your Firefox preferences to show a larger font.

To answer your question, the root account is disabled by default in Ubuntu as part of its security policy.  The account you created when you installed is an admin account by default, and should have full permissions to use "sudo".  You shouldn't set a password for the root account unless you really know what you're doing.  For more information, see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) .

Welcome to Ubuntu!

---

### Post by ndex477 on 2011-05-15
Sorry about the font size. So when prompted at the Terminal what do i enter when it asks me for my password? I only setup one password when i downloaded 10.01 and then I upgraded to 11.04. That password was my login password and that's the only one that I know of.

---

### Post by Rocket2DMn on 2011-05-15
When using sudo, you type in your user's password when prompted, not a root password. That's how sudo works - it allows users to execute commands as "root" (or even as another user).

---

### Post by dwhite on 2011-05-15
also when typing your password there is no indication that the keystokes are being registered (what i mean by that is you won't see any little stars or dots indicating that you hit a key), don't worry they are being registered, just type in your user ('login') password and then hit enter

---

### Post by ndex477 on 2011-05-15
Ok. Thanks all. One last question re: this. Since i'm new to Linux, pls explain how the whole sudo thing is analogous to the C:\ in Windows. Because knowing the command prompts or "Terminal commands" is very useful when dealing with any OS.

---

### Post by Rocket2DMn on 2011-05-15
sudo is not analagous to C:\ - these are different concepts altogether.  In linux the root of the filesystem is simply "/" rather than a drive letter like "C:\".  All the material in /home/yourusername/ is like your My Documents directory and then some.  You should store all your files here (unless you have them on another partition or hard drive), and this directory also stores configuration files and folders (most are hidden).  Using "sudo" is necessary to perform administrative tasks in Ubuntu since linux does not allow basic users to manipulate OS level settings.

In Windows a home user is often also an Administrator, but historically Windows does not prompt for credentials, or necessarily even alert you when you are changing system settings. Many linux OSes use "root" as the administrator, but for a home desktop system this is not needed, and Ubuntu disables it by default - one reason for this is so users don't simply login as root all the time as this is a security concern. Therefore when you change system settings, you need to elevate your permissions, which we use sudo for. In a sense, it makes you think twice before changing something that can have serious effects on your system.

---

### Post by ndex477 on 2011-05-15
O.K. Thank you very much.

---

### Post by JKyleOKC on 2011-05-15
There isn't any analogy between "sudo" and the C: drive in Windows. Using "sudo" is similar to the Windows "run as" command you get on a context menu.

Basically, in Linux the permission structure is much more detailed than it is in Windows. Each file or directory has three sets of permissions: one for the "owner" of the file/directory, one for the "group" to which it belongs, and a third for everyone else.

Each set has three different permission levels: read, write, and execute. For a directory, the "execute" permission allows one to view its content, so normally should be set for "everyone."

All the critical system files are owned by the "super user" or "root" but most of them are set to "read" and "execute" for everyone. Thus anyone can use them, but only the super user can modify them. This is one of the main reasons that Linux is more secure than Windows, where almost everyone (including invading malware) is an administrator by default and can modify critical files.

Your data is normally stored in your home directory, which is somewhat like the "My Documents" area of Windows but which also holds all your personal configuration settings, like the Windows Registry "user.dat" hive. In the home directory and its subdirectories, you are the owner, and everyone else has read-only permission by default (but you can change this on an individual basis).

The "sudo" program allows certain users (those who belong to the administrator group, and the user ID created at install time is automatically made a member of that group) to have "super user" power for the duration of a single command, but normally requires that the user prove his/her identify by entering the login password -- and does not echo anything to the screen to indicate that it's being accepted. To make life easier when you have to do lots of configuration, the program remembers the password for 15 minutes after it's entered and won't ask for it again during that time.

Hope this helps! It's quite a bit different from the way Windows works, but doesn't get in one's way very often.

As for the C: drive analogy, the closest that Linux offers is the "/" partition, which shows up in "Places" as "File System" and holds all of the other directories. In Linux, drive letters aren't used. Instead, "partitions" take their place, but each partition has to be mounted to the file system in order to be used at all.

---

