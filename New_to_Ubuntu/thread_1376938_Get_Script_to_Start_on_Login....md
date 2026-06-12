---
title: "Get Script to Start on Login..."
date: 2010-01-09
forum: New to Ubuntu
---

### Post by kamitsukai on 2010-01-09
I'm Trying to get the Bing wallpaper script to start on login (from the omgubuntu blog --> [http://www.omgubuntu.co.uk/2009/12/set-bingcoms-background-of-day-as-your.html](http://www.omgubuntu.co.uk/2009/12/set-bingcoms-background-of-day-as-your.html)) unfortunately the command

```
/home/carl/Scripts/bing_wallpaper.sh

``` 

will work from the command line but not in the startup applications gui....

I'm obviously missing something...

---

### Post by llawwehttam on 2010-01-09
Yeah you need to put sh before it

```
sh /home/carl/Scripts/bing_wallpaper.sh
```
should work.

---

### Post by kamitsukai on 2010-01-09
> **llawwehttam said:**
> Yeah you need to put sh before it

```
sh /home/carl/Scripts/bing_wallpaper.sh
```should work.

Nope didn't work...

---

### Post by daimaru on 2010-01-09
make the script executable?
```
chmod +x bing_wallpaper.sh
```add it to pref->startup apps

---

### Post by kamitsukai on 2010-01-09
> **daimaru said:**
> make the script executable?
```
chmod +x bing_wallpaper.sh
```add it to pref->startup apps

yep done all that =]

---

