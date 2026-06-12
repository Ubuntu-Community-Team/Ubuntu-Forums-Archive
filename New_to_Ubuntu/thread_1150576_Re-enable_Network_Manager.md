---
title: "Re-enable Network Manager?"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by DenverMike on 2009-05-06
Somehow I managed to get /network/interfaces enabled on my Ubuntu installation, but I want to go back to NetworkManager.

Can anyone suggest a way to disable /network/interfaces and get back to Network Manager?

Thanks!
Denver Mike

---

### Post by nandemonai on 2009-05-06
> **DenverMike said:**
> Somehow I managed to get /network/interfaces enabled on my Ubuntu installation, but I want to go back to NetworkManager.

Can anyone suggest a way to disable /network/interfaces and get back to Network Manager?

Thanks!
Denver Mike

I assume you mean /etc/network/interfaces?

In terminal:

```
sudo mv /etc/network/interfaces /etc/network/interfaces.bak
```

Then logout and log back in, and reconfigure the connection in network manager.

Should do the trick.

---

### Post by DenverMike on 2009-05-06
Thanks!  I did have to reboot to get that to take effect, but it definitely did the trick.

So essentially by renaming the file, it disabled /etc/network/interfaces, right?

I've just started with Ubuntu yesterday -- it's finally Linux for the everyman!

---

### Post by nandemonai on 2009-05-06
> **DenverMike said:**
> Thanks!  I did have to reboot to get that to take effect, but it definitely did the trick.

So essentially by renaming the file, it disabled /etc/network/interfaces, right?

I've just started with Ubuntu yesterday -- it's finally Linux for the everyman!

Yups. Enjoy.

Rather than reboot then, for anyone having trouble with this in the future I neglected to think ahead (it's late here heh). A networking restart would have done it:

```
sudo /etc/init.d/networking restart
```

---

