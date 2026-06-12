---
title: "Two folders. Both shared. One is accessible. One is not."
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by Roasted on 2008-06-16
Okay... I've got Hardy on my desktop and XP Pro on my laptop. I shared out a total of 2 folders. Music and my pre-shared "Shared Documents" known as "Shared Docs" on the network.

Firewall is off.

When I go to network and click on workgroup on my Ubuntu machine, Laptop appears. Okay, great. I click on laptop and I see the shared folders. I of course see several folders, like Windows$ and C$ as well as Print$ which aren't accessible. Okay, whatever. Music is accessible... yet Shared Docs is not... 

I went into sharing properties and they are both shared with the exact same permissions. 

When I try to click on Shared Docs, I get this error. Couldn't display "smb://laptop/shared%20docs/" There is no application installed for this file type.

Except... It's a folder! A shared folder! Just like music! Yet music works...

Why?

EDIT - I believe I fixed it. I kept unsharing/resharing it again to see if that was the problem. Then when I went into my home directory I noticed that there were several listings on the left side of "shared docs" "shareddocs" "shared documents" etc... so I just unmounted all of them and started fresh. Now it works fine. Guess I should have paid more attention!!

---

