---
title: "logging all terminal sessions and desktop layout"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by andyzammy on 2009-08-01
Hi all,

I would like to record all of my terminal sessions without having to initiate the recording - ie i would like everything to be automatically recorded when i open up the terminal (in fact i will probably using a screenlet terminal, and i'm not sure how multiple sessions work just in case this scenario would be a little different to configure than just using a normal terminal).

the closest thing i could find by myself was this:

[http://linux.byexamples.com/archives/279/record-the-terminal-session-and-replay-later/](http://linux.byexamples.com/archives/279/record-the-terminal-session-and-replay-later/)

but i don't know how to auto launch this script on bootup and stop it before shutdown.

also, i don't like this different layout to the normal ubuntu distribution. i've managed to add a bar at the bottom of the screen and moved my windows there, and moved the recycle bin. I still need to find out how to put the "minimise all windows" and virtual desktop buttons. mainly the windows "start" like button annoys me most. is there any way to change the layout?

---

### Post by Buce on 2009-08-01
If you want to run a script every time you open a terminal, just add the command you would invoke from the terminal to the end of your .bashrc.

```
echo '/path/to/script.sh' >> .bashrc
```

If that locks your terminal whenever you open it, try

```
echo '/path/to/script.sh &' >> .bashrc
```

Clarification: After glancing at the link you gave, I'm guessing what you need to type from the command prompt is

```
echo '/path/to/script.sh -r' >> .bashrc
```

F'rex, if you placed the script in ~/Desktop, you would type

```
echo '~/Desktop/script.sh -r' >> .bashrc
```

---

### Post by andyzammy on 2009-08-02
thanks for your reply.

i don't understand how .bashrc works - is this script launched every time the terminal is opened or (/and?) every time input is detected in the terminal?

i ask because when i put the line:
```
script -t 2> tutorial.timing -a tutorial.session
```
at the end of .bashrc the terminal would be in an infinate loop spitting out a "recording started" message. it sort of works (it does record them all to file) but obv the terminal is no use like that.

---

### Post by andyzammy on 2009-08-07
i've sort of given up on recording the terminal - i wanted to try keep track of all the programs i use/install but i came to the conclusion that if i can't do that myself then i probably didn't need the programs too much anyway - and i would probably learn more if i didn't copy+paste from a log.

(i was going to use aptoncd but its not 100% full-proof).

I'm not exactly warming up to Studio atm - it has fully frozen up on my 3 times - i tried the Ctrl+Alt SysReq R E I S U B but that didn't work, and i still can't get used to this single menu at the top left - i very much preferred the 3 menu's. is there a way to change this?

---

