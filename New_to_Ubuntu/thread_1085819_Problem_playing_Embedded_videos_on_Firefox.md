---
title: "Problem playing Embedded videos on Firefox"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by rausuar on 2009-03-03
Hi all,

I am using Ubuntu 8.10 x64, latest updates, with the Medibuntu Repository and Flashplayer, along with the mozilla-mplayer plugin.

The problem is that when I visit webpages, mainly from news services and newspapers, and try to play or watch embedded videos, they keep and keep loading, and never play.  When I do right click into the embedded video, it says that is using Flash Player 10.

Any help to fix this problem??? please if no answer can be found here, where can I post the problem to get a proper solution?

Thanks!

---

### Post by Het Irv on 2009-03-03
Heh, been there, done that.  Having NoScript turned on with produce similar results sometimes.

---

### Post by st33med on 2009-03-03
Nvmnvmnvm

---

### Post by davidcyber00 on 2009-03-03
hey ppz am a new ubuntu user and im having problems to find where to download the flash player from that i can use to watch videos such as youtube
please reply and help me make the most out of myyyy ubuntu 8.10
thanks for ur time

---

### Post by gandaran on 2009-03-03
> **davidcyber00 said:**
> hey ppz am a new ubuntu user and im having problems to find where to download the flash player from that i can use to watch videos such as youtube
please reply and help me make the most out of myyyy ubuntu 8.10
thanks for ur time
see [this]("http://gandaran.com.sapo.pt/ubuntu.html") for installing flash

---

### Post by gandaran on 2009-03-03
> **rausuar said:**
> Hi all,

I am using Ubuntu 8.10 x64, latest updates, with the Medibuntu Repository and Flashplayer, along with the mozilla-mplayer plugin.

The problem is that when I visit webpages, mainly from news services and newspapers, and try to play or watch embedded videos, they keep and keep loading, and never play.  When I do right click into the embedded video, it says that is using Flash Player 10.

Any help to fix this problem??? please if no answer can be found here, where can I post the problem to get a proper solution?

Thanks!
for 64-bits ubuntu  remove the flashplugin-nonfree (adobe flash 32-bits) and get the 64-bits package[ here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz"), to install extract the package and move the libflasplayer.so file to /home/'user'/.mozilla/plugins (make the plugins folder) or if you have more than one user account place it in /usr/lib/mozilla/plugins, thats all!

---

### Post by davidcyber00 on 2009-03-03
thx for taking the time but culd you maybe make me a screenshot guide caaause i really dooont get this
ppllleeeaaassseee

---

### Post by st33med on 2009-03-03
Okay a little more detail then:

1) Visit [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz") and tell Firefox to download and open with Archive Manager. 
2) Extract the folder by hitting 'Extract' at the top.
3) in the next window, navigate to 
.mozilla/plugins.  As he said, you need to create the plugins folder if it is not there, so, click 'Add New Folder' on the top-right corner and type 'plugins' and hit 'Enter'.  Next, click on the folder once to highlight it and hit 'Extract' at the bottom.
4) Restart Firefox.

Bam.

---

### Post by gandaran on 2009-03-03
> **davidcyber00 said:**
> thx for taking the time but culd you maybe make me a screenshot guide caaause i really dooont get this
ppllleeeaaassseee
what's the problem? if you running 32-bits ubuntu open the terminal/console (applications » accessories » terminal or console)  and type **sudo apt-get install ubuntu-restricted-extras** hit enter, you'll need this package, it installs flash, java and codecs

---

### Post by Het Irv on 2009-03-03
> **gandaran said:**
> what's the problem? if you running 32-bits ubuntu open the terminal/console (applications » accessories » terminal or console)  and type **sudo apt-get install ubuntu-restricted-extras** hit enter, you'll need this package, it installs flash, java and codecs

He is running 64-bit, but its not that much harder.

---

### Post by gandaran on 2009-03-03
> **Het Irv said:**
> He is running 64-bit, but its not that much harder.
davidcyber00 hasn't mentioned if it's 32-bits or 64-bits!

---

### Post by Het Irv on 2009-03-03
> **gandaran said:**
> davidcyber00 hasn't mentioned if it's 32-bits or 64-bits!

Your right I saw you quote the OP and assumed it was davidcyber00, without checking, my bad!:oops:

---

### Post by forestwalkerjoe on 2009-03-03
I know this is probably not the perfect place to ask for my question to be answered.. but i figurd .. I'll Try.. what the heck. 
Ok.. I DID have trouble with my firefox and flash player.. but largely.. that is now fixed. NOW.. i have a side question. When i play a embeded video.. or News Cast.. its default is this tiny little screen.. which some times is OK.. the screen is clear and sound and video is matched. 
IF i use one of the FULL SCREEN modes.. the audio is clear.. the video is not.. its close to in sync.. and some times IS in sync.. but the real problem is the little squares.. its not clear.. it looks terrible. IS there some sort of extra CODEX that i need to make sure that video is clear at Large screen? I am using a darn good video card.. in a 3 gig hurts system with over 2 gig ram.. on Ubuntu 810. 
thanks
FWJ

---

### Post by gandaran on 2009-03-04
> **forestwalkerjoe said:**
> I know this is probably not the perfect place to ask for my question to be answered.. but i figurd .. I'll Try.. what the heck. 
Ok.. I DID have trouble with my firefox and flash player.. but largely.. that is now fixed. NOW.. i have a side question. When i play a embeded video.. or News Cast.. its default is this tiny little screen.. which some times is OK.. the screen is clear and sound and video is matched. 
IF i use one of the FULL SCREEN modes.. the audio is clear.. the video is not.. its close to in sync.. and some times IS in sync.. but the real problem is the little squares.. its not clear.. it looks terrible. IS there some sort of extra CODEX that i need to make sure that video is clear at Large screen? I am using a darn good video card.. in a 3 gig hurts system with over 2 gig ram.. on Ubuntu 810. 
thanks
FWJ
normally videos posted on the web have small resolution, unless it's a HD video it won't look very clear in full screen

---

