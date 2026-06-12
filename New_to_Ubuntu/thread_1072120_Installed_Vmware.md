---
title: "Installed Vmware"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by halovivek on 2009-02-17
Hi
i have installed vmware server in the ubuntu. In Vmware server i have installed the windows xp os and it is doing fine. Now i could not hear the sound which is running in the windows xp os. 
i do have three problems
1. i could not here the songs or sound from windows xp.
2. i could not see my other hard disk from windows xp.
3. how to boost the volume of the mic? i am using head phone.

---

### Post by Felix-the-Cat on 2009-03-14
1. You have to have a audio device on the VM for the sound to be forwarded I don't think Vmware does this automatically look at the settings for that VM.

2. You can mount the physical harddrive by adding another drive (also in the Vm's settings) but that is very experimental and if the host tries to access at the same time as the guest you may have issues. Your best bet is to share that drive as a samba share through Ubuntu.

---

