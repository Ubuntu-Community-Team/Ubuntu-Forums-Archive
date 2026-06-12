---
title: "Adding veetle to firefox"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by Norman Thom on 2010-11-07
I am trying to add sh veetle-0.9.17-linux-install.sh to firefox so that I might watch some streaming TV.

The instructions I was given was to download veetle, to open a terminal and to 'run' sh veetle-0.9.17-linux-install.sh.

I tried to do this, ran as is, ran using sudo and nothing
I'm sure I am doing something wrong.  could someone give me a step by step to accomplish this.  It may be I do not understand the concept of 'run'

Thanks 

Norm

---

### Post by marl30 on 2010-11-07
Let me give the easy way to install it. Right click on the Veetle file and go to the selection to make it excitable. Then open terminal and drag the veetle file and drop it in terminal. Then press enter. Press enter again until you it says it's installing package. It will tell you when the installation has completed. However, if you are using 64bit, it won't work. Currently veetle only seem to work on 32bit.

---

### Post by marl30 on 2010-11-07
One more thing... in 64bit it has only worked in a browser called Flock for me. It doesn't work in Firefox and other browsers.

---

### Post by marl30 on 2010-11-07
I see you are from Jamaica, like myself. :) If it's football you are trying to watch, I could give you a few other options that I use to watch my live streams.

---

### Post by Norman Thom on 2010-11-07
Marl30

Thanks for the tip.

there is however a gap on my part when you say to make the file 'excitable'.

I'm not sure how to accomplish that as there is no listing that resembles 'excitable' in the menu when I right click on the veetle file.

I'm sure it must be some jargon specific to Linux that I am unaware of.

Thanks 

Norm

---

### Post by Norman Thom on 2010-11-07
Marl30

Unfortunately this Kingston is in Canada and we're about to get some chilly man.

Norm

---

### Post by marl30 on 2010-11-07
> **Norman Thom said:**
> Marl30

Thanks for the tip.

there is however a gap on my part when you say to make the file 'excitable'.

I'm not sure how to accomplish that as there is no listing that resembles 'excitable' in the menu when I right click on the veetle file.

I'm sure it must be some jargon specific to Linux that I am unaware of.

Thanks 

Norm

No prob , Norman. I actually was assuming you knew how to make it executable. Actually, when you right click, go to properties, then permission, then check the box which says execute. Then close the properties menu. You then open terminal, drag the file until it hovers over the terminal. You then drop it into terminal and hit enter, and continue  hitting enter until it you see it says it's installing. It should work then.

---

### Post by marl30 on 2010-11-07
> **Norman Thom said:**
> Marl30

Unfortunately this Kingston is in Canada and we're about to get some chilly man.

Norm
I heard how cold Canada gets. :) I can just imagine.

---

### Post by Norman Thom on 2010-11-07
Marl30

You are well and truly the man.

Once we defined our terms it was just a matter of a few clicks and presto changeo she works.  Now could you tell me how to mark this post as Solved so that everyone can see your magnificence.

Thanks again 

Norm

---

### Post by Norman Thom on 2010-11-07
BTW we will get days of -40 C (F is the same in this case) and I live in the most southerly part of Canada :(

---

### Post by marl30 on 2010-11-07
> **Norman Thom said:**
> Marl30

You are well and truly the man.

Once we defined our terms it was just a matter of a few clicks and presto changeo she works.  Now could you tell me how to mark this post as Solved so that everyone can see your magnificence.

Thanks again 

Norm

I'm glad you got it working. For making the thread show as solved... I don't have a clue about that one. Still a noob where that is concerned. :) 

You didn't say whether you're using 64bit or 32bit, as if you are using 64bit, that would give me hope. I'm yet to get it working in Firefox on 64bit. Flock browser is a headache, as it's one of those softwares that no deb file is available for, so it needs to be compiled in terminal in order to install it.

---

### Post by marl30 on 2010-11-07
> **Norman Thom said:**
> BTW we will get days of -40 C (F is the same in this case) and I live in the most southerly part of Canada :(

Wow, that is really COOOOOLD! I couldn't manage such low temperature. In my country it's warm all year round. The coldest it will get is between December and March, which is not unbearably cold.

---

### Post by Norman Thom on 2010-11-07
sorry I missed your query:

I'm using a 32 bit system so no help

Thanks again for your help and . . .

faesgar math

slainthe

Norm

---

### Post by Kir_B on 2010-12-01
> **Norman Thom said:**
> Marl30

You are well and truly the man.

Once we defined our terms it was just a matter of a few clicks and presto changeo she works.  Now could you tell me how to mark this post as Solved so that everyone can see your magnificence.

Thanks again 

Norm

Hi Norm.

I'm going too give you two methods to mark your thread as "Solved". Method one is my favorite, only because I used method 2 once and it resulted in locking the thread (No one else could add further thoughts to the thread). Just in case I or someone else wants to edit one of their posts, add some further thoughts, or some further clarification, method one works best. I'm not sure if this is still the way it works, but I use method one to avoid this possibility.

Method one:
> 
Go to your first post and click the edit button in the bottom right of the post's box. Once the edit box loads, just simply put {solved} before the actual title and save the changes (the save changes button is located beneath the editor box).Method 2:

> Go to the top of the page, just above the first post on the page. Click on the "Thread Tools" button and select the "Mark this thread as solved" option.I hope that helps.

Good day. Kirby ):P

---

### Post by xfinite on 2011-01-01
> **marl30 said:**
> I'm glad you got it working. For making the thread show as solved... I don't have a clue about that one. Still a noob where that is concerned. :) 

You didn't say whether you're using 64bit or 32bit, as if you are using 64bit, that would give me hope. I'm yet to get it working in Firefox on 64bit. Flock browser is a headache, as it's one of those softwares that no deb file is available for, so it needs to be compiled in terminal in order to install it.


Sorry to revive an old thread but I wanted to say that Veetle works perfect in the Flock browser. And to install the Flock browser you do not need to compile anything in terminal. I'm brand new to linux and I just installed Flock using the instructions below. But hopefully Veetle will get a fix for 64bit user's running Firefox!

[https://help.ubuntu.com/community/InstallingFlock](https://help.ubuntu.com/community/InstallingFlock)


[LIST]
[*]Download [Flock]("http://www.flock.com/") page for Linux. 
[*]Right click the file, choose **Extract Here** 
[*]Right click the desktop, choose **Create Launcher**
[*]For command, click **Browser** and chose the file called 'flock' in the folder you just extracted.  

[LIST]
[*]

[/LIST]
[/LIST]

---

### Post by jainnatural on 2011-10-17
[http://veetle-plugin-on-64bit-linux.tumblr.com/](http://veetle-plugin-on-64bit-linux.tumblr.com/)

It works. Tested it.

---

