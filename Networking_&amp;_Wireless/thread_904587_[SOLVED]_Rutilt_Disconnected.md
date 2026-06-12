---
title: "[SOLVED] Rutilt Disconnected"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by enderal on 2008-08-29
I installed Rutilt it worked but still had a weak signal so I uninstalled Network Manager as per another post.

Now Rutilt shows the network as being Disconnected.

Uh oh.

What do I do?

Thank you very much.

---

### Post by tangibleorange on 2008-08-29
you might need edit this file:
```
gksu gedit /etc/network/interfaces
```
and add these two lines:
```
auto wlan0
iface wlan0 inet dhcp
```

or replace wlan0 with your interface name. you can find your interface name with this command:

```
iwconfig
```

and its the one that has lots of text next to it...

---

### Post by snowpine on 2008-08-29
> **enderal said:**
> I installed Rutilt it worked but still had a weak signal so I uninstalled Network Manager as per another post.

Now Rutilt shows the network as being Disconnected.

Uh oh.

What do I do?

Thank you very much.

Hi Enderal, I was the one who recommended you try Rutilt in the other thread. Sorry if my post was misleading, but you didn't need to *uninstall *the default network manager, just like you wouldn't need to uninstall Firefox if you wanted to try Opera. :)

I hope Tangible Orange's instructions help you get back up and running. You should also check out all of the features in Rutilt because it is pretty easy to get a connection going using only the graphical interface. I found it to be very easy and intuitive to use. Good luck!

---

### Post by enderal on 2008-08-29
Thanks for your concern snowpine

Actually no problem. The install is only a couple days old so I uninstalled and reinstalled it and am now back up to speed and in much better condition.

I got the idea to uninstall Network manager from another post about installing Rutilt.

I still need to work on the wireless configuration but have probably had enough for today.

I'm lined (linuxed?) out on many of the basics now at least.

I did want to thank you for your reply to the other thread as well.

And thanks tangibleorange for your reply. I tried it and a few things but couldn't get anywhere so I took the easy way out.

I appreciate everyone's help!

---

### Post by snowpine on 2008-08-29
> **enderal said:**
> Thanks for your concern snowpine

Actually no problem. The install is only a couple days old so I uninstalled and reinstalled it and am now back up to speed and in much better condition.

I got the idea to uninstall Network manager from another post about installing Rutilt.

I still need to work on the wireless configuration but have probably had enough for today.

I'm lined (linuxed?) out on many of the basics now at least.

I did want to thank you for your reply to the other thread as well.

And thanks tangibleorange for your reply. I tried it and a few things but couldn't get anywhere so I took the easy way out.

I appreciate everyone's help!


Get a good night's sleep and better luck tomorrow! :)
Seriously, getting my wireless working was the hardest part of learning Linux for me. It's all been easy since then. It's easy to blame Linux, but really we should blame Linksys for not supporting us. Or, better yet, don't blame anyone, just look on it as a learning opportunity. 

ps When I'm troubleshooting problems like this, I keep a text file log of every step I take. That way, if I ever have to reinstall, I can easily retrace my steps.

---

### Post by tangibleorange on 2008-08-29
> **snowpine said:**
> Get a good night's sleep and better luck tomorrow! :)
Seriously, getting my wireless working was the hardest part of learning Linux for me. It's all been easy since then. It's easy to blame Linux, but really we should blame Linksys for not supporting us. Or, better yet, don't blame anyone, just look on it as a learning opportunity. 

ps When I'm troubleshooting problems like this, I keep a text file log of every step I take. That way, if I ever have to reinstall, I can easily retrace my steps.

yep same for me. and if you need any more help, just ask!

---

