---
title: "RTL8723BE dropping connection on Ubuntu 15"
date: 2015-07-18
forum: Networking &amp; Wireless
---

### Post by lorenzo24 on 2015-07-18
Hi,

that is happening since I first installed Ubuntu on my new machine.

I tried what is posted here: [http://ubuntuforums.org/showthread.php?t=2261702](http://ubuntuforums.org/showthread.php?t=2261702)
And I cannot find a .conf file to modify as suggested in the Ubuntu website.

Please find attached the output of the script suggested in the sticked thread.

[ATTACH]263281[/ATTACH]

Are there other things I can try?

Thank you in advance,
Lorenzo

---

### Post by praseodym on 2015-07-18
Hi,

those commands create that file. Just run them.

---

### Post by lorenzo24 on 2015-07-19
> **praseodym said:**
> Hi,

those commands create that file. Just run them.

Thank you very much for the answer and sorry for the incomplete report.

The command:
sudo modprobe rtl823be

Gives me as output:
modprobe: FATAL: Module rtl823be not found.

And if I look into the folder I cannot find the file.

---

### Post by praseodym on 2015-07-19
It is rtl8[COLOR="#FF0000"]7[/COLOR]23be. Lets try

```
sudo touch /etc/modprobe.d/rtl8723be.conf
echo "options rtl8723be fwlps=0 swlps=0" sudo tee -a /etc/mo[COLOR="#FF0000"]d[/COLOR]probe.d/rtl8723be.conf
```
There is a typo in that link

---

### Post by lorenzo24 on 2015-07-20
Thank you very much for the answer.
It seems like it's working!

I gave your lines to the console and an empty [COLOR=#000000][FONT=Ubuntu Mono]/etc/mo[/FONT][/COLOR][COLOR=#FF0000][FONT=Ubuntu Mono]d[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]probe.d/rtl8723be.conf file appeared, with no changes in the problem.
Then i edited it (sudo gedit) putting "[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]options rtl8723be fwlps=0 swlps=0[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]" and now it has been hours without disconnection!

Thank you very much![/FONT][/COLOR]

---

