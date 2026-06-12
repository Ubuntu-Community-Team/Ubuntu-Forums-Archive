---
title: "Xircom network issue"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by evile on 2005-11-26
I just recently installed Ubuntu 5.10 on a compaq presario 1688. My problem is this: I put the Xircom (ethernet/modem combo card) in the pcmcia slot and i get a positive beep indicating no problems, however i get no activity light on the card itself. eth0 is setup properly my routing is all setup as well. 

cardctl ident reports:

socket 0:

product info:: "Xircom", "Creditcard ethernet 10/100 + modem 56", "CEM56", "1.00"
manfid: 0x0105, 0x110a
function: 2 (serial)

No info about the card shows up in lspci -v but my cardbus does.
Under the device manager my card does show up as an unknown network device. I am really out of ideas here because it looks to me like everything should be in order? Any help or information would be welcomed! thanks!

Or if anyone can point me in the direction of a network card that is known to work under Ubuntu that would help as well.

---

