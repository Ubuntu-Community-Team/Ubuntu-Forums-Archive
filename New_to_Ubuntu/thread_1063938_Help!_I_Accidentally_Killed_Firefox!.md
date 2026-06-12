---
title: "Help! I Accidentally Killed Firefox!"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-02-08
I was trying to update Firefox 3.0.5. to 3.0.6, but was having some problems. After many failed attempts, I finally gave up and deleted the setup files.
Then, when I pressed the Firefox icon, an error box appeared saying that the no such "firefox" file or directory exists. It won't load Firefox anymore.
Please help. All assistance will be greatly appreciated.

Thank you for your time.

Take care,
RedStarYellowSun

---

### Post by paydaydaddy on 2009-02-08
So, what happens if you open synaptic and try to re-install firefox?

---

### Post by superprash2003 on 2009-02-08
go to the terminal and type sudo apt-get install firefox

---

### Post by ptn107 on 2009-02-08
Pop open a terminal (Applications -> Accessories -> Terminal) and type or copy/paste the following:

```
sudo apt-get remove --purge --auto-remove firefox firefox-3.0 firefox-3.0-branding firefox-gnome-support firefox-3.0-gnome-support ubufox -y; rm -r ~/.mozilla/; sudo apt-get install firefox -y
```

---

### Post by frank002 on 2009-02-08
Only thing I can think of is ....go to synaptic and redownload firefox. You will get 3.05. Eventually, you will get the upgrade to 3.06  in the software upgrades that Ubuntu regularly gets.

---

### Post by mkvnmtr on 2009-02-08
You might want to go to your home file and make a copy of your mozilla file. You will have to click under view where it says enable hidden files to see it. It will have all your bookmarks in it and you might loose them if you don't save them. Then go to the package manager and look for broken packages. You will probably find Firefox, Mark for complete removal. Then reinstall firefox. If you have lost your bookmarks and such just replace the fill that you saved for the new one and you should have it back the way it was.

---

### Post by RedStarYellowSun on 2009-02-08
I have tried reinstalling with Synamptic... many times, but it did not solve the problem.

---

### Post by benny bronx on 2009-02-08
Delete the firefox icon, go into the main menu and create a new icon.  That may work.

---

### Post by RedStarYellowSun on 2009-02-08
I tried it and deleted the icon from the upper bar. But unfortunately, it did not solve the problem.
It still gives off the same error report:

"**_Error_**
Could not launch menu item
Failed to execute child process
'firefix' (No such file or directory

[OK]"

---

### Post by kn1ghtus on 2009-02-08
what happens when you try to UNINSTALL it?  if you uninstall it, it still saves your user data so then maybe a reinstall will work.

---

### Post by RedStarYellowSun on 2009-02-08
I have. Using Synaptic, I had it completely removed. Then, I had it installed again. The problem still persists. I did this at least 8 times.

---

### Post by kansasnoob on 2009-02-08
You could install the official Mozilla build of Firefox using Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

It's super simple and then you'll get Firefox updates sooner.

---

### Post by Gramps on 2009-02-08
> **RedStarYellowSun said:**
> I have. Using Synaptic, I had it completely removed. Then, I had it installed again. The problem still persists. I did this at least 8 times.

Try opening a Terminal Applications/Terminal at the prompt type the following
```
sudo apt-get autoremove
```
When this is finished try this
```
sudo apt-get install firefox
```

When you remove programs with Synaptic or apt-get for that matter all the dependencies are not necessarly removed. The apt-get autoremove will clean these up.

---

### Post by LastWho on 2009-02-08
after u do that try to open firefox this way:
- alt + F2 
type: "firefox", then enter
??

- or in a terminal:
firefox
??

show us the error messages u get, may be that ll help!

---

### Post by RedStarYellowSun on 2009-02-09
It seems to have had no effect. I still get the same error message.
During the installation phase, it seems that Synaptic is ineffective. After the "uninstallation", "Firefox" still appears in the "Internet" tab of the "Applications" menu.
But, when I try to eliminate it completely with 

sudo rm /opt/firefox

it says that it cannot delete it because it already does not exist... but "Firefox" still appears in the Application tab!

There seems to be quite a contradiction here.

What do I do?

Thank you for your time.

Take care,
RedStarYellowSun

---

### Post by RedStarYellowSun on 2009-02-09
> **Gramps said:**
> Try opening a Terminal Applications/Terminal at the prompt type the following
```
sudo apt-get autoremove
```
When this is finished try this
```
sudo apt-get install firefox
```

When you remove programs with Synaptic or apt-get for that matter all the dependencies are not necessarly removed. The apt-get autoremove will clean these up.

I again had Firefox completely removed with Synamptic. Then I tried on Terminal ```
sudo apt-get autoremove
```, the response was
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

But, "Applications">"Internet">"Firefox Web Browser" still exists. 

As for the ```
sudo apt-get install firefox
```,

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
firefox is already the newest version.
`0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

After this, I still cannot access Firefox.

Thank you for your time and patience.

Take care,
RedStarYellowSun

---

### Post by kansasnoob on 2009-02-09
For crying out loud! Have you tried Ubuntuzilla?

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

It works! I did extensive testing to get it working on all Ubuntu based distros. Begin with post #66 here:

[http://ubuntuforums.org/showthread.php?t=467724&page=7](http://ubuntuforums.org/showthread.php?t=467724&page=7)

---

### Post by RedStarYellowSun on 2009-02-09
The instructions seem long and complex... but, I'll try it out. One moment... It is tough having to work on 2 computers.

Thanks for the advice.

Take care,
RedStarYellowSun

---

### Post by RedStarYellowSun on 2009-02-09
Oh my gosh! It killed my problem! Ubuntu is fixed! 
THANK YOU!!!!!!
Ubuntuzilla is awesome! Thanks!

Take care,
RedStarYellowSun

---

### Post by RedStarYellowSun on 2009-02-09
Oh, crud. Is it just me or was the "Mark this Thread as Solved" selection was removed?

Thanks for your time and patience.

Take care,
RedStarYellowSun

---

### Post by kansasnoob on 2009-02-09
> **RedStarYellowSun said:**
> The instructions seem long and complex... but, I'll try it out. One moment... It is tough having to work on 2 computers.

Thanks for the advice.

Take care,
RedStarYellowSun

Once Dapper and Gutsy are retired the instructions should become shorter! Although really it's mostly a matter of just explaining what's going to take place.

Currently it is important to explain why FF2 to FF3 may not work perfectly! Certain folders are even named differently!

---

