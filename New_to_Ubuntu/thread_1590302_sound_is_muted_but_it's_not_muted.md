---
title: "sound is muted but it's not muted?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by musendrophilus on 2010-10-07
Hello, I have no sound. I checked the wiki that says if you see the speaker icon followed by three hyphens then it means the sound is muted.

I went and looked under sound preferences under all four tabs and none of them are muted nor are the sliders set all the way to the left hand side.

Where else should I look to address the issue? I'm using the latest ubuntu lazy llama or whatever codename it was given by the team.

---

### Post by Ctrl-Alt-F1 on 2010-10-07
If you've had the same problem on other versions: Some hardware requires a specific configuration for example my laptop headphones don't work unless I modify /etc/alsa-base.conf
I figured out how to fix this by googling the model number of laptop followed by linux (eg. Asus xxx-xx Linux).

Good luck.

---

### Post by sikander3786 on 2010-10-07
> Hello, I have no sound. I checked the wiki that says if you see the speaker icon followed by three hyphens then it means the sound is muted.

I don't get the hyphens when I mute sound, instead the icon grays out.

> I'm using the latest ubuntu lazy llama

I haven't heard of that version so far.

Type

```
alsamixer
```

in a terminal and see if you can increase/decrease volume levels there.

---

### Post by Ctrl-Alt-F1 on 2010-10-07
> **sikander3786 said:**
> 
I haven't heard of that version so far.


The OP must mean Lucid Lynx.  I changed my post accordingly.  Sorry for the confusion.

---

