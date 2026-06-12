---
title: "Hamachi on Ubuntu"
date: 2013-11-12
forum: Networking &amp; Wireless
---

### Post by FenrirXIII on 2013-11-12
Hello community!

I have a dual boot Win7/Ubuntu12.04LTS... and i've got Hamachi on both OS for gaming purposes. **_now my question is, does Hamachi Auto-start on ubunut12.04LTS(or just ubuntu in general)_**? I know in windows the Hamachi auto-start after booting to it...

if it does, i got a fix on windows, just msconfig and uncheck in startup. what about in ubuntu?

Hamachi on ubuntu, by default, is ran in the TERMINAL. i have downloaded Haguichi (a GUI for hamachi) and if launched i would see an icon in the top panel... seeing that this is only a GUI, im thinking the Hamachi ran invisible... is this the case? this is what im worried about... i mean all the people in my hamachi server are friends and family, but i just dont like the idea of having an open port and i only strictly open Hamachi when im playing with them.

THANKS IN ADVANCE!

---

### Post by ztefn on 2013-11-28
Hi FenrirXIII,

For what i've seen, the Hamachi service is always started at boot time. But that doesn't yet mean a connection is established, that requires a login. Manually, this is done by entering "hamachi login" in the terminal or by pressing "Connect" in Haguichi. At boot time, by default (at least in my experience) the Hamachi service will login automatically if you where still logged in when you last shut down your computer. If you logged out ("hamachi logout" in terminal or "Disconnect" in Haguichi) before you shut down your computer, the Hamachi service will *not* login automatically next boot.

If you wish to change this behavior i would take a look at the h2-engine.cfg and h2-engine-override.cfg files inside the /var/lib/logmein-hamachi/ folder. In the h2-engine-override.cfg file you should be able to override any values from the h2-engine.cfg file. I've never tried that myself though, so if you give this a try please let me know if you got it working.

---

