---
title: "Configure WEP Transmission Key in Gutsy"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by Kardolf on 2007-10-10
I am running Gutsy on a laptop and trying to configure my wireless. However, it doesn't seem to like the fact that I use key 3 instead of key 1. I know that the wireless is working, because if I switch to key 1, I connect fine. However, I'd rather not have to reconfigure every laptop that connects to my AP, so I'd like to get key 3 to work. I have tried to do the interfaces edit, but that didn't ever let me connect. Am I doing something wrong, is Kubutnu just picky, or should I just resign myself to editing every other machine on my network?

---

### Post by kevdog on 2007-10-10
Take a look at this post:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Add the following line somewhere before the dhclient line:
sudo iwconfig <interface> key 3

---

### Post by Kardolf on 2007-10-10
:confused: Thanks. Looked at that post several times and never noticed that. Guess I need some more sleep....

---

