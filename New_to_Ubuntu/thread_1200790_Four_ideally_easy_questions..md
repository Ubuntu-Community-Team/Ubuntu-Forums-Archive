---
title: "Four ideally easy questions."
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Doman on 2009-06-30
1.  I have Conky installed.  How do I configure it?  I don't see it anywhere...

2.  My transition to Ubuntu was pretty abrupt.  I needed a stable OS and this was my best option after windows crashed.  I archived my larger files with winrar in volumes.  So far, even with unrar, I've been unable to extract these.  What am I doing wrong?

3.  I have Wine installed.  Tried to go through things such as winetools or winetricks but I still have no idea what to do.  All I really want it for is so I can continue casually playing Warcraft 3 with dorm-mates.  Any help?

4.  I'm still kinda hazy on how to install .tar.bz2 files too... sad, right?  & I'm usually a google-pro. -_-;

EDIT: 5.  If I'm updating firefox not through Synaptic n' all, will it overwrite as an update should?

---

### Post by LowSky on 2009-06-30
1 open a terminal, type conky if the command does not work, type conkey and hit the tab key twice, it will give you options on what command will work.

2 Dont know what you can try, storing volumes of info in compressed forms is never ideal, hopefully someone has an idea

3 [http://appdb.winehq.org/objectManager.php?sClass=application&iId=897](http://appdb.winehq.org/objectManager.php?sClass=application&iId=897)

4 what are you trying to install, you proabably dont need the .tar.bz2 files... use add/remove or synaptic to search for programs, like flash, java, and mp3 support, if you need dvd playback google "medibuntu"

5 No it will not, firefox installed through synaptic keeps fiels in a different place than those you install yourself.. btw firefox 3.5 is in synaptic if you need it updated

---

### Post by TeoBigusGeekus on 2009-06-30
1)
You have to create a custom file with instructions about the info conky will show. The file must be named .conkyrc and be placed in your home folder.
Usefull links:
[http://conky.sourceforge.net/documentation.html]("http://conky.sourceforge.net/documentation.html")
[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")
After that, you have to create a start script for conky, so that it starts whenever your pc boots.
Create a file called conky_start.sh and add this into it:
```
sleep 10
conky
```
right click it, go to permissions tab and make it executable.
Go then to System->Preferences->Startup Applications and
add a new startup application. Name it Conky and give as a command
```
sh /wherever/your/start/script/is/located/conky_start.sh
```
Reboot and enjoy...


2)
Go to Applications->Add/Remove and do a search for rar. Install the rar package.
Archive manager should now be able to manage rar files.


3)
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=897]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=897")


4)
What's in the tar.bz2 archive? Source code? If it is, then:
[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html")

5)
I think so...

---

### Post by Idefix82 on 2009-06-30
> **Doman said:**
> 1.  I have Conky installed.  How do I configure it?  I don't see it anywhere...

To configure conky is not entirely straightforward. You have to create a text file named .conkyrc in your home directory and in that file you describe in a special script language what info you want conky to display and how to format it. To get started, you might want to just copy somebody else's .conkyrc, e.g. from here [http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")

There are also separate scripts for displaying weather forecasts, news feeds or checking your email. Just google for those.

---

### Post by cariboo on 2009-06-30
> 1. I have Conky installed. How do I configure it? I don't see it anywhere...


You have to edit conkyrc, if you search for examples, by typing conkyrc in Google you will find plenty of examples.

> 2. My transition to Ubuntu was pretty abrupt. I needed a stable OS and this was my best option after windows crashed. I archived my larger files with winrar in volumes. So far, even with unrar, I've been unable to extract these. What am I doing wrong?

Sometimes you need to install rar in order to unarchive rar files. Rar is in the repositories, you can use Synaptic Package Manager to install it.

> 4. I'm still kinda hazy on how to install .tar.bz2 files too... sad, right? & I'm usually a google-pro. -_-;

You shouldn't have to install anything from a tar file, most of what you need is available through Synaptic Package Manager or Add/Remove Applications.

> EDIT: 5. If I'm updating firefox not through Synaptic n' all, will it overwrite as an update should? 

If you don't use the repositories to install applications, they will not be updated when updates are released.

For a new user, it is best to stick with the tools that Ubuntu provides for installing and updating applications. If you install random programs for random web sites, you never know what you are getting. The packages in the repositories are guaranteed secure.

---

### Post by Doman on 2009-06-30
Wow, you guys are good.  Okay, so I'm going through a pretty cool conky script and have a few questions about that.

1.  If they say "default_color black" does that mean I can also do "default_color #ABCDEF" or something?
 
2.  I've seen scripts around for external IPs, but knowing my local IP is much more handy & google wont turn up anything significant on doing that so it's probably something obvious I don't know from lack of experience.

3.  Is there an index of addons such as the weather and what not?

---

### Post by bekind2thenoob on 2009-06-30
For Conky you might want to check out this page:

[http://gnome-look.org/content/show.php/CONKY-colors?content=92328%29]("http://gnome-look.org/content/show.php/CONKY-colors?content=92328%29")

Its not much less complicated than starting from scratch but its a nice way to get an impressive setup quickly.

---

### Post by Doman on 2009-06-30
I actually just saw that literally seconds ago but didn't want to deal with the install.  I *think* I've something decent right now.  I don't know because it wont load...

---

### Post by Doman on 2009-06-30
Solved except for the wine, which I figure will work eventually.  Thanks everyone!

---

### Post by m_duck on 2009-07-01
> **Doman said:**
> 1.  If they say "default_color black" does that mean I can also do "default_color #ABCDEF" or something?Yes you can use hex color codes but lose the '#' otherwise I don't think it works.
 
> **Doman said:**
> 2.  I've seen scripts around for external IPs, but knowing my local IP is much more handy & google wont turn up anything significant on doing that so it's probably something obvious I don't know from lack of experience.For your local IP in conky, just use the **${addr <interface>}** variable, e.g. **${addr eth0}** for your first ethernet interface. The [conky website]("http://conky.sourceforge.net/") has a list of the [variables]("http://conky.sourceforge.net/variables.html") which you can use in the config, and a list of all the [configuration settings]("http://conky.sourceforge.net/config_settings.html") (i.e. above the TEXT line).

> **Doman said:**
> 3.  Is there an index of addons such as the weather and what not?I don't think there is an index of them as such as they are user created for the most part, but if you look at the conky thread in my sig (I think it was mentioned earlier too) and trawl through it there are loads of scripts to be found. You can get conky to display pretty much anything you want.

---

