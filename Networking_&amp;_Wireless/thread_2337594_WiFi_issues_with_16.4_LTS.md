---
title: "WiFi issues with 16.4 LTS"
date: 2016-09-19
forum: Networking &amp; Wireless
---

### Post by 7dEfOk4AgU on 2016-09-19
Following my post here  [https://ubuntuforums.org/showthread.php?t=2337331](https://ubuntuforums.org/showthread.php?t=2337331)

I am currently managing a project to deploy 150 desktops and 100 laptops. The laptops have similar WiFi chips to these and Ubuntu is being troublesome.

I do not have the machines at my office but my support team have advised they are unable to get the drivers/software to load via the extra software and proprietary software. They have advised me the chips in the Desktop units
are Broadcom BCM43142 802.11 bgn. They will have a look at one of the Notebooks and send me the details.

Are the issues with WiFi and Ubuntu wide spread or are they specific to card types? Do I need to rethink the Distribution?

I am aware of support available from Canonical but this is just at POC stage.

---

### Post by occasionalbicyclist on 2016-09-20
If you can't get the drivers to load at all, then you may need to ensure "Secure Boot" is disabled in the BIOS/firmware. More info can be found in this askubuntu response: [http://askubuntu.com/a/762055](http://askubuntu.com/a/762055)

---

### Post by 7dEfOk4AgU on 2016-09-20
Thanks for that, I am sure this would have been checked, I will email the team and ask them.

---

### Post by wildmanne39 on 2016-09-20
There is no way we can help you without more information, please have your team run the wireless script and email you the file it creates as previous mentioned in the other thread.

---

### Post by 7dEfOk4AgU on 2016-09-20
@Wild Man thanks for that. I will ask them but it will take a while, we will also need to check the NDA regarding the info

---

### Post by 7dEfOk4AgU on 2016-09-21
Problem solved, well for the Desktop units that is, I decided to get the team to swap out the Wifi NIC's in all the PC's. Will address the issues with the Notebooks now.

---

### Post by 7dEfOk4AgU on 2016-09-22
This thread can be marked as 'resolved' After a meeting with my engineers I have recommended to my client that they stop the planned rollout of Linux in particular Ubuntu, I have recommended that their systems be upgraded to Windows 10 and the new machines released with Windows 10. It is a shame that this decision has been forced on us as I would have liked the Linux option to be successful. The risks and issues are such that Linux is just not viable.

---

