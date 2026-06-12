---
title: "Why is my CPU at 100%"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by JohnJD on 2010-03-11
Everytime I try to view the hidden files in my user file, my cpu usage goes up to 100% and doesn't work.  Do I just need to get a new cpu? Or is something else happening?
 
My current cpu -->[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116264](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116264)

---

### Post by woodmaster on 2010-03-11
that processor should be waaaay good enough.  mine is a P4 2.66gHz and it spikes, but not that high.  Can you monitor your resource uses while you do that.  Use a sysmonitor widget/screenlet or just run top in terminal.  That should tell you which program is hogging resources

---

### Post by nitstorm on 2010-03-11
try typing *top* in the terminal as JohnJD says and see which program is hoggin all the cpu
and then u can use *killall programname *in the terminal (ofcourse programname is replaced by the program's name), maybe that could help...

edit:
or if u want to just view the hidden content in the folder or something
```
ls -a <path to te specific folder>
```

Ex:
If I want to view the contents of my Downloads folder which is a sub-directory in my home folder:
```
ls -a ~/Downloads 
```

this is just in case you didn't know that, if you did, sorry for the waste of time.

---

### Post by Choragos on 2010-03-11
If you use the System-->Administration-->System Monitor make sure you're viewing all the processes, not just user processes.

---

### Post by inobe on 2010-03-11
> **JohnJD said:**
> Everytime I try to view the hidden files in my user file, my cpu usage goes up to 100% and doesn't work.  Do I just need to get a new cpu? Or is something else happening?
 
My current cpu -->[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116264](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116264)

if you installed that chip i hope you used thermal paste and properly seated the heat sink :o

it seriously sounds like it's overheating.

---

### Post by JohnJD on 2010-03-11
The thermal paste came pre-applied and the heatsink and fan are installed properly for all I know.

---

### Post by inobe on 2010-03-11
> **JohnJD said:**
> **The thermal paste came pre-applied** and the heatsink and fan are installed properly for all I know.

never have i heard of this !


i build computers for a living and never seen this, i know about thermal pads you can stick on but you still have to apply it yourself.

you may want to verify this by having someone look at it.

---

### Post by mcduck on 2010-03-11
> **inobe said:**
> never have i heard of this !


i build computers for a living and never seen this, i know about thermal pads you can stick on but you still have to apply it yourself.

you may want to verify this by having someone look at it.

Having built quite a few machines myself I've actually seen many mid-range coolers that have thermal paste pre-applied.

Besides, it's irrelevant. Thermal paste or no, that's not going to cause high CPU when trying to view some files... :D That's clearly a software problem.

I'd bet there's some nasty file in the directory the OP is trying to view that causes troubles to the thumbnailer application... Some corrupted file or half-finished download or something would be a pretty hard thing to create a thumbnail for, and that would easily cause the thumbnailer app to freeze and use 100% of your CPU time. (actually this is quite a common situation)

So, check the files in that directory and try moving possible problem files to different place to see if that helps.

---

### Post by JohnJD on 2010-03-11
The heatsink had three stripes of grey stuff on the bottom and the instructions didn't mention that it needed thermal paste.  Also, the motherboard manual mentioned that some CPUs come with their own paste pre-applied, so that's what I assumed those three stripes were.
 
Any-who, I did try to download some updates from the synaptic manager and it said something didn't download properly, so I'm guessing that it has something to do with that.  After the download, Firefox would start and then disappear.  When I would try to download something from the software center I kept getting these "operation package failed" or something with a line in the details that said "last 'ure' newline missing' or something like that.
 
When I ran Ubuntu from the CD, all of these problems disappeared.
 
Should I reinstall Ubuntu and start over?  (I just finished building this computer--my first, which I'm sure I screwed up something--so I literally have nothing I need to save.)

---

### Post by swoll1980 on 2010-03-11
> **Choragos said:**
> If you use the System-->Administration-->System Monitor make sure you're viewing all the processes, not just user processes.

Use top command in the terminal if you want accuracy. The problem with system monitor is the fact that it's a resource hog it's self.

---

### Post by cascade9 on 2010-03-11
> **inobe said:**
> never have i heard of this !

i build computers for a living and never seen this, i know about thermal pads you can stick on but you still have to apply it yourself.

you may want to verify this by having someone look at it.

Like mcduck, I've seen this a lot. I also agree with.....err....the duck (I was going to say 'him' but I have no idea if the duck is a hen or a drake LOL) about it being a software problem. 

I'd try a command line command just to see how many hidden files there are-

 ls -a           

Its possible that you've got a whole heap of them. 

You could also try installing/using a different file manager (eg try thunar if your on KDE and using the stock dolphin). Another thing to try would be removing firefox (either from apt-get or synaptic) as I think that the duck is rigth about some corrupted file, and with your information about firefox it seems it could be the problem. 

Of coruse, reinstalling is always an option- but you might learn a bit more, and gain some confidence with linux if you manage to fix it without going to reinstall.

---

### Post by mcduck on 2010-03-11
I wouldn't go as far as reinstall, since the problem is most likely something really small and easy to fix.

Using a different file manager to move one file at a time away from the directory and then checking when Nautilus starts working correctly again would be the best option. Most likely you don't have that many files directly inside the directory that's causing you the problems, and if it only happens when you try to view hidden files you'll also know that it must be one of the hidden files in that directory, not any of the normal ones.

You can also do the same without having to install another file manager if you just disable thumbnails in Nautilus (Edit/Preferences, on the Preview-tab), but it's probably a bit more work to enable/disable thumbnails after moving each file...

..and if you want to make sure it really is a question of some offending file and not a problem with the system itself , or your hardware, you could simply create a new user and log into that user to see if Nautilus works fine. :)

In worst case, if you are not able to find the offending file, there's always the option of simply removing all the hidden files from the directory that's causing you problems. New files will be created automatically for you after you log out and back again (and when you start applications that use those files to store their settings) but this would really be the last option to try since it would mean resetting many of your programs back to their default settings.

---

### Post by mcduck on 2010-03-11
> **JohnJD said:**
> The heatsink had three stripes of grey stuff on the bottom and the instructions didn't mention that it needed thermal paste.  Also, the motherboard manual mentioned that some CPUs come with their own paste pre-applied, so that's what I assumed those three stripes were.
 
Any-who, I did try to download some updates from the synaptic manager and it said something didn't download properly, so I'm guessing that it has something to do with that.  After the download, Firefox would start and then disappear.  When I would try to download something from the software center I kept getting these "operation package failed" or something with a line in the details that said "last 'ure' newline missing' or something like that.
 
When I ran Ubuntu from the CD, all of these problems disappeared.
 
Should I reinstall Ubuntu and start over?  (I just finished building this computer--my first, which I'm sure I screwed up something--so I literally have nothing I need to save.)

That sounds like the cause of your problems, but it's hard to tell how to fix it without the exact error messages.

Since there's clearly something wrong with your package management at the moment, you could start by running "sudo apt-get update" and "sudo apt-get upgrade" in a terminal and post the outputs of those commands here.

---

### Post by no2498 on 2010-03-11
try this up top click 
system, preferences,multimedia systems selector 
click video,set the plugin to,,,,x window system (no xv)

restart the computer
come back tell us how its doing

---

