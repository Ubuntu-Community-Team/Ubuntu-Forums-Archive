---
title: "Vuze Annoyware Virus"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by misterfixit on 2009-02-15
OK, I never imagined that I would see Annoyware in Linux.  I installed Azureus, hoping it would work this time.  It didn't for a variety of reasons.  When installing it said that it is now "vuze".  Almost immediately an annoyware box kept popping up telling me that an upgrade and restart was needed.  I went to Synaptic and used the remove all traces option to get rid of azuerus and vuze, which seemed to be a different or separate listing.  Logged out and logged back in:  Same problem as before with the popup annoyware.  I went to terminal and did sudo find azureus* and vuze and then used rm to delete everything matching name azureus or vuze.  Then i did a complete reboot, just like Windows.  Guess what?  first message I get when I sign my workstation back on it the upgrade vuze trojan.  Next, I did grep for anything containing vuze or azureus and found a few logs, empty folders, and some hidden text files; also a load of matching crap in my tmp.  I individually went to each one of those using sudo nautilus, examined them and then deleted them.  I deleted the trash, I did a cold reboot again.

Guess what?  the vuze annoyware box is back again.  Yoo hoo!  "I'm baaaaaaack ...."

Anyone have a clue?  I sure hate to have to do the usual Windows thing and reformat and reload even if I do have everything rsync'd to an unattached 1TB drive.  So far, I have wasted some 2 hours on this nasty little bug/annoyware/crapyware/innovative enhancement.

---

### Post by Paqman on 2009-02-15
> **misterfixit said:**
> 
Anyone have a clue?

Check in System > Prefs > Sessions. That's all the stuff that starts up when you log in, and there might be something pointing to the culprit.

Pretty shocking behaviour from Vuze though. I dumped Azureus a couple of years ago when it had expanded to about the size of Jupiter's orbit, I can only imagine how bloated and evil it is now.

---

### Post by misterfixit on 2009-02-15
> **Paqman said:**
> Check in System > Prefs > Sessions. That's all the stuff that starts up when you log in, and there might be something pointing to the culprit.

Pretty shocking behaviour from Vuze though. I dumped Azureus a couple of years ago when it had expanded to about the size of Jupiter's orbit, I can only imagine how bloated and evil it is now.

Thanks for the tip ... I checked sessions at the first and nothing thre.  You are correct about Azureus being Bloatware as well as Annoyware.  I would also say Crapware, except that the folks did put what must have been thousands of hours into creation of the Pig.  I thought vuze would somehoe "be better".  Not so.  I went back to using Frostwire as my torrent client and it still works fine, it is just that there is not enough selectivity with Frostwire (Limewire clone).

We'll see if I can get this fixed ...

Thanks again and glad to see someone here who does not automatically attack me and all of my ancestors because I don't like a particular Linux product.  :lolflag:

Dave

---

