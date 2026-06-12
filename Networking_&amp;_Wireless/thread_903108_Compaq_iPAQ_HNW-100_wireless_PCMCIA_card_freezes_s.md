---
title: "Compaq iPAQ HNW-100 wireless PCMCIA card freezes system"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by Zinake on 2008-08-27
Hello, I'm new to Ubuntu and I'm still a novice to linux.  I just installed Ubuntu on a Dell Inspiron 1150 and I'm having problems with my wireless PCMCIA card.  I tested it on the same computer with Windows XP before installing Ubuntu and it worked without issue.

After installing Ubuntu, whenever I put in the card, the system freezes.  The only way to fix this is to power cycle the system.  It makes no difference if the system is on or off when I put in the card either.  If the system is on, it just locks up.  If the system is turned off when installed, it does not boot.

Has anyone seen this before or can someone point me in the right direction?  Any help is appreciated.  Thanks.

---

### Post by Zinake on 2008-08-28
Just an update...

I was doing some more research on this and found a [_Wireless Troubleshooting Guide_]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#System%20locks%20upon%20card%20insertion").  I'm not sure how I didn't find this before... but in the guide it says to try this.
> 
3.1.3. System locks upon card insertion

When a card is first inserted, the system attempts to read the card's memory. This can sometimes cause your system to lock-up. Try this to see if it helps: 

1) Open the file /etc/pcmcia/config.opts
```

gksudo gedit /etc/pcmcia/config.opts

```
2) Find the following section: IconsPage/IconExample48.png
```

        include memory 0xc0000-0xfffff
        include memory 0xa0000000-0xa0ffffff
        include memory 0x60000000-0x60ffffff

```
3) Change it to look like this:
```

        include memory 0xd0000-0xdffff
        include memory 0xc0000-0xcffff
        include memory 0xc8000-0xcffff
        include memory 0xd8000-0xdffff

```

I have no idea what that means or does, but it still isn't solving the problem.

---

