---
title: "[SOLVED] fresh install of ubuntu 6.06 and no internet...help please"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by tlommy187 on 2008-08-20
ok im new to all this so bear with me. So ive used ubuntu for a while and all has been well. log on and boom im on the net. i was using comcast high speed with a linksys router all wired. So i recently got comcast in my gues house so i wouldnt have to go inside steal my parents internet. so i did a fresh install of 6.06 (newer versions dont work on my old sony viao i use with linux) so after the fresh install i get no internet. i check the settings and there is nuthing in the dns tab for eth0. in my room im connecting directly to the modem no router. but yet if i take my computer in the main house and plug it in im on right away. i just cant figure it out. if anyone has any ideas id love to hear em! especially since im paying for internet i cant fully use yet! thanks!

---

### Post by Phases on 2008-08-20
Go into properties of eth0 and ensure it's set to DHCP?

(Edit: Question mark because I'm knew to Ubunut myself, but 8.04, and I'm at work right now so can't sit in front of my boxes (one desktop and one server)...)

---

### Post by jimv on 2008-08-20
This is going to sound stupid, but plug your computer into the modem, then unplug the power cord from the modem for 30 seconds and plug it back in.  When it comes back up, you should have internets.

---

### Post by tlommy187 on 2008-08-20
first off thanks to both of you for replying and trying to help me out. first off yea it is set to dhcp automatic. and u know i didnt try turning off the modem and waiting a bit and reconnecting it. i tried calling comcast they said they dont support linux so they had no help for me. then i asked them about my windows 2000 machine with the same problem. and they told me just that. to unplug the modedm let it sit for 30 seconds and try again. i guess some computers need it to be reset. so i will try it out soon as i get off and i'll repost with the results. thanks again to both of yoU!

---

### Post by Iowan on 2008-08-20
> **tlommy187 said:**
>  ...i guess some computers need it to be reset... Actually, it's the modem that needs the reset - from this and other stories I've read, some modems "lock onto" a MAC address, and must be reset to see a different one.  It'd almost be worth sticking a router in between to act as a "permanent interface.  If you should decide to add other machines later (servers, roommate, etc., you hopefully wouldn't need to repeat the exercise.

---

### Post by tlommy187 on 2008-08-21
just wanted to post back and say it works! lol. i cant believe it was that simple....i guess in the main house the router takes care of all that for me so i dont have to reset all the time. anyhow thanks again for puting up with my stupid problem!

---

### Post by Iowan on 2008-08-21
Glad it works! Mark this one [SOLVED] (Under Thread Tools), and go explore Ubuntu.  When (uh... IF) other problems arise, there are plenty of helpful folks who'd LOVE to lend a hand (or at least a word).

---

### Post by tlommy187 on 2008-08-22
cool wasnt sure how to do that lol... alright back to the forums for my next question! lol.

---

