---
title: "Wireless problems"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by wyliga on 2008-09-23
Ok, well I have a few problems with my wireless card/drivers. First off most of the time ubuntu doesn't recognize my card at all. It's as if there's no card in the system at all. However I just turned my lappy on, and it said new drivers ready to be used or whatever and my wireless drivers were under the hardware drivers thing, just not enabled. I enabled them and the red light turned blue (always a good sign) and I was able to see the words "wireless networks"  under my network tab. It didn't show any networks, even though I know that there are at least 3 that are 100% in range, but that's a different issue.

I rebooted my machine, and my drivers no longer appear. The happy blue light has turned back to red and it's again as if I have no wireless card at all. Seriously what's up with that?

---

### Post by dub_u on 2008-09-23
What brand of wireless card do you have?

Please post the output of
```
sudo lshw -C network
```

And which version of Ubuntu are you running?

---

### Post by wyliga on 2008-09-23
I'm sorry to say, but that command had no output at all. It did some things, but nothing stayed in the terminal if you know what I mean.

I think I have a broadcom 43something or something like that I don't even remember to be honest.

I'm running hardy 8.04.

---

### Post by dub_u on 2008-09-23
Ok, if this command doesn't result in any output, your card is most likely not recognized by the system.

Try ```
dmesg | grep Broadcom

```
or if that doesn't say anything

```
dmesg | grep Network
```

---

