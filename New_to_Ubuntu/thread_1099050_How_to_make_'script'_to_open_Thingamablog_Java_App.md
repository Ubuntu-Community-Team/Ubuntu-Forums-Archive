---
title: "How to make 'script' to open Thingamablog Java App"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by NEUR0M4NCER on 2009-03-17
Hi guys.

I started using Thingamablog blog writing app and it's great, but the only way I can start it successfully is through the terminal:
```

java -jar thingamablog.jar

```
If I just click the icon, it doesn't work properly. I saw a post somewhere that said it might be best to write a quick script to "go into the correct directory and start the app, then link the menu entry to that"...

I don't really know what to do with that - can someone help me?

---

### Post by yeats on 2009-03-17
There will be a Menu Editor under System -> Administration (I think - may be Preferences - I use Kubuntu, forgive me) and you should be able to edit the icon/menu item to use the command you're typing into the terminal.

---

### Post by NEUR0M4NCER on 2009-03-17
Thanks - I tried that:

java -jar /home/neur0m4ncer/thingamablog-1.1b6/thingamablog.jar

It didn't work though - have I written it wrong?

---

### Post by NEUR0M4NCER on 2009-03-19
... still haven't figured it out. Anyone know where i'm going wrong?

---

### Post by occams_beard on 2009-03-19
Download the rpm and convert it to a dpkg with alien. Then you can start it from the command line with just  'thingamablog'

---

### Post by NEUR0M4NCER on 2009-03-24
Thanks - I was surprised how painless that was! Works perfectly now!

---

