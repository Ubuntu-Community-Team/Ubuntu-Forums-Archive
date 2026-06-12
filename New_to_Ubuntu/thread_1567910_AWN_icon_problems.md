---
title: "AWN icon problems"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by Commisar Jimp on 2010-09-04
Hi,
I just downloaded Avant Window Navigator, and I am having icon problems. all the applications I have just use a grey box with a red line through it as their icon, and if I try and change it, they all change. Does anyone know how I can do this?

---

### Post by juil on 2010-09-04
More details please.
What version AWN are you using. I'm assuming 0.4.0.
If that's the case you can add applications by opening Dock preferences and just drag and drop applications in the task manager tab.
[COLOR="Red"]Do you also have Compiz installed?[/COLOR] You have to have Compiz for AWN to work. You have to enable extra visual effects in the appearance section.

---

### Post by Commisar Jimp on 2010-09-04
I think you miss understood. I added the icons to the task bar like you said already. my problem is now the icons themselves. GIMP is on the task bar, but it isn't a little dog with a paint brush, it is a grey square. I can still click the square and GIMP opens, but the icon is wrong.

sorry if this is poorly explained.

---

### Post by juil on 2010-09-04
You still haven't said if you have Compiz installed.

---

### Post by Commisar Jimp on 2010-09-04
Oh sorry, forgot. I've got compiz installed and running, with extra desktop effects if that matters. AWN is version .40

---

### Post by juil on 2010-09-04
Another user had the same problem. 
The_Orig says:
> So..... it turns out the bug existed, BUT not under the name "Gray" or "Box". All other bug reports were filed under "artifacts" or "white" and weren't revealed when I searched for previous bug reports >.<!

Anyway, the problem was resolved when NVidia released a newer driver version; simply install the NVidia drivers version 180.08 or newer and then restart and ALMOST all of the "artifacts" should be fixed.

If you can't install the newer driver version one hackish fix someone found was to move your applets to the left side of your dock and the launcher to the right. This seemed to have mixed results.

Here is the link to the bug report on launchpad:
[https://bugs.launchpad.net/awn/+bug/273326](https://bugs.launchpad.net/awn/+bug/273326)

And here is the link to the thread:
[http://ubuntuforums.org/showthread.php?t=1034049](http://ubuntuforums.org/showthread.php?t=1034049)

Hope it helps!

---

### Post by Commisar Jimp on 2010-09-04
under hardware drivers the three options I have are NVIDIA v. 173, NVIDIA v. 96 or NVIDIA current version. I've got the current version installed but I've still got the problem.

---

### Post by juil on 2010-09-04
If you read to the bottom of The_Orig's post, you may have noticed this link:
[https://bugs.launchpad.net/awn/+bug/273326](https://bugs.launchpad.net/awn/+bug/273326)

If you open that link, you will see posts of users saying that they are having problems with NVidia v.173 variants. 

Sorry, I don't know if there are any solutions to this problem yet, but you may have to continue to check that launchpad site.

---

### Post by Commisar Jimp on 2010-09-04
Alright. I'll keep an eye out for a newer driver. Thanks for all the patience.

---

### Post by juil on 2010-09-04
Keep searching. In the meantime, you can try using Cairo Dock or just Docky. All the best.

---

