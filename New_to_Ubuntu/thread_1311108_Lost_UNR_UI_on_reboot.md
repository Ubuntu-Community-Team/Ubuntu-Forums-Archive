---
title: "Lost UNR UI on reboot"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by dcoughler on 2009-11-02
I switched my EEE 701 PC to UNR 9.10 yesterday.  After getting the apps I wanted installed, and customizing my desktop, I shut the EEE down.  When I powered it up today, I was greeted by the ubuntu login screen. So far, so good.  Here's my problem: when I log in, I'm given two options: KDE and XTERM. XTERM (obviously) takes me to a terminal window. The KDE session takes me to a KDE interface that is completely different from the UNR UI I was working with yesterday.  How did I lose the UNR interface with the side-ribbon, and how do I get it back?

---

### Post by dcoughler on 2009-11-03
Love answering my own questions:

I tried a second time with the install, and did the following:

1. Launched Synaptic
2. Removed Evolution
3. Applied changes
4. Installed the following:
    - VLC
    - gFTP
    - Bluefish
    - Audacity
    - DeVeDe
    - Comix
    - K3B
    - Cups->SavetoPDF
    - tsclient
    - thunderbird
    - kpat

On reboot, GNOME was hosed.  

When I reinstalled everything using the apt-get command, GNOME was unaffected.  So, it looks like Synaptic was the culprit.

---

