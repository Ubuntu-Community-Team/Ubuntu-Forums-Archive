---
title: "[SOLVED] How to completely remove Firefox."
date: 2009-07-17
forum: New to Ubuntu
---

### Post by jestinjoy on 2009-07-17
I was using Firefox 3.1 with some plugins like twitterfox, adblock plus, flashblock,xmarks in Ubuntu Jaunty. Now firefox is behaving badly. The bottom bar, in which twitterfox, xmarks ar shown is not showing up now. Also adblockplus plugin is also not working. I tried uninstalling firefox from synaptic package manager and reinstalling it, but in vein. When firefox is reinstalled same problem again. How to completely remove firefox from my system? Please help.

---

### Post by nhasian on 2009-07-17
if you use the synaptic package manager, you have to click on the "remove completely"  that will tell it to delete all the configuration files as well.  alternatively you can type in the terminal:

```
sudo apt-get remove --purge firefox
```

---

### Post by SteveNorman on 2009-07-17
try this first

```
rm -rf .mozilla
```

then type firefox & at the terminal for \a like new firefox.

if you really want to start over you have to do 
```
sudo apt-get remove --purge firefox
```
then search out all remaining parts using
```
sudo updatedb
locate firefox
```

then manually delete everything you see using rm

The first instruction will give you a like new firefox though, and that should fix your firefox.

---

### Post by kpkeerthi on 2009-07-17
> **jestinjoy said:**
> I was using Firefox 3.1 with some plugins like twitterfox, adblock plus, flashblock,xmarks in Ubuntu Jaunty. Now firefox is behaving badly. The bottom bar, in which twitterfox, xmarks ar shown is not showing up now. Also adblockplus plugin is also not working. I tried uninstalling firefox from synaptic package manager and reinstalling it, but in vein. When firefox is reinstalled same problem again. How to completely remove firefox from my system? Please help.

The problem is not with firefox but its messed up settings. Delete the contents of ~/.mozilla and the settings will be restored to defaults. And yes, this will cause you loose all your plugins, bookmarks and other customizations.

EDIT: SteveNorman beat me to it!

---

### Post by mcduck on 2009-07-17
Before you do anything, I must tell that you _definitely don't want to remove Firefox_.

There are lots of other programs that depend on Firefox's Gecko engine for HTML rendering, and removing Firefox will remove these programs as well. If you don't use Firefox, then don't use it. And if you want, remove it from your menus. But don't uninstall it or you end breaking several other applications as well.

---

### Post by lovinglinux on 2009-07-17
> **SteveNorman said:**
> try this first
```
rm -rf .mozilla
```

> **kpkeerthi said:**
> The problem is not with firefox but its messed up settings. Delete the contents of ~/.mozilla and the settings will be restored to defaults. And yes, this will cause you loose all your plugins, bookmarks and other customizations.

EDIT: SteveNorman beat me to it!

Several posts on these forums recommends moving, renaming or deleting **[COLOR="Sienna"]~/.mozilla[/COLOR]** folder to solve Firefox issues. While this will certainly remove any corrupted Firefox profiles and thus solve many common issues, you should consider that the **[COLOR="Sienna"]~/.mozilla[/COLOR]** folder is also the place where other Mozilla applications might store their profiles (Sunbird, etc), so removing this folder will also remove their settings. 

Firefox profiles are stored under **[COLOR="Sienna"]~/.mozilla/firefox[/COLOR]** or **[COLOR="Sienna"]~/.mozilla/firefox-x.y[/COLOR]** folders, where **[COLOR="Sienna"]x.y[/COLOR]** is the Firefox version. So if you need to remove a Firefox profile to fix a problem, then remove **[COLOR="Sienna"]~/.mozilla/firefox[/COLOR]** or **[COLOR="Sienna"]~/.mozilla/firefox-x.y[/COLOR]** not **[COLOR="Sienna"]~/.mozilla[/COLOR]**. 

Nevertheless, there also no reason to delete the entire profile if you can pinpoint the culprit inside it. Most common Firefox issues can be traced back to a single profile file. So, if you can avoid removing the entire profile, you wil be able to preserve other settings like extensions, themes, bookmarks, cookies and passwords.

To fix this problem simply follow **Solution** [*[COLOR="Red"]**FOT002**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002).

In some cases, several common issues might appear together as a result of wrong permissions of the ~/.mozilla folder. See **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] if this is the case.

To avoid similar problems in the future, follow the **[color=#CC0000]Backup[/color]** section of the same tutorial.

BTW, reinstalling Firefox usually does not help.

---

### Post by jestinjoy on 2009-07-17
Thanks for the help. I removed ~/.mozilla and now firefox run fine. Again thanks for your great help. :P

---

### Post by SteveNorman on 2009-07-18
> **lovinglinux said:**
> Several posts on these forums recommends moving, renaming or deleting **[COLOR="Sienna"]~/.mozilla[/COLOR]** folder to solve Firefox issues. While this will certainly remove any corrupted Firefox profiles and thus solve many common issues, you should consider that the **[COLOR="Sienna"]~/.mozilla[/COLOR]** folder is also the place where other Mozilla applications might store their profiles (Sunbird, etc), so removing this folder will also remove their settings. 

Firefox profiles are stored under **[COLOR="Sienna"]~/.mozilla/firefox[/COLOR]** or **[COLOR="Sienna"]~/.mozilla/firefox-x.y[/COLOR]** folders, where **[COLOR="Sienna"]x.y[/COLOR]** is the Firefox version. So if you need to remove a Firefox profile to fix a problem, then remove **[COLOR="Sienna"]~/.mozilla/firefox[/COLOR]** or **[COLOR="Sienna"]~/.mozilla/firefox-x.y[/COLOR]** not **[COLOR="Sienna"]~/.mozilla[/COLOR]**. 

Nevertheless, there also no reason to delete the entire profile if you can pinpoint the culprit inside it. Most common Firefox issues can be traced back to a single profile file. So, if you can avoid removing the entire profile, you wil be able to preserve other settings like extensions, themes, bookmarks, cookies and passwords.

To fix this problem simply follow **Solution** [*[COLOR="Red"]**FOT002**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002).

In some cases, several common issues might appear together as a result of wrong permissions of the ~/.mozilla folder. See **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] if this is the case.

To avoid similar problems in the future, follow the **[color=#CC0000]Backup[/color]** section of the same tutorial.

BTW, reinstalling Firefox usually does not help.

This is great post, thanks!

---

### Post by lovinglinux on 2009-07-18
> **SteveNorman said:**
> This is great post, thanks!

You are welcome

---

### Post by SaintDanBert on 2010-04-14
I'm running Jaunty and I was running firefox-3.1 beside firefox-3.5.

My entire firefox world went haywire -- stalls, crasher, "not respinding", "force quit" -- BAH!  I tried to tinker with new, moved, altered profiles without success.  

Then I tried to "Mark for Reinstall" without success.

Then I tried to "Completely Remove" after getting a backup of anything in $HOME that mattered to me.

When I try to re-install firefox-3.0 (and parts) or firefox-3.1 (and parts) or firefox-3.5 (and parts) I do not get a running firefox.

Then I came to the web and found several warning saying "Do Not Remove Firefox..." but I'd already done that.

How do I get a working firefox-someVersion back on my system?

---

### Post by wojox on 2010-04-14
Did you read through here: [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT002")

---

### Post by zaphodbblx on 2011-11-04
> **nhasian said:**
> if you use the synaptic package manager, you have to click on the "remove completely"  that will tell it to delete all the configuration files as well.  alternatively you can type in the terminal:

```
sudo apt-get remove --purge firefox
```

Thanks!

---

