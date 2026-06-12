---
title: "Ndiswrapper - Dlink DWA2330 - &quot;Hardware present - Yes&quot; yet it doesn't connect..."
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by Roasted on 2007-11-29
I was given an old Sony Vaio laptop last night. PIII, 256mb ram, etc. I threw Linux Mint on it, which is nearly identical to Ubuntu. 

It came with ndiswrapper already installed, so I went through and installed the windows driver and it says hardware present - yes. However, I can't get online.

What's the deal? Little confused here.

---

### Post by kevdog on 2007-11-30
Dont know a lot about mint, but lets try to see what the problem is.

Can you do at the command line:

lsmod | grep ndis

Please post the output.

---

### Post by HokeyFry on 2007-11-30
What did you do after running "ndiswrapper -i driver.inf"?


or did you use the gui program "ndisgtk"?

---

