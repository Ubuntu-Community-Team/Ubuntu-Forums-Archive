---
title: "[SOLVED] Setting up &amp;quot;pand&amp;quot; for network access on Palm"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by johnnybeem on 2008-06-26
Just got a new Palm handheld and am trying to set up bluetooth/pand so that I can get network access through bluetooth.

I followed the instructions here:

[http://ubuntuforums.org/archive/index.php/t-598890.html](http://ubuntuforums.org/archive/index.php/t-598890.html)

which seem like they should work well. But when I go on my palm and click "Connect", I get "Initializing", then "Error: Serial (0x030B)".

Here is the output of "pand --connect <palm hw addr> -n" - not sure if this means anything

pand[6298]: Bluetooth PAN daemon version 3.26
pand[6298]: Connecting to <palm hw addr>
pand[6298]: Connect to <palm hw addr> failed. Connection refused(111)


Thanks in advance!!

---

### Post by johnnybeem on 2008-06-26
hmm... maybe I'm doing this wrong. Reading over when I'm not completely tired I see that pand is actually for your computer to connect to the internet, not your phone connecting to the internet.

Can somebody help me do the opposite :) I'm guessing I need to use dund in this case?

---

### Post by johnnybeem on 2008-06-26
Ugh, alright well this is a one man conversation so far :)

Found this tutorial: [https://help.ubuntu.com/community/PalmBluetoothHowto](https://help.ubuntu.com/community/PalmBluetoothHowto)

and it worked great. The first time I did it. Had internet access and everything.

I restarted, then followed the directions again (because obviously everything was reset on the reboot). Now my palm just hangs at "Initializing", then quits after 30 sec - 1 minute. Somebody's gotta know how this works. So frustrating :mad:

---

### Post by johnnybeem on 2008-06-30
After trying a million and one things... This is what worked:

1) Restarted the computer
2) Moved the bluetooth dongle to another USB port
3) Ran an "hcitool scan" and "hcitool info"
4) Might have restarted bluetooth, I forget

Tried connecting from the Palm again, and it worked. Don't know why, but it's working and I'm not touching it :)

---

