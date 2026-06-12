---
title: "Calling all rTorrent enthusiasts! SSH Tunneling Question"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by TheTaylorEffect on 2008-03-29
Hello everyone...

I've been running console based rTorrent on a headless 7.10 Server Edition for about 6 months now.

It has worked wonderfully! (I really can't say enough good things about rTorrent). 

But, lately I've become the victim of the Comcast "traffic shaping" campaign and I've noticed a VERY significant decrease in performance.

The suggestion on a lot of forums has been to use an SSH Tunnel with your BT client in order to skirt the snooping. 

I obtained a few  remote shell accounts, and spent yesterday afternoon familiarizing myself with its functionality mostly on an XP Machine, using Putty I  got the proxy working on Firefox

... and I've successfully connected to the remote shell account it with the my headless server using the:

```
ssh -D
```

command

Unfortunately, all of the tutorials I've found give instructions on how to configure a more robust client, like Azureus using its built in proxy support. 

Evidently rTorrent lacks this functionality (or if it has it, its not obvious to a novice like myself by from scrolling around the configuration file).

Do any of you rTorrent enthusiasts have a solution or an alternative suggestion? This is the first real issue I've encountered with rTorrent... and I'd hate to have to stop using it.

---

