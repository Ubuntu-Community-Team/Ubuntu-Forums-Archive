---
title: "updating Firefox"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by ~The~Killer~ on 2009-08-22
Hi.

I've installed the lastest version of Firefox 3.5.2 and it's on my desktop. Now what to do? I am totally Lost if I clicked it gives me the files inside it.

How can i update firefox now?

Thanks

---

### Post by philinux on 2009-08-22
If you are using Jaunty then install it from the repos.

In the address bar of firefox type this:

apt://firefox-3.5

During the install it will copy your 3.0 profile for it's use.

Dont worry it's called shiretoko for now and ends up in Apps>Internet. you can add a launcher to your panel.

When Karmic comes out in October 3.5 will be the default browser.

---

### Post by kelvin.illa on 2009-08-22
i think, if i get your problem correctly, what  you've done is _just downloaded the compressed file from Mozilla._ if that was right, then here's my response:

here's a tutorial i used when i did mine:

[http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html)
 -  by "Andrew," 18 June, 2009

it works.

it installs directly from the Mozilla-daily repository so no more "I am totally Lost if I clicked it gives me the files inside it."

---

### Post by sandyd on 2009-08-22
open up a terminal, and cd to the directory where you extracted the files.

Then 
```

./firefox

```
to run it.

Then, assuming the folder is on the desktop, and its called firefox*

```

sudo chmod 777 /opt
mv ~/Desktop/firefox* /opt/firefox3
cd /opt/firefox3
sudo ln /opt/firefox3/firefox /usr/bin/firefox3

```
create a new launcher that points to the command "firefox3"

---

### Post by oldsoundguy on 2009-08-22
or, if you have an older version of Ubuntu that WILL NOT have the latest Firefox in the repositories, there is another method that can be migrated across builds as it no longer will use the repositories, but a python script and terminal to update.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

I use it on 8.4 LTS, for instance.

---

### Post by lovinglinux on 2009-08-22
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

