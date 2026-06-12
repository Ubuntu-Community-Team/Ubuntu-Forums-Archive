---
title: "Gnome programs and the command line ..."
date: 2011-01-27
forum: New to Ubuntu
---

### Post by clbeltz on 2011-01-27
All,
I recently had a situation where File Manager would repeatedly launch during startup on my 10.04 machine.  I could only drop out to terminal, but realized there were many GUI programs I could not launch from the command line because I didn't know the command.  Is there a cross reference of Gnome programs and the terminal command to launch the GUI (e.g. File Manager and nautilus; Ubuntu Help and yelp; Hardware Drivers and jockey-gtk)?  I've searched, but cannot find a summarized table with these data.  Thanks so much.

Chris

---

### Post by Vaphell on 2011-01-27
check /usr/share/applications
there is a ton of .desktop files. Each one defines a registered app

```
for file in /usr/share/applications/*.desktop; do echo ----------------; grep -E '^Name=|^Exec=' "$file"; done;

```

this command will list names and commands
if you want to produce a txt file, replace 'done' with 'done > apps.txt' where apps.txt is the output file.

---

### Post by HermanAB on 2011-01-27
Howdy,

Click drag drop the program entry from the menu to the desktop to make a launcher, then right click on that and look at the properties to get the name of the program.

Once something is running, use 'ps -e' to see what it is.

---

### Post by sisco311 on 2011-01-27
EDIT: D'oh! I'm a little slow today. :)

Well, you can always create the list yourself :). The info is in the .desktop files from /usr/share/applications/. You just have to filter it out:

```
for file in /usr/share/applications/*.desktop; do 
  grep -e '^Name=' "$file"
  grep -e '^Comment=' "$file"
  grep -e '^Exec=' "$file"
  echo
done > ~/gui-apps
```

The above code will create a file *gui-apps* in your home directory with the name, description and command of the GUI applications.

---

### Post by nothingspecial on 2011-01-27
Or go System > Preferences > Main Menu

Find the app you want and click on properties and the command is in the command box.

---

