---
title: "AIM Video Chat?"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by seagullplayer77 on 2009-01-12
I've got a friend who's heading to Africa for a few months and I'm planning on keeping in touch with her with my webcam. She has hers set up with AIM, and unfortunately, I've burned through the past three days trying to come up with a way to get AIM video chat working on Ubuntu and I've failed miserably. 

I've managed to get my webcam working with Kopete, although it only supports video chat with Yahoo and MSN---not AIM. I've also got my webcam working with both Skype and Ekiga, but if I understand correctly, there's no way to interface either of those clients with AIM. For normal chat, I use Pidgin (which works great), but as of right now, there's no A/V support for Pidgin...sounds like it's in the works, though.

I really don't want to have to boot into Vista every time I want to start a video chat...is there any way I can get around doing that? I'm willing to try different clients and plugins, but I'm pretty sure my friend is bound to using AIM...she's not one of those computer literate types :-).

---

### Post by pytheas22 on 2009-01-13
Have you tried Empathy?  It has video chat, although I'm not sure if it supports AIM yet.  You can install it from the repositories.

You might also want to try running one of the Windows clients through wine; it might work, especially if you tweak it.

Finally, you could run Windows inside a virtual machine using software like VirtualBox, VMware or qemu.  It might be a little tricky to get the virtual machine to work with your camera, but it's probably possible.  VirtualBox would probably be the best choice because it makes it easy to get external physical hardware recognized by the virtual machine.

Sorry none of this provides a concrete answer, but I hope it helps.

---

