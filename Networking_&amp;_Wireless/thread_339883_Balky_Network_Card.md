---
title: "Balky Network Card"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by dblbogey on 2007-01-16
I'm running Dapper on an old computer with an ISA NIC. A few months ago a fellow forum resident helped me get my computer to see the card with the following:

[B]sudo modprobe 3c509

[login]

sudo config -a[/B]

That worked great. Then he said to make this a permanent fix, enter the following:

[B]sudo dhclient

sudo config -a[/B]

That also worked until I did a reinstall (another story!) Now the fix works for each time I start Ubuntu, but it isn't permanent, and I have to go to the terminal and reenter the commands every time I restart my computer. Can anyone tell me why this isn't working now?

---

