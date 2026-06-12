---
title: "Can't install &quot;nmtui&quot; a nice WiFi command line setup."
date: 2016-01-13
forum: Networking &amp; Wireless
---

### Post by Raymond Day on 2016-01-13
There is a neat command line WiFi command that I seen is built in to the $9 chip it's "nmtui" I like it on my main server. I did  **apt-get install network-manager** but it did not install the /usr/bin/nmtui I copied it from the $9 chip to /usr/bin on my X86 but because the chip is a ARM it says Exec format error.

Any one know how I would install the nmtui ? Looked on Google just can't find it out.

looking more I thought this would work.

```
root@rayday:~# apt-get install NetworkManager-tui
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package NetworkManager-tui
root@rayday:~#
```

On the chip if you run it at the top says NetworkManager TUI

But that did not work.

It's a real easy way to set up WiFi on the command line. But just can't install it on a X86 CPU I guess. Has any one got it to work on there X86?

-Raymond Day

---

### Post by chili555 on 2016-01-13
I have Network Manager installed on my laptop. I see:> chili@T410:~$ locate nmtui
/usr/bin/nmtui
/usr/bin/nmtui-connect
/usr/bin/nmtui-edit
/usr/bin/nmtui-hostname
/usr/share/man/man1/nmtui-connect.1.gz
/usr/share/man/man1/nmtui-edit.1.gz
/usr/share/man/man1/nmtui-hostname.1.gz
/usr/share/man/man1/nmtui.1.gzIf you are trying to get NM going on a server, that is, with no desktop environment, it will not work as NM requires a desktop.

Please clarify your question. What are you trying to accomplish?

---

### Post by Raymond Day on 2016-01-15
If I do:

locate nmtui it comes right back to the command line does not show any thing.

I had to reload this and it does have a desktop now. But I mostly use it as a headless server.

Still have not found out how to get nmtui to work on it.

-Raymond Day

---

### Post by chili555 on 2016-01-15
> But I mostly use it as a headless server.

Still have not found out how to get nmtui to work on it.As I explained above, it won't.

The usual way to configure wireless on a server is here: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

---

