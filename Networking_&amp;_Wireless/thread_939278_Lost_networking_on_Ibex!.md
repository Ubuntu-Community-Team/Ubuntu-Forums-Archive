---
title: "Lost networking on Ibex!"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by RevolutionMaster on 2008-10-05
When I updated to Ibex, I lost networking on  BOTH of my network cards.
They are the Intel 82566DC- 2 Gigabit, and the Linksys NC100 cards.
At this point, they show that they are there, and are receiving packets, yet can't ping ANYTHING. Also, I can't find the network config manager. It is NOT shown in the menus, yet I CAN find the Network Tools setting.

I need to get the Network Settings Manager up.

---

### Post by ryantriplett on 2008-10-05
Same problem here with Xubuntu Ibex Beta.

---

### Post by RevolutionMaster on 2008-10-05
> **ryantriplett said:**
> Same problem here with Xubuntu Ibex Beta.
My Kubuntu Ibex install didn't have networking on my T30. Then again, Kubuntu Hardy didn't have networking on my T30.:p

---

### Post by ryantriplett on 2008-10-05
That's the strange thing ... I have the network manager in the panel - however, when I click on it and click "enable networking" I get a message that says "networking disabled" (or something similar to that).

---

### Post by RevolutionMaster on 2008-10-05
> **ryantriplett said:**
> That's the strange thing ... I have the network manager in the panel - however, when I click on it and click "enable networking" I get a message that says "networking disabled" (or something similar to that).

Do you know what command will open the Network manager, Mine won't show up (network tools will however)

---

### Post by iponeverything on 2008-10-05
nm-applet &

in a terminal will start network manager. In most cases it will continue to show up after that first manual start.

You might need to add it under system->preferences->sessions

---

