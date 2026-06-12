---
title: "best way to set up a network to share files"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by jimmybarcelona on 2009-02-12
This is my first post ever on ubuntu forums, so I'm sorry if I'm asking something exceedingly obvious. I'm completely new to the world of ubuntu, though learning a lot. I suspect there are several possible ways to accomplish what I'm trying to do, so I was hoping that if I laid out a scenario, perhaps someone could help me find the best way to set it up so I'm not chasing my tail with thing that wouldn't work anyways.

     I have 3 computers running ubuntu hardy heron in a lab at the school where I work. They are mainly used by students to access the internet and write papers. It is a public lab, so each student be sitting at a different computer each time. Should I set up a shared folder (with sticky bits enabled) on one of the computers and put a desktop link to it in each of the student's Desktop folders? 

     I also have another desktop ubuntu hardy heron computer in my office. Right now it has no monitor, mouse, or keyboard attached to it. If I want to use it I log into it via my laptop using XDMCP. Would it be better to just set that computer up as a server?

     Any links, resources, or suggestions would be helpful. Thanks!

---

### Post by ethoxyethaan on 2009-02-12
right click on the desktop and add a quick launcher,
use this as the command:
```
nautilus smb://hello-world/
```
Replace /hello-world/ with the actual samba share server, if the students click this it will open the PC with the files.
you could make a account for every student on the server and hand out passwords, so they can safe / access files on the PC without deleting each-others content.

If you need help making accounts or Creating shared folder, just ask.

---

### Post by jimmybarcelona on 2009-02-12
Sounds good. Setting up the launcher is definitely doable. Another quick question: We get anywhere from 5 to 20 students a year. Rather than create each account individually and then add the launcher, is it possible to create a group called "students", and possibly tweak a config file somewhere so that whenever I add a new user the launcher will automatically be added to any new user assigned the group "student"?

---

### Post by ethoxyethaan on 2009-02-12
Ok its "Kinda" simple, but you just need to know how, 

i'll write you a howto once i figure out how to do it Via command line, since you don't have a monitor on the other PC.

how to:

```

sudo su
cd /usr/share/applications/
> students.desktop
gedit students.desktop

```

paste this:
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=student-share
Type=Application
Terminal=false
Icon[en_US]=nautilus
Exec=nautilus smb:///
Name[en_US]=student-share
Icon=nautilus
Comment[en_US]=

```

```

chmod 755 ./students.desktop
```


save in that same terminal after adding all the students (AS ROOT):
```
cp /usr/share/applications/students.desktop /home/*/Desktop/students.desktop
```

---

### Post by jimmybarcelona on 2009-02-12
alright, I think I got it. I've spent about an hour or more on the internet looking up all of the commands I didn't know. I don't just want to get it done, I want to learn so I can do things like this myself.

"sudo su" allows me to run bash as a root

"cd /usr/share/applications/" obviously changes me into the applications directory, which appears to be a folder containing what I would guess to be all of the applications that every user has access to?

"> students.desktop" When I ran it, it created a file called "students.desktop" I thought that the ">" symbol was used for redirecting output from a command into a file. If it is used without a command preceeding it, is it a shortcut that is equivalent to mkdir, but for files instead of directories?

"gedit students.desktop" This one I knew. It opens the "students.desktop" file in the gedit application in the gui.

All of that stuff I was supposed to paste in there, I didn't understand what it was. I'm assuming it was a program to make the launcher?

"chmod 755 ./students.desktop" Umm... that would change the file "students.desktop" to have rwx permissions for owner (root), and r-x permissions for group and others, correct?

Okay, then I use "adduser" (still working as root) to add all of the students. Correct?

"cp /usr/share/applications/students.desktop /home/*/Desktop/students.desktop"   And this command would copy the student.desktop launcher essentially onto the desktop of every user with their home folder in the /home directory, correct? Because of the wildcard (*)? Which by default would be every user on the system, correct? 

If necessary, I could avoid having staff folders affected by this by possibly storing all of my staff accounts in /home/staff/USERNAME? 

Wow, amazingly, after some time looking things up I think I understand all of that. Thanks so much for the help. It will be a few weeks before I have the complete student registry. So I have some time yet, but I didn't want to wait until the last minute to figure things out. Thanks so much!

---

