---
title: "Visual Appearance"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by riceandlentils on 2009-08-17
Hi,
Another nooby question. I have 2 users set up with the same theme. One has Extra settings enabled in the Visual Effects of the Appearances settings.The other will not allow the Extra option to be set (only None) and gives me a 'desktop effects cannot be enabled' message.
Why can it be enabled for one user and not another?
Thanks

---

### Post by SoftwareExplorer on 2009-08-17
If you go to System->Administration->Users and Groups, then unlock it an select the second user and click properties, go to the user priveliges tab, is the Capture video from TV or Webcams, and use 3d acceleration checked?

---

### Post by riceandlentils on 2009-08-17
> **SoftwareExplorer said:**
> If you go to System->Administration->Users and Groups, then unlock it an select the second user and click properties, go to the user priveliges tab, is the Capture video from TV or Webcams, and use 3d acceleration checked?

Yes it's already checked.

---

### Post by mcduck on 2009-08-17
The issue here is that using desktop effects requires using your graphics card to handle the drawing, and only one user can do that at a time. So if you have many users logged in at the same time only one of them can have desktop effects enabled.

However if you log that user out first, and then log in as another user, that user can enable the desktop effects.

So it's not a permission thing, just a limitation in the way how direct rendering with graphics cards works.

---

### Post by riceandlentils on 2009-08-17
That explains it. Thanks

---

### Post by SoftwareExplorer on 2009-08-17
> **mcduck said:**
> The issue here is that using desktop effects requires using your graphics card to handle the drawing, and only one user can do that at a time. So if you have many users logged in at the same time only one of them can have desktop effects enabled.

However if you log that user out first, and then log in as another user, that user can enable the desktop effects.

So it's not a permission thing, just a limitation in the way how direct rendering with graphics cards works.
That makes sense, but my computer lets all five of the users have desktop effects. Is this a limitation of some models of graphics cards? (Mine's a Nvidia). So I'm curious to hear if it works to log out user 1 and enable them on user 2.

---

### Post by northern lights on 2009-08-17
> **SoftwareExplorer said:**
> That makes sense, but my computer lets all five of the users have desktop effects. Is this a limitation of some models of graphics cards? (Mine's a Nvidia).
Have you had both logged in simultaneously?
Be aware that that'd be the culprit. Not user's existing.

---

### Post by SoftwareExplorer on 2009-08-17
> **northern lights said:**
> Have you had both logged in simultaneously?
Be aware that that'd be the culprit. Not user's existing.
Yes, I have multiple users logged in and we just switch users back and forth. Is that what you mean or are you talking about multiseat configuration?

---

### Post by northern lights on 2009-08-17
> **SoftwareExplorer said:**
> Is that what you mean or are you talking about multiseat configuration?
The latter is what would not allow both users to use the feature. Just like you can't run two windows games simultaneously, even if your CPU could.

---

### Post by SoftwareExplorer on 2009-08-20
Well, with a little testing, it's possible to have 2 users logged in with desktop effects with nvidia, but it doesn't seem to work with intel.

---

