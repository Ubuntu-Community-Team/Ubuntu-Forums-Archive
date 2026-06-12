---
title: "get firefox to use duluge as defualt?"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-10
Firefox Doesn't have an option to set deluge to open torrent files as default so I went to Edit--> Preferences --> Applications and then to the bittorrent Seed File option but there's still no way to select deluge the only thing is to browse for an application but I don't know where the program is stored...

---

### Post by _Purple_ on 2009-04-10
When you try to download a torrent file using firefox, do you get a popup box asking you to select a program to open the file with? There you can select Deluge and tick the box beside "Do this automatically for files like this from now on".

---

### Post by MrWES on 2009-04-10
> **kamitsukai said:**
> Firefox Doesn't have an option to set deluge to open torrent files as default so I went to Edit--> Preferences --> Applications and then to the bittorrent Seed File option but there's still no way to select deluge the only thing is to browse for an application but I don't know where the program is stored...


it's in /usr/bin/deluge

Next time, open up a terminal and type

```
which deluge
```

and you'll get your answer :)

Bill

---

### Post by KhaaL on 2009-04-10
Kami, i think if you install the MIME edit addon ( [https://addons.mozilla.org/en-US/firefox/addon/4498](https://addons.mozilla.org/en-US/firefox/addon/4498) ) then you could alter what program will open torrent files even further

---

### Post by kamitsukai on 2009-04-10
> **MrWES said:**
> it's in /usr/bin/deluge

Next time, open up a terminal and type

```
which deluge
```

and you'll get your answer :)

Bill

Thanks very much!:guitar:

---

### Post by lovinglinux on 2009-04-10
> **KhaaL said:**
> Kami, i think if you install the MIME edit addon ( [https://addons.mozilla.org/en-US/firefox/addon/4498](https://addons.mozilla.org/en-US/firefox/addon/4498) ) then you could alter what program will open torrent files even further

That extension is for Firefox 2.0.x.

> Addon creator 'White Alice' ([https://addons.mozilla.org/en-US/firefox/user/84420](https://addons.mozilla.org/en-US/firefox/user/84420)) has released an inofficial update of Mime Edit which works with FF 3.x.

---

