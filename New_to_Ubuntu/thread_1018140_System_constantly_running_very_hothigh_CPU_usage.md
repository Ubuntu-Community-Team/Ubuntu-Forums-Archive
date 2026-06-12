---
title: "System constantly running very hot/high CPU usage"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by sproaty on 2008-12-21
[[IMG]http://img242.imageshack.us/img242/4413/screenshot1pj7.th.png[/IMG]](http://img242.imageshack.us/my.php?image=screenshot1pj7.png)

that's just from me sitting here in just firefox, reading a few tabs. I'm running a couple of programs currently, sure, but only firefox was the 'active' program and I'm not doing anything CPU-heavy in the background, yet am getting crazy CPU usage fluxuations.

Due to this, after installing lm-sensors and configuring it, it's reporting that my CPU core temperatures are: ...currently 50c, what the hell?

Using XP, even after running my system for 12 hours under full load with Prime95 at full load on both cores, my temperature never reached that high. Average temperatures on windows was around 30c "idle", yet I'm getting constant high temperatures under Ubuntu - around 40 or so, yet I'm a bit worried after seeing 50c..

System:
Athlon X2-3800+ socket 939, overclocked to 2.5GHz [>12 hour Prime95 stable)
2GB DDR RAM overclocked too, stable in memtest
nvidia 8800gt

---

### Post by lovinglinux on 2008-12-21
Does this happens when Firefox is idle just after opening it with a blank page or a specific page? I'm asking this because my CPU usage also spikes like this when viewing poorly developed web pages with dhtml content. Even after the page is loaded and FF is idle, the CPU spikes continuously until I close the tab. I don't think there is much you can do other then avoiding those web sites.

About the temperature, I wouldn't trust lm-sensors. I have it installed here too, but it only worked after a lot of tweaks, otherwise the temperature showed was something like above boiling water. I still have no way to know if the temperature displayed is correct or not, so I just use it to see if the fan control is working when temperature and CPU usage rises.

You should check the temperature in the BIOS setup, to see if it is high like lm-sensors is displaying.

Nevertheless, I don't think that 50c temperature spikes are something to worry about, specially on a overclocked machine. You should check AMD specs tho.

---

### Post by nhasian on 2008-12-21
in a terminal type the command *top* and see if there are any processes using a lot of processing power.  use *top* instead of the system monitor as the system monitor takes a lot of resources itself.

---

### Post by sproaty on 2008-12-21
I've physically noticed about an hour after turning on my PC, I can really feel the heat coming off my box (it's to my right nearby, on the floor). The BIOS temperatures are fine, as they are on XP which is why I figured it was a linux-specific problem. 

According to top, firefox is taking up roughly 7-10% of my CPU, with compiz and xorg using around 5% too. That's what's weird about the temperature readings as there's not much going on in my system to be making my CPU run this hot. Hmm, just looked at sensors again and it's reporting 37/38...very strange

---

### Post by jrusso2 on 2008-12-21
> **sproaty said:**
> [[IMG]http://img242.imageshack.us/img242/4413/screenshot1pj7.th.png[/IMG]](http://img242.imageshack.us/my.php?image=screenshot1pj7.png)

that's just from me sitting here in just firefox, reading a few tabs. I'm running a couple of programs currently, sure, but only firefox was the 'active' program and I'm not doing anything CPU-heavy in the background, yet am getting crazy CPU usage fluxuations.

Due to this, after installing lm-sensors and configuring it, it's reporting that my CPU core temperatures are: ...currently 50c, what the hell?

Using XP, even after running my system for 12 hours under full load with Prime95 at full load on both cores, my temperature never reached that high. Average temperatures on windows was around 30c "idle", yet I'm getting constant high temperatures under Ubuntu - around 40 or so, yet I'm a bit worried after seeing 50c..

System:
Athlon X2-3800+ socket 939, overclocked to 2.5GHz [>12 hour Prime95 stable)
2GB DDR RAM overclocked too, stable in memtest
nvidia 8800gt

Are you using a stock heat sink and fan with an overclocked CPU?

---

### Post by lovinglinux on 2008-12-21
> **sproaty said:**
> I've physically noticed about an hour after turning on my PC, I can really feel the heat coming off my box (it's to my right nearby, on the floor). The BIOS temperatures are fine, as they are on XP which is why I figured it was a linux-specific problem. 

