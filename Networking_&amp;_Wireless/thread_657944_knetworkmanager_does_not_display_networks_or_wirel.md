---
title: "knetworkmanager does not display networks or wireless bars anymore"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by kaens on 2008-01-04
Well this is odd. I'm running gutsy on a Thinkpad R61e, Atheros drivers through ndiswrapper.

Anyhow, knetworkmanager was running fine, displaying a list of available wireless networks, letting me connect, so on and so forth.

Then, I was clicking through the config options, noticed that my wireless card didn't have an option for pulling the address set, set it to dhcp (which it should be using anyhow, right?), and now knetworkmanager does not display networks anymore, and I can't reset the config (or rather I don't know how to off the top of my head).

I can still connect to any ESSID that I know the name of, it's just not displaying the wireless strength bars or network names anymore?

Is there a config file I should delete and have auto-generated again? Or something? Anyone know what's up, or how this could have happened in the first place? I'm baffled.

---

### Post by Sir Chasm on 2008-01-04
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+source/knetworkmanager/+question/8140](https://answers.launchpad.net/ubuntu/+source/knetworkmanager/+question/8140) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+source/knetworkmanager/+question/8140](https://answers.launchpad.net/ubuntu/+source/knetworkmanager/+question/8140) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yeah, basically KNetworkManager is crap - as soon as you try "Manual Configuration", wireless will never work for you again. Handy, eh?

Anyway, you can get it back to auto-config by doing:

```
sudo nano /etc/network/interfaces
```

(might want to back up that file first)

and then comment out (or delete) all the lines except:

```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

```

After that, restart KDE, and it should be back to normal.

I found this solution here: [https://answers.launchpad.net/ubuntu/+source/knetworkmanager/+question/8140](https://answers.launchpad.net/ubuntu/+source/knetworkmanager/+question/8140)

---

### Post by kaens on 2008-01-04
Thanks for the reply, I'll try it here in a minute.

But what the crap? Why would this fix this? Does knetworkmanager write to the file when you hit "manually configure" or something?

Eh, I'll dive into the source for it later and see if I can't find out what's going on, or perhaps just add a "click here to work around this stupid crap" button....

---

