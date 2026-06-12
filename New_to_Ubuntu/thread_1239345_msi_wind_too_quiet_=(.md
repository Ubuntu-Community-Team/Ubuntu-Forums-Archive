---
title: "msi wind too quiet =("
date: 2009-08-13
forum: New to Ubuntu
---

### Post by JacKeown on 2009-08-13
I was wondering if there is a hack to make the msi wind speakers louder with ubuntu. 

thanks in advance =)

---

### Post by Hospadar on 2009-08-13
It's the msi *wind* not the msi thunderstorm or the msi heard of elephants.

But in all seriousness:
I would first check alsamixer and make sure all the channels are turned up, specifically master, pcm, front speaker (you may not have all these channels, that's ok).  Sometimes one app turns down channel a, and then another app only uses channel b, I have this problem in mythtv sometimes.

I realize not everyone is a l33t pro like I am - in case you've never done this:
Open a terminal, type "alsamixer"
up and down arrows to change volume, m to mute/unmute, q or esc to quit

=)

---

### Post by credobyte on 2009-08-13
You can try pulling up [COLOR=DimGray]PCI[/COLOR] in [COLOR=DimGray]alsamixer[/COLOR] :)

---

