---
title: "Start/Stop apache on demand"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by engineer on 2006-10-24
I installed apache on my laptop and now it's running all the time.
Because I'm new to debian based systes, I don't know how to prevent automatic startup at boot time and I'm looking for some easy way to start or stop it when I want to do it.

I know I could do it with apache2ctl, but this would require to open a terminal and enter these commands every time.
As far as I've seen, apache doesn't appear in the "Services" list in Gnome menu.

---

### Post by eeGhoong0ais on 2006-10-24
I've never had any problems just leaving apache running, but if you wanted to start & stop it on demand, you could create a little script like this: ```
#!/bin/bash
#apcon.sh - simple apache control script

  if pgrep apache2
  then
    zenity --question --title="Apache Controller" --text="Apache is running. Do you want to stop it now?" && gksudo apache2ctl stop
  else
    zenity --question --title="Apache Controller" --text="Apache is not running. Do you want to start it now?" && gksudo apache2ctl start
  fi
``` and add a custom launcher for it to your panel.

---

### Post by engineer on 2006-10-24
thanks! and how can i prevent apache from being started at boot time?
thats my bigger problem. most of the time i don't need it

---

### Post by eeGhoong0ais on 2006-10-24
Services are started and stopped by the /etc/rc... scripts. There's a directory for each runlevel, from /etc/rc0.d to /etc/rc6.d, and in each of those directories you'll find a symbolic link to the apache startup script.

So, for instance, on my system there are: ```
/etc/rc0.d/K91apache2
/etc/rc1.d/K91apache2
/etc/rc2.d/S91apache2
/etc/rc3.d/S91apache2
/etc/rc4.d/S91apache2
/etc/rc5.d/S91apache2
/etc/rc6.d/K91apache2
```S stands for Start, K stands for Kill, and 91 indicates when to run the script, compared to all the others in the directory. If I wanted to prevent apache from starting automatically, I'd do this: ```
sudo mv /etc/rc2.d/S91apache2 /etc/rc2.d/K91apache2
sudo mv /etc/rc3.d/S91apache2 /etc/rc3.d/K91apache2
sudo mv /etc/rc4.d/S91apache2 /etc/rc4.d/K91apache2
sudo mv /etc/rc5.d/S91apache2 /etc/rc5.d/K91apache2
``` ... which is better than just removing the links, firstly because it makes things easier if you change your mind, and secondly because package upgrade scripts will know that you've deliberately changed things and they shouldn't change them back.

---

### Post by engineer on 2006-10-24
thank you!

should i be able to control apaches run behavior with the "services" program in gnomes menu?
or is it normal that apache doesn't appear in that list?

---

### Post by eeGhoong0ais on 2006-10-24
Actually, apache is in my Panel > System > Administration > Services ... I generally don't bother with the GUI admin tools very much, so I hadn't looked before.

No idea why it hasn't appeared in yours - sorry.

---

### Post by goneskiing on 2007-01-07
I just upgraded to Edgy from Dapper and now Apache is gone from my System Admin Services menu also - maybe someone took it out thinking it is only on server installation ?  But web developers need it on desktop installation.  Back to command line (just have to keep cheatsheet with all these command line statements).

---

### Post by robertmf on 2008-03-08
> **goneskiing said:**
> I just upgraded to Edgy from Dapper and now Apache is gone from my System Admin Services menu also - maybe someone took it out thinking it is only on server installation ?  But web developers need it on desktop installation.  Back to command line (just have to keep cheatsheet with all these command line statements).

[COLOR="DarkRed"]**Etiol** thanks for the bash apache start/stop script :)

The LAMP 'Gutsy' install includes apache2 and mySql in [SYS->ADMIN->SERVICES][/COLOR]

---

