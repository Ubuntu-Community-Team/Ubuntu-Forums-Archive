---
title: "Modems supported in Hardy"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by sternkanz on 2008-04-27
Ok. I am fixing somebody's computer for them and they asked to get ubuntu on it for them as its an old computer and they only want to use it for web applications.

The modem he has installed is apparently only supported under ubuntu with kernel versions of 2.4.

I've tried going to linmodems.org and they have no solution.

My question is, what modem WILL work under hardy? Does anyone actually use a modem, using linmodems drivers or whatever, but actually get it to work under hardy?

Thanks,

Stern

---

### Post by sternkanz on 2008-04-28
I've borrowed a modem from a friend, and it appears that ubuntu detects it as such. In "System -> Preferences -> System Profiler and Benchmark -> Devices -> PCI Devices" it shows up as "Communications Controller - Intel Corporation 536EP Data Fax Modem".

I thought that sounded quite promising. I searched on the forums here, and got a link to this page:
[https://help.ubuntu.com/community/DialupModemHowto/Intel536EP]("https://help.ubuntu.com/community/DialupModemHowto/Intel536EP")

Now I didn't want to plunge head long into this and just try out the first drivers that presented themselves. I was wondering if there's anyone out there who might have at least managed to install this in Gutsy without problems? Or, considering what it says on the above list that I linked to, would Gutsy or Hardy even need drivers for it?

**Edit: I just followed the driver links that the above website gives, and checked the list of downloads. [Here]("http://linmodems.technion.ac.il/packages/Intel/Philippe.Vouters/"). There are updated drivers on this site, I was wondering if any has experience with them and if they are intended for use with Hardy?**

Thanks,

Stern

---

### Post by sternkanz on 2008-04-28
I've decided to attempt installing the modem as this is a fresh install so even if I do break something I can always reinstall easily. Everything has worked perfectly so far, following this page:
[https://help.ubuntu.com/community/DialupModemHowto/Intel536EP]("https://help.ubuntu.com/community/DialupModemHowto/Intel536EP")

However, once I get to the "Setting up the modem" section near the end of the page I try to enter the command:
sudo echo -e '# Intelmodem536ep\nKERNEL=="536ep0", SYMLINK=="modem"' >> /etc/udev/rules.d/10-local.rules

I get:
bash: /etc/udev/rules.d/10-local.rules: Permission denied

I can't seem to get past this step. I looked in the /etc/udev/rules.d/ folder and I can't actually see a file called '10-local.rules'.

Can anyone help with this? Thanks!

---

