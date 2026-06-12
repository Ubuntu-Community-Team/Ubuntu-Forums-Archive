---
title: "Creating bash file to launch minecraft server"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by Taryup on 2011-06-03
Hi!

I'm playing quite much minecraft and are also hosting servers sometimes at LAN-partys and stuff.

So what I'm wondering is how to create a desktop icon for my minecraft_server.jar (thats in another folder) and run it like this:
```
java -Xms2499M -Xmx2500M -jar minecraft_server.jar nogui
```This is because i need more memory than the normal settings, so i have to use these settings. When i cd in terminal it works fine, but when i put it in a script it doesn't work.

Thanks!

---

### Post by frankbooth on 2011-06-03
Shouldn't this do the trick?

```

#!/bin/bash
java -Xms2499M -Xmx2500M -jar /in/another/folder/minecraft_server.jar nogui

```

save it to a file called (for example): minecraft.sh
and make it executeable

**EDIT:** I'm not a big timer when it comes to bash scripting ;)

---

### Post by Taryup on 2011-06-03
That didn't work for me. There is no error. I just launch the minecraft_server.sh (that i made) with a program launcher from the desktop. What could I have done wrong? The ".sh" file contains the code you said.

---

### Post by Zorael on 2011-06-03
Try running it from a terminal and see what error messages it outputs there (if any).

```
$ ./minecraft.sh
```

---

### Post by Taryup on 2011-06-03
It said access denied when I tried to open it. Is there a command that gives me admin rights? Cause I'm admin on this account on the computer.

---

### Post by Zorael on 2011-06-03
You need to set it to be executable, else it's just a text file. Linux doesn't think in terms of file extensions the way Windows does; a file can be named **herp.txt** and still be a binary executable.

```
$ chmod +x minecraft.sh
$ ./minecraft.sh
```

---

### Post by Taryup on 2011-06-03
Still doesn't work :( Where am I gonna put the chmod? just anywhere in the ".sh" file?

---

### Post by Laforge129 on 2011-06-03
> **Taryup said:**
> Still doesn't work :( Where am I gonna put the chmod? just anywhere in the ".sh" file?

Have you tried:
edit minecraft.sh
```
#!/bin/bash
Sudo java -Xms2499M -Xmx2500M -jar /in/another/folder/minecraft_server.jar nogui
```

```
sh minecraft.sh
```

usually when it says access denied you need admin rights!

---

### Post by Taryup on 2011-06-03
Wrong post..

---

### Post by Zorael on 2011-06-03
> **Taryup said:**
> Still doesn't work :( Where am I gonna put the chmod? just anywhere in the ".sh" file?
No; you need to set the *script* to be executable, either from the terminal by running that command or graphically in a file browser. If you're not familiar with the terminal, forget my previous post.

Since what you want to create to begin with is a launcher (icon) on your desktop, you can either create the script and then make a launcher that runs it, or just make a launcher right away that does the same thing without needing the script. You need a **Folder View widget** to create such a launcher in, or alternatively have your whole desktop workspace be a Folder View.
[indent]This is determined by right-clicking your desktop and picking Settings, then in the View tab change Layout to what you want it to be. A "Desktop" *layout* houses widgets, be they either Folder Views or analogue clocks or whatnot. A "Folder View" *layout* is equavilent to the Windows desktop; it represents a folder someplace - the Desktop directory in your home being the default - and shows the files in there.[/indent]
Creating such a launcher can be done in the Applications Menu editor instead if you want the launcher to reside there.



--------------- [SIZE="3"]True launcher route (script-less)[/SIZE]

When in a Folder View, right click an empty space and pick Create New -> Link to Application.
[indent]Alternatively, right click your Applications Menu and pick Edit Applications. In there hit *New Item*. The tab names differ a bit in the two approaches, but the following guide should be easy enough to follow in either.[/indent]

**General tab**
[list][*]Name the application what you want, probably '**Minecraft Server**' or so[/list]
**Application tab**
[list][*]Description: the "alternative name" for the launcher. It has no effect when the launcher is outside the applications menu
[*]Comment: the little text that's shown when you mouseover your launcher. So you could put '**Sandbox Mining Game Serve**r' there, but it's optional
[*]Command: **java -Xms2499M -Xmx2500M -jar _[COLOR="Red"]/full/path/to/[/COLOR]_minecraft_server.jar nogui**
[*]Work path: **/full/path/to** (where **minecraft_server.jar** is located)
[*]Advanced options:
[list][*]check *Run in a terminal* and optionally *Do not close when command exits*[/list]
[/list]
**OK**

Once the launcher is created you can right-click it and then click the big icon in the General tab to change the launcher's icon.



--------------- [SIZE="3"]Script route (graphical way)[/SIZE]

Open up Dolphin and navigate to where the script is. Right-click it and select Properties. Head over to the Permissions tab and tick *Is executable*. Now try double-clicking the script and see if it starts properly. Note that this will probably make the script run in the background, which is not preferable with the Minecraft server if you want to run server commands.

Now that it's set to executable, if it *still* doesn't work then the error is elsewhere, probably in the script itself. It should no longer give an error about missing permissions, although it might give errors about not finding files, since you didn't run the script from its own directory.

You should never need to run it with sudo.


[SIZE="1"]holy markups again batman[/SIZE]

---

### Post by Taryup on 2011-06-03
I can't get into folder view. Right-clicking my desktop but I can't find any "Settings".

---

### Post by Taryup on 2011-06-03
Okey, I was in folder view. -.- And now it works. Seems that that the problem was that i didn't enter the whole path to the "minecraft_server.jar" in this command:
```
java -Xms2499M -Xmx2500M -jar (here** _[COLOR=Red]/full/path/to/[/COLOR]_ )**minecraft_server.jar nogui
```

Thank you really much for helping me out with this!

---

### Post by tvetter05 on 2011-06-20
Using Zorael's method works, only it creates a new world and files in /home/user and doesn't use my existing one in /home/user/minecraft-server.  How can I fix this?  Thanks.


```
java -Xmx1024M -Xmx1024M -jar /home/user/minecraft-server/minecraft_server.jar nogui
```

---

