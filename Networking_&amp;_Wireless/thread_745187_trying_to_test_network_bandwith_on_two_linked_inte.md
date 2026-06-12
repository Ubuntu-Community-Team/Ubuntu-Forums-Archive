---
title: "trying to test network bandwith on two linked interfaces"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by gm04030276 on 2008-04-04
Hey, I have 3 computer's all the same with with two aggregated Gigabit ethernet links for a theoretical 250MB/s throughput. I want to test just how fast it will actually go but naturally the hard drives won't hit near that to try just moving large files so i was trying this...

create smb share of user folder on node 3 and create a symbolic link to /dev/null
on node two, mount share
then use dd if=/dev/zero of=/media/gm/null

I see no reason why this shouldn't just dump huge amounts of null characters across the network to the null device on the other node but it doesn't seem to do anything, i get a quick blink on the link activity links when i first hit enter to run the command but no activity but the normal standby activity after that.

anyone know why this isn't working and/or something else i could try to test my bandwidth?
(ps tried using NFS before smb but that didn't work either)

---

### Post by spd106 on 2008-04-06
If you have a reasonable amount of memory then a ramdisk might work instead or you could always try iperf, it's in the universe repo.

---

