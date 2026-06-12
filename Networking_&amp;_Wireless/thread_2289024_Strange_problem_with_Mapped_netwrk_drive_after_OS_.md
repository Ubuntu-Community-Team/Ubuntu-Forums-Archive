---
title: "Strange problem with Mapped netwrk drive after OS restore (via Clonezilla)"
date: 2015-07-31
forum: Networking &amp; Wireless
---

### Post by misc-daminator on 2015-07-31
Hello all,

**The short story:**
One of my drives on my ubuntu server is behaving oddly as a mapped network drive from my windows machines. I first get the message "Cannot connect all network drives", then if I click on it says, "An error has occurred while reconnecting S: to [path] Microsoft Windows Network: Not enough storage is available to process this command. This connection has not been restored."

However, if I then click onto a different drive, and then back to the S drive, everything is fine, and continues to be fine forever!

This problem happens, without fail, every time a reboot a windows machine that's connected to the ubuntu server.

It all worked fine before. There's plenty of space on the drive.

Any idea what's going on?

**The long story:**
If more info is needed ...

I have an Ubuntu machine in the garage (actually Mythbubtu) which acts as a server for the house.

I have other Mythbuntu computers and Windows machines that connect to this machine.

The windows machines all map a couple of network drives on the server machine. This has all been working fine for years.

A couple of weeks ago, I tried to update Mythbuntu on the server (first to 14.10, then to 15.04). Unfortunately, the update from 14.10 to 15.04 didn't work (some problem with MySQL that I need to come back to). Luckily, I had made a ClonZilla back up of the OS at each stage, so it was easy to roll back to the last fully working system.

Everything seems to be working perfectly in the current 14.10 system, except for mapped drives from my windows machines.

I have drives S: and T: mapped to the Ubuntu server on all of my windows machines.

The T: drive is still working fine on all of them.
The S: drive is acting the way that I described in the 'short story' description above.

This is exactly the same on all of the windows machines, so I'm sure it's something on the server that's not as it was.

Any ideas what can be going on?
It all works eventually. It's just annoying to have to click past error messages on every reboot.

Thanks,
Damian

PS I'm pretty inexperienced with the terminal, so if you need to see any logs or output from commands, please tell me what I need to be typing or where I need to be looking.

---

### Post by misc-daminator on 2015-08-05
Update:

This problem is also the same with an Ubuntu to Ubuntu connection.

If I try to connect to the drive, I get an error saying not enough memory.
If I click a different drive, and then do the exact same thing again, then everything is fine.

How can I get to the bottom of this?

Thanks,
Damian

---

### Post by misc-daminator on 2015-08-06
Anyone got any ideas on this ???

Maybe I shouldn't have put [mythbuntu] as the prefix. I don't think that the problem is with mythbuntu.

EDIT .. I just got rid of the prefix in the original post.

---

### Post by misc-daminator on 2015-09-03
Can on one help with this?

---

