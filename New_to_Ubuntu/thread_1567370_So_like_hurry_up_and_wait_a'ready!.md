---
title: "So like hurry up and wait a'ready!"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by Langstracht on 2010-09-03
I have what may not be an uncommon problem that I don't know how to fix.

I want to use the start up programmes facility of 10.04 to bring up programmes which want to be connected to the internet (firefox, thunderbird and the like) and it brings them up quite successfully.

Alas it does so, apparently, before the computer has managed to make a wireless WiFi connection.  And so they complain bitterly.

Is there any way of building a delay in to start up?  Or is there some other (perhaps better) way to achieve smooth connections all round.

Thanks, appreciate it ...

---

### Post by uRock on 2010-09-03
You could remove the programs from the Startup Applications menu and make a launcher that opens all of them at the same time, which will allow you to launch them when you know that you are connected.

---

### Post by oldsoundguy on 2010-09-03
or you could put the launch icons in the panel .. that is what I did.

---

### Post by wolke on 2010-09-03
you could add a bash script that does this, and then select it as the app in the menu.

```

sleep 10
firefox &
thunderbird &

```

that should do it most of the time. if you wanna get fancy, it could do something like this (it waits until ifconfig returns wlan's ip address)

```

MAX_TIMEOUT=30
start=`date +%s`
COUNT=0
while [[ $COUNT != 1* ]];
do
  COUNT=`ifconfig wlan0 | grep inet\ addr: --count`
  end=`date +%s`
  let time=$end-$start
  if [ $time -gt $MAX_TIMEOUT ];
  then
    echo timed out!
    exit 1;
  fi;
done;

firefox &
thunderbird &

```

---

### Post by ajgreeny on 2010-09-03
Make a shell script for the applications adding a sleep option for them, and then point your startup application entry to the script.
```
#!/bin/bash
sleep 20; firefox &
sleep 20; thunderbird

```Save the script as startup.sh, make it executable.  That should do it.

EDIT:

Too slow again!

---

### Post by davidmohammed on 2010-09-03
...
or in the start up applications command line, use the following syntax

sh -c "sleep 30 && empathy -h &" 

this delays the startup of empathy by 30 secs.

---

### Post by jtarin on 2010-09-03
Or you could bring up your connection earlier.

---

### Post by Langstracht on 2010-09-04
Wow!  So many choices.  I'll give them a try.

Thanks to all.

---

### Post by oldsoundguy on 2010-09-04
> **Langstracht said:**
> Wow!  So many choices.  I'll give them a try.

Thanks to all.

That is what Linux and FOSS is all about .. choices and custom-ability ON TOP of stability and security!

---

