---
title: "setting the default file manager back to nautilus"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by nitstorm on 2010-04-26
Hey guys,

I just wanted to try out LXDE and Fluxbox yesterday so I got them installed and checked them out but changed no settings anywhere. But when I logged back into Gnome, if i go to places and then browse a drive, PCManFM opens it up (NOTE: the drive icons on the desktop when clicked open up with nautilus, these two drive icons are in place coz i added them to fstab)
I want to go back to nautilus when I am in Gnome. Please help.
Thanks & Cheers!

---

### Post by HarrisonNapper on 2010-04-26
More likely than not, (I use KDE), there is a Default Applications listing in Gnome. System>Administration (or Preferences, possibly) and look for something regarding default applications. If you can't find it there, look up how to do it in gconf-editor in a search engine. :)

---

### Post by nitstorm on 2010-04-26
> **HarrisonNapper said:**
> More likely than not, (I use KDE), there is a Default Applications listing in Gnome. System>Administration (or Preferences, possibly) and look for something regarding default applications. If you can't find it there, look up how to do it in gconf-editor in a search engine. :)


There is no option for default or preferred file manager in the preferred applications. Now looking into the gconf-editor thing. Thanks for the pointing out the way :D

---

### Post by nitstorm on 2010-04-26
> **HarrisonNapper said:**
> More likely than not, (I use KDE), there is a Default Applications listing in Gnome. System>Administration (or Preferences, possibly) and look for something regarding default applications. If you can't find it there, look up how to do it in gconf-editor in a search engine. :)

