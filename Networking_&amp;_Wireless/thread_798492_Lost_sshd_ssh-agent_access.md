---
title: "Lost sshd ssh-agent access?"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by neilblue on 2008-05-18
Hello,

I have upgraded one machine on my network to 8.04, and since the upgrade I can no longer use ssh-agent to log onto the 8.04 machine without a password. Is there something I should check or probably missed during the upgrade?

Thanks
Neil

---

### Post by neil.the.blue on 2008-05-18
OK a bit more information,

I am trying to connect to the 8.04 machine from a backup server running rsnapshot. From the backup machine I can ssh to other machines using the ssh-agent. From other machines I can also ssh to the 8.04 machine using ssh-agent. But from the backup machine I can't ssh to the 8.04 machine with ssh-agent. So maybe this isn't an update problem, but I am really confused how this can happen, any ideas?

Thanks
Neil

---

### Post by neil.the.blue on 2008-05-18
OK, I found the problem. It was due to a security update patch that was rejecting keys generated with an old bad random number seed :)

---

