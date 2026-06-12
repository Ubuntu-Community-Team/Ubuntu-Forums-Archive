---
title: "firefox 4"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by ECET on 2011-03-10
I just downloaded firefox 4 rc and I was expecting it to just update from the version I have now, which is 3.6.15. However it did not.....I extracted the file to my desktop, I can look at all the files....I just don't know what to do....please advise...thx...

---

### Post by ~Plue on 2011-03-10
just double click the shell script 'firefox' from within the extracted folder and you're good to go

---

### Post by wilee-nilee on 2011-03-10
The Mozilla version from their site will not update the version you have, FF 3.6.15 is a tweaked version for your distro. You can though use the daily build ppa and get the tweaked 4.0 version, installed alongside the 3.15. Either versions of FF4 work the tweaked have better fonts, and are for Ubuntu specifically.
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by NightwishFan on 2011-03-10
Yeah, that is the one thing about having a cool vendor like Ubuntu/Canonical is that you can get 64-bit optimised builds of firefox with the tweaks and etc. :D

---

### Post by Yudley on 2011-03-11
when firefox 4 final version comes out, will update manager give an alert?

in other words, will apt-get update 3.6.15 to firefox 4 or 3.6.16?

---

### Post by mikewhatever on 2011-03-11
When Firefox4 makes it into Ubuntu repositories, the update manager will alert you. There is no way of knowing whether 3.6.16 will be release before or after 4.0.

---

### Post by Krytarik on 2011-03-11
Unfortunately, I believe it's very unlikely that Firefox 4 makes it into the official repos of the current releases, 10.04 and 10.10.

Instead you will most probably have to use a third party PPA, I'll try to upgrade through Ubuntuzilla's repo when the final is out. I used it back in Gutsy 7.10, they update their packages when Mozilla releases new versions.
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/](http://sourceforge.net/apps/mediawiki/ubuntuzilla/)

---

### Post by el_koraco on 2011-03-11
terminal, and then

```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa

sudo apt-get update

sudo apt-get install firefox-4.0

sudo apt-get upgrade
```

you'll then find the new firefox under applications - internet, minefield firefox 4.0. the "old" ff will be called something like nakamura. if you like ff, give it a try, it's almost as fast as chrome, and much prettier.

---

### Post by W3N4 on 2011-03-11
Sorry for OT, but..
..Why does the UI of firefox 4 on linux look nothing like on Windows ? It looks worse than Firefox 3.0

---

### Post by adduds on 2011-03-11
ya I noticed that i was pretty dissapointed....

---

### Post by kidsodateless on 2011-03-11
> **el_koraco said:**
> terminal, and then

```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa

sudo apt-get update

sudo apt-get install firefox-4.0

sudo apt-get upgrade
```you'll then find the new firefox under applications - internet, minefield firefox 4.0. the "old" ff will be called something like nakamura. if you like ff, give it a try, it's almost as fast as chrome, and much prettier.

+1. 


I use firefox4 since alpha3.
Agree! " almost fast as chrome and much prettier".
on my calculation it is totally faster than chromium.imo. :D

---

### Post by el_koraco on 2011-03-11
> **W3N4 said:**
> Sorry for OT, but..
..Why does the UI of firefox 4 on linux look nothing like on Windows ? It looks worse than Firefox 3.0

because it has good integration with the gtk theme, meaning it follows the theme you set for you desktop. besides, you are more than welcome to find a windows 7 theme for ff and install it. it will then be "prettier".

---

### Post by W3N4 on 2011-03-11
Well.. I wouldn't be so disappointed if the toolbar (containing a menu bar, an address bar, a bookmarks bar etc) wasn't so thick and had integrated location bar and search bar into one. Since I work on my laptop that has resolution 1366*768, I prefer a thin toolbar (which chrome provides).
Windows 7 theme is really something that I don't want at all. I'd just like to have a similar layout (menu button instead of menu bar at least).. I may try to adjust it a little bit because it looks really fast and I'd like to use it.

---

### Post by el_koraco on 2011-03-11
you might wanna try epiphany. it's like a mix of firefox and chrome, fast as hell, fits into the gnome DI like a charm, and is incredibly simple to use. the only problem is that it's a little buggy.

edit, you can actually have a menu button instead of a bar, you just go to views, untick the enu bar, and the next time you open a tab, you're gonna have a menu.

---

### Post by W3N4 on 2011-03-11
Thanks! It looks much better without the menu bar, I may even start using it (I'll give it a try at least).

---

### Post by el_koraco on 2011-03-11
you can also go to preferences - tabs, and tick the option always show tabs. you'll then get a chrome like layout. i actually have the same resolution as you, just tried it., and it does save up on a lot of screen space. my only dilemma is whether or not to switch back from epiphany, which i really dig.

---

### Post by Frogs Hair on 2011-03-11
I had to use a theme to get minefield looking half way decent and there aren't many compatible yet . I had both the IE9 RC and FF4 RC on Windows last night  and they are both competitors for ugliest browser award .:-s

---

### Post by Krytarik on 2011-03-11
As for the removal of the menubar, you may try this extension:
[https://addons.mozilla.org/en-US/firefox/addon/personal-menu/](https://addons.mozilla.org/en-US/firefox/addon/personal-menu/)
 in combination with this extension (to also switch the Bookmarks Toolbar into a button), it saves a lot of space in my Firefox:
[https://addons.mozilla.org/en-US/firefox/addon/toolbar-buttons/](https://addons.mozilla.org/en-US/firefox/addon/toolbar-buttons/)

**EDIT:** Unfortunately, "Personal Menu" still doesn't work with FF4 (as it should). I have extensively tried to get it working earlier in the day.

---

### Post by ChrisWells on 2011-03-12
Look for a theme called ftgraphite made by bloomind, I think he's updated it for FF4 (I'm using it on 3.6.15) and it looks stunning, he deserves it to be promoted:)

---

### Post by beew on 2011-03-12
Beauty is in the eyes of the beholder. I think FF looks better in Ubuntu than in Windows. Some people think something looks better if it is more Windows like but I am the other way.I don't like the Windozy look on the Win desktop, even when I was using Windows I used wallpaper to make it as not Windozy as possible (no blue background, thank you very much) I am not a big fan of KDE or the Mint UI (even Unity is a 100 times better. :)) because they look too much like Windows.

---

### Post by Krytarik on 2011-03-12
> **beew said:**
> I am not a big fan of KDE or the Mint UI (even Unity is a 100 times better. :)) because they look too much like Windows.
So, then I'm apparently not the only one who finds that KDE looks *un-linux-like* and -like you said- *windozy*! Thanks! ;)

---

### Post by ECET on 2011-03-12
el_koraco...thanks for the code!.....I appreciate it......

---

### Post by 5149.5 on 2011-03-13
So whats the trick for pinning FF4 to the launcher?

---

### Post by lost. on 2011-03-23
> **el_koraco said:**
> because it has good integration with the gtk theme, meaning it follows the theme you set for you desktop. besides, you are more than welcome to find a windows 7 theme for ff and install it. it will then be "prettier".

It's not the "prettiness." It's the amount of space wasted by the title bar. That space isn't wasted in the windows version and it shouldn't be wasted here.

---

