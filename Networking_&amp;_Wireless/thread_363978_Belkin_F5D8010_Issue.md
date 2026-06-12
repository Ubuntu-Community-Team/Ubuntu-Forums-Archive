---
title: "Belkin F5D8010 Issue"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by SuperTeece on 2007-02-17
After searching the forums, I found my exact issue in a previous post located [[COLOR="Blue"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=259902&highlight=f5d8010") though no one ever responded to it.

I also installed the recommended driver from the wiki list using ndisgtk. It tells me that the hardware is present. In the terminal, ndiswrapper -l tells me:

```
Installed ndis drivers:
netani          driver present, hardware present
```

iwconfig states:

```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

System --> Admin --> Networking  does not show an entry for a wireless device. The card has no lights on.

If any more info is needed just let me know.

Thanks.

---

### Post by SuperTeece on 2007-02-18
so.... stumped? I don't understand what I am doing wrong here. I feel my question is pretty straight forward. I am sure it is just some simple step I am missing. Any ideas?

I apologize for the blatant bump, but how else can I get my question out there?

---

### Post by SuperTeece on 2007-02-18
I installed the driver for the onboard Broadcom card and I have the same exact issue. Am I missing an entry somewhere that tells the OS to use the card? Something like fstab is to storage devices? I remember when I was using Fedora core1 I had to make fstab entries to use an external USB hdd, is there something like that for PCI or networking devices?

---

### Post by justinmiller87 on 2008-03-02
Your card is an Airgo card. If you follow the link in my signature, it will give you an installation guide for the F5D8010.

Justin

---

