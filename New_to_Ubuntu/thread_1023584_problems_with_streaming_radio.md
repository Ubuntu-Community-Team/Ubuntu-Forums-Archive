---
title: "problems with streaming radio"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by marcusesses on 2008-12-28
I'm having problems playing streaming radio using ubuntu 8.04. 

Here's the URL

[http://www.barakastreaming.com:8088/cfcr](http://www.barakastreaming.com:8088/cfcr)

What it does for me is says "no video" and nothing ends up loading.

It's asf format. I have mplayer, plus a number of other applications I can't think of off the top of my head. But I haven't had a problem like this in a few months. 

Perhaps if I opened the site with mplayer instead, but I don't know how to do this. 

Anyway, thanks in advance!

---

### Post by Sealbhach on 2008-12-28
Hi, to make sure you have most of the multimedia plugins you need, install the Ubuntu restricted extras package. 

```
sudo apt-get install ubuntu-restricted-extras
```

This should include all the ncessary goodies you need.


.

---

### Post by RomeReactor on 2008-12-28
Hi. That link works in RhythmBox.

---

### Post by marcusesses on 2008-12-28
Updating the restricted-extras didn't seem to work...

Running the link using rhythmbox did work from the command line (which is what I want). However, it gives me an error when I run it using a script


```
export DISPLAY=:0
wake_up="03:14"

if [ "$(date +%R)" = "$wake_up" ]; then

/usr/bin/rhythmbox http://www.barakastreaming.com:8088/cfcr

fi


```

This is now getting into a completely different problem. This script works when I run it manually, but when I add it as a crontab, rhythmbox gives me an error that says:

"An error occured while loading or saving configuration information for rhythmbox. Some of your configuration settings may not work properly."

Reason? 

"Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-dgQWOXy5Uo: Connection refused)"

Help?

---

### Post by RomeReactor on 2008-12-28
Have you tried it with:
```
/usr/bin/rhythmbox --no-update -n http://www.barakastreaming.com:8088/cfcr
```
Or:
```
/usr/bin/rhythmbox-client --play-uri http://www.barakastreaming.com:8088/cfcr
```

---

### Post by marcusesses on 2008-12-28
> **RomeReactor said:**
> Have you tried it with:
```
/usr/bin/rhythmbox --no-update -n http://www.barakastreaming.com:8088/cfcr
```
Or:
```
/usr/bin/rhythmbox-client --play-uri http://www.barakastreaming.com:8088/cfcr
```

No, it didn't seem to make much difference. The first suggestion didn't work, but the second one did (and it still works if I just put the url).

When I run the script manually it works, but it doesn't get called by cron.

---

### Post by jimbob on 2008-12-28
Works just fine for me using Totem Browser Plugin 2.24.3, xine-lib version 1.1.15 in Intrepid.

---

### Post by marcusesses on 2008-12-28
Yeah, it works for me too (w/ mplayer, hardy).

My problem now is getting it to run at a specific time with cron, but I started a separate thread for that,.

---

