---
title: "helpppp :("
date: 2011-06-13
forum: New to Ubuntu
---

### Post by clgamer on 2011-06-13
Hi All,
decided to switch to Ubuntu last night, loving most of it so far BUT :( I user a number of Aopen machines at home and in the office and when I install the latest version of Ubuntu it doesn't pick up audio and video drivers. 

I am using an Aopen MP45-DU with intels GM45+ICH9M chipset and GMAX4500 Graphics Engine but cant find the drivers for this anywhere just for fedora (which I couldn't get used to) can anyone recommend whether or not its possible to fun Ubuntu off this machine- it would save me sooo much time and help me prove to my boss that it is worth us migrating all our machines to this OS.

---

### Post by ppv on 2011-06-13
This is because you do not have the audio and video codecs installed. Since Ubuntu is based on free-software and these codecs are usually proprietary they are not installed by default in Ubuntu. You can install them from the repositories. One way is to add the medibuntu repository and install the required codecs from that repository.
 
Even if you have the drivers for your video card installed most video will not play in Ubuntu because the codecs are not installed by default.
 
If you do have an nvidia or ati graphics cards you should install drivers for them also. You can do this from the "additional drivers" section in the Ubuntu menu.

---

### Post by gandaran on 2011-06-13
> **clgamer said:**
> Hi All,
decided to switch to Ubuntu last night, loving most of it so far BUT :( I user a number of Aopen machines at home and in the office and when I install the latest version of Ubuntu it doesn't pick up audio and video drivers. 

I am using an Aopen MP45-DU with intels GM45+ICH9M chipset and GMAX4500 Graphics Engine but cant find the drivers for this anywhere just for fedora (which I couldn't get used to) can anyone recommend whether or not its possible to fun Ubuntu off this machine- it would save me sooo much time and help me prove to my boss that it is worth us migrating all our machines to this OS.
Intel chipsets work out of the box on Ubuntu, no need to install audio or video drivers for Intel devices so what is exactly the problem you have?

---

### Post by ppv on 2011-06-14
The OP does not explicitly mention the issue but it looks that he/she is unable to play audio/video for which codecs would be needed. Else except for separate graphics cards, drivers aren't usually required.

---

### Post by clgamer on 2011-06-20
you guys are excellent,
thanks for all the quick responses, the only problem was hdmi screen res and I downloaded arandr to resolve it. would be good if there was a pnp for hdmi so then I could plug it in to any hdmi tv and it would just work.... guess I cant have everything though :)

---

