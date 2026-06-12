---
title: "IPv6 not diabling, slow Internet and Synaptic"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by Enil8 on 2006-07-25
My internet has been slow ever since I installed Ubuntu 6.06. Synaptic doesn't download packages in a decent amout of time, the speed is almost always unknown. I modified the /etc/modprobe.d/aliases like the other threads said, but it still gives me an IPv6 address when I type ifconfig. When I push Ctrl+Alt+F1 to get out of X and to a prompt, it keeps repeating irq 12: nobody cared and some other info and my system gets slow because it keeps requesting about once every second. Is this because of the IPv6 or is there something else w/ my BIOS settings or what?

Thanks much!!!

---

### Post by CVDpr on 2006-07-25
Yep thats Question everyboy ask. but this "ubuntu-users" dont know any answers to this ipv6 issues. I'm still waiting for my answers also.

---

### Post by Dev05 on 2006-07-25
[COLOR=Black]The modprobe thing worked for me. Anyway, just to disable it in Firefox, type in the address bar "about:config". Then filter "ipv6". There should appear just one boolean key. Double-Click it to set it to true. That should disable ipv6 at least for Firefox. Just in case you were doing it wrong, open the [/COLOR]/etc/modporbe.d/aliases [COLOR=Black]file and add these three lines:
[/COLOR] alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
[COLOR=Black]And comment the original:
[/COLOR]alias net-pf-10 ipv6
[COLOR=Black]like
[/COLOR] #alias net-pf-10 ipv6
[COLOR=Black]
 I hope that will work.[/COLOR]

---

### Post by blitzd on 2006-07-25
> **Dev05 said:**
> [COLOR=Black]The modprobe thing worked for me. Anyway, just to disable it in Firefox, type in the address bar "about:config". Then filter "ipv6". There should appear just one boolean key. Double-Click it to set it to true. That should disable ipv6 at least for Firefox. Just in case you were doing it wrong, open the [/COLOR]/etc/modporbe.d/aliases [COLOR=Black]file and add these three lines:
[/COLOR] alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
[COLOR=Black]And comment the original:
[/COLOR]alias net-pf-10 ipv6
[COLOR=Black]like
[/COLOR] #alias net-pf-10 ipv6
[COLOR=Black]
 I hope that will work.[/COLOR]

Actually that didn't work for me in 6.06. I think that fix was specific to 5.10.

What I found that did work (which was posted somewhere in a thread in these forums):

Create a file in /etc/modprobe.d called blacklist-ipv6
```
sudo nano -w /etc/modprobe.d/blacklist-ipv6
```
The file should contain something like this:
```
# Disable IPv6
blacklist ipv6
```
Next reboot, when you're up again if you do:
```
lsmod | grep ipv6
```
...you should not see the module loaded. Same for any IPv6 addresses when running ifconfig

Coincidentally on my first two installs of 6.06 I ran into this problem (and this fixed it), but on the third (that I am now using) I didn't. I have no idea what has changed other than the machine had SLED 10 and Gentoo on it in between installs.

Edit: If you are seeing a message like 'irq 12: nobody cared!' you most likely have an IRQ conflict on your system. Check in BIOS to see if you have a setting like 'Plug and Play OS' set to Yes - and if so switch it to No. Be aware that can have an effect on any other OS you may run on your system as well though. Make sure any important data is backed up and all that before you go changing BIOS settings, even if it is easy to change them back. It may not fix the problem either, there can be many reasons for IRQ conflicts - PnP OS being set when it's not a PnP OS, hardware that doesn't play nicely, etc. It's worth a try though.

---

### Post by Enil8 on 2006-07-25
blitzd was right about the blacklist-ipv6 file, that got rid of ipv6, but you were also correct that that's not going to help if i'm getting the irq 12: nobody cared message. I currently have PnP OS set to no, so that's good, but something else must be causing that problem.

---

### Post by blitzd on 2006-07-26
> **Enil8 said:**
> blitzd was right about the blacklist-ipv6 file, that got rid of ipv6, but you were also correct that that's not going to help if i'm getting the irq 12: nobody cared message. I currently have PnP OS set to no, so that's good, but something else must be causing that problem.

A few other things you could try are: 

Disabling any built in hardware that you aren't using, like parellel ports or serial ports - those all take up IRQ resources.

Disconnect any external peripherals one by one to try and narrow down which devices are involved in the conflict.

Post the full details of the error message, which may also give insight into what devices are involved in the conflict.

And.. Do you have any older cards in the system? Plenty of ISA cards require you to configure the IRQ resources they use by jumper.

---

