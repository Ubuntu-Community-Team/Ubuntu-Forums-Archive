---
title: "Accessing files through text? (Similar to &quot;Start -&gt; Run&quot; in Windows)"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by frustratednerd on 2010-06-11
Hi, I'm a newly transitioned Xubuntu user from Windows. In Windows, whenever I wanted to access a folder or a certain file, I was used to simply clicking "Start -> Run" and typing in the pathname.

Is this also possible to do in Xubuntu?

---

### Post by WinterRain on 2010-06-11
Yes. Just open a terminal, and as an example we'll select a text file on the desktop.
```
gedit /home/username/Desktop/weather_report.txt
```
gedit would be the application for viewing the text file. The above can also be written as the following:
```
gedit ~/Desktop/weather_report.txt
```
the ~ replaces /home/username

If I wanted to open a music file in my Music folder with vlc,
```
vlc ~/Music/rocketman.mp3
```

I'm sure other people will chime in with info. Enjoy.

Oh, btw, if the file in question has a space in it, such as- **job report.txt**, it would be typed into the terminal as: **job\ report.txt** otherwise it will not open.

---

### Post by blchinezu on 2010-06-11
the only thing you want to pay attention when you want to directly run a file is to make sure it has execute permissions.. which usually (if it's a script or user made file) doesn't have.

so you run this:
```
chmod +x /path/to/file/filename.extension
```and then you can simply run the file:
```
/path/to/file/filename.extension
```




> Oh, btw, if the file in question has a space in it, such as- **job  report.txt**, it would be typed into the terminal as: **job\  report.txt** otherwise it will not open
or just write it between quotes
instead of writing: [I]/home/user/new**\** folder/my**\** script.sh
[/I]just write: **"***/home/user/new folder/my script.sh***"**

---

### Post by WinterRain on 2010-06-11
> **blchinezu said:**
> 
or just write it between quotes
instead of writing: [I]/home/user/new**\** folder/my**\** script.sh
[/I]just write: **"***/home/user/new folder/my script.sh***"**

Either way it's 2 extra keystrokes. ;)

---

### Post by frustratednerd on 2010-06-11
Thanks for the help guys. But is there any way to open a **folder** through terminal as well? Or is it just possible for files?

Oh yeah, and if this helps, some of the files and folders I will want to open are on my secondary HDD (/media/[name of HDD]).

---

### Post by blchinezu on 2010-06-11
**cd** is still the same
here you won't have to change the hdd by **d:** or **c:** as everything is a tree structure under [B]/

[/B]some equivalents:
**dir** = **ls**
**del** = **rm**
**copy** = **cp**
**move** = **mv**
**ren** = **mv** (it actually moves the file under another name)

and that should do it for start


as for winterrain
> **WinterRain said:**
> Either way it's 2 extra keystrokes. ;)
in that case yes... but in more complex trees you might just want to use the quotes

---

### Post by julio_cortez on 2010-06-11
> **WinterRain said:**
> The above can also be written as the following:
```
gedit ~/Desktop/weather_report.txt
```the ~ replaces /home/username
For users that don't have the ~ on the keyboard, would this be the same?
```
cd
gedit ./Desktop/weather_report.txt
```

> **blchinezu said:**
> just write: **"***/home/user/new folder/my  script.sh***"**
And that's how I learned something new also today :D

---

### Post by EssexEagle on 2010-06-11
> **frustratednerd said:**
> Thanks for the help guys. But is there any way to open a **folder** through terminal as well? 

```
nautilus */path/to/folder*
```

Instead of using a terminal you can also type Alt+F2 to bring up a command box just like Start > Run in Windows.


Edit: Actually I don't know whether Nautilus is the file manager used in Xubuntu, but it is the one used by default in Ubuntu.  If Xubuntu uses something else then obviously use that in the command instead.

---

### Post by 3rdalbum on 2010-06-11
Instead of 'gedit' and 'nautilus', which are Ubuntu-specific programs, use 'mousepad' and 'thunar' respectively.

---

