---
title: "cant get online...?"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by ~Dave on 2007-02-25
ok i installed ubuntu and now try to get online ... and i've been sitting here for at least 3-4 hours trying to figure it out. OK now my wireless card is a Dell wireless 1350 and my computer that it is on is a Dell inspirion 1200 *i am currently on my desktop computer*

---

### Post by spd106 on 2007-02-25
Hi,
I suggest that you search the forum for a guide/howto for broadcom wifi cards. Maybe also check out this wiki page for ndiswrapper [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

You may find it useful to find the chipset revision by opening a terminal and entering this command
```
lspci
```

---

### Post by ~Dave on 2007-02-25
i dont have that type if wireless card though... i have a dell one

---

### Post by spd106 on 2007-02-25
AFAIK all Dell truemobile cards use Broadcom chipsets. 

What can I say, they're cheap and they work on Windows.

To check for certain try this command
```
sudo lshw -class network
```

---

### Post by ~Dave on 2007-02-25
ok, where do i put the command?

---

### Post by spd106 on 2007-02-25
Applications -> Accessories -> Terminal, you will be required to enter your password afterwards. This command doesn't need root privileges to work, but it does complain if you don't.

Also maybe have a look at this wiki page [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDell](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDell)

---

### Post by ~Dave on 2007-02-25
ok i'm there and typed that all in now what?

---