Found something here [http://bbs.archlinux.org/viewtopic.php?pid=709810](http://bbs.archlinux.org/viewtopic.php?pid=709810) . 
So went to gconf-editor-> Apps-> Nautilus->Preferences but the always_use_browser is already ticked.

What do I do now ????   :S

---

### Post by HarrisonNapper on 2010-04-26
You can do it this way (undo the change you made in gconf-editor first):

```
sudo dpkg-reconfigure nautilus
```

Cheers.

---

### Post by nitstorm on 2010-04-26
nope, that didn't work :(

---

### Post by HarrisonNapper on 2010-04-26
[http://www.ubuntugeek.com/how-to-change-back-nautilus-as-your-default-file-manager.html](http://www.ubuntugeek.com/how-to-change-back-nautilus-as-your-default-file-manager.html)

The above link says it should be in there somewhere. This should be stop number one.

Failing that, you can try this rather contrived method:

The script at this link sets Thunar as the default file manager, but accepts an argument to set nautilus back to default:

[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

So what you can do is install Thunar, run the script, then run the script with the "restorenautilusdefault" option. That should set nautilus back to default whereupon you can uninstall Thunar.

EDIT: for future users who are troubleshooting this problem, visit the link provided for the Thunar work around and pay careful attention to the part where you set Thunar to default FIRST. Then you set nautilus BACK to default using the restorenautilus default argument which would look like this: 


./scriptname restorenautilusdefault

---

### Post by dannyboy79 on 2010-04-26
are you sure you chose Gnome session as your desktop manager at the login prompt (gdm or kdm or xdm)? i have tried a million desktop managers but i know that when I chose the one I want within xdm, gdm, or kdm (example: openbox, lxde, xfce, xfce-session, gnome, gnome-session) the file manager has always reverted back to what the default is for that desktop manager. gnome's default file manager is nautilus

---

### Post by HarrisonNapper on 2010-04-26
> **dannyboy79 said:**
> are you sure you chose Gnome session as your desktop manager at the login prompt (gdm or kdm or xdm)? i have tried a million desktop managers but i know that when I chose the one I want within xdm, gdm, or kdm (example: openbox, lxde, xfce, xfce-session, gnome, gnome-session) the file manager has always reverted back to what the default is for that desktop manager. gnome's default file manager is nautilus

I didn't think of that. Assuming that this is the case, let's set gdm back to the default login:

```
sudo dpkg-reconfigure gdm
```

Cheers.

---

### Post by nitstorm on 2010-04-26
@HarrisonNapper:

Tried both of your links. The first one says go to system->Preferences->System Settings. There is no such things as System Settings(I am on Karmic btw), but there is an option called Default Session. Went in there to see if there was an option for Nautilus but there isn't. But there is something called GNOME Settings Daemon but it is unchecked. Should I check it?

And the script. I had looked into it earlier but i never thought of installing thunar and uninstalling it again. back to the point, Zilch, it just installed thunar. Nautilus wasn't restored when i ran the script again so just uninstalled thunar.

And the *dpkg-reconfigure gdm & dpkg-reconfigure nautilus *didn't work either

---

### Post by dannyboy79 on 2010-04-27
can you please answer me? when you boot up the computer and are presented with GDM (where you put in your username and password) is there an option for changing the session from lxde to gnome or someother session's (desktop environments) than what the default is currently?

---

### Post by nitstorm on 2010-04-27
Yes there is. I get the GDM login screen and i also am allowed to choose between lxde, fluxbox and gnome.

---

### Post by dannyboy79 on 2010-04-27
> **nitstorm said:**
> Yes there is. I get the GDM login screen and i also am allowed to choose between lxde, fluxbox and gnome.

and you're saying that when you chose gnome, you still have pcman file manager or whatever?

---

### Post by avtolle on 2010-04-27
> **dannyboy79 said:**
> and you're saying that when you chose gnome, you still have pcman file manager or whatever?
Sticking my nose in, to answer the question posed, yes, that is what happens if the OP's experience is the same as mine.

---

### Post by dannyboy79 on 2010-04-27
is this set in gconf editor?
gconf-editor -> apps -> nautilus -> preferences -> always_use_browser  (check mark).

found this elsewhere, maybe it'll help:
start nautilus (from the terminal if you have to)
go to your /home
right click on a folder > properties
open with... tab
click add
find file browser (if you have thunar aswell, its complicated as its .desktop file calls itself file manager or browser aswell. However, they use different icons and you can figure out which is which using the applications menu)
add that then set that to default

also, did you read this?
[http://ubuntuforums.org/showthread.php?t=692238](http://ubuntuforums.org/showthread.php?t=692238)

---

### Post by nitstorm on 2010-04-28
> is this set in gconf editor?
gconf-editor -> apps -> nautilus -> preferences -> always_use_browser  (check mark).yes, checked that already. the check mark is still there.

> 
found this elsewhere, maybe it'll help:
start nautilus (from the terminal if you have to)
go to your /home
right click on a folder > properties
open with... tab
click add
Followed the steps by opening up nautilus from the terminal and right-clicked and  gave the open with and selected nautilus. Then closed all the windows and tried opening up my drive from places and still pcman opens it up.
Set the default application to nautilus even via pcmanfm. Still nothing :(

> 
also, did you read this?
[http://ubuntuforums.org/showthread.php?t=692238](http://ubuntuforums.org/showthread.php?t=692238)
this is my output of the two files, highlighted the exec line jus for reference
[U][I]/usr/share/applications/nautilus-folder-handler.desktop :
[/I][/U]```

[Desktop Entry]
Encoding=UTF-8
Name=Open Folder
TryExec=nautilus
**Exec=nautilus --no-desktop %U**
NoDisplay=true
Terminal=false
Icon=folder-open
StartupNotify=true
Type=Application
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.28.1
X-Ubuntu-Gettext-Domain=nautilus

```[U][I]

gedit /usr/share/applications/nautilus-computer.desktop
[/I][/U]```

[Desktop Entry]
Encoding=UTF-8
Name=Computer
Comment=Browse all local and remote disks and folders accessible from this computer
TryExec=nautilus
**Exec=nautilus --no-desktop computer:**
Icon=computer
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.28.1
X-Ubuntu-Gettext-Domain=nautilus

```Also there is a line in */usr/bin/applications/pcmanfm-folder-handler.desktop* called NotShownIn=GNOME; which was commented(#) earlier. I removed the comment. I mean i changed it from ```

#NotShownIn=GNOME;
```to
```

NotShownIn=GNOME;

```Logged out and logged back in. No change still!!!

Also I am missing a file : **/usr/share/gnome/default.session **!!! I am using karmic so I don't know if that file should exist or not, but in the last link it was mentioned to tweak that file but it's missing!!!!!

---

### Post by nitstorm on 2010-04-28
Ok found the solution. No matter what I did nothing worked, until I installed ubuntutweak. There under file type manager i looked up folder and it said PCFileManager and I changed it there to nautilus file browser and now it's all good. Thanks for all the effort @dannyboy79

THREAD SOLVED!!!

Cheers guys!

---

### Post by dannyboy79 on 2010-04-28
can you at least let us know did that install the /usr/share/gnome/default.session file and what are it's contents so others can solve possibly without having to install ubuntu tweek.

---

### Post by nitstorm on 2010-04-28
> can you at least let us know did that install the /usr/share/gnome/default.session file and what are it's contents so others can solve possibly without having to install ubuntu tweek.

I just looked into the folder. No default.session file there even now...

---

### Post by sirrommit on 2011-06-25
I solved this issue by running exo-preferred-applications. This program gave me the option to change my file manager back to nautilus.

---

### Post by restofactor on 2011-08-30
wow dude, this also freaked me out for days!!! exo-preferred-applications also sorted it out for me

---

### Post by HarrisonNapper on 2011-08-31
I know this is solved, but for posterity, does this preserve pcmanfm as the default file manager in lxde?

---

### Post by rocuan on 2011-10-18
> **nitstorm said:**
> Ok found the solution. No matter what I did nothing worked, until I installed ubuntutweak. There under file type manager i looked up folder and it said PCFileManager and I changed it there to nautilus file browser and now it's all good
[COLOR=DarkRed]UbuntuTweak worked for me too![/COLOR]
If you're interested, here's the story.

[COLOR=Navy]BACKGROUND:[/COLOR]
I was organizing my Main Menu on Lucid and accidentally deleted something critical. 
So, when I clicked my home folder icon it failed and randomly opened [COLOR=DarkSlateGray]VLC[/COLOR] not nautilus.
[COLOR=Navy]
TROUBLESHOOTING[/COLOR][COLOR=Navy]:[/COLOR]
[COLOR=Black]I [/COLOR]checked the entries in [COLOR=Navy][COLOR=DarkGreen].local/share/applications/mimeapps.list [/COLOR][COLOR=Black]
found the line causing the mayhem
[/COLOR][/COLOR]```
inode/directory=nautilus-browser.desktop;vlc.desktop;
```deleted the vlc.desktop; 
but now my home folder opened with [COLOR=DarkSlateGray]Thunar[/COLOR] not nautilus.
Searched the forums, found this thread.

[COLOR=Navy]SOLUTION[/COLOR][COLOR=Navy]:[/COLOR]
UbuntuTweak -> File Type Manager -> All -> folder
[COLOR=DarkGreen]click[/COLOR] edit [COLOR=DarkGreen]
click[/COLOR] add 
change to Nautilus ( also called File Browser )

[COLOR=Navy]RESULT:[/COLOR][COLOR=Black]
UbuntuTweak modified the[/COLOR] [COLOR=Navy][COLOR=DarkGreen].local/share/applications/mimeapps.list [/COLOR][COLOR=Black]
[/COLOR][/COLOR]```
inode/directory=nautilus-browser.desktop;nautilus-folder-handler.desktop;
```Now nautilus is the default again.

---

### Post by Kabbo on 2011-11-30
I seted marlin default from it's default. I was looking for days how to set nautilus default! Did this with exo-preferred-applications.
I wonder how it did. Tried changing the [COLOR=Navy][COLOR=DarkGreen].local/share/applications/mimeapps.list [COLOR=Black]file as rocuan said but didn't work![/COLOR]
[/COLOR][/COLOR]

---

### Post by pakopako on 2011-12-02
It really helps to keep nautilus! I really liked PCman, but it wouldn't work well with Trash Applet. Also, it just died on me after I tried going to a non-existing directory (/etc/fstab) and just wouldn't start back up. (No error messages when executing pcmanfm from terminal either.)

---

### Post by youlikeicecream on 2011-12-13
> sudo dpkg-reconfigure nautilus
Worked for me.

Also:
> gconf-editor -> apps -> nautilus -> preferences -> always_use_browser (check mark)

This setting enables the browser style view in nautilus rather the windows 98 style "open a window per click" view setting.

---

### Post by karmila on 2012-01-13
Ubuntu-tweak also helped me revert default file manager from marlin to nautilus :)

---

### Post by kbrodenhau on 2012-11-08
12.04 Precise

Login to Gnome session.

Open a Terminal with CTRL-ALT-t.

Execute:
zulu:~> exo-preferred-applications &

Choose Utilities tab.
Select Nautilus for File Manager.
Select GNOME Terminal for Terminal Emulator.

---

