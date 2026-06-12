---
title: "What's happened to my firefox?"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-04-18
I'm missing the title bar... and the close and minimize, maximize buttons...

Did a cold boot and did not fix the missing title bar...

Any suggestions?

[IMG]http://i97.photobucket.com/albums/l238/lhester_12/Screenshot-2.png[/IMG]

---

### Post by presence1960 on 2009-04-18
> **LesterPalooza said:**
> I'm missing the title bar... and the close and minimize, maximize buttons...

Did a cold boot and did not fix the missing title bar...

Any suggestions?

try pressing F11

---

### Post by binbash on 2009-04-18
did you try emerald --replace OR metacity --replace ?

Also you can try this : Go to compizconfig settings manager > Workarounds > Untick legacy fullscreen support

---

### Post by Joeb454 on 2009-04-18
Try disabling compiz if you're running it by entering the following into a terminal/run prompt. ```
metacity --replace
```

Does that bring them all back?

---

### Post by LesterPalooza on 2009-04-18
I did... no title bar.

---

### Post by supersonicdarky on 2009-04-18
perhaps... its just oversized?

---

### Post by LesterPalooza on 2009-04-18
Okay I did

metacity --replace

brought back the title bar. did a cold boot and it's missing the title bar again...

is there a more long term solution to this one? :D

---

### Post by LesterPalooza on 2009-04-18
> **binbash said:**
> did you try emerald --replace OR metacity --replace ?

Also you can try this : Go to compizconfig settings manager > Workarounds > Untick legacy fullscreen support

+1

Hey... This solution works great! Can you please explain what Legacy Fullscreen support means? I just want to know what I unticked...

---

