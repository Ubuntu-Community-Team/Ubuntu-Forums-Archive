---
title: "Manually Add Network Adaptor"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by menawollas on 2006-08-28
Hi,

I asked this question in the beginners forum, but had no replies.

Ubuntu was working fine (triple boot XP/Ubuntu/Kubuntu). I have a wireless network, and everything was fine.

Ubuntu notified me of updates, I downloaded them all, rebooted and since then, no network connection hence no internet. XP and Kubuntu work fine (I have not updated Kubuntu yet!).

ath0 is in /etc/network/interfaces, yet if I go to system/networking it is not shown. 

If I try to do ifup -v -i /etc/network/interfaces -a  then I get the message that the device is not found. (ath0). Doing lspci doesn't show it (at least I think it doesn't).

So, why did it disappear, and, more importantly, how can I get it back without restoring or rebuilding (not an issue, but I'd like to know which files I should be looking in, and what commands to issue, to get this working again).

Thanks

---

### Post by mpvano on 2006-08-28
Did you install your own driver or did you use one built in to Ubuntu?

If you installed your own driver from a non-Ubuntu repository or from a source file that you built, you need to rebuild and reinstall it every time the kernel or kernel drivers is updated.

Most drivers need to exactly match the kernel version build and to do this, they need to either be built at the same time as the kernel, or need to be built with matching kernel headers and symbols.

If this is NOT what you did, I'd try the following:

run the command

sudo iwconfig

and see what it reports. If your card shows up in the output of this command as having wireless support, it's possible its name has changed.

I believe that one fairly recent update changed (corrected?) a problem with the way wireless devices were being named - with the unfortunate result of changing some existing names.

If this is your problem, you can correct it either by reconfiguring the card under its new name, or by editing the file called "/etc/iftab" to list the card's old name along with its MAC address (you can find this out with the  "ifconfig" command). Try

man iftab

for more info....

hope one of these suggestions helps...

Mario

---

### Post by menawollas on 2006-08-28
It was detected and installed when I installed Ubuntu.

Will try waht you said, when I get a spare half hour

Thanks.

---

