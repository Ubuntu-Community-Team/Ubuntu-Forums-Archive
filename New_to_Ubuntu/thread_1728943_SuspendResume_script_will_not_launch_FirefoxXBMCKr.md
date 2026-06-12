---
title: "Suspend/Resume script will not launch Firefox/XBMC/Krusader after resume"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by deckoff on 2011-04-14
I have tried this at Kubuntu 10.10 and Xubuntu 10.04.
My goal is to kill an XBMC and restart it after resume. The process should go that way:
1. Suspend command
2. XBMC killed
3. PC sleeping
4 Resume command
5 PC resuming
6 XBMC launched

OR

1. Suspend command
2. PC sleeping
3. Resume command
4. PC resuming 
5  XBMC killed
6  XBMC launched

I had some troubles with killing XBMC, so I tried the script with Firefox and Krusader too. The script will kill Krusader and Firefox, but will not relaunch them. 

Here is a script I tried with Firefox

```
sudo touch /etc/pm/sleep.d/99_restartFirefox
sudo chmod a+x /etc/pm/sleep.d/99_restartFirefox
sudo nano /etc/pm/sleep.d/99_restartFirefox
```I create the following content:

```

#!/bin/bash
#
# restart Firefox
# position /etc/pm/sleep.d/99_restartFirefox

#case "$1" in
    hibernate|suspend)
       killall firefox-bin
        ;;
    thaw|resume)
       /usr/bin/firefox
        ;;
    *)
        ;;
esac
exit $?

```
It seems I am missing something in the launch app command, any help

---

### Post by deckoff on 2011-04-16
Now I tried to modify the script that way

```
#!/bin/bash
#
# restart Firefox
# position /etc/pm/sleep.d/99_restartFirefox

case "$1" in
    hibernate|suspend)
        ;;
    thaw|resume)
       /home/deckoff/apps/firefox.sh
        ;;
    *)
        ;;
esac
exit $?
```This is the content of firefox.sh

```
#/bin/sh
killall xbmc.bin
sleep 5
/usr/bin/xbmc
```IT is strange, that when I click the script, it works as expected - firefox is killed and run again. When the pc is restarted, firefox is killed, as expected, but it will never run??!! Is it a bug. Do I miss something? I would ask te thread to be moved to general help, hope to find answer there, I could not post in this sub-forum for unknown reason...

EDIT: 
It is even stranger - when I suspend from the main menu only the killall command will execute, and when I suspend with pm-suspend from terminal, only the start app command will execute??!! 
Anyone...

---

