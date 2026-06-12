---
title: "Netgear WG311 configuration"
date: 2005-07-04
forum: Networking &amp; Wireless
---

### Post by lowriderdog37 on 2005-07-04
OK, I am brand spanking new to Linux. I just installed it today, and I cannot get my WG311 wireless network adapter to find my home network. I have tried to set up with DCHP, as well as setting up a static channel on Ubuntu and the wireless router.

The OS has identified the card, and says that the network connection is active, but always says that I  am denied access when trying to access my router.  When I try to find google, it simply says site not found.

I know next to nothing about Linux, learning as I go. So please be gentle with any replies. I know the system works, I am using it as I am writing this. I have my computer dual booting with XP. I have just decided that I hate windows, and I don't want to use it anymore. Any help would be appreciated.

JS

---

### Post by darrell on 2005-07-05
please post the output of 
```
ifconfig
```
and
```
iwconfig
```

---

### Post by Andre N. on 2005-07-05
I recently had this problem too. I solved it be setting up ndiswrapper by following this guide: [http://ubuntuforums.org/showthread.php?t=45876](http://ubuntuforums.org/showthread.php?t=45876)

I skipped the step in which you edited the interfaces file though.

I hope this helps.

---

