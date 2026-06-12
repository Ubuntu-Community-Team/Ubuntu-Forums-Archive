---
title: "edgy not finding wireless networks"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by jamaas on 2006-10-29
I recently upgraded my dell d410 from dapper to edgy, and it does find my own home wireless network, as it used to. However, now the wireless settings device will not find any other wireless networks, ones that I know are there and have used before, when I am somewhere else.  Is there a bug or do I need to change something?  I used to click on the Properties>network name buttons and it would show me all that were available.  Now all I get is a grey line below the name box, with no names at all, not even the home network I'm currently using?

All advice welcome, thanks.

Jim

---

### Post by Dinerty on 2006-10-29
> **jamaas said:**
> I recently upgraded my dell d410 from dapper to edgy, and it does find my own home wireless network, as it used to. However, now the wireless settings device will not find any other wireless networks, ones that I know are there and have used before, when I am somewhere else.  Is there a bug or do I need to change something?  I used to click on the Properties>network name buttons and it would show me all that were available.  Now all I get is a grey line below the name box, with no names at all, not even the home network I'm currently using?

All advice welcome, thanks.

Jim

Have excatly the same problem mate, all you have to do is enter the SSID of the network (Basically the network name), if you are not sure of it, log into your router and browse, should not be to hard to find.

---

### Post by jamaas on 2006-10-29
Thanks Dinerty,

It works fine at home because it was configured that way by default, its when I'm out and don't know the ssid of the network, particularly hotspots that it becomes frustrating.... used to work, why not now with an ... upgrade ...?

Thanks

Jim

---

### Post by Dinerty on 2006-10-29
Yes I can understand your frustration with the ssid, espically in hotspots and having to find it out.

Not sure why they removed this feature out, hopefully some updates i the near future bring it back

---

### Post by featherking on 2006-10-29
have either of you tried using network manager for you wireless? It seems to do what your asking, it places a little icon by the clock and automatically connects to an access point youve been to before, but if you click on it, it will show any available access points. You might want to check it out if you havent, i like it. Also you can easily switch to a wired connection by clicking on the icon too. To install

```
sudo apt-get install network-manager-gnome
```

Or you can install it from synaptic as well.

---

### Post by Dinerty on 2006-10-29
> **featherking said:**
> have either of you tried using network manager for you wireless? It seems to do what your asking, it places a little icon by the clock and automatically connects to an access point youve been to before, but if you click on it, it will show any available access points. You might want to check it out if you havent, i like it. Also you can easily switch to a wired connection by clicking on the icon too. To install

```
sudo apt-get install network-manager-gnome
```

Or you can install it from synaptic as well.

Thanks for this I will give it a try

---

### Post by lagartoflojo on 2006-10-29
You can also try wifi-radar (it's also in the repositories).

---

