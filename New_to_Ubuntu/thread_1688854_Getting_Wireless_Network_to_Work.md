---
title: "Getting Wireless Network to Work"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by andrew1992 on 2011-02-15
Hello! I just installed the Ubuntu 10.10 Desktop release. I am entirely new to linux, and I seem to be aving some issues with setting up a wireless network. I have dual-booted my machine, and I can connect to the network just fine on Windows. Any ideas? I'll post relevant information upon request.

Thanks!

---

### Post by Mariane on 2011-02-15
Have you tried wifi-radar? 

Mariane

---

### Post by Bucky Ball on 2011-02-15
Welcome.

Is the card actually up and you can see networks? 

If not, have you plugged in an ethernet cable, gotten online and gotten updates? That may well pick up your card and offer drivers/firmware. 

Always include machine type and other relevant details.

Try System>Administration>Additional Drivers. Anything there? Get online, get updates, and try that again. If still no luck, open a terminal (Appications>Accessories>Terminal) and paste or type this:

```
lspci
```Look for a line near the bottom that says, 'Network Controller.' Post that back here and we will know what card your using. ;)

Incidentally, 10.04 LTS (long term support) is a smoother ride for a newcomer and is more stable (supported until April 2013). Good luck.

* Mariane, don't think that has anything to do with OPs problem. ;)

---

### Post by andrew1992 on 2011-02-16
Thanks for the responses! I typed in the "lspci" command, and it appears to recognize my network card. It is Realtek RTL8192E Wireless Lan controller. I've taken a look at ndiswrapper, but apparently this card is supported by Ubuntu, so I'm not realsly sure what to do. Other than this, I cannot see any of the networks I created, so I don't think the card is actually up.

---

### Post by andrew1992 on 2011-02-18
Any ideas?

---

### Post by shutupsquare on 2011-02-18
Does ubuntu show you the little wireless symbol in the top right of your screen?

---

### Post by andrew1992 on 2011-02-18
I have a Network Manager Icon, if that's what you mean...it seems as though it doesn't detect any networks at all.

---

### Post by Bladeforger on 2011-02-18
I had the same issues, and the WICD Network Manager fixed it for me.  Download with Synaptic.  OH, you have to plug in directly to download it, then you can unplug the direct wired connection and proceed with the wireless.
Keith

---

