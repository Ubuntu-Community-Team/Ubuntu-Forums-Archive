---
title: "True Combat Elite Install Error"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by shoaibi on 2009-08-22
I downloaded wolfstein and its path, then tce and its patch. Saved them inside "True Combat Elite" in my home folder.
I installed wolfstein and its patch without any issues. Problems arose when i tried to install TCE:

```

[04:56 PM] shoaibi@blade:~/True Combat Elite $ sudo ./TrueCombatElite_v049_Linux.run.gz 
Verifying archive integrity... All good.
Uncompressing TrueCombat Elite: 0.48-english.................................................................................................................
Please visit http://www.liflg.org
Searching Return to Castle Wolfenstein: Enemy Territory....
md5sum: /home/shoaibi/True: No such file or directory
Return to Castle Wolfenstein: Enemy Territory found in /home/shoaibi
[: 85: !=: argument expected
Installing in /home/shoaibi

Gdk-WARNING **: locale not supported by C library
^C

```

cancelled because i didn;t want it to install in my homedir.

Renamed the directory containing files:
```

[04:59 PM] shoaibi@blade:~/True Combat Elite $ cd
[04:59 PM] shoaibi@blade:~ $ mv True\ Combat\ Elite/ TCE
`True Combat Elite/' -> `TCE'
[04:59 PM] shoaibi@blade:~ $ cd TCE/

```

Trying again:
```

[04:59 PM] shoaibi@blade:~/TCE $ sudo ./TrueCombatElite_v049_Linux.run.gz 
Verifying archive integrity... All good.
Uncompressing TrueCombat Elite: 0.48-english.................................................................................................................
Please visit http://www.liflg.org
Searching Return to Castle Wolfenstein: Enemy Territory....
md5sum: /home/shoaibi/TCE/Enemy: No such file or directory
Return to Castle Wolfenstein: Enemy Territory found in /home/shoaibi/TCE
[: 85: !=: argument expected
Installing in /home/shoaibi/TCE
sed: can't read uninstall.bak: No such file or directory
Done.

Gdk-WARNING **: locale not supported by C library

Gtk-CRITICAL **: file gtkwidget.c: line 1510 (gtk_widget_hide): assertion `widget != NULL' failed.



[05:00 PM] shoaibi@blade:~/TCE $ ls
Enemy Territory 2.60b  tce049b_all_os_fixed               uninstall
et_2.60b.zip           tce049b_all_os_fixed.zip
ET_v2.60_Linux.run.gz  TrueCombatElite_v049_Linux.run.gz

[05:00 PM] shoaibi@blade:~/TCE $ rm -rf Enemy\ Territory\ 2.60b/ uninstall 
removed `Enemy Territory 2.60b/win32/ET.exe'
removed `Enemy Territory 2.60b/win32/ETDED.exe'
removed directory: `Enemy Territory 2.60b/win32'
removed `Enemy Territory 2.60b/README.txt'
removed `Enemy Territory 2.60b/linux/et.x86'
removed `Enemy Territory 2.60b/linux/etded.x86'
removed directory: `Enemy Territory 2.60b/linux'
removed `Enemy Territory 2.60b/.DS_Store'
removed `Enemy Territory 2.60b/EULA_Wolfenstein_Enemy_Territory.txt'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/PkgInfo'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/Icon.icns'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/ui_mac.bundle/Contents/pbdevelopment.plist'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/ui_mac.bundle/Contents/Info.plist'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/ui_mac.bundle/Contents/MacOS/ui_mac'
removed directory: `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/ui_mac.bundle/Contents/MacOS'
removed directory: `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/ui_mac.bundle/Contents'
removed directory: `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/ui_mac.bundle'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/cgame_mac.bundle/Contents/pbdevelopment.plist'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/cgame_mac.bundle/Contents/Info.plist'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/cgame_mac.bundle/Contents/MacOS/cgame_mac'
removed directory: `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/cgame_mac.bundle/Contents/MacOS'
removed directory: `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/cgame_mac.bundle/Contents'
removed directory: `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/cgame_mac.bundle'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/Wolfenstein ET.rsrc'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/qagame_mac.bundle/Contents/pbdevelopment.plist'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/qagame_mac.bundle/Contents/Info.plist'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/qagame_mac.bundle/Contents/MacOS/qagame_mac'
removed directory: `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/qagame_mac.bundle/Contents/MacOS'
removed directory: `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/qagame_mac.bundle/Contents'
removed directory: `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/qagame_mac.bundle'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources/pk3.icns'
removed directory: `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Resources'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/Info.plist'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/MacOS/Wolfenstein ET'
removed directory: `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/MacOS'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents/.DS_Store'
removed directory: `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/Contents'
removed `Enemy Territory 2.60b/macosx/Wolfenstein ET.app/.DS_Store'
removed directory: `Enemy Territory 2.60b/macosx/Wolfenstein ET.app'
removed directory: `Enemy Territory 2.60b/macosx'
removed directory: `Enemy Territory 2.60b'
removed `uninstall'


[05:00 PM] shoaibi@blade:~/TCE $ sudo ./TrueCombatElite_v049_Linux.run.gz 
Verifying archive integrity... All good.
Uncompressing TrueCombat Elite: 0.48-english.................................................................................................................
Please visit http://www.liflg.org
Searching Return to Castle Wolfenstein: Enemy Territory....
Return to Castle Wolfenstein: Enemy Territory found in /usr/local/games/enemy-territory
-e 
ERROR!
You need Return to Castle Wolfenstein: Enemy Territory version 2.60!

Could not find Return to Castle Wolfenstein: Enemy Territory


[05:03 PM] shoaibi@blade:~/TCE $ sudo ./TrueCombatElite_v049_Linux.run.gz 
Verifying archive integrity... All good.
Uncompressing TrueCombat Elite: 0.48-english................................................................................................................^CSignal caught, cleaning up

[05:03 PM] shoaibi@blade:~/TCE $ sudo su

root@blade:/home/shoaibi/TCE# ./TrueCombatElite_v049_Linux.run.gz 
Verifying archive integrity... All good.
Uncompressing TrueCombat Elite: 0.48-english.................................................................................................................
Please visit http://www.liflg.org
Searching Return to Castle Wolfenstein: Enemy Territory....
Return to Castle Wolfenstein: Enemy Territory found in /usr/local/games/enemy-territory
-e 
ERROR!
You need Return to Castle Wolfenstein: Enemy Territory version 2.60!

Could not find Return to Castle Wolfenstein: Enemy Territory

root@blade:/home/shoaibi/TCE# 

```


And now i can't install it anymore...

---

### Post by ibuclaw on 2009-08-22
Run:
```
file TrueCombatElite_v049_Linux.run.gz
```
By the looks of it that is a gzip file, so no wonder it doesn't work. ;)

```
gunzip TrueCombatElite_v049_Linux.run.gz
sudo sh TrueCombatElite_v049_Linux.run
```
:)

