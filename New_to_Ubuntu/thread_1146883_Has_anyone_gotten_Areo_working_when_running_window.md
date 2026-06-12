---
title: "Has anyone gotten Areo working when running windows 7 in the new Sun VirtualBox?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by powel212 on 2009-05-03
I have Jaunty running better than any preceding Ubuntu version. It is really nice and I am very happy.

The new Sun VirtualBox is very nice and runs very smoothly on my machine.

I installed windows 7 in the VirtualBox and it runs very smoothly.

But I have not been able to get Aero glass running in the virtualBox. I am wondering if anyone else has? 

Is it a limit of the VirtualBox or my hardware? Or, is it just a driver issue?

Any insight is appreciated.

Powel

Asus-P5KE/6G-RAM/intel-2.66GhzDuo/Nvidia8600(512m)/

---

### Post by pspsampsp on 2009-05-03
i dont think its possible as virtual box doesnt has very limited support for 3d i think

---

### Post by RedSingularity on 2009-05-03
I havent herd anyone getting that working.  It may happen in future releases of virtualbox.

---

### Post by bumanie on 2009-05-03
Virtualbox doesn't support 3d acceleration = No modern, fast games, no fancy visual effects.

---

### Post by doas777 on 2009-05-03
I had to resort to vmware player for 3DA.

---

### Post by ravi_buz on 2009-05-03
Nope not as far as i know:(

---

### Post by powel212 on 2009-05-03
Thanks for the feedback. I thought this might be the case. 

I did notice though, in the virtualbox preferences there is a checkbox for "Enable 3D acceleration" But checked or unchecked there does not seem to be any difference. What is that about?

Powel

---

### Post by bumanie on 2009-05-03
I just read that virtualbox does now support opengl 3d acceleration (since version 2.1) - so I don't know why aero won't work, unless it's not compatible with opengl standards. Someone else may know the answer to that.

---

### Post by doas777 on 2009-05-03
> **bumanie said:**
> I just read that virtualbox does now support opengl 3d acceleration (since version 2.1) - so I don't know why aero won't work, unless it's not compatible with opengl standards. Someone else may know the answer to that.

I'm not sure where the choice between Dx3D and OpenGL 3d is made, but i think you need an openGL driver for your card to make it work, and I don't know if the client application (in this case aero) makes that choice. if so, MS would have specified Dx only. if that is the case, opengl won't help.

hopefully some genius will post back and illuminate both of us.

good luck

---

### Post by sneeks on 2009-05-03
iv'e had windows 7 for a bit now on disc but have done nothing with it,i will give it a go in the new virtual box released a few days ago,and see what happens,and let ya know.

---

