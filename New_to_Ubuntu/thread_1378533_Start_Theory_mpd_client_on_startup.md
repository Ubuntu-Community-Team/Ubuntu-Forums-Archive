---
title: "Start Theory mpd client on startup?"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by checksquid on 2010-01-11
Hi all,
I am running Ubuntu 9.10 (Karmic). I've installed mpd for music playback, and I'd like to use Theory, an mpd client that puts up a web page for controlling mpd at [http://localhost:9099](http://localhost:9099). Theory is a self-contained python program--it doesn't rely on other web server stuff.

Everything is fine if I start Theory from a terminal using the command 
```
/home/data/.theory/run-theory.sh start
```
In firefox, [http://localhost:9099](http://localhost:9099) displays the controls for mpd as expected and everything works wonderfully. However I'd rather have it start automatically when the computer turns on.

I tried adding the command 
```
/bin/sh /home/data/.theory/run-theory.sh start
```
to System->Preferences->Startup Programs, but it doesn't work. That is, when I point firefox to [http://localhost:9099](http://localhost:9099), it can't load anything.

A couple of questions: 
-I am also starting mpd the same way. Could it be that Theory is trying to start before mpd, and that's why it fails?

-When I start programs with "Startup Programs", what user runs them? The user that made the setting, or root? Will they run no matter what user logs on when the computer starts up? (That's what I'd like to achieve.)

-Is there a way to see any errors that are produced when "Startup Programs" tries to start Theory?

Thanks very much for any help!

By the way, these threads may be similar problems, but don't seem to have solutions yet:
[http://ubuntuforums.org/showthread.php?t=1376938&highlight=startup+script](http://ubuntuforums.org/showthread.php?t=1376938&highlight=startup+script)
[http://ubuntuforums.org/showthread.php?t=1376602&highlight=startup+script](http://ubuntuforums.org/showthread.php?t=1376602&highlight=startup+script)

---

### Post by kaivalagi on 2010-01-11
> **checksquid said:**
> Hi all,
I am running Ubuntu 9.10 (Karmic). I've installed mpd for music playback, and I'd like to use Theory, an mpd client that puts up a web page for controlling mpd at [http://localhost:9099](http://localhost:9099). Theory is a self-contained python program--it doesn't rely on other web server stuff.

Everything is fine if I start Theory from a terminal using the command 
```
/home/data/.theory/run-theory.sh start
```
In firefox, [http://localhost:9099](http://localhost:9099) displays the controls for mpd as expected and everything works wonderfully. However I'd rather have it start automatically when the computer turns on.

I tried adding the command 
```
/bin/sh /home/data/.theory/run-theory.sh start
```
to System->Preferences->Startup Programs, but it doesn't work. That is, when I point firefox to [http://localhost:9099](http://localhost:9099), it can't load anything.

A couple of questions: 
-I am also starting mpd the same way. Could it be that Theory is trying to start before mpd, and that's why it fails?

-When I start programs with "Startup Programs", what user runs them? The user that made the setting, or root? Will they run no matter what user logs on when the computer starts up? (That's what I'd like to achieve.)

-Is there a way to see any errors that are produced when "Startup Programs" tries to start Theory?

Thanks very much for any help!

By the way, these threads may be similar problems, but don't seem to have solutions yet:
[http://ubuntuforums.org/showthread.php?t=1376938&highlight=startup+script](http://ubuntuforums.org/showthread.php?t=1376938&highlight=startup+script)
[http://ubuntuforums.org/showthread.php?t=1376602&highlight=startup+script](http://ubuntuforums.org/showthread.php?t=1376602&highlight=startup+script)

You should really run mpd as a daemon, but I am not sure how it is done in ubuntu anymore, I am running Arch. Anyone care to explain?

You are best off, in your current position, creating a script which does everything you need, i.e. start mpd _and then_ start Theory. 

If you then call the script from startup you know the order of events will be correct

Hope that helps

Edit: Could you just run this (&& allows multiple commands in this way):

```
mpd && sh /home/data/.theory/run-theory.sh start
```

---

### Post by checksquid on 2010-01-12
Thanks, Kaivalagi,

I tried using 
```
mpd && sh /home/data/.theory/run-theory.sh start
```
but it didn't fix the problem. Do you think that eliminates the start order as the cause of the trouble?

I believe that mpd "daemonizes" itself when it starts up (though my understanding is slim). If I start it from the terminal, I get control back after it starts and it runs in the background.

---

### Post by VCoolio on 2010-01-12
If there is a problem in order my guess would be that the port can't yet be used. Anyway, try to delay theory to see if it fixes anything; try "sleep 20 && sh /home/data/.theory/run-theory.sh start" as startup command.
Mpd is a system daemon, it's not loaded on login. That's why you can continue playing music and log out at the same time.

---

### Post by checksquid on 2010-01-15
Thanks, VCoolio. I'll give that a try. (Won't be home for a few days, but I'll post the result when I have a chance to try it.)

---

