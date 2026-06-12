---
title: "shutdown in root crontab does not work"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-08-22
Hi Ubuntu Community:

I want my machine to shutdown every Sunday at 8:30am so that I can save electricity.

I wrote the script /home/philipsmith/Music/scripts/shutdown

**[COLOR="blue"]shutdown -h "now"[/COLOR]**

This script works perfectly when I type it into a termal windown as sudo user, ie:

sudo -i
<correct password entered>
/home/philipsmith/Music/scripts/shutdown

Then my machine shuts down!

However, I added the following line to my sudo crontab:

**[COLOR="Blue"]30  8 * * 0   /home/philipsmith/Music/scripts/shutdown[/COLOR]**

This doesn't work!!

Can somebody tell me why?

Thanks,
Phil Smith
DUluth, GA

---

### Post by martin_legion on 2010-08-23
you can try adding root before the command, like this:

> 30 8 * * 0 root /home/philipsmith/Music/scripts/shutdown

This means that the command must be ran as root.

Hope it helps!

---

### Post by Old Jimma on 2010-08-25
Did not work.

---

### Post by spjackson on 2010-08-25
> **Phil Smith said:**
> 
I wrote the script /home/philipsmith/Music/scripts/shutdown

**[COLOR=blue]shutdown -h "now"[/COLOR]**


This is almost certainly because shutdown is not in the PATH when run from cron. See also [http://ubuntuforums.org/showthread.php?t=1560696](http://ubuntuforums.org/showthread.php?t=1560696)

There are a number of solutions, the easiest perhaps being to change your script to
```

/sbin/shutdown -h "now"

```Of course it needs to be run as root too.

```

sudo crontab -e

```to edit root's crontab entries, but I see that you have done that.

---

### Post by trikster_x on 2010-08-25
first:
```
sudo crontab -e
```

then:
```
30 8 * * 0 sudo shutdown -h +0
```

You can run simple commands in crontab without making a script for them.  you can even run the apt-get update & upgrade commands if you remember to include the -y option to make scheduled update times followed by a shutdown -r to reboot.

And yes you need to include sudo in the command even though it is the root crontab, I just tested it.

---

### Post by spjackson on 2010-08-26
> **trikster_x said:**
> first:
```
sudo crontab -e
```then:
```
30 8 * * 0 sudo shutdown -h +0
```You can run simple commands in crontab without making a script for them.  you can even run the apt-get update & upgrade commands if you remember to include the -y option to make scheduled update times followed by a shutdown -r to reboot.

And yes you need to include sudo in the command even though it is the root crontab, I just tested it.
That's strange. I don't need sudo. The following in root's crontab shuts down my system; I just tested it.
```

# m h  dom mon dow   command
30 13 * * * /sbin/shutdown -h now

```

---

### Post by Old Jimma on 2010-08-26
[COLOR="Red"]***_SPJackson-Dude! You da man!_***[/COLOR]

putting the shutdown command in root crontab works great!!!  :p

For example

sudo -i
<password"
crontab -e

and then adding:

0 6 * * 5 /sbin/shutdown -h "now"

shuts Ubuntu down at ***_exactly 6am every Friday_***! 

Kaboom!! 6am? Friday? [COLOR="Red"]**Ubuntu shutsdown!!**[/COLOR]  \\:D/

Thanks for all who contributed to this post!

I can now save a little electricity! Every little bit helps!!

Many thanks,
Phil Smith
Duluth, GA

---

