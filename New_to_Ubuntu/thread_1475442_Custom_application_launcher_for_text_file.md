---
title: "Custom application launcher for text file"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Vistz on 2010-05-06
I recently installed TeamSpeak3 and I'm trying to put a shortcut on my desktop. The file I'm trying to link to is 

```
ts3client_runscript.sh
```

When I double click it, it says that it is an executable text file and gives me the option of running it.

When I create the launcher on my desktop, nothing happens when I double click it. I know there are some workarounds for this but I want to solve this problem for good.

---

### Post by jvc26 on 2010-05-08
By nothing happens, do you mean it doesnt launch it, or you get no graphical feedback as it is run in the background?

J

---

### Post by ankspo71 on 2010-05-08
Hi,
Try right clicking on the desktop and create a new shortcut but using "sh" as part of the command like this:
```
sh /path/to/ts3client_runscript.sh
```

---

### Post by QLee on 2010-05-08
[QUOTE=Vistz]I recently installed TeamSpeak3 and I'm trying to put a shortcut on my desktop. The file I'm trying to link to is 

```
ts3client_runscript.sh
```When I double click it, it says that it is an executable text file and gives me the option of running it.

When I create the launcher on my desktop, nothing happens when I double click it. I know there are some workarounds for this but I want to solve this problem for good.[/QUOTE]

Show us the command line you used in the custom launcher.

If I had such a situation, I would try the command I used in a terminal and see if it completed or dropped an error message. The error message might point you in the right direction.

You might decide to have the launcher run the command in a terminal (an option).

I don't know anything about Teamspeak.

---

### Post by Vistz on 2010-05-08
> **jvc26 said:**
> By nothing happens, do you mean it doesnt launch it, or you get no graphical feedback as it is run in the background?

J
It doesn't launch. And I'm nearly certain it's not running in the background.

> **ankspo71 said:**
> Hi,
Try right clicking on the desktop and create a new shortcut but using "sh" as part of the command like this:
```
sh /path/to/ts3client_runscript.sh
```

Tried that. Still doesn't work.

> **QLee said:**
> Show us the command line you used in the custom launcher.

If I had such a situation, I would try the command I used in a terminal and see if it completed or dropped an error message. The error message might point you in the right direction.

You might decide to have the launcher run the command in a terminal (an option).

I don't know anything about Teamspeak.

I didn't use the command line. I right-clicked on the desktop, chose "Create Launcher" and navigated to my file.

---

### Post by 3rdalbum on 2010-05-08
> **Vistz said:**
> I didn't use the command line. I right-clicked on the desktop, chose "Create Launcher" and navigated to my file.

When you create the launcher, in the dropdown menu choose "Application in Terminal".

---

### Post by Vistz on 2010-05-08
> **3rdalbum said:**
> When you create the launcher, in the dropdown menu choose "Application in Terminal".

When I run it like this, I see a window flash for an instant before disappearing.

---

### Post by Sealbhach on 2010-05-09
Try this command:

```
sh -c cd /path/to/ && ./ts3client_runscript.sh
```
.

---

### Post by Vistz on 2010-05-09
> **Sealbhach said:**
> Try this command:

```
sh -c cd /path/to/ && ./ts3client_runscript.sh
```
.

Just to clarify, should I replace /path with the path of the file or should I replace /path/to? Or neither?

---

### Post by QLee on 2010-05-09
[QUOTE=Vistz]Just to clarify, should I replace /path with the path of the file or should I replace /path/to? Or neither?[/QUOTE]

Sealbhach gave you a "generic" command string that changes to the directory where the file resides first (so the system prompt is in the directory where the file lives). If the file is in the path of the user running it, changing to that directory first is not strictly necessary. It's all about making sure the executable is found, Vistz, your choice of how you do it.

---

### Post by Sealbhach on 2010-05-09
> **Vistz said:**
> Just to clarify, should I replace /path with the path of the file or should I replace /path/to? Or neither?

If your file is on the desktop, it should be changed to

/home/Vistz/Desktop

or whatever username you have. 


.

---

### Post by Vistz on 2010-05-09
This was the command I used

```
sh -c cd /home/Vistz/Downloads/ && ./ts3client_runscript.sh
```

That didn't work. When I place the launcher in the same folder as the file, and simply use the name of the file as the command, I get an error message.

```
There was an error launching the application.
Details: Failed to execute child process "ts3client_runscript.sh" (No such file or directory)
```

---

### Post by QLee on 2010-05-09
Well, where exactly is the file, from what you wrote it seems to be in ~home/Downloads and that is sort of an odd place for you to have placed an executable.

If it will run from a dbl click in the file browser, then the same user that was able to run it that way should be able to run it from the CLI in the directory. 

As I mentioned previously, I have no experience with Teamspeak, I did look at the website though and they have both a blog and forum, maybe that forum would have more Teamspeak users, there is a FAQ and it looks like a page of tutorials too, maybe that might help you.

---

