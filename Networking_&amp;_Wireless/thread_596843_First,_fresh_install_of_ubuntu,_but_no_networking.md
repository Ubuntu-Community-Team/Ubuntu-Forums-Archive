---
title: "First, fresh install of ubuntu, but no networking"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by revi_2003 on 2007-10-30
Hello all,

I am a newbie to linux and ubuntu. I just installed ubuntu 5.10. I can't get to the internet. When i plug in my network cable i get no lights. I am running ubuntu on a dell optiplex gx260. It has an intel onboard nic card.

How do i install my network card?

when i look under Applications -> System Tools -> Network Tools, I get a Network Devices not found message.

Thanks in advance

---

### Post by Lambert on 2007-10-30
Can you open a terminal and run this command, post output here.

```

sudo lshw -C network

```

---

### Post by tospig on 2007-10-30
forgive me for hijacking this thread, but I've got a similar problem:

I used to have lights on my network card, and everything working fine, then the other day i turned my machine on and nothing, no internet/network.

i typed
```
sudo lshw -C network
```

and on the first line i got "network disabled"
then a whole list of things such as the type of network card...

I can move this to a new thread, rather than hijacking this one if people would prefer?

---

### Post by Lambert on 2007-10-30
> **tospig said:**
> forgive me for hijacking this thread, but I've got a similar problem:

I used to have lights on my network card, and everything working fine, then the other day i turned my machine on and nothing, no internet/network.

i typed
```
sudo lshw -C network
```

and on the first line i got "network disabled"
then a whole list of things such as the type of network card...

I can move this to a new thread, rather than hijacking this one if people would prefer?

Your radio sounds like it's turned off. Do you have a fn+ key combo to toggle your wireless? If not post the output of lshw here as there may be a command to flip device back on.

---

### Post by tospig on 2007-10-30
sorry, I should've said, it's not wireless. 

I went into system>admin>networking, selected the card and activated it through there. I then ran lshw -c network again and this time the first message was just "network".

but, the card still isn't showing any sign of life. I can post the output of the whole command if you wish, but the computer's in another room, which could get annoying...:)

---

### Post by Lambert on 2007-10-30
when you run the lshw command, do you see a line that says interface or logical name. might be eth0.

If so then run this command.

```

sudo ethtool eth0

```

Would really help if you had a usb storage device to copy and transfer the output here.

---

### Post by tospig on 2007-10-30
yep, got eth0 and I've run ethtool eth0.

output is (typed in, no storage device :( )

```


supported ports: [ tp MII ]
supported link modes:   10baseT/half   10baseT/full
                                      100baseT/half 100baseT/full
supports auto-negotiation: yes
advertised link modes:   10baseT.... etc
advertised auto-negotiation: yes
speed: 100mb/s
duplex: half
port: MII
PHYAD: 32
transceiver: internal
Auto-negotiation: on
supports wake-on: pumbg
wake-on: d
current message level: 0x0000000 (7)
link detected: no 
```

---

### Post by Lambert on 2007-10-30
Do you have another cord you can try?

The problem is on a hardware level. Either something is wrong with one of your ports you've plugged in, or the cord is bad.

> 
link detected: no


If you don't have another cord you can always try unplugging and plugging back in both sides of the cord. It could be with your router or onboard nic.

You can also try to power cycle your router to see if anything happens.

That last line needs to say Yes.

---

### Post by tospig on 2007-10-30
yes I've tried another card, and that didn't work either. 

There's a few more hardware options I can try out to get this sorted. Thanks for all your help, I really appreciate it :)

---

### Post by tospig on 2008-01-04
If anyone's followed this, the problem was that when I unplugged my cable, I plugged back in a cross-over cable, not a cat5 one - ubuntu didn't like this :)

---

### Post by Lostincyberspace on 2008-01-04
> **tospig said:**
> If anyone's followed this, the problem was that when I unplugged my cable, I plugged back in a cross-over cable, not a cat5 one - ubuntu didn't like this :)
I did that once it took me for ever to figure it out. Good thing I had a network cable checker handy and plugged it in and saw that it was flipped.

---

