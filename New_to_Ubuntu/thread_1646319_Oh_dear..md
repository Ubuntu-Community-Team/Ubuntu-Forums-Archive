---
title: "Oh dear."
date: 2010-12-15
forum: New to Ubuntu
---

### Post by Content_dog on 2010-12-15
Well, i decided "what the hell! I'm going to install ubuntu. Its feature rich and it looks great!"

WARNING: Extreme newbishness ahead. Use caution.

Unfortunately, its turned out to be quite a large ordeal. I was trying to set up a minecraft server so i downloaded the "linux" server installer. Upon double clicking it, it opens an archive with no sort of .exe file that would clue me in. Help on setting that up would be great!

Another thing, when i try to authenticate things i type my password in, hit enter but nothing happens. It sits there for ages and, upon mashing "authenticate" it eventually closes, and the program i was trying to run, doesnt run.

Any help would be great. Thanks guys
Content_dog

---

### Post by potat on 2010-12-15
Linux doesn't use .exe files; binary executables don't generally have an extension (sometimes they use ".bin"). Script files might have extensions such as .sh (shell script) or .py (Python script), but also might not. 

This is what I see on the Minecraft site:
> 
If you want to run the server on any other OS, or want to run it without the gui, it's a bit more involved.
First, make sure you can use java from the command line. On linux and mac, this should automatically work, but on windows you might want to set up a PATH system variable.
Then download minecraft_server.jar to anywhere, then launch it as:
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui


If this is what you downloaded you want to run the .jar (java archive) file using Java, with the command specified. Just make sure you "cd" to the directory where you downloaded it.

Hope this helps.

---

### Post by Content_dog on 2010-12-15
hey! thanks for the quick reply. I will try that as soon as possible. One question, how do you run commands such as the one you just gave me

---

### Post by kaldor on 2010-12-15
> **Content_dog said:**
> hey! thanks for the quick reply. I will try that as soon as possible. One question, how do you run commands such as the one you just gave me

Use Terminal (Applications > Accessories > Terminal)


[I]"Then download minecraft_server.jar to anywhere, then launch it as:
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui"[/I]

Run the Terminal command in the directory (folder) your minecraft_server.jar is located. 

For example, if it is in your Desktop:

```
cd ~/Desktop
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```

if it is in your Downloads folder:

```
cd ~/Downloads
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui
```

That should work.

"cd" means Change Directory. "~/" means */home/username*

---

### Post by qyot27 on 2010-12-15
A shortcut, if you're using the regular GNOME-based Ubuntu and Nautilus:

Use Synaptic, Software Center, or the Terminal* to install nautilus-open-terminal.  This will let you right-click in the directory you're browsing in Nautilus and use 'Open Terminal Here', which will launch the Terminal in the current directory.  Sure, 'cd' is an extremely easy command, but being able to skip a step is nice too.

*The command to issue is:
*sudo apt-get install nautilus-open-terminal*

---

### Post by Content_dog on 2010-12-15
thanks a lot for the help! now i wish i could figure out why i cant authorise things :/

---

### Post by kaldor on 2010-12-15
> **Content_dog said:**
> thanks a lot for the help! now i wish i could figure out why i cant authorise things :/

This is Ubuntu's way of keeping things secure. use *sudo* in front of a command to grant root (administrator) access.

example...

Without sudo:

```
michael@lmde-laptop /usr $ rmdir share
rmdir: failed to remove `share': Permission denied

```

The above would delete a needed system directory. Without sudo, it cannot be done.

So for your command, add sudo to the front. Instead of just "java" use "sudo java"

Edit:

> A shortcut, if you're using the regular GNOME-based Ubuntu and Nautilus:

Use Synaptic, Software Center, or the Terminal* to install nautilus-open-terminal. This will let you right-click in the directory you're browsing in Nautilus and use 'Open Terminal Here', which will launch the Terminal in the current directory. Sure, 'cd' is an extremely easy command, but being able to skip a step is nice too.

*The command to issue is:
sudo apt-get install nautilus-open-terminal

I highly recommend this. It's great to just be able to right click in any folder and say "open in terminal" :)

---

### Post by RedRat on 2010-12-15
If you are indeed a newbie and have not used Ubuntu before and this is your first attempt at using it, I think you might have bit off more than you can chew here. I would suggest that you first get comfortable with Ubuntu Gnome and then slowly move yourself to confidence in using the command line or CLI. Setting up a server, from other comments here in the forums, is a bit of a task and if you do not quite know what exactly you are doing, can lead you into a ring of despair. 

I would suggest that you get a good book on Linux/Ubuntu and do a bit of cautious exploration, especially the command line. Good Luck.

---

### Post by Content_dog on 2010-12-15
thanks for all the replies everyone! I think, for the time being, i am going to stick with windows for the most part. I am moving county soon and i will pick ubuntu up again when i am all moved in. 

Thanks again guys!
Content_dog

---

