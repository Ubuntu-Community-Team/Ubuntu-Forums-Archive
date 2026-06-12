---
title: "wxcam records too fast / cuts off 1 third"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Aszasz on 2009-06-30
Hi,

I use a Logitech quickcam E3500 and got it kind of working with skype, audacity (though no playback possible) and wxcam. The camera can take snapshots, but while recording videos it compresses them by one third of their original time (for instance instead of 30 seconds the application just records 20) I have all the packages recommended by the wxcam website. Tried cheese, worked a lot worse but was basically the same problem...
Anybody has any idea on that, would be greatful for any hint.

---

### Post by triften on 2009-10-12
I have a similar problem. I recently got a used "EyeToy" camera and started playing around with that. Using the Xvid recording, videos are about 80% of the length they should be. I recorded 10 seconds according to the recording window, but the playback length was 8 seconds in Movie Player.

Is this an xvid issue, and wxcam issue, or a Movie Player issue? I don't know. I think it's an issue with xvid or between wxcam and xvid, because recording uncompressed (no audio) seems to be fine.


-Triften

---

### Post by Aszasz on 2009-10-13
Yes, that's what I observed also recently, after installing Ubuntu on my new PC after my old Laptop broke down. Seems to be Xvid related, but I got no idea,perhaps one needs to download a xvidpackage or tools???

---

### Post by triften on 2009-10-13
Word from the wxcam mailing list is that the xvid codec requires a statement at the start of the fps, which can fluctuate, especially as the computer is trying to xvid compress in real time. They recommend aiming for a lower rate or a lower resolution.

-Triften

---

