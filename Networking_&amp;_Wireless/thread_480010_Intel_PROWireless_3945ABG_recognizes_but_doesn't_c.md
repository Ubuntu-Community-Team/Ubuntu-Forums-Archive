---
title: "Intel PRO/Wireless 3945ABG recognizes but doesn't connect to WEP network"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by 1212jtraceur on 2007-06-20
Hi everyone,

I just installed Feisty Fawn a couple days ago, and it works well! However, I have the problem listed in the title.

My card sees the network, SSID and all, but when I put in the WEP key, the little icon in the top toolbar spins for a while then quits, with no explanation.

I know there's [some drivers out there]("http://ipw3945.sourceforge.net/"), but it worked when I ran from the LiveCD, so maybe I could get what I need from the disc without having to download in Windows, then transfer to my shared partition, then to the Ubuntu partition...Does anyone know if that's possible?

Thanks,
1212jtraceur

EDIT: Oh yeah, I'm on a Dell Latitude D520, if that helps.

---

### Post by 1212jtraceur on 2007-06-21
Nevermind, it just started working, for no apparent reason. I did install the 50 or so packages recommended after I installed Ubuntu, maybe that had something to do with it.

I'll post back if I have any more issues.

---

### Post by floke on 2007-06-21
Do yourself a favour - download wifi-radar (sudo apt-get install wifi-radar) as soon as possible as a backup - the network manager by default is crap - it craps out on me all the time - I only use the radar now, and this works flawlessly. I also have the 3945.

---

### Post by n3le1101 on 2007-06-21
hi, i just installed ubuntu last night on my dv2000 HP Notebook.  wireless seems working properly- using Network Settings. (using WEp)  I just  migrated from windows and find it painless.  Just make sure that DNS Servers are properly working. - I'm actually connecting via Windows Domain. (DNS)

I know that WEP isn't the best encryption available. I will be testing IPSEC.  Keep posted. :p

Nel

---

### Post by explemonk on 2007-06-21
> **Steve.K said:**
> Do yourself a favour - download wifi-radar (sudo apt-get install wifi-radar) as soon as possible as a backup - the network manager by default is crap - it craps out on me all the time - I only use the radar now, and this works flawlessly. I also have the 3945.

I used wifi-radar initially, but couldn't get Gaim/Pidgin to realize that I was connected.  Network Manager seems to work pretty reliably for me on my 3945.

---

