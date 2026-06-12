---
title: "Display skewed left of center"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by Redmage913 on 2010-12-02
Greetings,

I just installed Ubuntu 10.10 on a Dell Dimension 4600 with an ATI Radeon 9550 (RV350), using a DVI to HDMI cable to display on an RCA HDTV. While the image is excellent at 1280x720, the image is slightly left of center (by about 3/4 or 7/8 of an inch), with a black bar on the right edge and the image going offscreen by about the same amount on the left.

Any ideas on how to move the image to the right enough to see my full display?

Thanks,

--Red

---

### Post by sandyd on 2010-12-02
> **Redmage913 said:**
> Greetings,

I just installed Ubuntu 10.10 on a Dell Dimension 4600 with an ATI Radeon 9550 (RV350), using a DVI to HDMI cable to display on an RCA HDTV. While the image is excellent at 1280x720, the image is slightly left of center (by about 3/4 or 7/8 of an inch), with a black bar on the right edge and the image going offscreen by about the same amount on the left.

Any ideas on how to move the image to the right enough to see my full display?

Thanks,

--Red
you can adjust the position of the image by using
```

xrandr --output <MONITOR> --pos <x>x<y>

```

you can find <MONITOR> by running
```

xrandr
```
it will probably be DVI-0 or something.

---

### Post by Redmage913 on 2010-12-02
Forgive me, but when I ran:

```
xrandr --output DVI-0 --pos 1280x720
```

Nothing changed. I also tried substituting 15x0 for the --pos argument.

I'm sure I'm doing this wrong.

--Red

---

### Post by Redmage913 on 2010-12-02
Recently Discovered Information:

When in 640x480, 800x600, and 1024x768, the display is slightly *right* of center in a similar manner, though much fewer pixels off.

Should I try the ATI driver and see if things work any differently?

--Red

EDIT: I redact my last question. After quick research, I found out that I cannot use any of the ATI-based drivers with Maverick, due to the X.org version requirements (Maverick is too new).

Yay, antiquated hardware...Maybe this isn't a very 'fixable' problem. I don't mind - I can get used to this, and I can still use a standard monitor when I need (another antiquated piece - an ancient Compaq monitor from 1998 :P )

---

