---
title: "Problem with Screen"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by yangt299 on 2009-09-11
Hi,

I am running Ubuntu 8.0.4 and have a question about the screen. There is nothing seriously wrong with it, the only concern that I have is that the colors are not mixing together smoothly. For example, I saw a really pretty menu bar on my Vista computer, with gray and white beautifully blended together. However, when I when back to the same page on my Ubuntu machine, the gray and white were completely separate, not blended at all, and really ugly. 

Although this is a relatively small issue, I was wondering if anyone could fix it. Do you have to change the screen resolution or something, because I have tried that already. Please help...

Thnx

---

### Post by RabbitWho on 2009-09-11
Is this problem only while you're online or do the colours look wrong all the time? 

Because that sounds like a browser/html problem to me.

---

### Post by pastalavista on 2009-09-11
Depending on the graphics/drivers you have running... go to System > Preferences > Appearance and open the 'Effects' tab and select 'normal' or 'extra'. Also make sure your window manager (Metacity, Compiz, Emerald, etc.) has composite enabled.

---

### Post by yangt299 on 2009-09-11
> **RabbitWho said:**
> Is this problem only while you're online or do the colours look wrong all the time? 

Because that sounds like a browser/html problem to me.

It only happens when I am online. 

By the way, my graphics are already set as "extra", so that isn't the problem. And could you please be more specific when you say to "enable composite"? Thanks

---

### Post by pastalavista on 2009-09-11
Since you don't know what I mean, you're probably using Metacity which is the default. Compositing is sort of like layering in photoshop (I think). Open a terminal and enter```
metacity -c
``` to turn compositing on and```
metacity --no-composite
``` to turn it off

---

### Post by yangt299 on 2009-09-11
The terminal returns > unknown option -c

Could this be because I am running on 8.0.4?

Thanks for all of your help.

---

### Post by pastalavista on 2009-09-11
```
metacity --composite
```

maybe.. or try

```
metacity --help
```

---

