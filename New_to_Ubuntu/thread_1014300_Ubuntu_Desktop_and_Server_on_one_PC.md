---
title: "Ubuntu Desktop and Server on one PC ?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Derrick Fellowes on 2008-12-17
Hi I am a TOTAL ubuntu novice. Today I installed ubuntu desktop on an ancient two disk XP desktop with dual booting.  That went so well I hope to ditch XP and install ubuntu server on C: drive and reinstall ubuntu desktop on E: drive.  Reason for the server install is to use this as a web server (ambitious for a unix novice). Can anyone advise if this is possible and any likely pitfalls?  I have to say so far I find ubuntu amazing and FREE - wow that doesn't happen in Windows world.  Thanks, Del.

---

### Post by donkyhotay on 2008-12-17
Unlike windows the only real difference between the desktop and server versions is the default applications installed. Desktop versions have GUI's and web browsers in them, server versions is CLI only and full of web hosting, DNS, DHCP, etc goodness. Generally if your going to run a webserver you want to do it on a computer that isn't going to be turned off very often (preferably never) and dedicated to the task. If you only have one computer, you can simply install a regular desktop then install the apache webserver software and have it run in the background.

---

### Post by SunnyRabbiera on 2008-12-17
> **donkyhotay said:**
> Unlike windows the only real difference between the desktop and server versions is the default applications installed. Desktop versions have GUI's and web browsers in them, server versions is CLI only and full of web hosting, DNS, DHCP, etc goodness. Generally if your going to run a webserver you want to do it on a computer that isn't going to be turned off very often (preferably never) and dedicated to the task. If you only have one computer, you can simply install a regular desktop then install the apache webserver software and have it run in the background.

Indeed, its not a sudden jump to turn a desktop into a server in linux...
Though many would advise against it as there are risks involved.
Mainly the GUI will slow it down, and a typical desktop PC might not be able to act as a server that well.

---

### Post by indytim on 2008-12-17
If your intent is to run a captive web server (local only) as in for development, this can certainly be accomplished within either Gnome (Ubuntu) or KDE (Kubuntu).  The easiest way to install the LAMP server is
```

$sudo tasksel

```

I've currently have a LAMP server installed in Ubuntu 8.04 (along with a number of other distro's & versions) that I use for development.  Works great and I still retain the convenience of a GUI ops.

IndyTim

---

### Post by donkyhotay on 2008-12-17
> **SunnyRabbiera said:**
> Indeed, its not a sudden jump to turn a desktop into a server in linux...
Though many would advise against it as there are risks involved.
Mainly the GUI will slow it down, and a typical desktop PC might not be able to act as a server that well.

I didn't say I would recommend running apache on a system with a GUI, just that it can be done if there is no choice. I've done it on my desktop at LAN parties for making it easier to distribute files but my 'real' webserver that I use for hosting things online runs ubuntu server without a GUI and I just SSH into it. Regardless though it's a good idea to have at least a decent grounding in the CLI before trying to run your own linux webhost. If you have absolutely *no* linux experience whatsoever I would recommend using desktop linux for awhile (at least a few months) before even attempting to work seriously with apache. You need to learn to crawl before you walk and walk before you run. I would consider running/configuring apache on a headless linux webserver to be running, you might want to also see if there is a geek in your area you can hire to help you if you need this right away.

---

### Post by Kellemora on 2008-12-17
Hi DF

Don't know if this will help you or not?

I knew absolutely nothing about Servers, other than I had a print server to run 12 printers dividing up the load.  But I didn't program it, just kept it working is all.

Since I didn't know how to set up a server and wanted to learn, I installed a program called EDUBUNTU which is a Server already set up to run thin clients from.  

I used an old machine for that, plus a couple of really ancient Doze 98 machines as the workstations, just to learn what some of the settings did and why.

Thin Clients is NOT the way I wanted to go, but I learned a little more than I knew before.  I've dismantled that so to speak to build a super file server. 
But while it was set up, I made a little mini in-house web server of sorts as a test.  I just simply loaded the files I had on my real web site onto it as a test.  I couldn't tell the difference as to whether I was on-line or connected to my own server as far as what I saw and how it acted.  Except of course, I only had that one web site to visit, hi hi..........

You can pick up some decent used computers for under 100 bucks to use as your experimental computer and not mess up the one you NEED to use everyday.

TTUL
Gary

---

