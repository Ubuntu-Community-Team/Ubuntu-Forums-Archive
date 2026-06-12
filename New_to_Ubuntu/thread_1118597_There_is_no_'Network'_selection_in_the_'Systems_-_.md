---
title: "There is no 'Network' selection in the 'Systems - Adminisrator' dropdown menu"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by judeisadawson on 2009-04-07
Hi Guys,
There is no 'Network' selection in the 'Systems - Administrator' dropdown menu. I've posted my comments on Launchpad on 06/04/09. I have received some suggestions for the launchpad team. I thought that I could get more suggestions from the Ubuntu Forums.

The following is the thread:


Posted on 05/04/09)
Hi All,
I upgraded from Hardy to Intrepid yesterday. I downloaded an alternative installation apps & followed instructions provided in the Ubuntu documentation pages to upgrade the OS.
Everything went well during & after the upgrade.
Today, however, I noticed something wrong. My modem connection was missing from Network Manager at the top-toolbar. So I proceeded to configure the settings once again. I had done it before in hardyu & it was relatively easy with the instructions provided.
Here's the problem. There is no 'Network' selection in the 'Systems - Administrator' dropdown menu. Very strange...

Do I need to reinstall 8.10?

(Posted on 06/04/09)
...Thanks for the info. Unfortunately, I have not solved the problem yet.

Before I continue, here's what I'm trying to do. I'm trying to configure Intrepid to work with my 56k dialup modem connected to my PC via serial connection (don't laugh...). I ran 'wvdial conf' in 'Terminal' and the modem was detected. Moreover, it was working fine in Hardy.

Here's what I've done so far. I right-clicked on the toolbar at the top of the screen & selected 'Add to Panel'. I selected the 'Modem Monitor 2.24.1' apps. The icon appeared on the toolbar.
However, double-clicking it does nothing to it. I then right-clicked the icon & selected 'Properties'. An error message appeared. It said : 'Could not launch network configuration tool. Check that's it's installed in the correct path and that it has the correct permissions.'

Also, I still cannot find the 'Network' tab in the 'System - Administrator' dropdown menu.'

I hope all this information helps in finding out what the problem is & what needs to be done.

Thanks, all.

From,
Jude

---

### Post by Penguin Guy on 2009-04-07
Try: System -> Prefrences -> Main Menu
Then scroll down to the Administration section and check that 'Network Tools' exists and is checked. If it is not checked; check it.

---

### Post by gandaran on 2009-04-07
look in system » preferences » network configuration, thats where you find it in ubuntu 8.10 not system » administration.

---

### Post by judeisadawson on 2009-04-07
Thanks, guys.
I'll try these out on my pc back home tonight & let you know the outcome. 
Now, it'a time to leave the office :p
From,
Jude

---

### Post by judeisadawson on 2009-04-07
Hi guys,
I've followed the instructions . Yes, network configuration is in 'Preferences'. 
However, I do not see 'network configuration' in 'System -> Prefrences -> Main Menu'. 

Another thing that bugs me is why doesn't the 'Modem Monitor' apps work, why does that error message appear when I click on its properties & what does it mean?

Could this be part of the problem?

Also, assuming there is no problem & I am just very unfamiliar with Intrepid's layout, how do I setup & configure my 56k-dialup?

Thanks VERY much,all.

From,
Jude

---