According to top, firefox is taking up roughly 7-10% of my CPU, with compiz and xorg using around 5% too. That's what's weird about the temperature readings as there's not much going on in my system to be making my CPU run this hot. Hmm, just looked at sensors again and it's reporting 37/38...very strange

I'm pretty sure this is web site related or an application going crazy sporadically. When this happens again, run top while the CPU usage is spiking to see which application is the culprit. Sometimes there is an application called scrollkeeper (or something like that) that runs like crazy and only stops if killing it with the "killall" command. Sometimes when the machine is checking for updates the CPU usage also spikes. You should only be concerned if this happens all the time, otherwise, just runs top and kill the culprit if necessary.

---

### Post by tuxxy on 2008-12-21
I agree its likely to be app or web related, I had a similar issue running Opera a while back it constantly used around 20% of my CPU compared to Firefox 2% my CPU was also running 10 degrees hotter while using Opera :confused:

My advice you could try another browser worked for me

---

### Post by sproaty on 2008-12-21
Thanks all, I'll monitor my system using top over the next few hours to see how it plays. 

jrusso2, I'm using a thermaltake fan on my CPU along with a big beefy heatsink :)

---

### Post by euchrid33 on 2008-12-23
Are you running BOINC by any chance?  I was having a problem with my CPU spiking wildly up and down, I tracked down BOINC as the culprit and removed it.  No troubles since.  I didn't even realise that it was running in the background until I spotted it with the *top* command.

---

### Post by sproaty on 2008-12-23
Nup, never heard of BOINC. I've had my PC on for about 15mins now and ls-sensors is reporting 31/32 which seems right, except in an hour or so it will have increased permanently by a good 7c or so. I'm not sure if the thread is actually solved, seems like some long-term problem

---

### Post by alexyz on 2008-12-23
For debugging, try running the system monitor applet in a panel and keep an eye on cpu, you might notice that it jumps up at some point.  Also just to confirm that after startup, your cpu should go down to near zero.

A long shot, but I've noticed when I visit certain blogs, even after the page is done loading firefox cpu holds steady at 40-50% and sometimes goes to 100%.  What's really weird, cpu holds steady even if I go to another page, or close the tab.  I have to close the ff instance to get back to normal.  Here's one of the problem blogs:

[http://calculatedrisk.blogspot.com/](http://calculatedrisk.blogspot.com/)

Same thing with no plugins.  Driving me crazy because based on endless web searches I think I'm the only person in the universe who has this problem.

---

### Post by lovinglinux on 2008-12-23
> **alexyz said:**
> A long shot, but I've noticed when I visit certain blogs, even after the page is done loading firefox cpu holds steady at 40-50% and sometimes goes to 100%.  What's really weird, cpu holds steady even if I go to another page, or close the tab.  I have to close the ff instance to get back to normal.  Here's one of the problem blogs:

[http://calculatedrisk.blogspot.com/](http://calculatedrisk.blogspot.com/)

Same thing with no plugins.  Driving me crazy because based on endless web searches I think I'm the only person in the universe who has this problem.

That page does not increase CPU usage here, even with Noscript and AdBlock plus disabled.

---

### Post by alexyz on 2008-12-23
> **lovinglinux said:**
> That page does not increase CPU usage here, even with Noscript and AdBlock plus disabled.

arghh I'm never going to figure this out.  Thanks for checking. :-/

anyhow keep an eye on the cpu monitor and at least you can figure out if your cpu usage is changing or relatively constant.

---

### Post by lovinglinux on 2008-12-24
> **alexyz said:**
> anyhow keep an eye on the cpu monitor and at least you can figure out if your cpu usage is changing or relatively constant.

I always keep. The problem is I'm now officially paranoid about my cpu usage and temperature :)

My CPU temperature fluctuates between 33 C and 58 C when using Firefox.

---

