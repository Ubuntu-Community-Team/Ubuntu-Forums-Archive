---
title: "ndisgtk can't unlock to configure"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by iansane on 2008-08-29
Hi,

I used the how to in hardy documentation to install ndiswrapper on AMD64.

I then opened wireless network manager and installed the inf file from my cd that came with netgear wg111 usb wireless dongle.

It shows the hardware is present but that's all.

The unlock button is greyed out when I click on configure and if I run in terminal it gives the error,

```
** (network-admin:9313): CRITICAL **: Unable to lookup session information for process '9313'

```

I noticed the process number changes each time. I guess that's normal?

Anyway, when I use the regular network admin, there's no wireless network available.

I also tried lshw -C network and it acts glitchy and then returns to prompt without displaying any info. When I use lsusb the wireless dongle shows up.

I tried also using -force-architecture to install 32 bit ndis since the only wireless driver I have is 32 bit. I tried other ones from netgear. None of them say if they are for 64 bit. I also tried the one in the ndis5 folder on the driver cd.

Same thing everytime no matter how I try to install.

Is there a known issue with hardy amd64 and ndis? I'd like to know before I keep trying. I've been trying for weeks.

Thanks

---

### Post by iansane on 2008-08-29
Sorry, I should add...

When I use iwconfig it shows

```

lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by iansane on 2008-10-03
Made a lot of changes in the past few weeks and learned how to configure everything through terminal. Can still just use the nm console, to configure wired and wireless but I'm wondering is this problem with the wireless nm console a bug or is it something in my setup? If it's a bug will it eventually be fixed?

Like I said not a big deal cause I don't need it but still wondering about it.

Thanks

---

