---
title: "Turn my laptop into a wireless card for my Xbox?"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by mrplaid on 2007-10-04
Hello Ubuntu,
I've got kind of an odd question. Is it possible for me to turn my spare laptop that's running Feisty Fawn into a 'wireless card' for my Xbox?
I've done a little bit of research into the subject, but my knowledge is lacking. I've tried bridging my eth0 and ath0 connections and setting up a static route to my wireless access point, but it still seems as though I'm missing something. I gave my Xbox at a static IP since I don't think DHCP is running on that AP. I've hit a wall and I've begun to wonder if what I'm trying to do is even possible.
Any advice/hints/verbal abuse?

---

### Post by El Rogueo on 2007-10-05
> **mrplaid said:**
> Hello Ubuntu,
I've got kind of an odd question. Is it possible for me to turn my spare laptop that's running Feisty Fawn into a 'wireless card' for my Xbox?
I've done a little bit of research into the subject, but my knowledge is lacking. I've tried bridging my eth0 and ath0 connections and setting up a static route to my wireless access point, but it still seems as though I'm missing something. I gave my Xbox at a static IP since I don't think DHCP is running on that AP. I've hit a wall and I've begun to wonder if what I'm trying to do is even possible.
Any advice/hints/verbal abuse?

Can you reexplain what you've done? I understand the jargon but there's so much of it I'm having trouble knowing exactly what you've done ;) 

I would assume it's possible; what you're trying to do is effectively use your laptop as a gateway to whatever wireless network you encounter, correct? If that's what you want, then it's definitely possible, but I've never actually seen it done before. According to Google, the fact you have a wired connection and a wireless connection means it's certainly plausible, but I'll have to do more research.

Some questions:

Why did you bridge eth0 and ath0? 

To what purpose would you create a static route to your wireless access point? I can see why, but it seems like it could lead to false positives as far as successes go.

The Xbox having a static IP only helps with connecting to your laptop and simplifying that process, not in connecting to the AP. Remember, the laptop is the part that's connecting to the AP, and if you're taking the Xbox places where you want a wireless connection you probably want the laptop staying DHCP. Why your AP wouldn't support DHCP I have no idea, and could mean you should test this against a different AP.

Will post more later after consulting Google, heh

---

### Post by El Rogueo on 2007-10-05
a ten second google search reveals there's really two ways to do this

utilize internet connection sharing, which is less efficient but simpler, or what I thought you were trying to do, being make the laptop into a network gateway, which would be more efficient but probably also take more work.

Which were you doing?

---