Regards
Iain

---

### Post by shoaibi on 2009-08-22
i did try that:
root@blade:/home/shoaibi/TCE# file TrueCombatElite_v049_Linux.run.gz 
TrueCombatElite_v049_Linux.run.gz: POSIX shell script text executable

so i just executed it.

---

### Post by ibuclaw on 2009-08-22
> **shoaibi said:**
> i did try that:
root@blade:/home/shoaibi/TCE# file TrueCombatElite_v049_Linux.run.gz 
TrueCombatElite_v049_Linux.run.gz: POSIX shell script text executable

so i just executed it.
Oh I see... how strange ...

Anyway, as for ET missing:

If you are on 32bit Ubuntu, follow this guide on gwos: [http://gwos.org/doku.php/guides:32bit:et_wolfenstein](http://gwos.org/doku.php/guides:32bit:et_wolfenstein)

Likewise for 64bit Ubuntu: [http://gwos.org/doku.php/guides:64bit:et_wolfenstein](http://gwos.org/doku.php/guides:64bit:et_wolfenstein)

Regards
Iain

---

### Post by shoaibi on 2009-08-22
already did, tried again, no use...
ET installs fine, TCE gives error.

---

### Post by shoaibi on 2009-08-22
latest output:

```

 sudo ./TrueCombatElite_v049_Linux.run.gz 
Verifying archive integrity... All good.
Uncompressing TrueCombat Elite: 0.48-english.................................................................................................................
Please visit http://www.liflg.org
Searching Return to Castle Wolfenstein: Enemy Territory....
Return to Castle Wolfenstein: Enemy Territory found in /home/shoaibi/TCE/etpath/linux
-e 
ERROR!
You need Return to Castle Wolfenstein: Enemy Territory version 2.60!

Return to Castle Wolfenstein: Enemy Territory found in /usr/local/games/enemy-territory
-e 
ERROR!
You need Return to Castle Wolfenstein: Enemy Territory version 2.60!

Could not find Return to Castle Wolfenstein: Enemy Territory


```


and after deleting the patch folder:

```

sudo ./TrueCombatElite_v049_Linux.run.gz 
Verifying archive integrity... All good.
Uncompressing TrueCombat Elite: 0.48-english.................................................................................................................
Please visit http://www.liflg.org
Searching Return to Castle Wolfenstein: Enemy Territory....
Return to Castle Wolfenstein: Enemy Territory found in /usr/local/games/enemy-territory
-e 
ERROR!
You need Return to Castle Wolfenstein: Enemy Territory version 2.60!

Could not find Return to Castle Wolfenstein: Enemy Territory

```

---

### Post by ibuclaw on 2009-08-22
Hmm... seems to have installed just fine for me. What architechture are you running on?


I could build a deb package for it, if you like...

---

### Post by shoaibi on 2009-08-22
I am using ubuntu 9.04 jaunty jackalope x86_64. Would appreciate the effort of you building a package. While you are at it, can you build two packages, one fro 32b and one for 64b if possible? i would like to test it on my other machine which has been giving same issues.

PS:
how can uninstall the current installs of ET?

---

### Post by ibuclaw on 2009-08-22
> **shoaibi said:**
> I am using ubuntu 9.04 jaunty jackalope x86_64. Would appreciate the effort of you building a package. While you are at it, can you build two packages, one fro 32b and one for 64b if possible? i would like to test it on my other machine which has been giving same issues.

PS:
how can uninstall the current installs of ET?

No point really doing 64/32 in different packages. You can just use [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") to satisfy binary dependencies.

To uninstall:
```
sudo rm -r /usr/local/games/enemy-territory
find -L /usr/local/bin -type l | xargs sudo rm
sudo rm /usr/share/applications/et.desktop

```

Regards
Iain

---

### Post by shoaibi on 2009-08-22
okay, i guess i am waiting then...

---

### Post by ibuclaw on 2009-08-22
> **shoaibi said:**
> okay, i guess i am waiting then...

Yes, have built and tested the package.

Everything seems fine ... (although it took me 30 minutes before I could begin playing because I needed alot of .pk3 files from the server I went on ... it would make sense to get them one at a time for the current map you are playing, but oh well ...).

Just uploading the (700MB) file now. Will take about 2 hours to finish.

Regards
Iain

---

### Post by shoaibi on 2009-08-22
Thanks a lot.... really appreciate it, infact i would suggest you make a PPA, would really help people like me...

---

### Post by ibuclaw on 2009-08-22
OK, here we go:
[true_combat]("http://jumbofiles.com/5vwbvmjrkfcq")
[enemy_territory]("http://jumbofiles.com/8um02fli2pch")
[et_punkbuster]("http://jumbofiles.com/qlovgff69apl")

In the end, I had to split them into separate packages. At least, that is my interpretation of the license agreement that comes along with them.
you can redistribute so long as (1) They come with the EULA, and (2) they aren't bundled together with any other software other than what they originally came with.

I may look into seeing if they could be hosted on getdeb/playdeb. Other than that, if anyone wants them. Come get and have fun playing. :)

Regards
Iain

---

### Post by shoaibi on 2009-08-23
install squence would be:
enemy_territory
true_combat
et_punkbuster

right? and whats punkbuster? anticheat software or such?

btw, thanks :D

---

### Post by ibuclaw on 2009-08-23
> **shoaibi said:**
> install squence would be:
enemy_territory
true_combat
et_punkbuster

right? and whats punkbuster? anticheat software or such?

btw, thanks :D

Yeah, it comes with ET, and I thought that I might just split it off.

You will probably need it if you want to join servers in ET.
Also, you may want to consider updating it too, as I do believe that it is rather outdated (some/the vast majority of servers may kick you on entry).

Just download the update here and apply it to the ET game folder: [http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php)

Regards
Iain

---

### Post by shoaibi on 2009-08-23
okay, i have downloaded and installed it.
Two things:
1. Is the game just for online multiplayer? no bots to play it locally for practice?
2. It runs pretty slow on my system, like when i enabled pb for the first time my system hung up for about 40 seconds, takes years to connect to a server, My system config is:
Intel 2.0 Dual Core
4G RAM
4G Swap

I have Dell Inspiron 1545.

---

### Post by ibuclaw on 2009-08-23
> **shoaibi said:**
> okay, i have downloaded and installed it.
Two things:
1. Is the game just for online multiplayer? no bots to play it locally for practice?
2. It runs pretty slow on my system, like when i enabled pb for the first time my system hung up for about 40 seconds, takes years to connect to a server, My system config is:
Intel 2.0 Dual Core
4G RAM
4G Swap

I have Dell Inspiron 1545.

1) Yep, it is all multiplayer. :)
2) I did mention that it took me about 40 minutes to download all the server .pk3 files ... and **then** the games began.
There is nothing wrong with your system, it is the application downloading a mass load of packs from the servers.

If you want to speed it up, set your internet connection to "**LAN/Cable/xDSL**". That help things get along quicker for me.
It is an unfortunate setting, yes, I would rather that I get the maps one at a time when I need them, rather than downloading a further 400MB of data.

Equally, it is not the games' fault either ... by default you have 6 maps, and since the game's inception there have been 100s more created.

Trust me, once you get past the first 40 minutes of waiting/downloading maps, the games start rolling, and life gets easier. ;)
I think I'll have a few rounds in the "TCE-0.49b BC TCE-MASSA.COM" server. If you can catch up, I may just see you there.

edit: 
perhaps giving the game more memory allocation will help things speed up:

In the game, press the backtick **`** key, and type in:
```

/com_hunkmegs "128"

```
Then restart.

Regards
Iain

---

### Post by shoaibi on 2009-08-23
when  i talked about slow, it was gameplay...
Plus after the first start of the game, there is no sound, headache starts..

---

### Post by CRAY-4 on 2009-11-05
kill pulseaudio, that should fix things

---

