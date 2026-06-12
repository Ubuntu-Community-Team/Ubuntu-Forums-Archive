---
title: "Monitor/Display problems"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by haileris23 on 2009-08-24
Hi folks,

I'm having a bit of a problem and I was hoping that someone here could point me in the right direction. I'm trying to install Ubuntu 8.10 on my Asus Essentio CM5570-AP002. I can get it installed, but I'm trying to use my TV as my monitor which is when everything falls apart. I've got the TV and the tower hooked together through the HDMI port in the Intel GMA X4500 Dynamic Video graphics card. The only display option that Ubuntu is showing is a 95" display running at 1920x540! I've looked all over trying to figure out how to fix this, but I'm so new to Linux that most of the answers I have found don't really make any sense to me. For example, it sounds like I might need to edit my xorg.conf file, but I have no idea how to do that. Any advice would be greatly appreciated. Right now I'm stuck using Windows Vista, and nobody wants to see that. :p

---

### Post by jrothwell97 on 2009-08-24
Welcome to the Ubuntu forums!

My first advice would be for you to try installing Ubuntu 9.04, the Jaunty Jackalope, instead of Ubuntu 8.10. Later releases generally have better hardware support.

Good luck!

---

### Post by Wim Sturkenboom on 2009-08-24
> **jrothwell97 said:**
> Welcome to the Ubuntu forums!

My first advice would be for you to try installing Ubuntu 9.04, the Jaunty Jackalope, instead of Ubuntu 8.10. Later releases generally have better hardware support.

Good luck!Are the issues surrounding Intel drivers solved for Jaunty? Else I would stay away from it.

---

### Post by LewRockwell on 2009-08-24
> **Wim Sturkenboom said:**
> Are the issues surrounding Intel drivers solved for Jaunty? Else I would stay away from it.

there is no harm in having the latest release

even if it doesn't work on this particular equipment the OP might procur different units and/or have friends who might like to try it out

also the OP might want to try the alternate install if the regular doesn't work

.

---

### Post by inobe on 2009-08-24
> **haileris23 said:**
> Hi folks,

I'm having a bit of a problem and I was hoping that someone here could point me in the right direction. I'm trying to install Ubuntu 8.10 on my Asus Essentio CM5570-AP002. I can get it installed, but I'm trying to use my TV as my monitor which is when everything falls apart. I've got the TV and the tower hooked together through the HDMI port in the Intel GMA X4500 Dynamic Video graphics card. The only display option that Ubuntu is showing is a 95" display running at 1920x540! I've looked all over trying to figure out how to fix this, but I'm so new to Linux that most of the answers I have found don't really make any sense to me. For example, it sounds like I might need to edit my xorg.conf file, but I have no idea how to do that. Any advice would be greatly appreciated. Right now I'm stuck using Windows Vista, and nobody wants to see that. :p

the problem sounds like mirroring !

click system ->preferences ->screen resolution.

enable the external monitor and guess at its native resolution.

disable the desktop monitor assuming the external is mirroring it's resolution.


in ubuntu 9.04' it's called display and not screen resolution.

---

### Post by jrothwell97 on 2009-08-24
> **Wim Sturkenboom said:**
> Are the issues surrounding Intel drivers solved for Jaunty? Else I would stay away from it.
I can't remember where, but I found evidence of it working on Hardy and Jaunty, but not Intrepid. I'd be inclined to go with Jaunty because its hardware support is better (and, IMHO, Hardy wasn't a great release.)

---

### Post by haileris23 on 2009-08-24
Wow! Thanks to everybody for the super fast responses! 

jrothwell97, the first time I tried to install I did use Jaunty, and got even worse results, so I switched back to Intrepid (which I had been using with great success on my old, now defunct, machine).

inobe, I'm trying to use the TV as my only monitor, and I got this issue as soon as I installed Ubuntu, when the TV was the only thing I had conncted to the computer. I tried to hook up an old monitor later through the VGA port (that isn't on the video card) and it worked fine. So while I can tell that the issue probably lies with the video card, I have no idea what to do about it.

---

