---
title: "Borhter HL-1250"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by gnarly_buttons on 2007-09-13
I am trying to connect to a Brother HL-1250 printer on a network.  The printer is connected directly to the network, not through another computer.  However, I can't seem to get it to work.  I am using Feisty.  Here is the status message it gives me:

Ready: Unable to get printer status (server-error-operation-not-supported)!

Thanks for your help.

Scott

---

### Post by tvrg on 2007-09-13
please provide the steps and selections you made during the setup

I think you need to select network printer, then tcp socket while you are selecting network printer > ipp printer on cups server

---

### Post by gnarly_buttons on 2007-09-18
You were right.  I was just using the ipp instead of tcp.  Now it works.  Thanks.

Scott

---

