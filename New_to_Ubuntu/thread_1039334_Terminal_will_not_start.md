---
title: "Terminal will not start"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-01-14
Tried to customize my terminal prompt and checked the Run a Custom Command in the preferences with a code. Now the terminal starts and shuts off instantly. Need help to fix this/reset it.

Tried reinstalling gnome-terminal with Synaptic Package Manager but doesn't solve the problem.

I can access the terminal with ctrl+alt+F1 but not sure what to do from there to reset so I can use it in a window on the desktop.

Thank you!

---

### Post by oldos2er on 2009-01-14
If you made a backup copy of bashrc before changing it, just copy it over the newer one. Or if you used gedit to edit your bashrc, it should've made a backup copy for you. To restore it, run "cp .bashrc~ .bashrc"

---

### Post by sylvainrb on 2009-01-14
Tried it but still isn't working.

Sorry if it was unclear from my post but I didn't change the .bashrc file. From the terminal window, I did Edit->Preferences and there checked the checkbox Run a Custom Command and typed in: sudo PS1="$ "

I put sudo since when I first typed in PS1="$ ", it gave me an error message.

---

### Post by Bölvaður on 2009-01-14
~/.gconf/apps/gnome-terminal

is what you changed stored there?

---

### Post by jerome1232 on 2009-01-14
then purge gnome-terminal and reinstall it to wipe out the config files.

```
sudo apt-get remove --purge gnome-terminal
sudo apt-get install gnome-terminal
```

Alternativly you could find and delete gnome-terminals configuration directory but I don't know where it's at off the top of my head (probably something like ~/.gnome/gnome-terminal or something)

---

### Post by sylvainrb on 2009-01-14
@Bolvaour

I'm not sure what I should be looking for in the folder but there is a profiles folder with a Default sub-folder, each with a %gconf.xml file. What should I do? And how would I open the .xml files if I need to alter them?

---

### Post by sylvainrb on 2009-01-14
@jerome1232

I entered the code and restarted the computer after the uninstall and the install but the problem is still here. There is a gnome-terminal folder at ~/.gconf/apps should I delete it after I uninstall the terminal?

---

### Post by Bölvaður on 2009-01-14
> **sylvainrb said:**
>  There is a gnome-terminal folder at ~/.gconf/apps should I delete it after I uninstall the terminal?

Yes I think you should do that if you uninstall it again. But I think you may not need to.
If you copy my settings then this should be no problem I think.


~/.gconf/apps/gnome-terminal/%gconf.xml is empty

~/.gconf/apps/gnome-terminal/profiles/%gconf.xml is empty

~/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml contains the following
```

<?xml version="1.0"?>
<gconf>
        <entry name="visible_name" mtime="1231944230" type="string">
                <stringvalue>Default</stringvalue>
        </entry>
        <entry name="foreground_color" mtime="1231944230" type="string">
                <stringvalue>#000000000000</stringvalue>
        </entry>
        <entry name="alternate_screen_scroll" mtime="1231944230" type="bool" value="true">
        </entry>
        <entry name="background_color" mtime="1231944230" type="string">
                <stringvalue>#FFFFFFFFDDDD</stringvalue>
        </entry>
</gconf>
```

xml files are text files that are.. well just look at the text, it is structured similarly to HTML.

---

### Post by sylvainrb on 2009-01-14
Yes! Deleting the .xml files in the folder and subfolders after rebooting after the uninstall works.

Thanks to all of you. Only 3 days using Ubuntu and the forum has helped/taught me a lot!

---

