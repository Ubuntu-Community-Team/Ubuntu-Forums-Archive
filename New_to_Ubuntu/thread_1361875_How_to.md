---
title: "How to"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by simpleblue on 2009-12-22
Ver 9.1

Sorry about the 'How to'. Please be gentle, I'm new. :P

I was looking in my "system monitor" program and I noticed that while my CPU usage is extremely low (2-7%), my "Memory" was about 291mb/500mb (60%) and that's with only Firefox and these forums open.

Is there any way I can print out a list of programs so that people users on here can tell me which ones are unnecessary? That would be so helpful.

As well, I would like to somehow donate to Linux or the forum. Wherever my money is most needed. My experience has been great and I believe in supporting something I like, especially if it's FREE!

---

### Post by howefield on 2009-12-22
> **simpleblue said:**
> Sorry about the 'How to'. Please be gentle, I'm new. :P

You're sorry but still do it ? Hmmm.. I'll work that one out later ;)

> I was looking in my "system monitor" program and I noticed that while my CPU usage is extremely low (2-7%), my "Memory" was about 291mb/500mb (60%) and that's with only Firefox and these forums open.

That sounds pretty reasonable memory usage to me. Open a terminal and type 

```
top
```

which will tell you where the memory is being used. Also you might look at System > Preferences > Startup Applications and remove what is not required.

> As well, I would like to somehow donate to Linux or the forum. Wherever my money is most needed.

That sounds admirable. Take some time till you decide where you want most to donate. 

[http://www.ubuntu.com/community/donations](http://www.ubuntu.com/community/donations)

---

### Post by audiomick on 2009-12-22
Hi.
First of all, welcome.

Your memory usage is about the same as what mine is showing, so let's assume it is normal. If you want some more headroom, install (if possible) some more RAM. That is what the memory statistic is showing you.

Why do you want to remove programs? Is your disc space tight?


Participation is a good way to give back. Have a look here:
[http://www.ubuntu.com/community/participate](http://www.ubuntu.com/community/participate)
to see if you can contribute something.

Spending time in the forum sharing your knowledge is a good start, and a good way to learn things for yourself at the same time. There is always someone who knows less than you! :)

---

### Post by simpleblue on 2009-12-22
> **audiomick said:**
> Why do you want to remove programs?

Is your disc space tight?
I wanted to remove any unnecessary programs because my ram is low. Disk space is good.


> Participation is a good way to give back. Have a look here:
[http://www.ubuntu.com/community/participate](http://www.ubuntu.com/community/participate)
to see if you can contribute something.I'll see what I can do to help.



> **howefield said:**
> You're sorry but still do it ? Hmmm.. I'll work that one out later ;)
I had posted it and then realised it and then found out it couldn't be edited. * embarassed *



> That sounds pretty reasonable memory usage to me. Open a terminal and type 

```
top
```which will tell you where the memory is being used. Also you might look at System > Preferences > Startup Applications and remove what is not required.
There are no startup Apps at all.

Typing 'top' in the terminal I saw:

Firefox
Xorg
Metacity ?
Gnome-panel
Gnome-terminal
python
ibus-deamon

But it moves too fast to show memory usage.



> That sounds admirable. Take some time till you decide where you want most to donate. 

[http://www.ubuntu.com/community/donations](http://www.ubuntu.com/community/donations)I'd rather have my hard earned money go into the pockets of people who care, and not super-giant corporations that plan to take over the world.

---

### Post by audiomick on 2009-12-22
Hi.
I feel the same about where my money goes...:)

It is really unlikely that you have no startup applications. Did you look in the right place?
system> administration> startup applications

I have a number of things in there, but, to be honest, not much that I was game to disable. I am not sure enough of what they all do.

According to what you report from top, there is not much running at all. If you watch it a bit, you will get an idea of what is using memory. Where the numbers appear is where it is happening. There is a small lag on mine.
If I open something from "places", a see an entry for nautilus
If I move a window, I see an entry for compiz
typing here produces a firefox entry.
I just saw one for the gnome screensaver, that I don't have activated :confused:

However, I think things are probably pretty normal on your machine. Can you put more RAM in?

---

### Post by bodhi.zazen on 2009-12-22
My first piece of advise, Linux uses RAM very different then Windows, so I would point you to a few tutorials on that :

[http://www.linuxjournal.com/article/2770](http://www.linuxjournal.com/article/2770)

[http://www.cyberciti.biz/faq/linux-check-memory-usage/](http://www.cyberciti.biz/faq/linux-check-memory-usage/)

[http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

IMO the easiest way to lighten up is to use lighter weight apps. For example , gedit rather then open office.

Next , it is IMO far easier to start with a light OS and add only what you need. Crunchbang or LUbuntu are nice starting points. They will probably not have all the apps you want, but you can install almost anything you want.

[http://ubuntuforums.org/showthread.php?t=355717](http://ubuntuforums.org/showthread.php?t=355717)

---

### Post by chuina on 2009-12-22
Hi, simpleblue,

I have just face the same memory statistics 2 days ago.
Then install this software "htop"
And find out the other statics are giving memory+cache result.
So, i prefer you to use "htop"
To install it: 
Open a terminal type and press Enter:
```
sudo apt-get install htop
```when installation done, type and press Enter:
```
htop
```This time you will able to manipulate your memory using more easily.

Thanks.

---

### Post by simpleblue on 2009-12-22
> **audiomick said:**
> It is really unlikely that you have no startup applications. Did you look in the right place?
system> administration> startup applications

However, I think things are probably pretty normal on your machine. Can you put more RAM in?
Yes, there are no startup apps. I deleted them all, and that's when Ubuntu really started speeding up.

About the ram, upgrading is not a possibility right now. Though a good suggestion.


bodhi.zazen,

I read the House/Barn Analogy. Helps to put things more into perspective. Thanks.

> 
I have just face the same memory statistics 2 days ago.
Then install this software "htop"
And find out the other statics are giving memory+cache result.
So, i prefer you to use "htop"
To install it: 
Open a terminal type and press Enter:
     Code:
     sudo apt-get install htop 
when installation done, type and press Enter:
     Code:
     htop 
This time you will able to manipulate your memory using more easily.

Thanks.     I don't know what this does or how it works, but it lowered my memory usage from 290MB to 148MB and 0MB swap. CPU usage is at 2.5 - 8%! I LOVE it!  :P

Thank you all so much!!!!

That being said,.. how do I change this to a 'Solved' Thread. ;)

---

### Post by audiomick on 2009-12-22
> **simpleblue said:**
> 

That being said,.. how do I change this to a 'Solved' Thread. ;)

The thread tools button at the top of the thread

Info about htop:
[http://en.wikipedia.org/wiki/Htop](http://en.wikipedia.org/wiki/Htop)

---

