---
title: "[SOLVED] timed shutdown scripting help"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-01-07
first, i have been using linux for about a year and a half now dumped vista and only use ubuntu. and i never ask a question on this board unless i try to find the answers myself  or check other linux boards. however if i get completely confused i come here because i have always received some great replies. here is what i would like to to and cron still completely confuses me. i want to make a shutdown timer that will shutdown the computer at 9:30pm every day. there are two users on my machine me and my daughter. i have the appl gshutdown installed but if my daughter forgets to go back to my user screen the timer wont work unless i have activated it for both users. okay if you have the time pls provide a how to do for this 60 year old linux user. maybe use the kiss principle {make it simple,stupid}. i am not a newbie i moderate a linux board on another form but i am confused on how to do this/tks cheesemaker

---

### Post by handydan918 on 2009-01-07
Have you installed gnome-schedule? it's a gui frontend for cron. Might help get past the syntax issues...

---

### Post by rburkartjo on 2009-01-07
handy will give it a try/cheesemaker

---

### Post by rburkartjo on 2009-01-07
handy,
okay installed cant find the program in appl menu and how do i use. been a long day. no stupid question if you dont know the answer/cheesemaker

---

### Post by handydan918 on 2009-01-07
I can't say definitively, as I'm in front of a KDE box right now, but if you open a terminal and type the program name, that will usually suffice.

---

### Post by weboide on 2009-01-07
You can try running gshutdown as root (sudo).

---

### Post by rburkartjo on 2009-01-07
okay handy,
found it see if i did it correctly will post back if successful and mark this thread as solved/cheesemaker

---

### Post by Guille Damke on 2009-01-07
Hi,

I did not know about gshutdown, it looks nice! But I don't know if it is possible to set it up to perform the action everyday.

That's why I'll post what I think you can do in crontab (please, correct it if you found a mistake). I think using cron is not extremely difficult.

This is my guess, it worked for me.

1- In a terminal, edit crontab file (as 'sudo' since you want to shutdown the machine):
```
sudo crontab -e
```

I just tried in Ubuntu, it will ask you which editor you want to use, it suggests Nano as the easiest (just ctrl+o to save and ctrl+x to exit).

2.- Each crontab line has the structure:
```
minute(0 to 59) hour(0 to 23) Day_of_month(1 to 31) Month(1 to 12) Day_of_week(0 to 6) Command_to _execute 
```
So I will add this in a new line to shutdown at 21:30:
```
20 21 * * * shutdown -P +10
```
Which means that at 21:20 (the 20 is not a typo, continue reading) in any day (that's *), any month and any day of week run:
```
sudo shutdown -P +10
```
where -P powers off the computer and +10 gives the chance of informing the users that the system will be shutdown in 10 minutes and not now. (You can run cron at 21:30 and use instead "shutdown -P now").
Also, I installed beep (sudo apt-get install beep), probably it is not needed, but if you have the pc-speaker volume up in volume control, you'll hear a beep when the shutdown command is executed by cron. Also, if you have terminals opened, it will even print a message. (QUESTION: I DON'T know if there is a way of running a command on a terminal as sudo under cron to open a message in the notification area or open a window with a custom message for any user, any ideas?????).

3.- If you want to check the tasks in your (actually 'sudo') crontab file:
```
sudo crontab -l
```

4.- If you want to cancel the shutdown command after it is executed:
```
sudo shutdown -c
```
Good luck, I hope it helps.

---

