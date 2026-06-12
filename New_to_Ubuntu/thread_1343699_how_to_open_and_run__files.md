---
title: "how to open and run  files"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by gridd on 2009-12-02
hi I don't think I'm  going to bother trying to find answers  by my self any more I have been up the entire night trawling through countless posts that nearly but not quite give the answer.I never seem to have any luck with it.

I am trying to load a simple ap called grandfatherclock Ive downloaded it with synaptic  I have found it in /var/cache/apt/archives I have tried to open it with G debi ive tried apt-get grandfatherclock sudo apt-get grandfatherclock   sudo apt-get update first basically I want to Know how to open  and run  a tar bz or gz file in Karmic but this one is in  the repo's so why cant i get it to work? 

I know theirs a how to somewhere but i cant find it after  hours of searching.  no wonder people just give up.

---

### Post by 3rdalbum on 2009-12-02
This is not a newbie-friendly program.

It's a command-line program that plays a sound file a number of times depending on what the hour hand of the clock says.

You can see the manual here:

```
man grandfatherclock
```

Basically it requires that you put it into your crontab to run every hour. Because this is the suggested mode of operation, it doesn't have a menu item.

If you want to run it manually:

```
grandfatherclock
```

in the terminal.

Maybe stick with graphical programs at least until you find your feet?

---

### Post by jbrown96 on 2009-12-02
the file in /var/cache/archives is the installation file. You can run the program with Alt+F2 ```
grandfatherclock
```

---

### Post by gridd on 2009-12-02
> **3rdalbum said:**
> This is not a newbie-friendly program.

It's a command-line program that plays a sound file a number of times depending on what the hour hand of the clock says.

You can see the manual here:

```
man grandfatherclock
```

Basically it requires that you put it into your crontab to run every hour. Because this is the suggested mode of operation, it doesn't have a menu item.

If you want to run it manually:

```
grandfatherclock
```

in the terminal.

Maybe stick with graphical programs at least until you find your feet?

-desktop:~$ grandfatherclock
sox FAIL formats: no handler for given file type `ossdsp'
Unable to execute >sox -v 1.0 /usr/share/grandfatherclock/Grandfather.au -t ossdsp /dev/dsp: Inappropriate ioctl for device
-desktop:~$  

it doesnt seem to run thanks for your help anyway.ditto j brown.

---

### Post by llamabr on 2009-12-02
When you say "downloaded it with synaptic", what do you mean?

Does sound work on your system, otherwise?  Can you play mp3's for example?

---

### Post by gridd on 2009-12-02
yes I can play mp3 files with movie player whether that would be the right app for this program I'm not sure.I downloaded it with synaptic it is in the repo's but although it looks simple it obviously isn't.

ps what is "crontab"?

---

### Post by jbrown96 on 2009-12-02
Grandfatherclock seems to use a very old sound system. The project hasn't had any activity in 2895 days, according to the website. I can't believe that Ubuntu still includes it. You probably just want to set up a cron job.

Cron is a scheduler in linux. It will automatically run commands at defined times. You could create a job in crontab (the file where cron jobs reside) to run every week, day, hour, or whatever. This seems to be all that grandfatherclock does is create entries in crontab. 


I would just manually create the crontab entries. 
mplayer is a good way to play these files. ```
sudo apt-get install mplayer
``` All of the grandfatherclock sounds are located in /usr/share/grandfatherclock/. 

Here's an example crontrab entry to play the Cuckoo sound at the top of every hour.
00 * * * * justin mplayer /usr/share/grandfatherclock/Cuckoo.au
justin is my username; replace it with your own. 

[Here's]("http://www.unixgeeks.org/security/newbie/unix/cron-1.html") a good introduction to cron. There are some good examples about half-way down the page.

---

### Post by gridd on 2009-12-02
> **jbrown96 said:**
> Grandfatherclock seems to use a very old sound system. The project hasn't had any activity in 2895 days, according to the website. I can't believe that Ubuntu still includes it. You probably just want to set up a cron job.

Cron is a scheduler in linux. It will automatically run commands at defined times. You could create a job in crontab (the file where cron jobs reside) to run every week, day, hour, or whatever. This seems to be all that grandfatherclock does is create entries in crontab. 


I would just manually create the crontab entries. 
mplayer is a good way to play these files. ```
sudo apt-get install mplayer
``` All of the grandfatherclock sounds are located in /usr/share/grandfatherclock/. 

Here's an example crontrab entry to play the Cuckoo sound at the top of every hour.
00 * * * * justin mplayer /usr/share/grandfatherclock/Cuckoo.au
justin is my username; replace it with your own. 

[Here's]("http://www.unixgeeks.org/security/newbie/unix/cron-1.html") a good introduction to cron. There are some good examples about half-way down the page.
 
many thanks obviously a lot to study ill try and digest some of this over the coming days thanks again.

---

