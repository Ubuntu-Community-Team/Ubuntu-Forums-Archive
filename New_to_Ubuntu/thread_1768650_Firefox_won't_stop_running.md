---
title: "Firefox won't stop running"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by fractalman on 2011-05-27
Ok, everytime i close firefox, it carries on running in the background, then when i try and start another firefox session i get a pop up sayng 'firefox is still running please close firefox or restart the system'  (or words to that effect)   when i look in the system monitor it shows 'firefox bin' as sleeping and i have to manually end the process to be able to start firefox again.

Anybody have any ideas what's causing this and how i can get firefox to stop running when it's meant to

I'm on 11:04 but i had this problem on 10:10 as well,  any help would be much appreciated 
thanks


Edit:  i should just add it doesn't do this everytime i close firefox but a good percentage of the time

---

### Post by frankbooth on 2011-05-27
I also had this problem with Firefox, but I switched to Chromium a year ago... 
Anyway, when this happends, open a terminal and write:
```

kill -9 firefox-bin

```
I think the process is called firefox-bin? please correct me if I'm wrong, haven't used FF in a long time.

---

### Post by el_koraco on 2011-05-27
> **frankbooth said:**
> I also had this problem with Firefox, but I switched to Chromium a year ago... 
Anyway, when this happends, open a terminal and write:
```

kill -9 firefox-bin

```
I think the process is called firefox-bin? please correct me if I'm wrong, haven't used FF in a long time.

That's not gonna do anything. You need a PID for the kill -9 command. 
You can do a killall firefox, or killall firefox-bin, though.

---

### Post by mastablasta on 2011-05-27
same happens to me occasionally in windows. i guess occasioanlly something crahses in FF and can't close propperly. instead it still runs in background. i know this because when i start new one the old users starts up. i use multiple users on it.

---

### Post by fractalman on 2011-05-27
Quote:
 	 	 		 			 				 					Originally Posted by **frankbooth** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10868393#post10868393") 				
 				[I]I also had this problem with Firefox, but I switched to Chromium a year ago... 
Anyway, when this happends, open a terminal and write:
 	Code:
 	kill -9 firefox-bin 
I think the process is called firefox-bin? please correct me if I'm wrong, haven't used FF in a long time.[/I]

shall add that to my list of commands

> **el_koraco said:**
> That's not gonna do anything. You need a PID for the kill -9 command. 
You can do a killall firefox, or killall firefox-bin, though.

so how should the command read with the pid? it's showing as 3049

kill -9 3049 firefox-bin?
kill -9 3049?

thanks for the replies guys, much appreciated:D

---

### Post by jre6 on 2011-05-27
Firstly, do this:
```

ps ajxf | grep firefox

```
Look for the PID of the firefox process (its the second number from left). Let us assume PID of '/usr/bin/firefox' = 3049
Then, do this:
```

kill -SIGTERM 3049

```
If it fails (you might do this directly):
```
kill 3049
```

---

### Post by fractalman on 2011-05-27
Cheers, i shall give those codes a try next time it glitches, funny thing is though since i started this thread it hasn't caused a problem. weird!

---

### Post by el_koraco on 2011-05-27
> **fractalman said:**
> 
so how should the command read with the pid? it's showing as 3049


With the PID, it's kill -9 3049, or whatever. there are numeorus ways to find the PID, either through the System Monitor, with the command you got above, or an even simpler one - pgrep firefox-bin
You can also open a terminal and type 

```
xkill
```

After that, you'll see that your mouse has turned into an x. so you go to the firefox window and click, this will also kill it. Just be careful, the first click kills whatever process is running under it, so if you click on the panel, it will kill the panel, if you click on the desktop, it will kill nautilus, etc.

---

### Post by fractalman on 2011-05-27
Cheers, i'll try the pid one,  

 once i shut firefox i cant re-open it, and it's only once i shut firefox that i discover it's actually still running, it would be a bit tedious to open a terminal at the end of every ff session so i could type xkill to end the process:)

---

