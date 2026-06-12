---
title: "Untangle FW OpenVPN wireless NIC configs"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by Tallwood on 2008-10-17
Hello all,

The project we've been assigned is to install an Untangle FW, which runs on Debian, and configure the box to use a wireless NIC, as this is the only WAN service available for this location.

We've found directions on how to install and config an Engenius EPI3601S wireless card, which is an Atheros based card. Our problem it seems though is that those directions are to provide a WAP internally. We need to receive an already available WAP.

Would this seem to work or are we going to run in to different configs for internal and external WAPs?

Thanks in advance.

---

### Post by Tallwood on 2008-10-17
and furthermore,

If configuring and receiving this WAP becomes an impossible task, then we've already ordered a 3Com wireless bridge that should do the trick.

Any and all advice would be appreciated.

---

### Post by Tallwood on 2008-10-17
So after much research and conversation, I think we are going to go with a 3Com wireless bridge solution to pull in the WAP signal and provide us an external address, then send the internal NIC in to a basic ethernet switch.

This project is taking place in the Bahamas, where internet is access is hard to find, hence the project at hand.

I'll update the project as we progress.

---

### Post by Tallwood on 2008-10-21
So we have successfully setup and tested this configuration.
Our 3Com bridge received a neighboring WiFi signal which we have no control over and we were able to distribute it internally to our LAN. This will simulate the signal on the island which we have no control over.
We also successfully setup a site to site VPN off this WiFi signal to our other branches.

The only issues we may run in to are any kind of router filtering that we do not know about, or WiFi signal dependent upon weather conditions. And, possibly some addressing conflicts, which could be remedied without too much trouble.

---

### Post by Tallwood on 2008-11-03
This solution has been deployed for well over a week now with no major problems at all.
The main hurdle we had to get over was finding a decent signal strength, which we had figured would be a part of the problem.
We ended up setting up a third party external antenna as the one 3Com provided with the bridge was far too insufficient.
After the signal was acquired we were able to setup the FW and VPN with ease. And it has been up since we left.
Now it's all in mother natures hands.

---

### Post by Tallwood on 2009-02-05
So, four months or so now and running strong. Loss of power has shut the server down a few times, but it has seemed to reboot upon power restore without problems yet.

---

### Post by Tallwood on 2009-04-16
We now have 7 sites up and running with Untangle FW in place and VPN connections back to the corporate location. We are setting up an 8th site tomorrow.

---

### Post by Tallwood on 2010-05-21
Just an update.

We have over 2 dozen Untangle FWs in place at various locations. The majority of them run on Dell PE 850s, but we also run quite a few on Dell OptiPlex GX270s without any problems. The OptiPlex platforms see significantly less traffic though.

---

