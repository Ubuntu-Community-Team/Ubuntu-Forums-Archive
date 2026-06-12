---
title: "Ralink 5390 wireless chip in Asus  laptop not working"
date: 2019-04-23
forum: Networking &amp; Wireless
---

### Post by stanbrow on 2019-04-23
data.I am having problems getting the Ralink 5390 wireless chip in my Asus laptop working.

I found the script that some helpful person wrote to query and  aquire all the pertinant data. It uploaded this data to   [https://paste/ubuntu.com/p/K78sdgVdS6/](https://paste/ubuntu.com/p/K78sdgVdS6/)

Can anyone sugest what to try to get this working?

Any sugestions will be grealy appreciated.

---

### Post by chili555 on 2019-04-23
The correct link is this: [https://paste.ubuntu.com/p/K78sdgVdS6/](https://paste.ubuntu.com/p/K78sdgVdS6/)

---

### Post by stanbrow on 2019-04-23
Thnak you for fixing my mistake.
is by hand 
Cut and paste was not working, so I tried to do this by hand :=)

---

### Post by stanbrow on 2019-04-23
for the typos in these posts. I was in a place where I had to use the touchpad, and it was  acting weird.

---

### Post by stanbrow on 2019-04-23
Let me give a better description of the issue. The card is detected, and shows that locally available wirelesss access points. But when I tell it connect, it fails with a "Cannot authenticate". I have tried a number of different AP's, some of which do not require a password.

---

### Post by chili555 on 2019-04-23
Does the USB authenticate?

---

### Post by stanbrow on 2019-04-23
I am a little confused about the question about "the USB". I do have a USB based wireless adapter, and yes it authenticates to all the networks just fine. Having said that, I did not mention that in my post, so I am not certain that answers your question.

---

### Post by chili555 on 2019-04-23
Please open a terminal and do:

```
sudo -i
echo "options rt2800pci nohwcrypt=Y"  >  /etc/modprobe.d/rt2800pci.conf
exit
```Detach the USB wireless, reboot and tell us if there is any improvement.

---

### Post by stanbrow on 2019-04-23
FYI, that line was already in the file you named, with a 1 instead of a Y. Nevertheless, I changed it to a Y and rebooted. Same result. Here is a spinet of dmesg, if it helps.

At least I tried to attach  the file. Not certain it worked.

---

### Post by stanbrow on 2019-04-24
Think maybe I figured out the atachments.

---

### Post by chili555 on 2019-04-24
> FYI, that line was already in the file you named, with a 1 instead of a Y. Nevertheless, I changed it to a Y and rebooted. Same result.Let's try *without *the driver parameter in place, then.

```
sudo rm /etc/modprobe.d/rt2800pci.conf
```Detach the USB wireless, reboot and tell us if there is any change. If you can capture and post the relevant dmesg listings, that will be helpful.

---

