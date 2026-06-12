---
title: "Rythmbox MP3"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by shardvexspangler on 2010-06-18
How do I make Rythmbox play mp3?

---

### Post by pete1983 on 2010-06-18
Hello shardvexspangler

Ubuntu can play the most popular non-free media formats, including DVD, MP3, Quicktime, Windows Media, and more by following the instructions 

Go to Applications-software center- type in Ubuntu restricted extras they should come up in the results, Then install and enjoy.

Have fun and enjoy.

---

### Post by jecaestevez on 2010-06-18
sudo add-apt-repository ppa:nilarimogard/webupd8

sudo apt-get update

sudo apt-get update && sudo apt-get install rhythmbox  rhythmbox-plugins rhythmbox-plugin-coherence rhythmbox-plugin-cdrecorder

---

### Post by shardvexspangler on 2010-06-18
OK, the Ubuntu computer I have working right now doesn't have internet access, but I know an alternate way to get stuff.    I got Ubuntu Restricted Extras, but I still can't play mp3.  When I open an mp3 with Rythmbox it says, "plugin not found, do you want to search for plugin?" I click yes.  It can't do any plugin searching though, cause my network isn't up.  What do I need?  And I know I should get my network running, but I can't right now.

---

### Post by sandyd on 2010-06-18
> **shardvexspangler said:**
> OK, the Ubuntu computer I have working right now doesn't have internet access, but I know an alternate way to get stuff.    I got Ubuntu Restricted Extras, but I still can't play mp3.  When I open an mp3 with Rythmbox it says, "plugin not found, do you want to search for plugin?" I click yes.  It can't do any plugin searching though, cause my network isn't up.  What do I need?  And I know I should get my network running, but I can't right now.
grab "libxine1-ffmpeg" and "gsreamer0.10-ffmpeg"

---

### Post by pete1983 on 2010-06-18
When you get online do a ubdate and see if that fixes it.
If that fails give this a shot and see if it works

su[COLOR="Red"]do apt-get purge rhythmbox

sudo apt-get update

sudo dpkg --configure -a

sudo apt-get install -f

sudo apt-get install rhythmbox rhythmbox-plugins[/COLOR]

this will reinstall Rhythmbox, this is a bit over kill but it might do the trick at worst Rhythmbox gets reinstalled.I did this in the past and it cured all Rhythmbox's issues.
Good luck

---

