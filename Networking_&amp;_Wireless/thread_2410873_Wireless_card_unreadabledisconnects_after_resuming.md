---
title: "Wireless card unreadable/disconnects after resuming from suspend on Dell XPS 13 9360"
date: 2019-01-21
forum: Networking &amp; Wireless
---

### Post by j.c on 2019-01-21
Hi, all. 
I am currently on Ubuntu 18.10, GNOME 3.30. 
Whenever my laptop (Dell XPS 13 9360) goes into sleep mode, it sometimes cannot read / connect to the wireless card (Killer 1535 AC) once it wakes back up. 
Usually, this can require a restart but on occasion even that does not help.
'sudo systemctl restart network-manager' does not work, either.
The card works fine, otherwise.

Typically, I'm able to solve the problem by putting the laptop to sleep again and then waking it up, but this succeeding isn't consistent. 
I was told that this was a problem where PCI device power levels not being reset correctly after resuming from suspend. Here is the bugzilla link detailing this: 
[https://bugzilla.kernel.org/show_bug.cgi?id=201469](https://bugzilla.kernel.org/show_bug.cgi?id=201469)

On occasion, when waking back up and being unable to find the wireless card, GNOME will display a notification on the lock screen preview titled "Power" with a black-and-white icon with a cross inside a circle. I am never able to read the notification when I log in, though. This leads me to believe that I am suffering from the bug linked above, but it describes the iwlwifi driver rather than the ath10k driver which my card needs, so I am not ruling out that it is possibly something else.

Is there any short-term (or even definite) solution to this problem, such as a kernel upgrade (not exactly short-term haha) / a modprobe command / etc.? Has anyone else experienced this problem?

Thanks for your help!

Extra details, if you need them (I am happy to provide any extra details you might need.):
Linux Kernel: 4.18.0-13-generic
Network Controller, as revealed by 'lspci': Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
Dell XPS BIOS: 2.10.0

---

