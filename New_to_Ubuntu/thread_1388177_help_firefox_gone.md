---
title: "help firefox gone"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-01-22
I went to open firefox and it is gone from panel, from all menus. I don't want to lose all my bookmarks and sessions settings etc. It is listed as installed by the software center. I tried adding to panel and it is even gone from the internet list there! How can I find it and open it.There was a black box in panel I deleted as it was not anything I recognized and now no firefox! When I try to open a web page I get it looking something like fire fox but it is Namoroka web browser this is after I did a bunch of firefox updates, what is going on?

---

### Post by epicoder on 2010-01-22
In the future, please try to make your posts more readable. We can't help you if we have no idea what you're saying. ;)

Press Alt + F2, then type 'firefox' without the quotes, then click Run.

---

### Post by kansasnoob on 2010-01-22
> **cmcanulty said:**
> I went to open firefox and it is gone from panel, from all menus. I don't want to lose all my bookmarks and sessions settings etc. It is listed as installed by the software center. I tried adding to panel and it is even gone from the internet list there! How can I find it and open it.There was a black box in panel I deleted as it was not anything I recognized and now no firefox! When I try to open a web page I get it looking something like fire fox but it is Namoroka web browser this is after I did a bunch of firefox updates, what is going on?

If you go to Software Sources you'll probably see under the Other Software tab that you have an "ubuntu-mozilla-daily" repo enabled. That's pre-release, often unstable stuff.

You didn't say whether this is 32 bit or 64 bit?

I like using Ubuntuzilla to get the latest updates:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

I doubt you lost anything. I wrote this last night:

[http://ubuntuforums.org/showpost.php?p=8705493&postcount=6](http://ubuntuforums.org/showpost.php?p=8705493&postcount=6)

---

### Post by kansasnoob on 2010-01-22
> **sh228 said:**
> In the future, please try to make your posts more readable. We can't help you if we have no idea what you're saying. ;)

Press Alt + F2, then type 'firefox' without the quotes, then click Run.

I see nothing at all "unreadable"????????????

---

### Post by kansasnoob on 2010-01-22
Another hint, when something is gone from the menu go to System > Preferences > Main Menu and search under the correct category :)

---

### Post by lovinglinux on 2010-01-22
Here we go, the first Namoroka complain thread...

Namoroka is the development name of Firefox 3.6. Like already pointed on another reply, you probably have *ubuntu-mozilla-daily* ppa repository and thus your Firefox was updated with the latest release from that repository. There is nothing wrong with it. 

The only possible drawback of using this repository is that it will continue to serve you with updates of Firefox, even if they are alphas, betas or release candidates. But if you if you are using 64bit, that is the best way to update Firefox to 3.6 right now.

If you don't want Firefox 3.6, simply disable the *ubuntu-mozilla-daily* ppa, remove firefox from the software manager and install it again. You will get the default Firefox 3.5, which eventually will be officially updated to 3.6.

About losing your settings, don't worry. Firefox works with user profiles, so everything like bookmarks, extensions, passwords, cookies and settings are saved in your home directory, under the hidden folder named .mozilla. You can completely remove Firefox and install it again, because your profile will still be there and you won't notice any difference when you start Firefox again. Nevertheless, I strongly recommend making backups of your Firefox profile if these settings are so important to you, because they can become corrupted with regular usage. You can do that by simply copying the .mozilla/firefox folder or using [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension, which does scheduled backups too.

Additionally, I recommend that you read the **[COLOR="Sienna"]Install Other Versions[/COLOR]** section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567), so you can have a better understanding of what is going on. That tutorial will also provide you with a lot of information about optimizing and avoiding problems with Firefox.

---

### Post by mkvnmtr on 2010-01-22
After tje update I restarted and that funny black box was gone and the normalicon was there. Now you will need to drag rhe icon from your menu and put it back on the panel. You will like the new Firefox with the funny name.

---

### Post by cmcanulty on 2010-01-23
It isn't on the options to add back to the menu. Also I uninstalled disabled the daily updates and reinstalled with synaptic firefox 3.5 and I still get namaroka not firefox.OK I reinstalled and 2nd time it put firefox and lost the namoroka, thanks everyone. Oh an update, now when I open any session I get all blank tabs. My sessions are still in the session folder. Is there a fix for this?

---

### Post by lovinglinux on 2010-01-23
> **cmcanulty said:**
> It isn't on the options to add back to the menu. Also I uninstalled disabled the daily updates and reinstalled with synaptic firefox 3.5 and I still get namaroka not firefox.OK I reinstalled and 2nd time it put firefox and lost the namoroka, thanks everyone. Oh an update, now when I open any session I get all blank tabs. My sessions are still in the session folder. Is there a fix for this?

Close Firefox and delete ~/.mozilla/firefox/sessionstore.js

---

### Post by cmcanulty on 2010-01-23
thanks all, saved my precious ff settings

---

