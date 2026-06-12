---
title: "Start up script"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by RichardCL on 2009-08-25
Dear Forum,

I'm surprised that I've not found a tutorial...

What I want to do is set up Ubuntu so that it loads my common programs on startup. Ideally selecting the modes and desktops that I prefer.

i.e.
[LIST]
[*]Evolution on desktop 1, maximised
[*]Firefox on desktop 2, restored last session
[*]Virtual box with Win Vista Business on desktop 4, seamless mode
[*]Create a tar.gz archive of my home directory and save as the current date in a directory called backup.
[/LIST]

What kind of scripting do I need to read up on?

---

### Post by VCoolio on 2009-08-25
To start up evolution and firefox on specific desktops and stuff use [devilspie]("http://foosel.org/linux/devilspie"). Install it, then make .ds files with your texteditor in ~/.devilspie (examples are in the link, use one .ds file for each app you want to rule, devilspie will use all .ds files in ~/.devilspie automatically).

Then make a startup script like this and add to startup applications:

```
#!/bin/sh

tar -czf /path/to/backup/`date +%F`.tar.gz /home/user &
devilspie &
sleep 5 && firefox & evolution &
sleep 60 && killall devilspie &

```

Kill devilspie at the end of the file if you don't want next firefox and evolution windows you open during your session also on these desktops and maximized etc. If you do, than don't kill devilspie.

About virtualbox I don't know. Put the command you would use in the terminal in the above script and use devilspie to open it on 4th desktop.

---

### Post by aktiwers on 2009-08-25
That would take some time to load all that stuff.

In gnome you could go to :
 System ->Preferences ->Sessions

And add the programs you need. I don't know how to assign them to each workspace though I know this can help a lot
[http://live.gnome.org/DevilsPie](http://live.gnome.org/DevilsPie)
[B]
..  but this is how I would go:[/B]
> Evolution on desktop 1, maximisedAdd it to Sessions (again for Maximized check out DevilsPie)> 

Firefox on desktop 2, restored last sessionAgain add it to Sessions and set Firefox to remember your Firefox tabs Session [http://www.davidtan.org/how-to-remember-reopen-closed-tabs-firefox/](http://www.davidtan.org/how-to-remember-reopen-closed-tabs-firefox/)

> Virtual box with Win Vista Business on desktop 4, seamless modeAdd ```
vboxheadless -s "Windows Vista"
``` to Sessions (remember to change "windows vista" to the name of your Virtualmachine. Now it will be running in complete headless mode. You can look into the possibilities of vboxmanage    vboxsdl       vboxwebsrv, but none of them does seamless mode. So I guess your best guess is:
[http://vbox.innotek.de/pipermail/vbox-trac/2009-June/125197.html](http://vbox.innotek.de/pipermail/vbox-trac/2009-June/125197.html) and the reply to that message.

> Create a tar.gz archive of my home directory and save as the current date in a directory called backup.Place this in sessions: 
```
tar -pczf /var/backup.tar.gz /home/*
```

---

### Post by drs305 on 2009-08-25
If you are using Compiz, you can set up the CompizConfig Settings Manager to place an app on a specific workspace. It's in the Window Management > Place Windows: Fixed Window Position section. There are two sections for window size and workspace location.

---

### Post by RichardCL on 2009-08-26
Many thanks. I've downloaded Devilspie and am just getting to grips with it. Seems easier than I'd expected.

Now I can turn on the PC and get a coffee while it sets itself up as I'd wanted.

---

