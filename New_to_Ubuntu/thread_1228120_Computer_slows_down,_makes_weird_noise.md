---
title: "Computer slows down, makes weird noise"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by jalehtor on 2009-07-31
I've had Ubuntu for nearly a year now, and the last few months, it's been slowing down. 

It'll start up OK, but then when I get going the computer goes through periods where it's obviously louder than at other times, as if it's trying extra hard (no click sounds etc), the whole thing slows down, and it sometimes freezes. 

When I get to a screen with too many gifs the problem's really obvious, and the whole thing gets very, very slow...I'm having to forcequit a number of times a day. 

My specs: HP Compaq D530 2.6GHz 3800GB 40GB

---

### Post by TeoBigusGeekus on 2009-07-31
Have you opened the cased and cleaned any dust there?
Perhaps it's a hardware problem.
Check empty space on your root partition as well.

---

### Post by jalehtor on 2009-07-31
> **TeoBigusGeekus said:**
> Have you opened the cased and cleaned any dust there?
Perhaps it's a hardware problem.
Check empty space on your root partition as well.

How do you clean the dust? Not with a feather duster, surely??? JK

Also, what is the empty space on my root partition? 



Here's what's going on: 

[IMG]http://i142.photobucket.com/albums/r113/jaletoran/Screenshot-SystemMonitor.png[/IMG]

---

### Post by Liolikas on 2009-07-31
oioi CPU 99% not good. Show processes or just:
```

top

```

> 
Also, what is the empty space on my root partition? 

```

df -h

```

---

### Post by jalehtor on 2009-07-31
> **Liolikas said:**
> oioi CPU 99% not good. Show processes or just:
```

top

```

[/code]

Here are the processes

[IMG]http://i142.photobucket.com/albums/r113/jaletoran/Screenshot2.png[/IMG]

---

### Post by Liolikas on 2009-07-31
Now just 11% good. 
Next time you feel you have problem get *top* and try to find what eats 99% CPU power. You have no many options just remove that thing if possible. If not post output here we will see what can be done.

---

### Post by jalehtor on 2009-07-31
> **Liolikas said:**
> Now just 11% good. 
Next time you feel you have problem get *top* and try to find what eats 99% CPU power. You have no many options just remove that thing if possible. If not post output here we will see what can be done.

Thank you so very much for helping. The problem is that I don't understand what 11% good means, or what 99% CPU power getting eaten is. What is the "thing" I need to remove? 

I'm so very sorry for my ignorance. :confused:

---

### Post by Liolikas on 2009-07-31
You see CPU 11%us in top?
That means CPU works now at only 11% of his max power.
If CPU 99%us so CPU uses entire his power and still unable to deal with all tasks that is not good you have to find which program makes him work so hard and get rid of that program.

---

### Post by gastly on 2009-07-31
I had a similar problem a while ago...for me it was Xorg which was eating all the CPU (90%). And you said that the computer slows down when you're seeing a page with lots of gif's? So, this could be a graphics issue. 
Try disabling compiz and any other effects that you may have enabled.

My issue was solved when I eventually got fed up of slow Gnome and migrated to Xubuntu ;)

---

### Post by jalehtor on 2009-07-31
> **gastly said:**
> I had a similar problem a while ago...for me it was Xorg which was eating all the CPU (90%). And you said that the computer slows down when you're seeing a page with lots of gif's? So, this could be a graphics issue. 
Try disabling compiz and any other effects that you may have enabled.

My issue was solved when I eventually got fed up of slow Gnome and migrated to Xubuntu ;)

I have compiz and Wine because my kid NEEDS his games. However, I'm going to be divvying up with xp and Ubuntu soon, so that I can limit Ubuntu to online stuff, and XP to playing games, which means that I won't need Wine, which never did work well for me. 

After I get rid of Wine and limit Ubuntu to online stuff, do you think this mess will improve? I HATE microsoft, but for games, xp's pretty damned useful.

