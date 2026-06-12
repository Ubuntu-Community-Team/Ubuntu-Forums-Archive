---
title: "Script, crontab and killing the script"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by Beto on 2011-02-25
If I have a script which is run using cron with the command "sh /home/foo/mydir/myscript.sh".

How can I kill it later if I can't tell with "ps" which one of all the scripts running is? I have many "sh"'s in ps....

Regards

---

### Post by yeats on 2011-02-25
> **Beto said:**
> If I have a script which is run using cron with the command "sh /home/foo/mydir/myscript.sh".

How can I kill it later if I can't tell with "ps" which one of all the scripts running is? I have many "sh"'s in ps....

You could do something like: 

```
ps aux | grep myscript
```

which would target the relevant process(es)

---

### Post by seawolf167 on 2011-02-25
You could also use

```
top
```

though I prefer

```
sudo apt-get install htop
```

when you run htop, if you hit F3, you can search for running processes, then F9 or 'k' will allow you to kill the process

---

### Post by Beto on 2011-02-25
> **yeats said:**
> You could do something like: 

```
ps aux | grep myscript
```

which would target the relevant process(es)

Thanks, "ps aux" was the answer I needed.

---

### Post by Beto on 2011-02-25
> **seawolf167 said:**
> You could also use

```
top
```

though I prefer

```
sudo apt-get install htop
```

when you run htop, if you hit F3, you can search for running processes, then F9 or 'k' will allow you to kill the process

top would have been good if a human were killing the script process, but it has to be killed by cron. So I guess is no good this time.

Thanks anyway.

---

### Post by aeiah on 2011-02-25
> **yeats said:**
> You could do something like: 

```
ps aux | grep myscript
```

which would target the relevant process(es)

this isnt the best way to do it, because your grep process will also have the name 'myscript' in it, and will show up regardless. you need to then pipe it to 'grep -v grep', which does an inverse search and gets rid of the grep result :D

i have this set up as an alias:

```

alias alive='ps -ef|grep -v grep|grep -i '

```
so i can just type 'alive mplayer' and it'll show me the mplayer process if it's running (but not the grep mplayer process).

i also use it in a bash script to toggle deluge on and off
```

#!/bin/sh
icon='/home/satsuma/.icons/Faenza/apps/48/deluge.png'
# Test to see if deluged is running first
if ps -ef|grep -v grep|grep -i deluged
then
killall deluged;
echo 'dead'
notify-send -i ${icon} 'Deluge daemon' 'disabled';
exit
else
deluged;
notify-send -i ${icon} 'Deluge daemon' 'enabled';
fi
exit

```

---

### Post by yeats on 2011-02-25
> **aeiah said:**
> this isnt the best way to do it, because your grep process will also have the name 'myscript' in it, and will show up regardless. you need to then pipe it to 'grep -v grep', which does an inverse search and gets rid of the grep result :D

Ah - good point - wasn't thinking about that. ;-)  Another way do exclude grep that I saw recently is to put square brackets around the first letter (in effect creating a "set" of one letter):

```
ps aux | grep [m]yscript
```

---

### Post by Beto on 2011-02-26
I realized that and was already trying to circumvent that problem... thanks again for the answers!

---

