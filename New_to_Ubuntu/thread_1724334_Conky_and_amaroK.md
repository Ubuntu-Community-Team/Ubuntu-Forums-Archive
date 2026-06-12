---
title: "Conky and amaroK"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by mugenfanatic on 2011-04-08
not sure if this is the right place or not

Hi guys i've been searching all over the web for a tutorial to have amarok display in my conky for the past 3 or 4 hours now and i can't seem to find a simple howto.

i have amarok 2.2.3.2 and conky 1.8.0 can someone show me a easy howto or explain to me the steps please thank you in advance

---

### Post by K.Mandla on 2011-04-08
Moved to Absolute Beginner Talk.

---

### Post by rosencrantz on 2011-04-08
Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=481720](http://ubuntuforums.org/showthread.php?t=481720)

---

### Post by mugenfanatic on 2011-04-08
> **rosencrantz said:**
> Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=481720](http://ubuntuforums.org/showthread.php?t=481720)

yes i have seen that thread but i don't really understand. I mean for my main conky i have the file .conkyrc right? now for amarok would i need another file like that also and where would i put it. Not sure what they were talking about "MySQL" really noobie sorry.

---

### Post by rosencrantz on 2011-04-08
I have never used conky before, so a lot of this is experimental for me.
MySQL is one of the database management systems Amarok can use to manage your collection, by default it's using SQLite. If you want conky to include statistics, amarok has to run on MySQL for the example code to work. 
This is what I tried:
Save [http://conky.sourceforge.net/conkyrc-ke49](http://conky.sourceforge.net/conkyrc-ke49) as ~/.conkyrc
Then create a subdirectory .conky, also in home. Save 
[http://conky.sourceforge.net/amarok-ke49](http://conky.sourceforge.net/amarok-ke49) as ~/.conky/amarok and make it executable.
I tried to get the script to work with some modifications, but it seems to be a) quite specific to someone else's machine and b) dated.
The script uses dcop calls to communicate with Amarok - dcop has been replaced by DBus since KDE4.
So this would require a lot of tweaking.
Do you have any special reason to use conky?
If you're on KDE, there are a lot of Superkaramba and Plasma system monitor widgets doing pretty much what conky does - and much more up to date.
kde-look.org has a good selection in the Karamba and Plasmoids sections.
On gnome, you'll have to look for screenlets or gdesklets.

---

### Post by mugenfanatic on 2011-04-08
> **rosencrantz said:**
> I have never used conky before, so a lot of this is experimental for me.
MySQL is one of the database management systems Amarok can use to manage your collection, by default it's using SQLite. If you want conky to include statistics, amarok has to run on MySQL for the example code to work. 
This is what I tried:
Save [http://conky.sourceforge.net/conkyrc-ke49](http://conky.sourceforge.net/conkyrc-ke49) as ~/.conkyrc
Then create a subdirectory .conky, also in home. Save 
[http://conky.sourceforge.net/amarok-ke49](http://conky.sourceforge.net/amarok-ke49) as ~/.conky/amarok and make it executable.
I tried to get the script to work with some modifications, but it seems to be a) quite specific to someone else's machine and b) dated.
The script uses dcop calls to communicate with Amarok - dcop has been replaced by DBus since KDE4.
So this would require a lot of tweaking.
Do you have any special reason to use conky?
If you're on KDE, there are a lot of Superkaramba and Plasma system monitor widgets doing pretty much what conky does - and much more up to date.
kde-look.org has a good selection in the Karamba and Plasmoids sections.
On gnome, you'll have to look for screenlets or gdesklets.

i just love what conky can do that's why..  ok i did the following as you requested now what would i do afterwards? is it like my gmail set up in conky? I have a file in ~/.scripts named as gmail.py

---

### Post by rosencrantz on 2011-04-08
I'm not sure where that gmail script is from (did you look at it in a text editor? Nice programmers leave comments), but I'd assume it's not conky. I don't think conky uses python - and shouldn't it be in ~/.conky?
Run conky from the command line and try to weed out the errors.
A few hints:
I assume your Amarok doesn't use MySQL, so remove everything statistics related from the amarok script.
Try to replace the dcop commands with dbus ones. I haven't found a good amarok dbus tutorial with google, so you're on your own there, sorry.

---

