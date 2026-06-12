---
title: "best download manager for linux"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by konsolelover on 2011-05-20
hello everyone, i was wondering that which is best download manager for Linux (as there is Internet Download Manager for windows) which can support resumability and let me download youtube videos with that ease.if it is torrent supported then it would be great.....please reply guys...thanks

---

### Post by Anuovis on 2011-05-20
You could try the ["_[COLOR=Black]DownThemAll[/COLOR]_"]("https://addons.mozilla.org/en-US/firefox/addon/downthemall/") addon for Firefox if you are using this browser. It's a little clumsy to use but seems to work well.

As for torrents, a good stand-alone app is called Deluge. Available from Ubuntu Software Center.

---

### Post by konsolelover on 2011-05-20
i guess that this addon won't support resumability...and i want a resumable download manager bcoz sometimes i'll have to download larger files and i will have to shutdown my laptop or i can ordeal some network glitch.....:(

---

### Post by HermanAB on 2011-05-20
wget

---

### Post by sandyd on 2011-05-20
> **konsolelover said:**
> i guess that this addon won't support resumability...and i want a resumable download manager bcoz sometimes i'll have to download larger files and i will have to shutdown my laptop or i can ordeal some network glitch.....:(
what do you mean it doesn't support resumable downloads?
It supports them just fine, as long as you press the 'pause' button.

---

### Post by ivanovnegro on 2011-05-20
There is also JDownloader for direct downloads and for You Tube videos you can use it also but its an ugly Java app but works pefectly.

---

### Post by ngubk on 2011-05-20
One vote for Jdownloader. It can be a bit slow when open up. BUT it catch link perfectly.

---

### Post by 1991sudarshan on 2011-05-20
I use Jdownloder and Tucan! But Tucan is very simple and it can access only few sites only! For torrents better use KTorrent, It is very good!

---

### Post by beew on 2011-05-20
> **konsolelover said:**
> i guess that this addon won't support resumability...and i want a resumable download manager bcoz sometimes i'll have to download larger files and i will have to shutdown my laptop or i can ordeal some network glitch.....:(

It does and I have resumed successfully days later I logged off. But to resume you have to start Firefox and go to Tools > DownThemAll Tools and open the manager to click resume.

it also supports meta links, nothing else i know supports meta link except some obscure command line thingy whose name I have forgotten.

kget also supports resume but it is odd that the interface disappears after download is complete, it is feature rather than a bug apparently, it also does torrent though I would prefer a standalone program like deluge (actually kget may support meta links also but I am not sure since I no longer use it)

For youtube you can use the download helper addon.

---

### Post by the.lost.one on 2011-06-01
kget was running fine on my Ubuntu 11.04 64bit, but now i cant get it to work or even show up


```
$ kget
KGlobal::locale::Warning your global KLocale is being recreated with a valid main component instead of a fake component, this usually means you tried to call i18n related functions before your main component was created. You should not do that since it most likely will not work 
"/usr/bin/kget(2957)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/kget(2957)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/kget(2957)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/kget(2957)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/kget(2957)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/kget(2957)" Soprano: "QLocalSocket::connectToServer: Invalid name"
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kbuildsycoca4 running...
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action

```

What is kbuildsycoca4 btw?

---

### Post by jacob2012 on 2011-06-01
For Linux I generally just use wget, or rsync (for sites which support it). I've never tried a GUI-based Linux download manager.

---

### Post by marios88 on 2011-06-01
Firefox addons do the job for me

---

### Post by DinoT1985 on 2011-06-01
have a look at Steadyflow Download Manager.

---

