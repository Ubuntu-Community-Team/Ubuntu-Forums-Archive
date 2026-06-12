---
title: "I want to digress"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by mhanes_1 on 2011-05-28
When I was upgrading to 11.04 the upgrade stopped running at the step just prior to the cleaning phase. It appears that the system is intact, but my keyring runs twice for unlocking. Also, the system freezes up randomly. I want to go back to 10.10.

Can anyone help with suggestions which do not include a completely fresh install? I want to keep my home directory intact. This has become my primary computer system, and I am depending on it much more than my windows pc. 

:confused:

---

### Post by Hedgehog1 on 2011-05-28
If you have your data in a separate '/home' partition you can reinstall 10.00 over your 11.04 '/' partition; just be sure to not format the '/home' partition:

Run the install from the 10.10 LiveCD/LiveUSB, and when you get to here, Select the advanced install:

[IMG]http://img534.imageshack.us/img534/4196/02specifypartitons.png[/IMG]

Define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DOWNGRADE OR REINSTALL DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by mhanes_1 on 2011-05-28
Thanks for the help.

:)

---

