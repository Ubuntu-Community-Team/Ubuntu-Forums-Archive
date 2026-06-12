---
title: "Wireless problem from hell"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by High Chief on 2008-09-01
Ok so I installed wicd and had some success off and on with that, but then it quit working altogether. So I installed wicd 1.51 and it worked great until I shut down my computer. Now it will not obtain an IP address. I tried to setup a static IP and it says that it is connected, but no websites will load. I can access my router however(DNS problems???). 

I have no idea what else to do. I am running 64 bit Hardy and have a WEP encrypted network. Any help would be appreciated.

---

### Post by High Chief on 2008-09-01
bump pretty please?

---

### Post by caljohnsmith on 2008-09-01
What do you mean you can access your router? Can you get into its settings via your web browser, or can you just ping it? Also, what is the content of your /etc/resolv.conf file? Does it show a DNS IP address?

---

### Post by High Chief on 2008-09-01
I meant that I could access my router's settings via Firefox but that's not working now. Resolv.conf lists the address that I specified.

Edit: I installed a [64 bit madwifi driver]("http://ubuntuforums.org/showthread.php?t=816780") and everything is working (for the moment).

---

