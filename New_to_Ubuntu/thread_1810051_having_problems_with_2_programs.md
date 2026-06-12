---
title: "having problems with 2 programs"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-07-22
Ok, first some info. I'm running 11.04 on an Acer Aspire 5000, on Classic view, since the hardware doesn't support Unity.

Yesterday, I downloaded Emc2 and ReplicatorG. Both worked perfectly upon install, but neither showed up in the applications menu. So I copied the icon into the desktop.
Now, I'm trying to open them (either from the desktop icon or from the original file) and they won't run at all. The Emc2 asks me for my password, and once I input it, nothing happens, and the ReplicatorG won't even do that.

So, my questions are 2:

1. How do I get the programs running again?

2. How do I get them to show up in the applications menu, so I can clean up my desktop?


Thanks in advance. :)

---

### Post by Inodoro Pereyra on 2011-07-22
Nobody? :(

---

### Post by hhh on 2011-07-22
I've never heard of these programs, but...

It looks like RelicatorG is broken on 11.04...
[https://groups.google.com/group/makerbot/browse_thread/thread/1d6490e7abf82611/ed722433a8e68684?lnk=raot](https://groups.google.com/group/makerbot/browse_thread/thread/1d6490e7abf82611/ed722433a8e68684?lnk=raot)

Someone here claims reinstalling Emc2 from the Live CD works...
[http://www.linuxcnc.org/component/option,com_kunena/Itemid,20/func,view/catid,9/id,6711/limit,6/limitstart,6/lang,german/](http://www.linuxcnc.org/component/option,com_kunena/Itemid,20/func,view/catid,9/id,6711/limit,6/limitstart,6/lang,german/)

Emc2 Live CD...
[http://www.linuxcnc.org/content/view/21/4/lang,en/](http://www.linuxcnc.org/content/view/21/4/lang,en/)

I hope that helps.

---

### Post by Inodoro Pereyra on 2011-07-22
Thanks hhh! ReplicatorG  is working! :D
I will start downloading Emc2 live disc now.

Now, I still can't get it to run from the "Applications" menu. Can anybody tell me how to do that?

---

### Post by hhh on 2011-07-23
> **Inodoro Pereyra said:**
> Now, I still can't get it to run from the "Applications" menu. Can anybody tell me how to do that?
You'll need to create ".desktop" file for it and store it in either /usr/share/applications (for all user accounts) or in ~/.local/applications (for 1 user). Open a file in /usr/share/applications in a text editor to see the structure. Be careful, those are system files, and the .desktop extensions are hidden. See this blog post for some more info, especially the bottom section...
[http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/](http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/)

Post back if you have problems.

---

### Post by Inodoro Pereyra on 2011-07-23
Thanks again. :D

So, let me see if I understand. Based on that link you provided, this is what I came up with:

I open Gedit, and I type:

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Exec=$home/bernardo/Documents/replicatorg-0025/replicatorg
Name=Replicatorg

Then I save it as: Replicatorg.desktop

And then I "put a copy" (how do I do that?) in:  usr/share/applications , and I should be ok?:confused:

Just in case I'm messing up on something, here's what I know:

The file I have to run is located at (from top to bottom) File System/home/bernardo/Documents/replicatorg-0025/replicatorg
There's already a menu under Applications, named "Other". I want to put the Replicatorg in there. How do I do that?

Thanks again for all the help. :)
[FONT=courier][/FONT]

---

### Post by Inodoro Pereyra on 2011-07-24
Bump? :(

---

### Post by hhh on 2011-07-24
To move it to /usr/share/applications you need to open your file manager as root. Alt+F2 to open the Run dialog and enter```
gksu nautilus
```
Be careful, you now have root privelages over your system files. Don't delete anything by accident. Right click your new file and Cut/Paste it into /usr/share/applications or /home/[Your User Name}/.local/applications. .local is a hidden file, Ctrl+h in Nautilus to display hidden files.

Your Exec line is wrong, you need a slash (/) before"home".

You need a line name "Categories" to determine where in the menu it will display. More info...
[http://library.gnome.org/admin/system-admin-guide/stable/menustructure-desktopentry.html.en](http://library.gnome.org/admin/system-admin-guide/stable/menustructure-desktopentry.html.en)
[http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html#category-registry](http://standards.freedesktop.org/menu-spec/menu-spec-1.0.html#category-registry)

I'm not sure how to get it to display in "Other", maybe just...```
Categories=;
```

I'm not at home till Tuesday but post back and let me know how it's going, I'll have internet acces where I am.

I hope that helps.

---

### Post by Inodoro Pereyra on 2011-07-24
Thank you. I will do some reading on those links, and post back. :D

---

### Post by Inodoro Pereyra on 2011-07-24
Ok, I followed your instructions, and everything went perfect...until I tried to paste the file into the applications folder. I tried in both the .usr and the .local folders, and, in both cases, I could copy the file without a problem, but it won't let me paste it.:(

What am I doing wrong?

---

### Post by hhh on 2011-07-24
Weird. You should be able to copy/paste or drag/drop the file into the ~/.local/share/applications folder without even having root privileges in Nautilus. Try that.

BTW, ~/ is a shorthand notation of /home/"Your User Name Goes Here". I'm Googling "gnome .desktop file locations" and I'm seeing variations of ~/.local/share, ~/.local/applications and ~/.local/share/applications. I think the last one is right, as that's how my file structure is, though I use Debian Squeeze, not Ubuntu (though I used to).

---

### Post by Inodoro Pereyra on 2011-07-24
Done!  Thank you very much, hhh, for all the help!:D

I did the drag and drop thing, and even then it didn't work at first. Then I went back and took the "$" sign off the "Exec" path, and now it works like a charm. 

One little detail didn't go as planned though: I added the "categories" line as you suggested, but, instead of putting "Other", I put "Robotics" (as it's shown as an available category in your second link) and "CNC". So, the final file is as follows:

> [Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Exec=/home/bernardo/Documents/replicatorg-0025/replicatorg
Name=Replicatorg
Categories=Robotics;CNC

Yet, when I looked in the "Applications" menu, there was no "Robotics" category, and the program was under "Other"...:confused::confused:

Either way, I'm so happy right now, it could be under "Kiss my a$$" and I still wouldn't mind.:lolflag::lolflag:

Thanks again for everything.:)

---

