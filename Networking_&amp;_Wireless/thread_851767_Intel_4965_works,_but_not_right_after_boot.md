---
title: "Intel 4965 works, but not right after boot"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by slavka012 on 2008-07-07
Sorry if this was discussed.... I searched and could not find anything.

When I boot the Ubuntu 8.04, I don't have my wireless network. But it is configured, and if I go to terminal and execute 

```
sudo ifdown wlan0
sudo ifup wlan0

```

the wireless network comes on.

What is going on?

Another question, is there functionality similar to the XP's network selection? I would like to have different network at work and at home to be able to connect automatically....

---

### Post by lisati on 2008-07-07
> **slavka012 said:**
> Sorry if this was discussed.... I searched and could not find anything.

When I boot the Ubuntu 8.04, I don't have my wireless network. But it is configured, and if I go to terminal and execute 

```
sudo ifdown wlan0
sudo ifup wlan0

```the wireless network comes on.

What is going on?
This *might* help: [http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2)

> **slavka012 said:**
> Another question, is there functionality similar to the XP's network selection? I would like to have different network at work and at home to be able to connect automatically....

The network manager has the ability to save different profiles that can be recalled according to where you are. When you're at, say, home, you can get your networking running, and click on the "save" icon on the network manager, which will prompt you for a name. Then at work, you do whatever tinkering is needed and save it. Leter you can call up the proper one, and click on the green check mark.

---

### Post by slavka012 on 2008-07-07
thanks, that worked...

I changed the 

```
/etc/init.d/networking restart
```

to 

```
/etc/init.d/networking restart&
```

That way restart goes in background, otherwise it makes boot much longer

---

