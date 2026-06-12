---
title: "Help on panels?"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by paparoo on 2010-12-30
**Help**! I got myself into a mess and cannot get out. Newbie with only a week or so of Ubuntu under my belt.

I will try to describe the problem. Please accept the fact that I will not use all the correct terminology, but I will try my best.

I seem to have lost my panels, is the best way to describe it.

When you minimize an app, the icon goes to a space at the bottom of the desktop. This is what I am calling a 'panel'.

When I minimize Firefox, for example, the icon disappears. If I'm playing a news video and I minimize it, the icon disappears. I can still hear the video. 

Now I have no way to restore the app, so it runs forever. I don't know where the icon went to.

Understand? Sorry for the poor explanation, but I am new to Linux/Ubuntu.

This started when I tried to changed something in a solitaire game called Jumbo.

 One solution, if available, would be to fall back to a restore point, if Ubuntu supports them. I have nothing of any importance on the system yet. But I have no backup, either.

---

### Post by Verbeck on 2010-12-30
so is it the entire panel which is missing or only the window list?

if the bottom panel is missing : right click the top panel> New panel
to add the window list : right click the panel > add to panel > window list

---

### Post by szrobert on 2010-12-30
Look, you can tray this, if you don't mind to lose your actual configurations (you set thos again after that). Go to your home folder in nautilus. Type ctrl+h or from the menu/view/show hidden files. Then you'll see a lot of file and folder that begone with . ( a dot - in linux the hidden files are marked in this way). In thous files and folder are stored your settings. Delete all ! I told you that because now I don't remember were are stored exactly the settings for the panels and I have to go away now but , if you want , googalize for it. After deleting all and after you empty the garbage basket just logout and login. You should have an user interface like an fresh install. Remember, delete ONLY files and folder that begin with an dot, nothing else. I suppose that you don't want to delete your Pictures or Documents folder :razz:. Have a nice day.

---

### Post by howefield on 2010-12-30
To restore the panels to default setup, run the following three commands in terminal, (Applications > Accessories > Terminal).

```
gconftool-2 --shutdown
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```

---

### Post by Frogs Hair on 2010-12-30
I assume you have a top panel because you seem to have menu . Right click the top panel and select new panel. This should restore the bottom panel.

Right click the bottom panel and select add to panel  and add workspace switcher , trash , and window list from the menu .  You can add anything you wish from the menu.

---

### Post by judedawson on 2010-12-30
Hi paparoo,

Try the suggestions in the below-link:

[http://ubuntuforums.org/showthread.php?t=1634213&highlight=bottom+panel+deleted](http://ubuntuforums.org/showthread.php?t=1634213&highlight=bottom+panel+deleted)

It should point you in the right direction. 

Most of the time, you can find postings of similar problems in the Ubuntu forums. I would suggest you try searching first. Here's how I found the above-link. I typed 'bottom panel deleted' in the Search bar on the top-right corner of the Ubuntu forums web-page and looked for the most relevant posting. 

Don't give up :p

From,
Jude

---

### Post by paparoo on 2010-12-30
I am going to go through every response here, but I wanted to let you know that the 3 commands from howiefield restored the panels. 

Thanks a million, howiefield - I owe you one. And thanks to everybody else that helped.

paparoo:popcorn:

---

### Post by paparoo on 2010-12-30
> **judedawson said:**
> Hi paparoo,

Try the suggestions in the below-link:

[http://ubuntuforums.org/showthread.php?t=1634213&highlight=bottom+panel+deleted](http://ubuntuforums.org/showthread.php?t=1634213&highlight=bottom+panel+deleted)

It should point you in the right direction. 

Most of the time, you can find postings of similar problems in the Ubuntu forums. I would suggest you try searching first. Here's how I found the above-link. I typed 'bottom panel deleted' in the Search bar on the top-right corner of the Ubuntu forums web-page and looked for the most relevant posting. 

Don't give up :p

From,
Jude

Jude

Thanks for the tip on searching. Normally I try to do the footwork before asking for help. But I am still very new to Linux, and didn't want to use incorrect terminology (read: didn't want to get embarassed). I wasn't even sure that panels was the correct term. Ha!

I'll do better as time goes on. My hope is to become an asset to this forum, not a nuisance.

paparoo

---

### Post by Paqman on 2010-12-30
> **paparoo said:**
> 
When I minimize Firefox, for example, the icon disappears. If I'm playing a news video and I minimize it, the icon disappears. I can still hear the video. 

Now I have no way to restore the app, so it runs forever.

Just a tip: Alt-Tab cycles through all the currently open apps.

---

### Post by judedawson on 2010-12-30
Hi paparoo,

No worries. I'm new to Ubuntu as well. Ubuntu is amazing!

Searching for fixes from within the forums can be a daunting task (I've had my fair share of sleepless nights searching but not finding...)

After some time spent reading as many postings as possible, I began to better understand how to look for information within the forums. 

Just thought I'd share that with you. 

Enjoy your journey in the world of Ubuntu and Linux in general.

Cheers :)

From,
Jude

---

### Post by paparoo on 2010-12-31
> **judedawson said:**
> Hi paparoo,

Searching for fixes from within the forums can be a daunting task (I've had my fair share of sleepless nights searching but not finding...)

After some time spent reading as many postings as possible, I began to better understand how to look for information within the forums. .

Cheers :)

From,
Jude

Thanks, Jude. You're right - forums can be a great source of info, because it's likely that some other newbie has encountered the same problem at some point. This site seems to be at the top end of sites, as far as I've seen, also. I'm glad I 'discovered' it.

paparoo

---

### Post by howefield on 2010-12-31
Just a quick tip.

You'll often get better results by using google to search the forum instead of the forum search function itself.

Append the following to your search terms.

```
site:ubuntuforums.org
```

---

### Post by judedawson on 2011-01-11
Can we mark this thread as [SOLVED]?

---

### Post by Megaptera on 2011-01-11
For future some folks might like "PanelRestore, that allows you to quickly and easily restore the default Gnome panels in Ubuntu and to backup and restore your existing custom panel configurations."

Here:[http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/](http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/)

---

