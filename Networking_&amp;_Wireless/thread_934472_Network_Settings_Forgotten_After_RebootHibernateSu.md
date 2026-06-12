---
title: "Network Settings Forgotten After Reboot/Hibernate/Suspend"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by Kaseas on 2008-09-30
The network manager forgets my wireless settings. I know others have had this problem, but to date I haven't found a fix.

I'm running Hardy.

---

### Post by lisati on 2008-09-30
There's a known issue - I don't know if it has been fixed yet or if it's quite what you had in mind - where if you have security settings, you sometimes have to restart your networking on a reboot.

Details of a work-around can be found [here]("http://ubuntuforums.org/showpost.php?p=1351902&postcount=2")

---

### Post by Kaseas on 2008-09-30
Thanks, but this isn't the issue.

What I have is a WPA Personal encrypted network that doesn't broadcast the SSID, so after every boot, suspend, or hibernate, I have to go to the network manager, hit connect to other wireless network, etc.

Is there a way to write a script that would do that for me at logon?

---

### Post by Kaseas on 2008-09-30
Update: My /etc/network/interfaces file is intact after a reboot, it still contains the ssid and the tkip key, but for some reason I still have to re-connect manually each time.

---

### Post by Kaseas on 2008-09-30
Anyone else have this issue?

---

