---
title: "Kubuntu desktop effects gone missing"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Linux&amp;Gsus on 2011-05-03
Hi everyone,
I would like to have a problem... :D

I installed 11.04 two or three days ago and all was fine. Worked almost too perfect for a new system. ;)
Today I added a guest account on that machine and discovered that I can't just log out. All I see then is a black screen. (Not a major issue to me, since I hardly need that 2nd account anyway) So, I had to hard reboot. Logged in to the guest account, all works fine.

Back in my normal user account I realised that no desktop effects work. Went back to the guest account again, everything is working fine there. Again back in my normal account, I checked in the System Settings for the desktop effects. They are disabled. Tried to enable them, didn't work. Only then I discovered that in the tab "All Effects" there is actually no desktop effect listed, it's just blank. In the guest account it looks like it's supposed to.

Any ideas how I can get that stuff back in my normal user account?



Thanks and Cheers,
L&G

---

### Post by Linux&amp;Gsus on 2011-05-05
So, it's still not working.

Update, reboot, trying to make sense of config files... nothing seems to change anything. The only things I *successfully* managed to to was to change in the "Advanced" tab in System Settings -> Desktop Effects to change the compositing type from OpenGL to XRender. But I can't revert that any more to OpenGL with the following error message:
> Failed to activate desktop effects using the given configuration opetions. Settings will be reverted to their previous values.

Check your X configuration. You may also consider changing advanced options, especially changing the compositing type.
Funny enough, that change I made is in the advanced options. :D

My wild guess is that some config file isn't read properly, gone missing, or is corrupted. But I can't figure out which one it should be.
Specifically since it's still working in the other user account. So, (1) the computer is able to do it even though a bit older and (2) nothing needed for the compositing effects can be erased or corrupted on a system wide level.

---

### Post by el_koraco on 2011-05-05
A quick way that worked for me when Kwin had a fit. I renamed my .kde folder, which reset the entire Plasma and Kwin config to default. Had to reenable the effects and wallpapers. If you do that, do not delete the folder, there is useful info in there. There seems to be some sort of bug with Kwin or Plasma, I'm just nor sure what it is.

---

### Post by Linux&amp;Gsus on 2011-05-07
Now I almost forgot to rely... :oops:
Thank you very much, that basically did the trick. I somehow suspected the issue have something to do with this folder, or better say the contents thereof. So, I tried to figure out a way to rename just a bunch of files that might cause the issue. Thus reducing the work of what would need to be redone, e.g. it resets Amarok completely. Of course, that is fixed easy enough with copying back the related directory.
Still, I tried to find the file/s that cause the issue at hand, but I couldn't find it. So, I did end up renaming the whole thing which fixed my problem.

Thanks again, my test/media machine is a happy camper again.
L&G

---

