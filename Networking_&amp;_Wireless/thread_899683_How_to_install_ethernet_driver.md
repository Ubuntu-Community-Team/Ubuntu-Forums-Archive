---
title: "How to install ethernet driver"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by Louis de Broglie on 2008-08-24
Hi,

I bought a dlink-530TX ethernet card. I have downloaded the latest linux driver from their site. Now when i tried to install the driver according to their instructions , I am stuck.

They instructed to :

1. Untar the file i downloaded
2. Then Compile it using make install

But the compilation process failed. Can anybody tell me why ? :)

P.S. My card is not detected by lspci.

---

### Post by dmizer on 2008-08-24
What kind of errors did you get when the compile exited?

---

### Post by cariboo on 2008-08-25
I just got one of those nics it uses the via-rhine driver, it should be auto detected and load on boot.

To check if the module is loaded, in a terminal type:

```
lsmod | grep via*
```

If it's not loaded, in a terminal type:

```
sudo modprobe via-rhine
```

Jim

---

### Post by Louis de Broglie on 2008-08-25
Hmm, I had a tplink ethernet adapter. I used to have internet problems . So I thought it's a adapter issue. But I am not sure where's the problem.:confused:

My old adapter works OK most of the time. But sometimes it does not work. Can you guys help me whether it's a adapter problem or, some settings issue ?:) If it can be resolved , then I will not mess around trying to install a new driver because I am not that expert and I don't want to mess up things right now.:lolflag:

---

### Post by cariboo on 2008-08-25
Just install your new nic it will be automagically detected, no having to install drivers or anything else, your settings for your previous card should work with the new one. One other thing to check is the network cable, an intermittent connection can act like the problem you described.

JIm

---

### Post by BLTicklemonster on 2009-11-09
My onboard lan stopped working, seems as though it's just not a well made jack, because if you move the plug slightly it connects briefly. Tried it with several plugs and it's the same with all of them, so it's got to be the jack on the board.

I put a pci card in, and no, it does not automagically load up.

Of course having no connection bugged the heck out of me this weekend, as the actual onboard finally stopped working totally. Green light, but no orange unless I jiggle the plug, but it won't stay on.

So how can I get drivers on it if it won't go online!!!???

---

