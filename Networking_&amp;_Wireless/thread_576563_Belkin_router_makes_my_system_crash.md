---
title: "Belkin router makes my system crash"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by dannyboy2k on 2007-10-15
I've just purchased a shiny new Belkin N1 router and have a Belkin G+ Mimo card in my ACER laptop.

I've set the router up correctly and it works fine in Windows XP (I've a dual boot system). But when I try to connect to the router using Ubuntu (Feisty) the system stalls and won't move again. If I say that it is an open system it won't connect and if I say it has a shared passphrase it just stalls.

Like I say, the system works just fine in Windows so it can't be a hardware fault and Ubuntu connects to other wireless networks just lovely. So what's going on?

Anybody have any ideas?:confused:

---

### Post by Lambert on 2007-10-15
What card model # is it and can you post terminal out put from following commands.

```

sudo lshw
sudo lspci -nn
dmesg

```

You can try shortening the output by running the command this way

```

sudo lshw -C network

```

If you can run dmesg after trying to connect we're looking for the last few lines related to the action of trying to connect.

---

