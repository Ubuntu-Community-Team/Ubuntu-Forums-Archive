---
title: "Camcorder is not picked up by ubuntu."
date: 2011-07-21
forum: New to Ubuntu
---

### Post by Zundap on 2011-07-21
Hi everyone, could some one please advise on what to do, i have connected my camcorder to the computer, there is an electrical connection since when i plug the camcorder in via a USB lead, a light comes on the cam corder, but Ubuntu does not see the camcorder at all. I have check in computer and the camcorder is not there at all. I am only trying to get photo's off the camcorder, not film.

Could anyone tell me what the problem is and how i can fix it? Thanks.

---

### Post by Zundap on 2011-07-22
I have just connected the camcorder to a computer with XP O/S and it detects the camcorder no problem, so the camcorder is not the problem, its strictly down to ubuntu i guess. 

I would be grateful for any ideas on this problem. Thanks.

---

### Post by halitech on 2011-07-22
what type of camcorder is it?

---

### Post by anewguy on 2011-07-22
Is it connected via USB?  If so, try lsusb as just your normal user, then try sudo lsusb.  See any difference?

BTW - if you could post those outputs back here it might halp as well.

In the past, UDEV rules used to not play nice with some USB devices, either not mounting them or mounting them with root ownership, making them unaccessable to the user.  I don't know if this still holds true or not.

---

