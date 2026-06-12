---
title: "help with simple script"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by Tconnors123 on 2009-09-21
i am new to linux so please bear with me.  i am running ubuntu 9.04 and had a question about writing a script.  I wanted to write a small program that would open once aday and scan my file system for .mp3 files.  Then i wanted it to update a list all the music files including there location. And finally i was going to use the alias command to create a shortcut to run mpg321 -Zv-@playlistname and call it shuffle so i can play all my music with one easy command

---

### Post by Tconnors123 on 2009-09-21
i am new to linux so please bear with me.  i am running ubuntu 9.04 and had a question about writing a script.  I wanted to write a small program that would open once aday and scan my file system for .mp3 files.  Then i wanted it to update a list all the music files including there location. And finally i was going to use the alias command to create a shortcut to run mpg321 -Zv-@playlistname and call it shuffle so i can play all my music with one easy command

---

### Post by j7%&lt;RmUg on 2009-09-21
Well im not too sure how this could be done, but in any case using a bash script is probably the best way.

You could probably use cron jobs to run the script daily, or just make it run at startup if you want it to only run when you boot up the computer.

---

### Post by hamsandwich on 2009-09-21
I am not an expert but maybe put something like this in a text file:
```

#!/bin/bash

find /path/to/search/in/ -mount -iname *.mp3 >> /home/myhomedir/mp3list.txt
```

say you've saved it as myscript, you need to make it executable:

```
chmod +x myscript
```

then stick a copy in /etc/cron.daily like so

```
ln -s myscript /etc/cron.daily/
```

where basically /path/to/search/in/ can be any path, even "/" for the entire filesystem. The -mount option means don't check networked file systems (remove if you want to) and it outputs a text file in your home directory call mp3list.txt. Any script in /etc/cron.daily gets run once a day, I think at midnight.

hope that is helpful.

---

### Post by j.bell730 on 2009-09-21
This was quite a fun project for me, no matter how simple it was, I got it to work with just two lines.

```
find ~ -name \*.mp3 -print > ~/scannedmusic.txt
mpg321 -Zv-@~/scannedmusic.txt
```

Save it as anything you want .sh, and launch it with
```
sh <nameofscript>.sh
```

---

### Post by hailtothethief on 2009-09-21
Yep, you'll need a cron job to be sure.

You'll probably want to run

```
find / -name *.mp3
```

Which will list all .mp3's on your system. Be careful though, some proprietary games carry audio files (sound effects) as .mp3's. You might want to trim the results by files size (using the `**du**` command).

And here's [a guide about using cron]("http://www.unixgeeks.org/security/newbie/unix/cron-1.html")

This is an interesting idea. I'd like to see how this turns out.

---

### Post by Rocket2DMn on 2009-09-21
Threads merged.  Please don't cross-post, it isn't fair to the volunteers contributing their time here, and doesn't really result in getting more or better help.  Thank you.

---

### Post by lswb on 2009-09-21
FYI, there is already a service running via a daily cron job on a default ubuntu install named updatedb. It creates an indexes of **all** files on the system. The database can be queried with the "locate" command. For example using the command 

locate *.mp3

will list all files whose names end in '.mp3' Check the man page for info on how to use regex searches. Note that by default "locate string" will return all filenames matching "*string*" according to usual shell filename globbing rules. 

Adantage of using locate & the updatedb database are that it runs anyway, so it will run much faster using less resources than "find"

---

