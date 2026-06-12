---
title: "How do I add my own 'sound Theme' to Sound preferences?"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by DayLite on 2010-09-16
I want to add my own alert sounds to "Sound Preferences". How do I add it? I use Ubuntu 10.04. 

The only sound theme that I can select is 'Ubuntu', no other choices are listed.

---

### Post by vagrale13 on 2010-09-16
> **DayLite said:**
> I want to add my own alert sounds to "Sound Preferences". How do I add it? I use Ubuntu 10.04. 

The only sound theme that I can select is 'Ubuntu', no other choices are listed.
Try to search here [http://gnome-look.org/index.php?xcontentmode=25](http://gnome-look.org/index.php?xcontentmode=25)

---

### Post by DayLite on 2010-09-16
> **vagrale13 said:**
> Try to search here [http://gnome-look.org/index.php?xcontentmode=25](http://gnome-look.org/index.php?xcontentmode=25)

I downloaded some sound themes, I don't know how to get it to show under 'sound preferences. They give install directions but I don't understand it.

---

### Post by vagrale13 on 2010-09-17
> **DayLite said:**
> I downloaded some sound themes, I don't know how to get it to show under 'sound preferences. They give install directions but I don't understand it.
Extract the archive and move the folder to */usr/share/sound*
```
cd /path/to_the/extract_folder
sudo mv folder_name /usr/share/sounds
```replace the name *folder_name* 
or use command
```
sudo nautilus
```and move the folder to the path [I]/usr/share/sound
[/I] Then go to Settings - Sounds and select :KS

---

### Post by DayLite on 2010-09-17
> **vagrale13 said:**
> Extract the archive and move the folder to */usr/share/sound*
```
cd /path/to_the/extract_folder
sudo mv folder_name /usr/share/sounds
```replace the name *folder_name* 
or use command
```
sudo nautilus
```and move the folder to the path [I]/usr/share/sound
[/I] Then go to Settings - Sounds and select :KS
I extracted the folder and when I tried to move it (drag) it said I didn't have permission. I don't understand how to use the terminal so I extracted it myself. Now I can't get permission.
[B]
I followed your instructions and this is what I got.[/B]

> daylite@daylite-desktop:~$ cd /path/to_the/extract_folder
bash: cd: /path/to_the/extract_folder: No such file or directory
daylite@daylite-desktop:~$ sudo Borealis /usr/share/sounds
sudo: Borealis: command not found]

---

### Post by gandaran on 2010-09-17
> **DayLite said:**
> I extracted the folder and when I tried to move it (drag) it said I didn't have permission. I don't understand how to use the terminal so I extracted it myself. Now I can't get permission.
[B]
I followed your instructions and this is what I got.[/B]
try this simple way to move files to root, move the extracted file or folder to home user directory first, (this way no need to cd the terminal) open the terminal and type
```
sudo mv name /usr/share/sounds
```
change the "name" to the actual file or folder name to move
its very simple if you do it right.

---

### Post by DayLite on 2010-09-17
> **gandaran said:**
> try this simple way to move files to root, move the extracted file or folder to home user directory first, (this way no need to cd the terminal) open the terminal and type
```
sudo mv name /usr/share/sounds
```change the "name" to the actual file or folder name to move
its very simple if you do it right.

[SIZE=5][COLOR=Black]**It worked !**[/COLOR][/SIZE] :D
Thank you very much.

---

### Post by DayLite on 2010-09-17
> **DayLite said:**
> [SIZE=5][COLOR=Black]**It worked !**[/COLOR][/SIZE] :D
Thank you very much.

[SIZE=3]**New problem**[/SIZE] I moved additional folders but they don't show up in the drop down menu in Preferences>sound.

The only one that is there is the first.

---

### Post by gandaran on 2010-09-17
> **DayLite said:**
> [SIZE=3]**New problem**[/SIZE] I moved additional folders but they don't show up in the drop down menu in Preferences>sound.

The only one that is there is the first.
have you checked in /usr/share/sounds if the folders are there?

---

### Post by DayLite on 2010-09-17
> **gandaran said:**
> have you checked in /usr/share/sounds if the folders are there?

Yes, the other folders are there. I can't figure out why only one has showed up.

---

### Post by gandaran on 2010-09-18
> **DayLite said:**
> Yes, the other folders are there. I can't figure out why only one has showed up.
then probably they aren't the right sound applications, remove them and try another.
the remove command is 
```
sudo rm -r /usr/share/sounds/name
```
change the "name" to the actual folder name to remove
or open root nautilus and delete the folder, use the delete key don't send it to trash.
to open root nautilus type in terminal
```
gksu nautilus
```

---

### Post by DayLite on 2010-09-18
> **gandaran said:**
> then probably they aren't the right sound applications, remove them and try another.
the remove command is 
```
sudo rm -r /usr/share/sounds/name
```change the "name" to the actual folder name to remove
or open root nautilus and delete the folder, use the delete key don't send it to trash.
to open root nautilus type in terminal
```
gksu nautilus
```
Thanks

---

### Post by vagrale13 on 2010-09-18
The theme you download, is for **KDE**, and it doesn' t work in **GNOME**!
The folder with the sound theme must be has one folder with name **stereo** and one archive with the name **index.theme**.
Then must be works!

e.g.
Download this sound theme [http://gnome-look.org/content/show.php/Guitar+theme+for+sounds%3A+Jam?content=120602](http://gnome-look.org/content/show.php/Guitar+theme+for+sounds%3A+Jam?content=120602)
and move the archive to home folder /home/username
open terminal and run
```
tar -xzf *-Jam.tar.gz
sudo mv Jam /usr/share/sounds
```Then go *System - Preferences - Sounds* and choose Jam to the sound theme!

To remove the theme, run the command
```
sudo rm -rf /usr/share/sounds/Jam
```Please be careful with the remove command.
Make a copy-paste to avoid wrong!

All the commands, you can replace with
to extract the archive - run  
```
sudo nautilus
```and move the sound theme folder (e.g. Jam) to folder */usr/share/sounds*
And to delete, read the post of **gandaran**

When run the command **sudo nautilus **or **gksudo nautilus** you have root permissions, then be careful what you doing, and if you don' t know 100% what you doing, don' t do it! :KS

---

### Post by DayLite on 2010-09-18
> **vagrale13 said:**
> The theme you download, is for **KDE**, and it doesn' t work in **GNOME**!
The folder with the sound theme must be has one folder with name **stereo** and one archive with the name **index.theme**.
Then must be works!

e.g.
Download this sound theme [http://gnome-look.org/content/show.php/Guitar+theme+for+sounds%3A+Jam?content=120602](http://gnome-look.org/content/show.php/Guitar+theme+for+sounds%3A+Jam?content=120602)
and move the archive to home folder /home/username
open terminal and run
```
tar -xzf *-Jam.tar.gz
sudo mv Jam /usr/share/sounds
```Then go *System - Preferences - Sounds* and choose Jam to the sound theme!

To remove the theme, run the command
```
sudo rm -rf /usr/share/sounds/Jam
```Please be careful with the remove command.
Make a copy-paste to avoid wrong!

All the commands, you can replace with
to extract the archive - run  
```
sudo nautilus
```and move the sound theme folder (e.g. Jam) to folder */usr/share/sounds*
And to delete, read the post of **gandaran**

When run the command **sudo nautilus **or **gksudo nautilus** you have root permissions, then be careful what you doing, and if you don' t know 100% what you doing, don' t do it! :KS

Thanks, I did notice that the other themes didn't have a folder that said 'stereo'.  I did move all the sounds to the folder that said 'stereo' but that didn't make a difference.

The theme that works is[ **Implora**]("http://gnome-look.org/content/show.php/Implora?content=129930"). The ones that didn't:
[Borealis]("http://gnome-look.org/content/show.php/%22Borealis%22+sound+theme?content=12584")
[Cleanus]("http://gnome-look.org/content/show.php/Cleanus?content=61245")
[Kinper]("http://gnome-look.org/content/show.php/Kinper?content=50607")
[B]
[/B]

---

