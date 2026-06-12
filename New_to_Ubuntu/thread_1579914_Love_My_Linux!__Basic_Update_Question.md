---
title: "Love My Linux!  Basic Update Question"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by Phil92804 on 2010-09-22
I am a beginner - came from Mac.  Graphics chip went in my iMac and only had an older Window's Laptop to use.  Tried Ubuntu 10.04 - now I am not going to go back to Mac!  It's simple, elegant and complete - can be used by a novice.  

My question is will Ubuntu 10.10 be downloaded, upgraded or whatever it's called, automatically through the Update Manager when it's available? 

And, thank you to all who have worked on and improved Linux over the years so that a non-techie who only uses a computer as a tool finds it useful.  It's not perfect - a little quirk here and there, but I am no longer under the thumb of MS or Apple - it's kind of freeing.  

Thank you, again!

---

### Post by TCHebb on 2010-09-22
Yes, once Ubuntu 10.10 comes out, if your system if fully updated, Update Manager will prompt you to install it. The in-place upgrade from Update Manager won't damage any of your data (though it's still a good idea to back up regularly).

Some people, me included, prefer to start from a fresh install every time a new version comes out, but that's completely personal preference.

EDIT Whoops, I forgot that 10.04 was an LTS. It won't automatically prompt you to upgrade from an LTS to a non-LTS, but there will be instructions for upgrading to 10.10 once it comes out [here]("http://www.ubuntu.com/desktop/get-ubuntu/upgrade").

---

### Post by e79 on 2010-09-22
> **Phil92804 said:**
>  
My question is will Ubuntu 10.10 be downloaded, upgraded or whatever it's called, automatically through the Update Manager when it's available? 
 
Welcome to the 'real' world :) and I'm glad you enjoy Ubuntu ! To answer your question, the Update Manager should ask you (propose) the upgrade to 10.10 when it will be available (not in Beta as it is now) and you will only have to acknowledge and it will do the rest. I always suggest you take a backup of your /home directory before upgrading to a new version (Eg 10.04-10.10). Another way to do it when its ready would be to :
```
sudo apt-get update && sudo apt-get dist-upgrade
```
 
Have fun !

---

### Post by madmax75 on 2010-09-22
Yes, the System -> Administration -> Update thingie (? sorry, I don't use the English-version Ubuntu, so I'm not sure what these are in English :)) will prompt you when 10.10 is available. It will tell you that an upgrade is available and asks you if you want to download and install.

I suggest that you do not upgrade immediately when it comes available - the servers will be busy at first, and there probably is bugs still in the new version. I upgraded from 9.04 to 9.10 last fall, and the update stopped my USB broadband modem from working! I had to rig it manually so I could get updates...

So keep it cool and follow the forums for a while for any glitches and workarounds for them. Maybe a couple of weeks, then upgrade if you like.

Or, you could make a clean install (backup your important stuff, fetch and burn a new .iso on a CD/DVD and install over the old one). This might be a better way than upgrading, you get rid of all the old crud that's built up in the system this way.

---