---

### Post by jalehtor on 2009-07-31
> **Liolikas said:**
> You see CPU 11%us in top?
That means CPU works now at only 11% of his max power.
If CPU 99%us so CPU uses entire his power and still unable to deal with all tasks that is not good you have to find which program makes him work so hard and get rid of that program.

How do I find that program? I'm terribly sorry to sound like an idiot, but that's exactly what I am.

---

### Post by gastly on 2009-07-31
> **jalehtor said:**
> I have compiz and Wine because my kid NEEDS his games. However, I'm going to be divvying up with xp and Ubuntu soon, so that I can limit Ubuntu to online stuff, and XP to playing games, which means that I won't need Wine, which never did work well for me. 

After I get rid of Wine and limit Ubuntu to online stuff, do you think this mess will improve? I HATE microsoft, but for games, xp's pretty damned useful.

Actually, you don't need Compiz for games, it's just for effects. If you only need to play games, disable compiz, it slows down things anyway.

And I second your idea to install XP. XP is really useful for playing games. In fact, my bro plays games on XP and surf's the net and does all other things in Vista and I use Ubuntu :-\" 

So, basically, I have a triple boot of XP, Vista and Ubuntu! :biggrin:

---

### Post by Liolikas on 2009-07-31
> 
but that's exactly what I am.

Nop you are not idiot would think ~:
> 
w00t lagz so I need new PC with WIN 7


You will see that program name in COMMAND part of top output with %CPU ~90% in same line.

---

### Post by jalehtor on 2009-07-31
> **gastly said:**
> Actually, you don't need Compiz for games, it's just for effects. If you only need to play games, disable compiz, it slows down things anyway.

And I second your idea to install XP. XP is really useful for playing games. In fact, my bro plays games on XP and surf's the net and does all other things in Vista and I use Ubuntu :-\" 

So, basically, I have a triple boot of XP, Vista and Ubuntu! :biggrin:

I'm just curious...will disabling Wine make it difficult for me to play videos etc on Ubuntu? I'm guessing that it won't, but I just want to make sure.

Btw, if Wine were a more reliable program, life would be so much simpler!

---

### Post by jalehtor on 2009-07-31
> **Liolikas said:**
> Nop you are not idiot would think ~:


You will see that program name in COMMAND part of top output with %CPU ~90% in same line.

Er....you were being generous with the "you're not an idiot," I fear, as I have no idea what you mean by the "COMMAND part of top output with %CPU ~90% in same line."

I'm going to be divvying up the computer with xp soon, and I'd like to know what I've got in Ubuntu that is slowing it down. :confused:

---

### Post by Liolikas on 2009-07-31
You can do everything without wine except if you are addicted to some kind of windows program so you have to use wine then.

---

### Post by jalehtor on 2009-07-31
> **Liolikas said:**
> You can do everything without wine except if you are addicted to some kind of windows program so you have to use wine then.

Thank you! I should be fine, then...I'd rather use a windows program for windows. Actually, the kids will be gone for ten days, and this is probably the perfect time to get rid of Wine.

---

### Post by TUOggy on 2009-07-31
> **jalehtor said:**
> Er....you were being generous with the "you're not an idiot," I fear, as I have no idea what you mean by the "COMMAND part of top output with %CPU ~90% in same line."

I'm going to be divvying up the computer with xp soon, and I'd like to know what I've got in Ubuntu that is slowing it down. :confused:

I must admit, I think there is a slight language barrier here.

When you have 99% CPU usage, it means that there is a program running that is taking up a massive amount of your processing power.  If you have other apps that are attempting to use some of the processing power to run, then you will have bad lag and lockups.  This is when you need to try to figure out what application is using so much of your CPU.  If it is indeed Compiz, then there is an easy solution.  Disable Compiz.  It isn't a necessary application and only serves to give you a little eye candy.

