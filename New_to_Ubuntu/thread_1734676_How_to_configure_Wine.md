---
title: "How to configure Wine?"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Arifcatalyst on 2011-04-20
Hey..Guys 
I Just Tried Ubuntu Through Webi Installer And cant stop myself from it!!!:D:D

I have some queries. As I am a freaking noobs in ubuntu
1)How to MAnuallly install apps?
2)HOw to root My account?
3)how to RuN windows aPps through Wine-When I try to change the properties of.exe files As executable?--it doesnt wish to??

Plzz Help me learNing UbuNtu And GEttInG awAY fORM WindOWS!!!:D:D

Thanxxx
Warm regards
Arif KHan

---

### Post by GWBouge on 2011-04-20
1)  Depends on the app.  Most programs will have installation docs available either on the website or in a readme file.  In most cases you can just give it execute permissions and double-click on it, or in the terminal:
```
$ cd /path/to/app
$ chmod +x app
$ ./app
```

2) You can run a command or program as root by using sudo/gksu, but if you're looking for something like the Administrator account in Windows to where you never have to enter a password to do anything ... well, don't.  HUGE security risk.  I've made it a point to NOT learn how to do that, lol.

3) You don't generally need to give an .exe executable permissions.  Just call it with wine.  But do remember, not all Windows programs work with wine, and just because it might work doesn't mean it will work flawlessly.  Time's better spent looking for native alternatives than trying to get something working through wine (that is, IF there's a suitable alternative).
```
$ cd /path/to/program.exe
$ wine program.exe
```

---

### Post by cmcanulty on 2011-04-20
usually just rt cl exe file and pick open with wine.

---

### Post by Arifcatalyst on 2011-04-21
> **GWBouge said:**
> 1)  Depends on the app.  Most programs will have installation docs available either on the website or in a readme file.  In most cases you can just give it execute permissions and double-click on it, or in the terminal:
```
$ cd /path/to/app
$ chmod +x app
$ ./app
```2) You can run a command or program as root by using sudo/gksu, but if you're looking for something like the Administrator account in Windows to where you never have to enter a password to do anything ... well, don't.  HUGE security risk.  I've made it a point to NOT learn how to do that, lol.

3) You don't generally need to give an .exe executable permissions.  Just call it with wine.  But do remember, not all Windows programs work with wine, and just because it might work doesn't mean it will work flawlessly.  Time's better spent looking for native alternatives than trying to get something working through wine (that is, IF there's a suitable alternative).
```
$ cd /path/to/program.exe
$ wine program.exe
```
AH!!! THanxx for The quicK reply
I tried To Run An Exe file by Just Right clicking, open with Wine App- But It shows the following error!!!
[IMG]http://ubuntuforums.org/%3Ca%20href=http://kma-img.com/viewer.php?file=88433478487548518266.png%20target=_blank%3E[IMG]http://kma-img.com/images/88433478487548518266_thumb.png[/IMG]
[IMG]http://kma-img.com/images/88433478487548518266.png[/IMG]


And WhenI Tried To mark It as Executableit doesNT wissH to!!! ItJust Clicks nd vanISH!!!

PLzz HElp ME
See The BElow SS

[IMG]http://kma-img.com/images/10257000980476598821.png[/IMG]
[IMG]http://kma-img.com/viewer.php?file=88433478487548518266.png][IMG]http://kma-img.com/images/88433478487548518266_thumb.png[/IMG]

---

### Post by cmcanulty on 2011-04-21
I have a few programs that won't open with the rt cl wine So I choose a custom command and browse to the wine app /usr/bin/wine and then they open after first time they just open, this is a very weird bug.

---

### Post by stoneage on 2011-04-21
You are trying to install Firefox 4.0 in Wine?

Why not install the native version:-
[http://www.mozilla.com/en-US/firefox/new/](http://www.mozilla.com/en-US/firefox/new/)
[http://techie-buzz.com/ubuntu/install-firefox-4-in-ubuntu.html](http://techie-buzz.com/ubuntu/install-firefox-4-in-ubuntu.html)

---

### Post by computerandu on 2011-04-21
Try installing only those programs by wine that are not available in Ubuntu by default.(Like firefox is available in Ubuntu). Ubuntu softwares can be downloaded from Ubuntu Software center and also through the website of the application.

If you want to know how to use Wine you can see my blog for it: 

[http://computerandu.wordpress.com/2011/04/10/how-to-install-windows-application-exe-on-linux-ubuntu-with-wine/](http://computerandu.wordpress.com/2011/04/10/how-to-install-windows-application-exe-on-linux-ubuntu-with-wine/)

---

### Post by Arifcatalyst on 2011-04-21
> **computerandu said:**
> Try installing only those programs by wine that are not available in Ubuntu by default.(Like firefox is available in Ubuntu). Ubuntu softwares can be downloaded from Ubuntu Software center and also through the website of the application.
 
If you want to know how to use Wine you can see my blog for it: 
 
[http://computerandu.wordpress.com/2011/04/10/how-to-install-windows-application-exe-on-linux-ubuntu-with-wine/](http://computerandu.wordpress.com/2011/04/10/how-to-install-windows-application-exe-on-linux-ubuntu-with-wine/)
I JusT SHowed U the example!!!!!

The ProBleM z Wid All The APps!!

Btw...I have lOst My partition!!!

Can ANy1 Guide me To dual boot UbUntu v11.04>>windows 7 installed First!!!!:(

---

