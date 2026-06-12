---
title: "wireless connection in a compaq mini netbook"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by maryalesia on 2011-03-02
I'm helping my friend set up Ubuntu netbook edition 10.10 on his compaq mini. I have it installed, but I can't get it to connect to the internet. I get to wireless connections, hit "ADD", type in all the info, but the next "ADD" button is grey and un-clickable. On the little pull down box at the top of the screen, it says "Wireless networks - device not ready, firmware missing".

How can I get the firmware without connecting to the internet / what does this mean? This is an older netbook, probably first generation. It came with windows XP.

---

### Post by maryalesia on 2011-03-02
okay - I'm on the netbook now, connected via and ethernet cord. 

I tried to download two proprietary drivers: "broadcom B43 wireless driver" and then "broadcom STA wireless driver". Each time I got this error message:

"SystemError: installArchives() failed"

---

### Post by maryalesia on 2011-03-02
HOKAY. I went into synaptic and marked to re-download the firmware-b43-installer. It didn't work.

In the details of the error message, it said:

Not supported low-power chip with PCI id 14e4:4315!
Aborting.


So I have an old chipset that isn't supported? Is there a different package I should download for this chipset, or is this netbook too old to get wireless?

---

