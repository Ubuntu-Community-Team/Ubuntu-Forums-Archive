---
title: "IP Renewal"
date: 2005-06-15
forum: Networking &amp; Wireless
---

### Post by vtechstu on 2005-06-15
Everytime i boot my computer i have to red modprobe ndiswrapper, and then doing sudo dhclient wlan0.  This works, but I'de like to know if theres a way to set up the boot so it loads all of this on its own. 

Also, the IP seems to run out after so many hundred thousand seconds.  Anyway to get it to auto request that also? 

Thanks for the support!

---

### Post by imightbegiant on 2005-06-16
Adding ndiswrapper to /etc/modules should load it at boot. Not sure what you mean by "red" though.
 
> Also, the IP seems to run out after so many hundred thousand seconds. Anyway to get it to auto request that also?  

There might be a configuation file somewhere to set it longer, but you can always run dhclient as a cron job every so often. check out [http://ubuntuforums.org/showthread.php?t=2543](http://ubuntuforums.org/showthread.php?t=2543) for setting that up.

---

### Post by vtechstu on 2005-06-16
Sorry, "red" was suppose to be "re-do".  Thanks for your reply.  How do i add ndiswrapper to that dir.?  Thanks

---

### Post by imightbegiant on 2005-06-17
[QUOTE=vtechstu]Sorry, "red" was suppose to be "re-do".  Thanks for your reply.  How do i add ndiswrapper to that dir.?  Thanks[/QUOTE]
 /etc/modules is a text file not a directory. Just open it up with an editor and add a line at the bottom for ndiswrapper.

---

### Post by vtechstu on 2005-06-17
just put "ndiswrapper -m" ?  Thanks.

---

