---
title: "Trying to Intstall Chromium"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by Monrizzy on 2010-01-03
When I typed 
> sudo apt-get install chromium-browser
 in the terminal I get 
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package chromium-browser


Any ideas on how to resolve this?

---

### Post by spcwingo on 2010-01-03
Did you add their ppa first?

---

### Post by Sef on 2010-01-03
Do you mean [Google Chrome]("http://www.google.com/chrome"), the browser which is beta? If so, then afaik it is not in the respositories, so click on the link above to download it.

If you do want chromium from the PPA, click [here]("https://launchpad.net/%7Echromium-daily/+archive/ppa").

---

### Post by lol768 on 2010-01-03
This error occurs because apt-get cannot find the package. You might need to add extra sources to your repositories to fix this or compile the source manually.

---

### Post by danastasio on 2010-01-03
its not in the repos, you have to add the source manually, which is simple, in a terminal do

```
sudo nano /etc/apt/sources.list
```

and arrow down to the very bottom and enter

> deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main # Chromium
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main #Chromium source


once you paste this at the bottom, hold CTRL+O (thats the letter "o" not a zero)

and 
```
sudo apt-get update
sudo apt-get install chromium-browser
```

and you're all set!

---

### Post by lol768 on 2010-01-03
I think you can do this in synaptic too, if you prefer a graphical interface. Just click settings > repositories > Other software and click the add button.

---

### Post by tacantara on 2010-01-03
Oops...late post, please disregard.  Besides, I see now that the OP is using 9.04, so my info is incorrect :(

> **spcwingo said:**
> Did you add their ppa first?

If you haven't added the PPA, here's the info to do that:

> Adding this PPA to your system (Karmic Koala)
You can update your system with unsupported packages from this untrusted PPA by adding ppa:chromium-daily/ppa to your system's Software Sources.

---

### Post by Monrizzy on 2010-01-03
First of all, thanks so much for your help!  I was able to get Google Chrome installed.  Once again you guys have proven that this Linux community is far superior to anything from those crooks @ MS & Apple.

I've noticed that I've been getting this message a lot when I'm attempting to install something via apt-get:

> E: Couldn't find package ********

Is there a way to most of the repositories so that I won't get that message anymore?  

Thanks,

---

### Post by Monrizzy on 2010-01-03
Also does anyone know if Google Chrome has an add blocking feature?

---

### Post by danastasio on 2010-01-03
> **Monrizzy said:**
> First of all, thanks so much for your help!  I was able to get Google Chrome installed.  Once again you guys have proven that this Linux community is far superior to anything from those crooks @ MS & Apple.

I've noticed that I've been getting this message a lot when I'm attempting to install something via apt-get:



Is there a way to most of the repositories so that I won't get that message anymore?  

Thanks,

Glad we could help :D

and not really, if you so 

```
sudo apt-get install freakingawesome
```

it'll tell you that it didnt find the package "freakingawesome"

you can enable the universe and multiverse repositories, but that should already be done by default, that will give you access to A LOT more packages than the standard repo's. But so long as you try to install a package that isn't in your current repo's, you will get that error.

Though i find that I come across it very infrequently.

EDIT: you can find the options to enable universe and multiverse in system>administration>software sources

---

### Post by Monrizzy on 2010-01-03
I just went to system>administration>software sources.  I noticed that the universe box was not check so I check it.  Then it prompted me to reload and update the data.  When I click on reload I got this message.
> **Could not download all repository indexes**
> The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
> GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DEGPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by spcwingo on 2010-01-03
As far as the cdrom error just untick it in synaptic or software sources.  The GPG error solution is here:

[http://ubuntuforums.org/showthread.php?p=1653773]("http://ubuntuforums.org/showthread.php?p=1653773")

---

### Post by mkvnmtr on 2010-01-03
You will find if you add the program Ubuntu Tweek that adding the repositories for some very good stuff is very easy. Theings like Chromium, Opera and developement Firefox are just a click or two.

---

### Post by Monrizzy on 2010-01-03
> **mkvnmtr said:**
> You will find if you add the program Ubuntu Tweek that adding the repositories for some very good stuff is very easy. Theings like Chromium, Opera and developement Firefox are just a click or two.
Do I add that via Synaptic?

---

### Post by spcwingo on 2010-01-03
You can download Ubuntu-Tweak from here:

[https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9.2]("https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9.2")

After it's installed you can add the repo through Ubuntu-Tweak (along with many others).  ;)

---

### Post by Monrizzy on 2010-01-03
Thanks again folks!

I've said it before & I'll say it again.  This community is great!  I truly aspire to be as helpful as you folks have been.  Thank you.

---

### Post by dmaxel on 2010-01-03
> **Monrizzy said:**
> Also does anyone know if Google Chrome has an add blocking feature?
Since it seems that all other problems are solved, I'll answer this question then. :D

The answer is no. Unlike Firefox, which has Adblock Plus, Google Chrome has nothing (yet). I am not sure, but I believe I read somewhere that Adblock Plus is being developed to work on the Google Chrome extension system that is currently in the beta/dev channel.

---

### Post by shuttleworthwannabe on 2010-01-03
Adblocking in Chrome--take your pick from these [chrome extensions]("https://chrome.google.com/extensions?hl=en-US")

---

### Post by TBABill on 2010-01-03
Go to your Chrome browser and click the spanner (wrench icon next to the URL). Click extensions and you'll be taken to their site where you can find many extensions, including several ad blockers.

---

