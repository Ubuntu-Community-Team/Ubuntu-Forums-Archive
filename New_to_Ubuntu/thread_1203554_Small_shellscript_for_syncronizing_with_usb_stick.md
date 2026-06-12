---
title: "Small shellscript for syncronizing with usb stick"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by supasnashbuhl on 2009-07-03
Hi!
First things first: You have a very cool forum and i've got lots of help here even without ever writing here my self so thank you for that!
Now to my little "project" here:
I'm playing a little around with really small shell scripts, and i'm currently trying to make my usb-stick autosync with my netbook. The idea is that i have a ~/Sync folder in which i place links to directories and files that i want to synchronize and a Sync folder on the Stick where the synchronized files should wind up. Everytime i sync the stick i want to save the changes to a logfile. So here is what i've come up with so far:

```

date >> /media/disk/Sync/Synclog.txt
echo >> /media/disk/Sync/Synclog.txt ""
cp -L -u -r -v >> /media/disk/Sync/Synclog.txt ~/Sync /media/disk
echo >> /media/disk/Sync/Synclog.txt ""
cp -L -u -r -v >> /media/disk/Sync/Synclog.txt /media/disk/Sync ~/
echo >> /media/disk/Sync/Synclog.txt ""
echo >> /media/disk/Sync/Synclog.txt ""

```BUT there are a few problemos now.. First of all the piping to the Synclog.txt doesn't work well with cp:
This is the terminal output:
```

cp: reguläre Datei „/media/disk/Sync/workspace/propro4/java.util.*“ kann nicht angelegt werden: Invalid argument
cp: reguläre Datei „/media/disk/Sync/workspace/propro3/src/java.util.*“ kann nicht angelegt werden: Invalid argument
cp: reguläre Datei „/media/disk/Sync/workspace/propro3/bin/java.util.*“ kann nicht angelegt werden: Invalid argument
cp: Überschreiben des Nicht&#8208;Verzeichnisses „/home/jokke/Sync/workspace“ mit Verzeichnis „/media/disk/Sync/workspace“ nicht möglich.
cp: Überschreiben des Nicht&#8208;Verzeichnisses „/home/jokke/Sync/Bilder“ mit Verzeichnis „/media/disk/Sync/Bilder“ nicht möglich.
cp: Überschreiben des Nicht&#8208;Verzeichnisses „/home/jokke/Sync/Uni“ mit Verzeichnis „/media/disk/Sync/Uni“ nicht möglich.

```Sorry for the german. "reguläre Datei ,,blablabla" kann nicht angelegt werden" means regular file "blablabla" cannot be created, or sth.. And "Uberschreiben des Nicht-Verzeichnisses "bla" mit Verzeichnis "blabla" nicht möglich" means overwriting the not-directory "bla" with the directory "blabla" not possible.
And this is what my logfile says:
```

Do 2. Jul 19:44:30 CEST 2009

„/home/jokke/Sync/workspace/propro4/java.util.*“ -> „/media/disk/Sync/workspace/propro4/java.util.*“
„/home/jokke/Sync/workspace/propro3/src/java.util.*“ -> „/media/disk/Sync/workspace/propro3/src/java.util.*“
„/home/jokke/Sync/workspace/propro3/bin/java.util.*“ -> „/media/disk/Sync/workspace/propro3/bin/java.util.*“

„/media/disk/Sync/Sync~“ -> „/home/jokke/Sync/Sync~“
„/media/disk/Sync/Sync“ -> „/home/jokke/Sync/Sync“
„/media/disk/Sync/Synclog.txt“ -> „/home/jokke/Sync/Synclog.txt“
„/media/disk/Sync/Synclog.txt~“ -> „/home/jokke/Sync/Synclog.txt~“

```That is really ennoying, since it looks as if the files were copied just fine which clearly wasn't the case. How could i help that? Now to the causes of those errors.. I think the problem with the java.util.* files is the *.. Probably treats as a wildcard..? The second ones, the ones back from the stick to the ~/Sync directory.. How can tell the shell, that i want to update the linked directories, not the links?

---

### Post by Elfy on 2009-07-03
You already have this posted here [http://ubuntuforums.org/showthread.php?t=1202720](http://ubuntuforums.org/showthread.php?t=1202720)

Please do not post duplicates.

Thank you.

---

