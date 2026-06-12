---
title: "No sound!"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by JasonGOrtiz on 2010-03-22
My computer was recently shut off in the middle of running update manager. Now the volume control icon has a red circle on it and I don't have any sound. When I click on the volume control icon it gives me this message: 

"No volume control GStreamer plugins and/or devices found."

I have no idea how to fix this problem. I'm not computer savvy and I know very little about ubuntu and have had major difficulties figuring out how to solve problems when they occur. I'm about to the point of switching back to Windows, but I would really appreciate help with this problem in the meantime. Thanks.

---

### Post by teeliina on 2010-03-22
Hi! have you tried reinstalling gstreamer plugins with synaptic (system->administration->synaptic) the packages you have, are marked. by clicking them for reinstallation and apply might do the trick. Restart the update manager also, you might have missed some other important update too. then restart your computer to make sure that devices are really found, if they didn't reappear earlier.

---

### Post by cgroza on 2010-03-22
You can try resume the update my running sudo apt-get upgrade in your terminal.

---

### Post by JasonGOrtiz on 2010-03-22
I'm in Synaptic Package Manager and there are about 40 packages with various gstreamer names. Only a few show "installed version". I'm guessing that means most are not installed yet. Should I go ahead and mark all of them either "reinstall" or "install"?

---

### Post by JasonGOrtiz on 2010-03-22
Thank you Teeliina! All I had to do was go into Synaptic and reinstall some of the GStreamer packages. Worked like a charm. Once again, I'm grateful for the quick help. I don't know if I'm supposed to mark this thread as "solved" or if that's something that an administrator has to do, but if that's the case please do.

---

