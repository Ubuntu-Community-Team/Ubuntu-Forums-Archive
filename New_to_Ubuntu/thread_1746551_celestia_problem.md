---
title: "celestia problem"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by abnordude on 2011-05-01
Hi.
I installed celestia.
But many of the planets and stars are colourless, white and dull. No textures.
How can I fix this?
PLease help me.

---

### Post by Achilles124 on 2011-05-02
Try running celestia from terminal. If there are any errormessages, post them here.

---

### Post by NightwishFan on 2011-05-02
I can confirm this problem with an Integrated Intel GPU.

---

### Post by madmax75 on 2011-05-04
Did you install Celestia through the Software Center?

Installing Celestia through the Software Center leaves out the **celestia-common-nonfree** package, which actually holds many of the textures. Yeah, leaves it out, and also fails to mention this little detail, if I remember correctly :confused: Some of the textures have an unclear license, and that's the reason it is left out from the installation.

You can install this package through the Synaptic package manager and also through the Software Center, and it should give you the necessary textures.

---

### Post by abnordude on 2011-05-12
I think that was the problem.
Thanks everyone.

---

