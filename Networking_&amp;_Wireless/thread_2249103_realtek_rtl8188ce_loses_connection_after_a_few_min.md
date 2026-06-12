---
title: "realtek rtl8188ce loses connection after a few minutes"
date: 2014-10-19
forum: Networking &amp; Wireless
---

### Post by chris272 on 2014-10-19
Hello all,
I am using ubuntu on my Toshiba satellite laptop. The Wi-Fi worked great under Windows 7, but on ubuntu and mint linux it is junk. I used to download over 1 Mbps on public wifi. Now I see spikes at that level, but mostly get around 100bps. That is a crawl. It is ok at around 1-12kbps, but that does not last long. I have tried it on several different networks, public and private (secured).  As an automotive technician, I feel the mode of failure to be like a hardware fault. However, it just started when I made the switch to ubuntu. I have checked internal temperatures, they are good. I tried to update the drivers. I don't think I did that correctly. I bought a cheap netgear wn111 usb network adapter. That is no better. However, I am not sure about the drivers for that either. The netgear came with Windows drivers on disk. I just plugged it in and it worked great (with the realtek turned off) for a few minutes. Same problem different drivers. The netgear uses atheros drivers. Does that mean the problem is my motherboard? I like this old laptop, and I would like to just replace the bad part ( or driver) and go back to using it. I have never repaired computer hardware but I have taken several apart and put back together as proof of concept.

Sorry for the crummy long paragraph. I'm having to do this on my phone :)

---

### Post by chris272 on 2014-10-19
Just remembered, I tried using Windows drivers (per my searches) with ndiswrapper. I can't figure that out. It asked for .inf files, but I can't find any. I am using the gtk+ graphical front end.

---

### Post by Bas_Kooijman on 2014-10-19
follow this thread, it worked for me: [http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver](http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver)

---

### Post by Vladlenin5000 on 2014-10-19
> **Bas_Kooijman said:**
> follow this thread, it worked for me: [http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver](http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver)

The Ask Ubuntu thread you posted has a few different answers. Can you please describe which one worked for you? Thank you.

---

### Post by chris272 on 2014-10-22
I tried the driver from freedom Ben. Performance seems more consistent, but not fast. Thanks for the help so far. I need to do more testing.

---

### Post by chris272 on 2014-10-29
Update, I disassembled my laptop. One of the wire s to the network card had popped off. Thanks for the help.

---

