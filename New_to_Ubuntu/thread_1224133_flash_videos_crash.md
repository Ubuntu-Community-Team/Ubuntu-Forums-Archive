---
title: "flash videos crash"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by Brelen on 2009-07-27
Hi all, I'm new to Ubuntu and linux in general, but so far I love it! ^_^

now that this is out of the way, I have a problem with flash videos in firefox, they will play for a while (sometimes a few seconds, sometimes 10 mins, sometimes the whole thing, there doesn't seem to be a pattern), and then they stop and get replaced by a black screen. i first used adobe's flash plugin, they did it, tried switching to swfc?(i dont remember the spelling :P) something, my videos simply wouldn't play, then i tried to switch to gnash, it did the same thing as adobe.

I tried to install them both by using the automatic firefox plugin finder and synaptic, had the results i described above no matter how i did it, so it's most likely something else. I'm not too sure about what kind of info would be needed to help with this so i'll leave it at that for now, just tell me what else you guy's would need to know and how to get them and i'll provide the info asap.

Thanks in advance for the help. =)

---

### Post by peakshysteria on 2009-07-27
Which FF version do you have and which addons do you have? What OS are you running?

---

### Post by Brelen on 2009-07-27
I'm using firefox 3.0.12, the only add-ons i have are ubuntu firefox pack 0.6 and Unplug 2.003 which is disabled. I'm running Ubuntu 8.10, intrepid Ibex

---

### Post by peakshysteria on 2009-07-27
Have you tried to [Install Firefox 3.5 in Ubuntu 9.04 using Ubuntuzilla]("http://tombuntu.com/")? Not sure it will work. If you search the forums there are several threads mentioning similar problems.

---

### Post by Brelen on 2009-07-27
I don't really want to upgrade to 9.04 yet, i've tried it and couldn't find any proprietary driverfor my graphic card in it, is it possible to get FF 3.5 in 8.10?

---

### Post by Brelen on 2009-07-27
Well, i tried Ubuntuzilla, and it updated to 3.5 without any problems, i'll see if the videos work now, thank you very much for your time and quick replies peakshysteria they were very appreciated and sorry if i asked a redundant question. :D

Edit: The videos still crash using FF3.5 =/ any other ideas?

---

### Post by Garyhans on 2009-07-27
Out of curiosity try right clicking the video and uncheck hardware acceleration.

---

### Post by Brelen on 2009-07-27
Just tried it, didn't work, the video crashed a few seconds later =/

---

### Post by peakshysteria on 2009-07-29
As far as I can see with a quick google search this looks to be [**Bug #333127: Firefox 3.5 and above crash on full screen flash video.**]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/333127") Related to Nvidia drivers. I cannot see any similar problems on my intel or Ati machines.

Down close to the bottom of the page if you follow the above link there seems to be a temporary fix.

You can also swing by [**Mozillazine's Frequently asked questions**]("http://forums.mozillazine.org/viewtopic.php?f=38&t=106431&sid=5b90faa69ac54618ab97154ab5ca73d8") (though they seldom answer as fast as the people right here). [**Firefox crashes**]("http://support.mozilla.com/en-US/kb/Firefox+crashes") might also be of some help.

---

