---
title: "Screen saver wont turn off"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by HittingSmoke on 2009-02-23
Since switching to Kubuntu Intrepid and KDE 4.2 I cant get my screen saver to stop coming on. This is a huge problem as I use my PC for all my TV and movie watching and cant be bothered to get up every few minutes to shake my mouse just to get through a movie.

I've turned off the Screen Saver under Desktop setting as well as Power Management under Display settings. Is there something else I'm missing? I even set one of my corners to prevent the screen saver from starting with no results.

---

### Post by WatchingThePain on 2009-02-23
What are you using to play movies?, there's usually an option in the player to disable screen savers.

---

### Post by HittingSmoke on 2009-02-24
> **WatchingThePain said:**
> What are you using to play movies?, there's usually an option in the player to disable screen savers.

I'm using dragon. The problem here isn't the movie player though, it's within KDE. The times the screen turns off are totally erratic.

Earlier I tried to watch Tropic Thunder, I got about 30 mins in before the screen went blank. Just a few minutes ago I was reading a one page article and I had to reactivate my screen twice by moving the mouse within five minutes.

---

### Post by HittingSmoke on 2009-02-24
I seem to have found a work around for it. When the "Enable display power management" box is unchecked under "System Settings > Display > Power Control" the monitor will turn off at completely random intervals when the system is idle. All the individual power settings are greyed out when this is unchecked.

However, if I check the Enable box then turn each individual setting down until it says "Disabled" the screen wont ever turn off by itself.

I've never had to submit a bug report here before, how do I go about submitting this one if it isn't already? Would it go to the KDE site or Kubuntu site?

---

### Post by enchesss on 2010-07-11
There is probably a better way but this worked for me:

using kde 10.04:

go system settings> advanced> power management> check Let Powerdevil manage screen powersaving

In profile assignment choose performance

then edit profiles in left menu

click on performance and set the 'dim display when idle' to 200 mins for movies

also

on teh screen tab - set these settings too

---

