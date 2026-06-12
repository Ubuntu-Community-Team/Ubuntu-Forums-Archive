---
title: "Amazon.com's MP3 Downloader"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Teasdale on 2009-10-15
I'd like to use this, and I see that they now offer a [Linux download]("http://www.amazon.com/gp/dmusic/help/amd.html/ref=dm_dp_amd") - but for Ubuntu 8.10, and I have 9.10. When I try to download the MP3 downloader (or the Debian option), I get an error message saying "wrong architecture." Also, my PC is 64-bit, which may make a difference.

Am I just out of luck, or is there a work-around?

---

### Post by SuperSonic4 on 2009-10-15
Amazon's downloader is 32 bit, You'd need to the 32 bit libs

edit: The package in the AUR says that there are the following dependencies (These are arch so look for small variations and ignore the inverted commas)

```
'bash' 'lib32-libxdamage' 'lib32-curl' 'lib32-pango' 'lib32-gtk2'
```

---

### Post by Teasdale on 2009-10-15
> **SuperSonic4 said:**
> Amazon's downloader is 32 bit, You'd need to the 32 bit libs

edit: The package in the AUR says that there are the following dependencies (These are arch so look for small variations and ignore the inverted commas)

```
'bash' 'lib32-libxdamage' 'lib32-curl' 'lib32-pango' 'lib32-gtk2'
```

So I need to type :
sudo apt-get install bash
sudo apt-get install lib32-libxdamage
sudo apt-get install lib32-curl
sudo apt-get install lib32-pango
sudo apt-get install lib32-gtk2

and then click the Ubuntu 8.10 download at amazon.com, and it should install?

---

### Post by SuperSonic4 on 2009-10-15
In theory yes, no idea if they are the right packages though. You may want to check in Synaptic

---

### Post by Teasdale on 2009-10-15
I see 'bash' (it was already installed) but nothing close to the others in the synaptic package manager with a 'lib32' prefix.

---

### Post by oldos2er on 2009-10-15
[http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

### Post by kanikilu on 2009-10-15
Haven't tried it myself, but here are instructions to get the Amazon MP3 downloader working in 64-bit Ubuntu: [http://www.ensode.net/roller/dheffelfinger/entry/installing_amazon_mp3_downloader_under](http://www.ensode.net/roller/dheffelfinger/entry/installing_amazon_mp3_downloader_under)

---

### Post by Crunchy the Headcrab on 2009-10-15
> **Teasdale said:**
> So I need to type :
sudo apt-get install bash
sudo apt-get install lib32-libxdamage
sudo apt-get install lib32-curl
sudo apt-get install lib32-pango
sudo apt-get install lib32-gtk2

and then click the Ubuntu 8.10 download at amazon.com, and it should install?

You don't need to redo an install command for every individual item.  Try this:

sudo apt-get install bash lib32-libxdamage lib32-curl lib32-pango lib32-gtk2

I'm not saying this will fix your problem.  I have no idea what those packages do :).  Why are you installing bash?  It should be installed.

---

### Post by ElSlunko on 2009-10-15
I can confirm that once you install the dependencies and use the flag to force architecture as mentioned in the links above Amazon's MP3 downloader works in 9.10 64bit.

---

### Post by The Cog on 2009-10-15
I won't use it. There is no good reason for them to not allow use of a browser to download the tracks, other than that they want to install their software on your PC. Now, why would they want to do that? You have Sony to thank for my uncompromising attitude towards that idea: No thanks, it's my computer and I want it to stay that way.

---

### Post by Teasdale on 2009-10-16
> **The Cog said:**
> I won't use it. There is no good reason for them to not allow use of a browser to download the tracks, other than that they want to install their software on your PC.

I can download entire CD's much cheaper than purchasing each song individually - but it requires the software. The price difference for something like Les Miserables, with many short songs, is significant. And right now, they're offering a free CD that I'd like.

---

