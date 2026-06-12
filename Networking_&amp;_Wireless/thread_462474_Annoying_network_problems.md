---
title: "Annoying network problems"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by ShishKabab on 2007-06-02
Hello,

I'm using Ubuntu 7.04. I have two network cards: one onboard 3Com and one nVidia. When I have the two enabled at the same time I experience random system freezes with kubuntu and knoppix(!?). No problem: I don't need both at once.

So I disabled the nVidia one and I'm now working via the 3Com one. But there's an annoying problem: 9 out of ten times I have no natwork at startup. I have to pull out my cable, reinsert it and run ifdown/up to get my network back.

So I tried to disable the 3Com and enable the nVidia. And that's the point where thing get messed up. The progress bar at startup fills. Good. Then I get a new one that always stays black. In other words: X refuses to start. So I press ctrl+alt+f1 to get a console. I login and try to start X by typing "startx". The error message is that no screens are found and a message with a bus number above that. Huh? So I reboot my computer, disable nVidia and enable 3Com. The system boots normally again.

Anyone knows why I have to reinsert my cable at startup and why the nVidia network card interferes with X?

Thnx in advance,
ShishKabab

---

### Post by ShishKabab on 2007-06-08
It's been five days since I started this thread and there are still no replies... The problem is driving me crazy... Doesn't anyone have a clue of what's going on?

---

### Post by Honig on 2007-06-08
> **ShishKabab said:**
> It's been five days since I started this thread and there are still no replies... The problem is driving me crazy... Doesn't anyone have a clue of what's going on?

Nope.

---

