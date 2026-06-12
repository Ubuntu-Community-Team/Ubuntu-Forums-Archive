---
title: "&quot;The Interface does not exist&quot; after upgrade, but only one user affected"
date: 2016-05-14
forum: Networking &amp; Wireless
---

### Post by rdh61 on 2016-05-14
Hi,

I recently upgraded Lubuntu 14.04 LTS to 16.04 LTS. As the main user, I can connect to the Internet with a wired connection. However, the second user (who has all privileges) cannot. The networking icon (which I note is different from mine) carries a red exclamation mark. If I click on it and then click "configure", I am told: "The Interface does not exist. Check that it is correctly typed and is supported by your system."

Any help gratefully received.

---

### Post by rdh61 on 2016-05-14
OK, I should have used my brain before posting. After clicking "Configure" all I had to do was to change "eth0" to "enp1s5" in the drop down menu. Solved.

---

