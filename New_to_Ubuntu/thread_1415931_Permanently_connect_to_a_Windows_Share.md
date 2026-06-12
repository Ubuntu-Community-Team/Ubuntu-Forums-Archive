---
title: "Permanently connect to a Windows Share"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by RedOctober on 2010-02-25
I have ubuntu 9.10 installed on over half of my clinic computers.  All working great.  I would like to connect the Ubuntu units to a MS Windows 2003 Server share.  I have the share name and passwords and folder all set up, and I can successfully connect to it from Ubuntu using "Places/Connect to server..."

However, I can't "save" the resulting desktiop icon, nor it's settings, so every time the user logs out, they loose the share connection and of course, don't want the hassle of filling in properties to reconnect.

How do I save the connection so that it either logs into the share automatically, or, at least will only ask for a password on double click an icon or some such.

I tried the "Save running application" under "Startup Applications" and it did not keep the share connection next reboot.

Thanks in advance for any help.

---

### Post by earthpigg on 2010-02-25
hi,

> How do I save the connection so that it either logs into the share automatically, or, at least will only ask for a password on double click an icon or some such.

look at the files in /usr/share/applications... open a few in your favorite text editor.

look at the "Exec" line in one, that is the command that is run when that icon is double clicked on.

make your own .desktop file to do what you want (this means you will first have to learn the command line way to connect to the server), then put that on the /home/username/Desktop of each user.

that's the easiest way i can think of, but someone else may have an easier way.

---

### Post by rustutzman on 2010-02-25
I use the bookmark feature to save my network connections. When you connect tell the system to remember the password forever and then bookmark the connection.

Russ

---

### Post by DennisFolsom on 2010-02-26
Earthpigg has part of the solution.  You need to find the syntax to mount the drive(s) from the command line.  However, I have a different suggestion on how to use them.

I'm not up-to-date on the specifics right now, but here's a concept that I remember from years ago when I used to administer Unix and VMS systems.

There are script files that run when your systems boot up that can be customized.  There are other scripts that run when a user logs in.  You will have to research which one would be the best place to put your mounting commands.  Since you seem to be dealing with a situation involving multiple users, I would suggest the boot scripts.

Since I don't remember the syntax off-hand, I'll outline my concept in psuedo-code:

Put an empty file in the root of each share or disk you want to mount to serve as a flag.  Name it something like *MountThis.flag* and make it a read-only file.

In the appropriate boot script, place the following logic:[INDENT][I]If not fileexists //servername/sharename/MountThis.flag then
[/I][INDENT][I]Mount //servername/sharename as alias on mountpoint
[/I][/INDENT]*end if*

[/INDENT]This way, the system will only attempt to mount the share if it is not already mounted.  When the user logs in, the share will be mounted already.

I'm relatively new at Ubuntu Linux.  Perhaps someone else can give you the file this logic should be placed in, and the exact syntax.  However, a little digging in the documentation should yield the answer.  

We used essentially this logic for years in a large multi-user CADD system.  An advantage of using the flag file as a test is that you can quickly rename it if you need to temporarily take the disk out of service without editing the scripts.

---

