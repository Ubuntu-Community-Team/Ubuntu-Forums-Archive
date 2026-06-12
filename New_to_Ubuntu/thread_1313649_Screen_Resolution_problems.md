---
title: "Screen Resolution problems"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Louie82Y on 2009-11-03
The default screen resolution for Ubuntu 9.10 (1440xX900)  is waaaay too small for my eyes. Whenever I change it to 1024x768 like it used to be for 8.04 every thing becomes insanely blurry. I tried installing msttcorefonts and adjusting the text rendering, but it doesn't seem to help much. I remember having a similar problem like this with 8.04, can't remember how I resolved it though D:. Any help would be appreciated.

---

### Post by timinator94 on 2009-11-03
> **Louie82Y said:**
> The default screen resolution for Ubuntu 9.10 (1440xX900)  is waaaay too small for my eyes. Whenever I change it to 1024x768 like it used to be for 8.04 every thing becomes insanely blurry. I tried installing msttcorefonts and adjusting the text rendering, but it doesn't seem to help much. I remember having a similar problem like this with 8.04, can't remember how I resolved it though D:. Any help would be appreciated.
go into system-administration-hardware drivers and see if there's any drivers needed to be enabled. If so enable them.
Hope that helps
The Timinator

---

### Post by Louie82Y on 2009-11-03
> **timinator94 said:**
> go into system-administration-hardware drivers and see if there's any drivers needed to be enabled. If so enable them.
Hope that helps
The Timinator

Nope no drivers needed to be enabled. :/

---

### Post by timinator94 on 2009-11-04
> **Louie82Y said:**
> Nope no drivers needed to be enabled. :/
Huh.... What king of computer are you using... as in cpu, gpu etcetera,

---

### Post by Louie82Y on 2009-11-04
[quote=Louie82Y]Nope no drivers needed to be enabled. :/[/quote]

[quote=timinator94]Huh.... What king of computer are you using... as in cpu, gpu etcetera,[/quote]

Not exactly sure what you mean by that.

Also I meant I didn't need to enable anymore drivers. I already had the recommended one installed.

---

### Post by JPorter on 2009-11-04
If the system is defaulting to 1440x900, then that is the native resolution of your display and is the ONLY resolution that you should be using on it... it's incapable of displaying anything else at 1:1 pixel ratio.

To make the text larger, go into System -> Preferences -> Appearance -> Fonts and increase the text sizes used by default.

Alternatively, you can click Details at the bottom of the same dialog and change the DPI setting for the whole interface.  Beware though, it may have some odd side effects for certain applications.

---

### Post by Louie82Y on 2009-11-04
> **JPorter said:**
> If the system is defaulting to 1440x900, then that is the native resolution of your display and is the ONLY resolution that you should be using on it... it's incapable of displaying anything else at 1:1 pixel ratio.

To make the text larger, go into System -> Preferences -> Appearance -> Fonts and increase the text sizes used by default.

Alternatively, you can click Details at the bottom of the same dialog and change the DPI setting for the whole interface.  Beware though, it may have some odd side effects for certain applications.

I don't see how it's the native resolution. The default for Vista is 1024x768 and back when I used Ubuntu 8.04 the resolution was fine at 1024x768.

---

### Post by JPorter on 2009-11-04
Forget the OS.  It's an LCD monitor, right?  They only have one resolution.  In your case, it sounds like the resolution of your display is 1440x900.

Is it a widescreen monitor?  If so, it's impossible for its native display resolution to be 1024x768.

---

### Post by emptybox on 2009-11-04
If your laptop screen (or monitor) has a resolution of 1024 x 768, then set that in Preferences>Display. Likewise if it's 1440 x 900.

You may not know what the native resolution of your monitor is, but 1024 x 768 is a 4:3 ratio, and 1440 x 900 is a 16:10 **widescreen** ratio so go by that. :)

---

