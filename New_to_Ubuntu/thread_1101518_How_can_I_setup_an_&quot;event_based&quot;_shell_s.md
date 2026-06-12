---
title: "How can I setup an &quot;event based&quot; shell script?"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by hovzio on 2009-03-20
Hi, 

  I'm not sure if the above question is properly phrased. With "event based" I am attempting to say I have a shell script (bash) that I want to have executed when triggered by a certain action. 

  For example, lets say that I have a script that cleans up flash remains in ~/.macromedia. How could I have this script executed every time firefox is closed? I know about cron and shutdown, but thats not what I'm looking for. What I'm interested in is (in general) on how to make a script execute if a certain event takes place. Is this possible? Kinda makes me think of control-alt-delete or something along the lines of that.

Any help is appreciated. Even some "keywords" to google or a general direction as to where to look or start. Thank you :)

---

### Post by issih on 2009-03-20
maybe not the most perfect solution, but you could look at creating little tiny wrapper scripts that launch the program in question, then launchs the cleanup script afterwards, that should be pretty simple.

you might be able to alias things so that firefox still runs from the "firefox" command.

I'm not sure though, I'm mostly splurging thoughts, there may well be a much better way.

---

### Post by hovzio on 2009-03-20
> **issih said:**
> maybe not the most perfect solution, but you could look at creating little tiny wrapper scripts that launch the program in question, then launchs the cleanup script afterwards, that should be pretty simple.

you might be able to alias things so that firefox still runs from the "firefox" command.

I'm not sure though, I'm mostly splurging thoughts, there may well be a much better way.

Cool, thanks for the reply! Very innovative, I think it would work for the firefox example. I will try it.

What I'm looking to learn about is how to trigger an event. Like when this and this or that take place, execute this script. The next step/question would be how can the script be executed as root, but one thing at a time. 

I've thought about a continuous "until" loop that checks to see when "firefox" exits. (Although I'm thinking this might be VERY sloppy even with a sleep command in there) Is it possible for an until loop to recognize when firefox exits. I think this is not easily done, could only easily test if firefox is running or not by filtering the output of ps or something like that. How can I "catch" the kill signal sent to firefox or any program for that matter. How would I go about describing the so called event that I'm trying to "catch" and then make that trigger some other event? 

I hope this makes sense, appreciate the help;)

---

### Post by hovzio on 2009-03-22
Bump :D

I tried the firefox "wrapper" and this worked, but I'm looking to learn how things "work" and how to trigger certain things etc. Anyone else have any ideas!? Thank you.

---

### Post by brian_p on 2009-03-22
> **hovzio said:**
> 

  I'm not sure if the above question is properly phrased. With "event based" I am attempting to say I have a shell script (bash) that I want to have executed when triggered by a certain action.

```
sudo apt-get install sec

```

---

### Post by hovzio on 2009-03-22
> **brian_p said:**
> ```
sudo apt-get install sec

```

Thank you, this seams to be what I was looking for. (And a whole lot more) 

I have read the man page twice and I am having troubles with it. For starters I'm looking to do pretty simple tasks and I am having a hard time distinguishing all the various options in the man page. By no means am I blaming the man page.. :confused:  I guess what I need are some basic examples, I have googled but google is coming up with many a thing for "sec". Found the man pages.. 

Does anyone know where I can find some basic info on sec. A website with some simple examples would be awesome. Thanks ;)

---

### Post by unutbu on 2009-03-22
Here is something I found by googling "simple event correlation":
[http://sixshooter.v6.thrupoint.net/SEC-examples/article.html#GETTINGSTARTED](http://sixshooter.v6.thrupoint.net/SEC-examples/article.html#GETTINGSTARTED)

It looks like SEC performs actions based on input from a file or pipe. I don't see how you can use that to perform actions when an app like Firefox quits, however, since I don't know of any file which you could monitor to show you Firefox has ended...

---

### Post by hovzio on 2009-03-22
> **unutbu said:**
> Here is something I found by googling "simple event correlation":
[http://sixshooter.v6.thrupoint.net/SEC-examples/article.html#GETTINGSTARTED](http://sixshooter.v6.thrupoint.net/SEC-examples/article.html#GETTINGSTARTED)

It looks like SEC performs actions based on input from a file or pipe. I don't see how you can use that to perform actions when an app like Firefox quits, however, since I don't know of any file which you could monitor to show you Firefox has ended...

Thanks for the site, from what I can tell I couldn't or wouldnt know how to make sec catch firefox's exit.(Or any program for that matter) Does anyone have any ideas as to how could this be done? Many thanks

---

### Post by brian_p on 2009-03-22
> **hovzio said:**
> Thanks for the site, from what I can tell I couldn't or wouldnt know how to make sec catch firefox's exit.(Or any program for that matter) Does anyone have any ideas as to how could this be done? Many thanks

Capture firefox's PID from ps when it starts. Monitor with sec. Perform an action when the PID disappears.

---

### Post by hovzio on 2009-03-22
Thanks brian, sounds interesting, how specifically can I make this part happen?

> **brian_p said:**
> Capture firefox's PID from ps when it starts.

How would this be done automatically when I start firefox? How would I trigger this? Thanks

---