Wine is only useful for running Windows applications.  If you decide that you are going to dual boot Windows and Ubuntu, then there is no need to have Wine installed.  If you do decide that you want to stick with wine, then you may want to check out:
[http://www.winehq.org/](http://www.winehq.org/)

They have an application library available that will have many fixes for Windows applications available.  I got World of Warcraft to run brilliantly on my Ubuntu desktop for a long time until the newest expansion came out.

I hope this helps.

---

### Post by jalehtor on 2009-07-31
> **TUOggy said:**
> I must admit, I think there is a slight language barrier here.

When you have 99% CPU usage, it means that there is a program running that is taking up a massive amount of your processing power.  If you have other apps that are attempting to use some of the processing power to run, then you will have bad lag and lockups.  This is when you need to try to figure out what application is using so much of your CPU.  If it is indeed Compiz, then there is an easy solution.  Disable Compiz.  It isn't a necessary application and only serves to give you a little eye candy.

Wine is only useful for running Windows applications.  If you decide that you are going to dual boot Windows and Ubuntu, then there is no need to have Wine installed.  If you do decide that you want to stick with wine, then you may want to check out:
[http://www.winehq.org/](http://www.winehq.org/)

They have an application library available that will have many fixes for Windows applications available.  I got World of Warcraft to run brilliantly on my Ubuntu desktop for a long time until the newest expansion came out.

I hope this helps.

Tuoggy, how do I figure out which program is using all that power?

---

### Post by Liolikas on 2009-07-31
Just analyze top output. 
I tired to explain in detail, but really my English is not that good.

---

### Post by TUOggy on 2009-07-31
> **jalehtor said:**
> Tuoggy, how do I figure out which program is using all that power?

The easiest way is to go into system monitor (System > Administration > System Monitor) and click the processes tab.  Then search for the process that has the highest CPU rating.  I usually sort the screen by CPU so that the highest number is on the top.  It makes it really easy to check what is eating up all your resources.

---

### Post by jalehtor on 2009-07-31
> **TUOggy said:**
> The easiest way is to go into system monitor (System > Administration > System Monitor) and click the processes tab.  Then search for the process that has the highest CPU rating.  I usually sort the screen by CPU so that the highest number is on the top.  It makes it really easy to check what is eating up all your resources.

What's eating up my resources is apparently the gnome system monitor...varies anywhere from 90% to 4%, depending on the split second. I'm not sure if it'd be a good idea to get rid of it?

---

### Post by TUOggy on 2009-07-31
> **jalehtor said:**
> What's eating up my resources is apparently the gnome system monitor...varies anywhere from 90% to 4%, depending on the split second. I'm not sure if it'd be a good idea to get rid of it?

The system monitor will only use up resources when you have it open (and will be very much higher when you first open it).  You can run top in terminal as well.  Top will show you the exact same thing as the processes list in system monitor.  The only difference is that top is less resource intensive and it's text based rather than in a nice gui.

You should check one of these two when you notice that your computer is beginning to slow down.  That is when your system will be using the most resources.

Unfortunately there isn't much of a way to check it when the problem isn't happening though...

---

### Post by jalehtor on 2009-07-31
Will do! I'll find a page full of gifs, and then figure out what's happening.

---

### Post by gastly on 2009-07-31
> **jalehtor said:**
> What's eating up my resources is apparently the gnome system monitor...varies anywhere from 90% to 4%, depending on the split second. I'm not sure if it'd be a good idea to get rid of it?
Just as a tip...open up 'top' in the terminal or use the gnome system monitor, whichever you prefer. I recommend top tho...

Try to reproduce the thing...open up a heavy page with lots of gif's (like you said earlier :biggrin:) and then as soon as you see things slow down a bit, quickly switch to the terminal where 'top' is open (or the gnome system monitor) and see what program has the highest CPU usage.

Good luck ;)

---

### Post by jacklinux on 2009-07-31
Well when i boot up on 5GB of RAM its slow for the first 5-10 mins, i usally leave it and let it settle

---

