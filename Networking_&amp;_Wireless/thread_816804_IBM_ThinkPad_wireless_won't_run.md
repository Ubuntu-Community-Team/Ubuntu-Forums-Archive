---
title: "IBM ThinkPad wireless won't run"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by pacman5 on 2008-06-03
**Preamble**: I've just stripped Windows XP Pro out of my trusty IBM ThinkPad T40 and installed Ubuntu 8.04 (the Hardy Heron). My total experience with Ubuntu/Linux is 2 hours. I'm still struggling with the basic concepts such as the Terminal/command line interface (which takes me back 30 years). And I'm very grateful to the Ubuntu  community for providing me with this system, and free of charge to boot (excuse the unintended pun). If all goes well I should reach the stage where I can plough something back into the community rather than just asking for help.

**The Problem** (or Challenge, as we say in corporate-speak): the wireless on the ThinkPad no longer functions. It was working up to the point where I removed Windows XP. Running lspci in the Terminal reports the wireless as "02:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)". I've searched around in the Ubuntu world for hints as to the next step but hitherto with no success, partly because many of the postings contain acronyms and Linux concepts which are still unfamiliar to me (give me a little slack here; I'll soon be up to speed).

**Request**: can someone tell me what might be wrong here and how to correct it ?

Thanks in advance

Paddy

---

### Post by ahmedh on 2008-06-04
Did you get the Thinkpad with the standard Intel wireless card or with the 4965 or 3945 upgrade?

---

### Post by pacman5 on 2008-06-04
Thanks for this, Ahmed.

I'm not sure how to find this out. The only wireless-related name I can find is Atheros but, if I understand correctly, that is the chip and not the card. The labels on the back of the laptop don't say anything about a wireless card (there are two labels which list different MAC numbers but they don't bear the name of a manufacturer or say anything about wireless).

If I go into the IBM boot facility it doesn't mention a wireless card in the system configuration list. But Ubuntu seems to have found one, as I mentioned in my previous posting.

Right now I'm going back to square one by erasing everything on the T40 disk with the intention of re-installing XP to see whether it "sees" the wireless card. If it does I'll then removed the XP and re-install Ubuntu.

Paddy

---

### Post by chili555 on 2008-06-04
The T40  never came with the 3945ABG nor the 4965. We have all the information we need:> 02:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)Drivers for the Atheros cards are inluded in *linux-restricted-modules*. Hook up an ethernet cable and go to System -> Administration -> Synaptic and install it. Your card should then be ready to configure.

---

### Post by pacman5 on 2008-06-04
Thanks very much for this help.

Right now I'm re-installing XP Pro to make absolutely sure that the wireless is still working as it was in the previous Windows world and then I'll re-install Ubuntu (probably as a dual-boot) and take your advice.

Why a dual boot ? Well, at this stage of my Linux/Ubuntu ignorance I want to have a fallback in case I do something fatal to my Linux installation. Does that make sense ?

Paddy

---

### Post by chili555 on 2008-06-04
> Does that make sense ?Sure. I've often been glad I had computer #2 running properly so I could fix computer #1! With dual-boot, it's all in one. The only downside is you have to shut down and reboot to try something, and if it doesn't work, reboot back to Windows, find another suggestion to try, reboot back to Ubuntu, ad infinitum.

Some day soon, in a 12-step group, you will confess you have been Windows clean for 3 months. We will congratulate you and give you a poker chip to carry.

---

### Post by ahmedh on 2008-06-04
I apologize about my wireless card mistake. May I suggest, however, you install Ubuntu with Wubi? It will probably make it easier to remove if you have trouble down the road again.

---

### Post by pacman5 on 2008-06-05
Thanks very much for this tip.

I went off to read up on Wubi and have a question to which I couldn't find an answer. As I understand it Wubi installs Ubuntu within Windows. If that is the case then presumably, whenever I fire up a Wubi-installed Ubuntu, Windows is running in the background with all its security risks. Is that correct ? If so it might be better to install Ubuntu on a separate partition so that it can run totally independently of Windows. Is that correct or have I misunderstood Wubi ?

Paddy

---

### Post by ahmedh on 2008-06-05
Wubi is a small .exe file that you run from within Windows. It will automatically download and prep an installation .iso. This creates a dual boot system. Windows is used only to install Ubuntu, but when you boot into Ubuntu, that's the only operating system running. Wubi will also adjust the GRUB so that on bootup, you get the option of Windows or Ubuntu. It acts exactly like a partition-based install, but it uses a virtual disk instead. Thus it is easier to remove. (When you boot into Ubuntu for the first time, it will take about 30 minutes for it to complete the installation) After you do this, follow Chilli's advice and hopefully you will be up and running.

Edit: I just thought of this; you may have to disable your antivirus program or firewall to allow Wubi to fetch the .iso correctly. If you are afraid of doing this, just download the .iso from [here]("http://www.ubuntu.com/getubuntu/download") and place wubi.exe in the same folder as the .iso you downloaded. Wubi will use the downloaded .iso rather than fetching a new one from the internet.

---

### Post by pacman5 on 2008-06-05
Aaah, thanks for this, Ahmed. Everything clear. I'll report back once I have my Windows system correctly installed (at the moment I'm having difficulty getting it to recognize the Ethernet and Wireless adapters on the IBM T40 laptop, but that's another problem) and can move on to Ubuntu, which is my ultimate target.

Paddy

---

