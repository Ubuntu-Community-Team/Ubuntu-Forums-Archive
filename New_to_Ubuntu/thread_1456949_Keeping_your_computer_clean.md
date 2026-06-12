---
title: "Keeping your computer clean"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by noworldorder on 2010-04-17
With windows I used an uninstaller program tro remove programs so that I would get rid of everything.  Is this necessary with Ubuntu?  I recently removed a couple programs and discovered that the file folder and some files were still on my computer.  Does Ubuntu get messy with a lot of installing and installing like windows does?

I have a messy house but I want a tidy computer.

Thanks - chris

---

### Post by Yvan300 on 2010-04-17
For me i use ubuntu tweak to do just about everything. Try it and you would be able to meet your needs !

---

### Post by wojox on 2010-04-17
Did you run:

```
sudo apt-get purge <packageName>
```

```
sudo apt-get autoremove
```

Where did you find the files and folder? If it was your home directory you need to delete those yourself.

---

### Post by noworldorder on 2010-04-18
> Where did you find the files and folder? If it was your home directory you need to delete those yourself.

Yes they were in my home directory.  I deleted them via the Ubuntu Software Center.  Is it better to delete programs through the terminal?  

thanks - chris

---

### Post by gmxgeek on 2010-04-18
The software center is really just a GUI for the terminal commands above. It's mostly just preference. I personally prefer to use the terminal, just because it shows you what its doing a little more clearly than the GUI does. It's also usually faster, since the terminal laucnhes quickly, and its a single line of text rather than searching for the program.

In general, (whichever way you remove a program), ubuntu will do its best to remove uneeded files. However, if there are any files in your home directory, ubunru respects your privacy and leaves them alone.

---

### Post by Drenriza on 2010-04-18
> **wojox said:**
> Did you run:

```
sudo apt-get purge <packageName>
```

```
sudo apt-get autoremove
```

Where did you find the files and folder? If it was your home directory you need to delete those yourself.

The commands ```
sudo apt-get --purge
```
removes configuration files. I cannot see how to use this command with ```
sudo apt-get -autoremove
``` to clean up the system. Since -autoremove only removes packages that no longer are needed. This could be older versions of a specific program, that has been upgraded to a newer version.

---

### Post by 3rdalbum on 2010-04-18
Preferences files will stay in your home directory. Removing preferences files automatically when a program is removed is a Sure-Fire Disaster*. So they stay - but they're usually only a hundred kilobytes or so. Remove them if you want, but there's no reason why they can't happily sit on your computer.

*Want an example? Well, there are two note-taker programs that are very similar - Tomboy and Gnote. If you want to switch from Tomboy to Gnote, currently your existing Tomboy notes and preferences will stay on the disk, and you'll be able to import them into Gnote. If removing software also removed the preferences, you'd lose your notes.

Another example: You remove The Gimp from your system with the package manager so you can install a later version by compiling it from source. You still want your preferences.

Another example: Three people use the same computer, with different user accounts. The administrator of the computer decides to remove the e-mail program that the other three use. They complain and so the administrator reinstalls the program. Fortunately, the system has retained the data in their home directories, so they don't lose their e-mail account information and contacts.

---

