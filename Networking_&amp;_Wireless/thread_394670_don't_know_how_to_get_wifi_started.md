---
title: "don't know how to get wifi started"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by narvus on 2007-03-27
Hi, I'm using ubuntu 6.10 and I need to get my wireless connection to work.

How can I do it? I've read that i should use the driver windows uses and ndiswrapper.

Can my card be RT2500?

Which is the driver windows uses?

As you can see I'm totally lost, please help me!!

---

### Post by Kobalt on 2007-03-27
To know if it's a RT2500 chipset based card you're using, enter this command in a Terminal and find your internet hardware line, you'll see your wifi card model and the chip it uses :
```
lspci
```
If it is a RT2500 based card then it's installed out of the box, and you won't have much troubles... 
Here is [some help]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500") on configuring your connection.

---

