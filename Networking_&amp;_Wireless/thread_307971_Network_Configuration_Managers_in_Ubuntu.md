---
title: "Network Configuration Managers in Ubuntu?"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by ahbazan on 2006-11-27
I've been using 6.10 for a while now on my laptop and I am struggling with one specific issue.  When I travel I never really know what networks are available in any given area.  In Windows I could pull up an app that would show me all the available networks, let me select one, put in the security code, and save that information.

Is there a similar app in Ubuntu?  I've tried searching for "network manager" and similar terms in the forums but have come up dry.  Any ideas?  What do you all use to save your configurations?

---

### Post by cilynx on 2006-11-27
System->Admin->Networking

Select your wireless card

Click Properties

Look in the ESSID drop-down

---

### Post by ahbazan on 2006-11-27
I've tried that one, but I found that when I got to school today, my wireless was still setup for my home network.  When I clicked the pull-down menu the ESSID for the school network didn't show up.

In this case it wasn't a big deal since I know the ID and could type it in, but when I fly to meetings and stop at the airport or a hotel and want to check my email I don't usually know the ESSIDs of those networks.

I just want to know what other options are out there.  Are there any?

---

### Post by CrazyDesi on 2006-11-27
I have the same problem

---

### Post by cilynx on 2006-11-27
Which distribution of Ubuntu are you running?  I know that essid hunting is broken in Edgy and Feisty right now.  So far as I know it's supposed to be working in Dapper.

---

### Post by ahbazan on 2006-11-27
Ah, that would explain it then, I'm using Edgy.

So if I was running Dapper, would it also remember the settings I might give to a network ESSID?  Like a WEP Key or similar?

---

### Post by cilynx on 2006-11-27
Even in Edgy profiling works.  You just have to "save a location" after you set it all up.  The only thing that doesn't work is the listing of available ESSIDs.

---

### Post by ssalman on 2006-11-27
I used NetworkManager for that.
I've tried wifiradar
and just as I was reading your post, i found [this ]("http://www.ubuntuforums.org/showthread.php?t=299462")post... see what fits you best and report back!

---

### Post by matsiacc on 2006-11-27
i have the same problem. does not anyone know?

---

### Post by Patrick-Ruff on 2006-12-15
it's because the network settings shortcut is missing a gksudo, it's not using sudo, therefore, it cannot work.

---

