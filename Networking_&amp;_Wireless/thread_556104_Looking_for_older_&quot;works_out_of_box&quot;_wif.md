---
title: "Looking for older &quot;works out of box&quot; wifi for Feisty"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by maestrobwh1 on 2007-09-20
Anyone have any success with cheap, older desktop pci cards that I could find used on e-bay that will work in Feisty without any fiddling around?  802.11 b is fine, as the router I am using is a b.  I looked in the wifi wiki, and copied and pasted a few things into e-bay, but the wiki doesn't always list the distro.

I am a teacher and I had acquired a few P III machines at school that have been running Kubuntu just fine but upon attempts to upgrade from Edgy to Feisty, two machines that I stuck some old Belkin F5D6001 PCI wireless cards (worked out of the box for Edgy), on reboot into Feisty, the cards do not show up in System settings-->Network settings.  The cards are different revisions, and the one with the one with Prism2 still works well with Edgy, though it "disappears" with Feisty upgrade.  I had to revert to a partition image to get the wifi working again, as there aren't any wired ports within practical range.

Reason for wanting to upgrade... the connection isn't stable in Edgy and drops out and then I have to help students reconnect.  The network manager package in Edgy doesn't pick up networks, so I am stuck using wlassistant to connect and kwifimanager to show the signal.  I tried WICD, as it doesn't need a password, but it doesn't seem to work with these cards and locks up when trying to renew the IP..

I realize I could goof around and try to get these to work but I don't have that kind of time.  I have only had success with ndiswrapper with one other card, so I am looking to avoid these kinds of steps.  I suppose if restricted manager recognizes the card and and will download the firmware, that is an okay route.

---

### Post by kevdog on 2007-09-20
Check the madwifi website -- this lists cards that should be out of the box compatible with feisty via the restricted drivers (which contain the madwifi drivers).

---

### Post by maestrobwh1 on 2007-09-21
Thanks... I'll check that for atheros cards.  The older ones will be a sure thing.

---

