---
title: "The easiest way to install a bcm34xx card"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by wil313 on 2008-03-08
[size=5]**[COLOR="Red"]PLEASE NOTE:[/size] This is now outdated and will still work on feisty but will NOT work on Hardy.[/COLOR]**

[SIZE=4][COLOR=DarkRed]**Note:[/COLOR][/SIZE]
This was done on a Dell Inspirion 1200 with a dell 1350 card, actual turn out may depend.

I achieved wireless connection in three steps, if help is needed, please list computer type, which Ubuntu being used, and card type.

Good luck!
First, click on this link and open with any package manager. Allow for the package manager to install then move to the next step. [http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133)

Secondly, in Terminal enter:
sudo modprobe bcm43xx

Thirdly, in the same Terminal window enter (this step insures that your wireless card starts when computer is rebooted):
echo 'sudo modprobe bcm43xx' | sudo tee -a /etc/modules

---

