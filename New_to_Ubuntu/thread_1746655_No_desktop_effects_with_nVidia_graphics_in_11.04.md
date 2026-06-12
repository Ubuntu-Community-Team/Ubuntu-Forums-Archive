---
title: "No desktop effects with nVidia graphics in 11.04"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by the8thstar on 2011-05-02
I can't get the nVidia graphics driver to enable desktop effects in 11.04.

Typically the system says that the driver is installed but not active, which would explain why the desktop defaults to a basic appearance. How do I set it to active?

Thanks for your help.


[[img]http://ompldr.org/tOGluOQ[/img]](http://ompldr.org/vOGluOQ)

---

### Post by cobolt01 on 2011-05-02
Try run jockey-gtk

---

### Post by beew on 2011-05-02
> **cobolt01 said:**
> Try run jockey-gtk

He tried, see the screenshot.

---

### Post by cobolt01 on 2011-05-02
Oh sorry, I didn't notice it for some reason.

---

### Post by the8thstar on 2011-05-02
So, has anyone got an idea on how to solve this incompatibility with the nvidia card?

---

### Post by Gone fishing on 2011-05-02
The 7300 card is blacklisted, my GeForce 7300 LE card wasn't blacklisted as such and just froze Unity, scrabbled tty and refused to work with classic Ubuntu if the desktop effects were enabled.

I have heard that some people have got the 173 driver to work (give it a go), I tried it and the experimental open source driver nothing worked well, so I changed the card to a GeForce GT 220 which works perfectly.

I do find this all rather odd as the GeForce 7300 LE worked perfectly with the last few Ubuntu releases.

---

### Post by beew on 2011-05-02
Since this is an old card that doesn't support neat stuffs like Vdpau anyway if the Nvidia driver is giving you troubles you may as well remove it and try the nouveau one. 

If you use nouveau and install the package libgl1-mesa-dri-experimental you may be able to get 3d effects and Unity. I use Nouveau on my natty install (in an external drive so I use only open source drivers to keep it portable). Unity and 3d effect run without problem when I boot it off my main laptop which has a Nvidia card. But that is a newer card though (G105M)

(Aside: Unity and 3d effects also work out of the box with the open drivers when I boot the external drive from my friends' netbook which has an ATI card)

---

### Post by the8thstar on 2011-05-02
Thanks for the replies guys. Looks like I'm out of luck on this one and I can't even change the card as it is embedded in my laptop. 

I guess I have no other option but to remove Ubuntu and reinstall Windows instead. Pity.

---

### Post by beew on 2011-05-02
Why not try nouveau first?

---

### Post by the8thstar on 2011-05-02
Alright, I'll give a try before I give up for good. Can you tell me where can I find it?

---

### Post by beew on 2011-05-02
the nouveau drivers are installed by default unless you have removed them. So you need to remove the Nvidia stuffs and install the package libgl-mesa-dri-experimental and reboot.
Good luck.

EDITED: well come to think about it maybe your Nvidia driver is not working because you haven't removed the Nouveau driver. You may need to do that though with 10.10 I installed the nvidia driver with jockey (Additional Drivers) and it just worked without me having to remove or blacklist nouveau.

---

### Post by New Linux Usr on 2011-05-02
the8thstar,

You may want to check what option you have selected in the login screen setting, as I set the default session to &quot;Ubuntu Classic (No effects)&quot; - which gave the appearance like yours minus the bottom icon bar in the middle of your screen. I then changed this to &quot;Ubuntu&quot; and restarted the system, and then the effects kicked in when I logged in to the desktop.

You might want to check it out? Its in System -> Admin (*i think*) -> Logon Screen Settings

Kind regards,

New Linux Usr

---

### Post by the8thstar on 2011-05-03
I had to fiddle a bit (it's Ubuntu after all) but it worked somehow with the Nouveau driver. Let's hope the fix sticks! Thanks for the good help!

---

