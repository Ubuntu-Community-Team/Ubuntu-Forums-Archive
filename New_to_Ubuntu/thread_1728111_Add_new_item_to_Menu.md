---
title: "Add new item to Menu"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by IHeequ5i on 2011-04-13
I have an application that I currently run from Terminal by cd'ing to the proper directory and executing the command "./program-name".  I'd like to add an item to my Applications menu so I can launch it.

Putting /path/to/file/name as the command doesn't work. I get a brief flicker as (I assume) the program tries to load, and then nothing.

If I use the "Open in Terminal" option, the terminal window appears briefly and then closes.

Any ideas?

---

### Post by seawolf167 on 2011-04-13
You can add an item to the Applications menu by right clicking the applications menu and selecting "Edit Menus", then config as you like.

You can also create a custom launcher by right-clicking the panel, then selecting to add to panel and make a custom launcher with your program/path. Additionally, you can hit [ALT][F2] to open the run box where you can launch a program.

---

### Post by dcsoldschool53 on 2011-04-13
**Right click on Application > Edit Menus Search where you want to place your new entry. Click New Item. When the new box pops up, enter you information in there. Add the icon for it too.**
[B]
Here is an example.[/B]

[B]Name: XnView
Command: /home/dcsoldschool53/Downloads/XnViewMP-035/xnview.sh
Comment:A program similar to infanview
icon: /home/dcsoldschool53/Downloads/XnViewMP-035/xnview.png[/B]

---

### Post by IHeequ5i on 2011-04-13
> **dcsoldschool53 said:**
> **Right click on Application > Edit Menus Search where you want to place your new entry. Click New Item. When the new box pops up, enter you information in there. Add the icon for it too.**
[B]
Here is an example.[/B]

[B]Name: XnView
Command: /home/dcsoldschool53/Downloads/XnViewMP-035/xnview.sh
Comment:A program similar to infanview
icon: /home/dcsoldschool53/Downloads/XnViewMP-035/xnview.png[/B]

Doesn't work. Same results as listed above.

---

### Post by Nytram on 2011-04-13
> **Doomspark said:**
> Doesn't work. Same results as listed above.

I think the reason it's not working is because you need to CD to the right directory.

Create a shell script with the commands you use to start the program, eg:

[B]cd program_dir
./program[/B]

Then point your launcher to the shell script.

---

### Post by IHeequ5i on 2011-04-13
> **Nytram said:**
> I think the reason it's not working is because you need to CD to the right directory.

Create a shell script with the commands you use to start the program, eg:

[B]cd program_dir
./program[/B]

Then point your launcher to the shell script.

I'll try that and post back. I assume I can use any text editor to create the script?

---

### Post by Nytram on 2011-04-13
> **Doomspark said:**
> I'll try that and post back. I assume I can use any text editor to create the script?

Yes any text editor will do. After creating the script set the executable flag (in Nautilus right-click the file, Properties/Permissions) or in your launcher use **sh  path/yourscriptname** as the command.

---

### Post by dcsoldschool53 on 2011-04-13
[B]Can you tell me the extract name of the program that you are talking about. You may need to run the chmod command to make it executable first.

See what your Read me text has to say for that program.
[/B]

---

### Post by dcsoldschool53 on 2011-04-13
[B]Check out this link for using the chmod command.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

If this works, try my example again, and don't forget to mark the thread as solved.
[/B]

---

### Post by ankspo71 on 2011-04-13
Hi,
Is this a command line program that runs inside the terminal, or a graphical application that isn't supposed to need the terminal?
If it is a command line application then try changing your start menu entry to launch the program using the terminal:

```
gnome-terminal -e /path/to/application
gnome-terminal -e 'sh /path/to/application'
gnome-terminal -e 'bash /path/to/application'

```

If it is a graphical application, then as the other posters have mentioned, try using "sh" (or even "bash") to launch the script or application.

```
sh /path/to/application
bash /path/to/application
```

Also, like the other posters have mentioned too, make sure to mark the application (or script) as executable:
This can be done by right clicking on the application (or script), select properties, click on the permissions tab, and enable "allow executing file as program".
Hope this helps.

---

### Post by cmcanulty on 2011-04-13
I find this issue one of the most difficult with Ubuntu. Often I install an app and can't find it anywhere. So I go to synaptic find it and click properties which lists a ton of files to look through to try and find the app so I can set a menu shortcut. Often it seems none of them work to open to app.This really needs improvement.

---

### Post by sisco311 on 2011-04-13
> **Doomspark said:**
> I have an application that I currently run from Terminal by cd'ing to the proper directory and executing the command "./program-name".  I'd like to add an item to my Applications menu so I can launch it.


Try:
```
sh -e "cd /path/to/dir && ./program name"
```

The issue is that the application must be executed from a specific working directory. In a .desktop file you can set the working directory with the Path key, but alacarte does not allow you to set the value of this key. 

So you either use the above code to launch the application or create the launcher's .desktop file manually (or create it with alacarte and add the Path key manually).  

e.g.

~/.local/share/applications/application.desktop
```
**[Desktop Entry]**
Version=1.0
Type=Application
Terminal=false
**Name=application**
Icon=/path/to/icon.png
[B]Path=/path/to/dir/
Exec=/path/to/dir/application[/B]

```

---

### Post by jtarin on 2011-04-13
What's the name of the application?

---

### Post by dcsoldschool53 on 2011-04-14
[B]> **Doomspark said:**
> I have an application that I currently run from Terminal by cd'ing to the proper directory and executing the command "./program-name".  I'd like to add an item to my Applications menu so I can launch it.

Putting /path/to/file/name as the command doesn't work. I get a brief flicker as (I assume) the program tries to load, and then nothing.[/B]> **Doomspark said:**
>  [B]

If I use the "Open in Terminal" option, the terminal window appears briefly and then closes.[/B] [B]

Any ideas?[/B] [B]

What you actually downloaded was a script from the Internet. I did not understand why this[/B] [quote=dcsoldschool53] [B]Name: XnView
Command: /home/dcsoldschool53/Downloads/XnViewMP-035/xnview.sh
Comment:A program similar to infanview
icon: /home/dcsoldschool53/Downloads/XnViewMP-035/xnview.png[/B][/quote][B]

did not work for you, until I went to my friend's computer. I had written a script, and added it to applications for her. She does not like doing anything from the terminal. So the correct way to add it to a menu is:[/B] [B]
```
 Name: Program-name
```[/B]```
**Command: ****/home/user-name/Directory-name/./Program-name**
```**There is no space between the /./**

---

