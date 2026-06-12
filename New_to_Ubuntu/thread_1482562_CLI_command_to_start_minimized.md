---
title: "CLI command to start minimized?"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by spydeyrch on 2010-05-13
Hey guys, quick question for you all. Pretty simple question.

what would the terminal command be to start both evolution & empathy at the same time BUT have them start minimized to the programs bar? Hopefully that makes sense.

I want to have a custom icon that I can run and it will start both evolution and empathy at the same time but have them both minimized when they startup.

I think that it would be something like:

evolution && empathy -??????

The issue is that I don't know what option/argument I need to add to have them started minimized .... or if I even have the right command to start them at the same time.

Thanks for the clarification!

-Spydey :guitar:

---

### Post by Kafubie on 2010-05-13
Bump for knowledge!

---

### Post by cariboo on 2010-05-13
Please don't unnecessarily bump a thread.

Have a look at [this]("https://help.ubuntu.com/community/AddingProgramToSessionStartup") for what you need.

---

### Post by spydeyrch on 2010-05-13
> **cariboo907 said:**
> Please don't unnecessarily bump a thread.

Have a look at [this]("https://help.ubuntu.com/community/AddingProgramToSessionStartup") for what you need.

Thanks for the link. I will check it out right now. :)

-Spydey :guitar:

---

### Post by mechro on 2010-05-13
The command to launch the two applications simultaneously would be...

```
sh -c "evolution & empathy"
```

To launch them minimised/iconified is more difficult. You'll have to try cariboo907's link which mentions devilspie.

---

### Post by wojox on 2010-05-13
Have a look at Devilspie [https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

It's my favorite.

---

### Post by spydeyrch on 2010-05-13
So I did some research, read that link and it gave me info that I already knew. :(

I know how to create short-cuts, startup apps, etc. I just don't know what the option would be to have the program start minimized.

I don't need to autostart it when I login, just when I click on the icon do I want them to start.

Also, I tried

```
evolution && empathy
```

to see if it would at least just start both of them up at the same time. It kind of did it but not with the results that I was expecting/hoping for. The first app would start but the second one wouldn't start until I closed the first one.

Any pointers, thoughts, ideas? I really don't have to have to use another program, like Devilspie as mentioned in the link previously provided, just to do something that should be very simple to do.

Any pointers?

Thanks guys.

-Spydey :guitar:

---

### Post by spydeyrch on 2010-05-13
really, I need to use devilspie?  Well, ok, I will take a second look at it. Thanks guys. :)

-Spydey :guitar:

---

### Post by wojox on 2010-05-13
```

(if
    (is (application_name) "evolution")
    (begin
       (set_workspace 2)
       (minimize)
    )
)

```


See here ( best tutorial on Devilspie ) [http://foosel.org/linux/devilspie](http://foosel.org/linux/devilspie)

---

### Post by spydeyrch on 2010-05-13
> **mechro said:**
> The command to launch the two applications simultaneously would be...

```
sh -c "evolution & empathy"
```

To launch them minimised/iconified is more difficult. You'll have to try cariboo907's link which mentions devilspie.

so why wouldn't I just use

```

evolution & empathy

```

Just curious. I tried both of them and to me, it appears like they do the same thing. So why would I need the sh -c prior to the two programs? Thanks!

-Spydey

---

### Post by LinuxGEEK7288 on 2010-05-23
Hey found this thread while trying to figure out how to start Evolution minimized, still no no luck but I can answer this question.

> **spydeyrch said:**
> so why wouldn't I just use

```

evolution & empathy

```

Just curious. I tried both of them and to me, it appears like they do the same thing. So why would I need the sh -c prior to the two programs? Thanks!

-Spydey


Fist check out this link: 
[http://tldp.org/LDP/abs/html/special-chars.html](http://tldp.org/LDP/abs/html/special-chars.html) 

It answers most the great questions of bash special characters

But the quick and dirty is this; the "&" simply tells the the program to run in the background so you can continue using the terminal. While "evolution && empathy" say not to run the second command till the first one completes successfully.

What you want to run them both in the background would be "evolution ; empathy &" the ";" is a command separator.

Hope that helps and if anyone knows how to start evolution minimized at startup I would be most thankful

---

### Post by iamajd on 2011-01-21
I know I'm resurrecting an ancient (by Ubuntu forums standards) thread, but Empathy can be started with the --start-hidden option so that it runs in the messaging notifier but doesn't show any windows.

---

### Post by spydeyrch on 2011-01-23
@iamajd

Thanks man for the info!! That helps a ton. :D

-Spydey

---

### Post by ink_rus on 2011-10-24
Maybe:
> empathy -h
but how to minimize evolution? Try to use evolution indicator applet.

---

### Post by decoherence on 2011-10-24
> **LinuxGEEK7288 said:**
> 
What you want to run them both in the background would be "evolution ; empathy &" the ";" is a command separator.


This might work because evolution forks in to a background process (maybe? i don't use evolution) however the correct way that will work with any programs is similar to what spydeyrch mentioned. '&' is also a command separator.

evolution & empathy &

compare:

xeyes ; glxgears &
and
xeyes & glxgears &

the first will start xeyes, then start glxgears once xeyes closes (because xeyes doesn't fork another process, it blocks the command.) the second will behave the way that was suggested, with both starting simultaneously.

---

### Post by sup on 2012-04-08
First, create a file somewhere (for example ~/.devilspie/minimize_evolution.ds with the following:
```
(if  
(is (applicatio_name) "Evolution")  
(begin (minimize) )  
)  
```
(Note I do not have Evolution installed, so it's application name might be different, you can find out with running devilspie with a file containing ```
(debug)
``` and nothing else)

Then you could do something like 

```
devilspie ~/.devilspie/minimize_evolution.ds &  xxx=$!; evolution & empathy --start-hiden & sleep 10;  kill $xxx
```

It basically runs devilspie with a rule to minimize evolution in the background, saves its PID to variable xxx, launches evolution, launches empathy minimized, waits 10 seconds (you can make this longer if it takes evolution a long time to start) and then kills devilspies. If you did not kill devilspie, it Evolution would keep minimizing when you would interact with it later. Hope this works, I have tested this only partially.

---

