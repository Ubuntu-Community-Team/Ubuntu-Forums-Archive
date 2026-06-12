---
title: "media converter"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by wizardfingers on 2009-11-13
Is there a converter like PSPVC (a PSP video converter) for Ubuntu or an alternate program. It doesn't have to be psp dedicated but I would prefer it is.

---

### Post by scorp123 on 2009-11-13
What do you want to achieve? There are plenty of video converters out there. Some have a GUI but are not so powerful, others are extremely powerful but you'll have to learn their syntax because they have no GUI.

I myself prefer the latter ones.

Maybe you'd also like to read this thread:
[http://ubuntuforums.org/showthread.php?t=1228294](http://ubuntuforums.org/showthread.php?t=1228294)

Towards the bottom of the page someone suggests a program called "iriverter" .... maybe you could use that? In the same thread there is also an example for the "mencoder" shell program. Works too.

---

### Post by ricardo.gloe on 2009-11-13
You can try Mobile Media Converter [HTML]www.miksoft.net/mobileMediaConverter.htm[/HTML].

Very simple but practical converter.

There is also ffmpeg (this is a command line converter).
```
sudo apt-get install ffmpeg
```

Fortunately, if you prefer graphical, there is a GUI for ffmpeg called winff at [http://winff.org](http://winff.org). It says it's for 9.04 but it may work for 9.10.

---

### Post by brandonsh on 2009-11-13
If all else fails, you could try to run PSPVC in WINE.

---

### Post by cranecreek on 2009-11-13
> **scorp123 said:**
> What do you want to achieve? There are plenty of video converters out there. Some have a GUI but are not so powerful, others are extremely powerful but you'll have to learn their syntax because they have no GUI.

I myself prefer the latter ones.

Maybe you'd also like to read this thread:
[http://ubuntuforums.org/showthread.php?t=1228294](http://ubuntuforums.org/showthread.php?t=1228294)

Towards the bottom of the page someone suggests a program called "iriverter" .... maybe you could use that? In the same thread there is also an example for the "mencoder" shell program. Works too.

What terminal program do you suggest scorp123 since you like it so much

---

### Post by sandyd on 2009-11-13
ffmpeg, avidemux and winff whould be what your looking for.

---

### Post by mangurt on 2009-11-13
Winff, handbrake, mencoder.....there are so many it's not even funny.

---

### Post by scorp123 on 2009-11-14
> **cranecreek said:**
> What terminal program do you suggest scorp123 since you like it so much I guess you didn't follow the link I posted? :)

**mencoder** .... does pretty much anything one would need. Others here have mentioned it too. What I do: I Google up the syntax I need and then place it into shell scripts, so I don't have to bother remembering it all everytime I need something ...

So I have a script e.g. "Convert_to_Archos2.sh" that will execute mencoder with the right parameters for my wife's "Archos 2" media player, and so on. Or "Convert_to_XVID.sh" which would convert a file to XVID, etc.

If you look into "Nautilus Actions" you can even combine such scripts with the file manager. e.g. right-click on a file, choose the desired action such as "Convert to XVID ... " and it just happens automagically, right from the file manager.

If you Google for "Nautilus Actions" or "Nautilus Scripts" and/or search this very forum you should find plenty of examples.

---

