---
title: "Weird 82547EI problems"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by ignem on 2008-03-30
The system recognizes my Intel 82547EI network card (e1000 driver) and I can do basic networking with it (ping/traceroute), but when I try to download anything I only get about 4k of data then the transfer hangs.

I have tried using different download programs (wget and ftp) and different servers to get data from. I get the same problem no matter how I do it. I even tried upgrading the driver version to the latest (7.6.15.5-NAPI) but it didn't help.

Other computers on the same network does not have this program and the computer did not have this problem when it had WinXP installed on it.

I have searched the forums and googled for hours but have not found anyone with the same problem as me. Anyone have any ideas how to get around this?

---

### Post by ignem on 2008-03-30
Another weird thing with this problem is that I have no problem scp:ing large files to the problematic computer. So it looks like I have only problem if the file transfer starts from the problematic computer itself.

---

