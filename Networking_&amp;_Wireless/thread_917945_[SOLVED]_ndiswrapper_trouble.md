---
title: "[SOLVED] ndiswrapper trouble?"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by cyclonedr on 2008-09-12
Hi all,
  I recently got annoyed with having to "sudo modprobe ndiswrapper" every time I turned on my computer and then plug in my USB adapter.  So I did a little searching on the forums and found an article that said to have ubuntu automatically do that for me do the following in the terminal ```
echo ndiswrapper|sudo tee -a /etc/modules
```  Upon reboot, my wireless network failed to connect, and I tired the sudo modprobe ndiswrapper procedure, but to no avail, I can't get my internet working again.  How can I undo this?  Thanks for any suggestions.

---

### Post by cyclonedr on 2008-09-12
Ok, I solved it by entering sudo gedit /etc/modules in the terminal, then I simply deleted the entry for ndiswrapper, rebooted and all is well agian.

---

