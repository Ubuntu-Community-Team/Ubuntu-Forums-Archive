---
title: "[SOLVED] Dell Vostro wireless won't connect"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by djbon2112 on 2008-03-24
I'm using Ubuntu Gutsy on a Dell Vostro 1700. I've used the restricted driver manager to install drivers for my wireless, and it all seems to work. However, when I try to connect to a wireless network, it asks for my key, and then sits there saying "waiting for wireless key from <router>", before disconnecting (auto connecting back to my wired Ethernet). It does this with every wireless network I try to connect to, regardless of encryption type (if any). Any suggestions?

---

### Post by Eiríkr on 2008-03-24
I've read in other threads that the default Network Manager app is quite problematic when you have more than one network interface.  Other posters have recommended replacing Network Manager with WICD, which unfortunately isn't included in the Ubuntu repositories and thus must be downloaded from [its Sourceforge page]("http://wicd.sourceforge.net/").  

HTH,

Eiríkr

---

### Post by djbon2112 on 2008-03-24
Tried that, and now I can connect flawlessly! Thanks so much!

---

### Post by Eiríkr on 2008-03-24
Glad it worked!  :D  If that does it for this thread, please mark it as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Cheers,

Eiríkr

---

