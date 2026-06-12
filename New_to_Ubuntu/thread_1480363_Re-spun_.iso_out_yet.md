---
title: "Re-spun .iso out yet?"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by spydeyrch on 2010-05-11
Just a simple question here:

When the 10.04 .iso first came out, a bug appeared that made it so GRUB 2 wouldn't detect other OSs properly and add them to the GRUB menu. therefore it was difficult to boot into a second or third OS because they wouldn't show up in the GRUB menu. 10.04 would just boot straight into 10.04 (if I remember the issue correctly :confused:)
I remember it being mentioned somewhere that the .iso was being re-spun to include a fix/patch to the issue. I haven't heard much in regards to the issue/fix since then and was just wondering if the re-spun .iso has come out yet? Just curious. :)

I wasn't affected by the initial bug because of how I setup my different systems but I know many people were.

Thanks. :KS

-Spydey :guitar:

---

### Post by doas777 on 2010-05-11
well, they finished the respin before they released the iso's on the 29th. release was only delayed by a few hours. the bug was the result of a failure to reupdate the grub config after migrating data from a windows account. after that, any time grub was updated the correct entries would appear. they had initially considered jsut letting it go, since the first kernel update (which would appear immediately after install) would reconfigure grub and the other os boot options would then appear.

---

### Post by spydeyrch on 2010-05-11
> **doas777 said:**
> well, they finished the respin before they released the iso's on the 29th. release was only delayed by a few hours.

Oh really? :-k Interesting. I wasn't aware of that. I had understood that the initial release on the 29th had the bug but then supposedly the re-spin was going to be out the 30th or something like that.

I have a few friends that had recently downloaded the .iso from the ubuntu site directly and it seemed that they suffered from the issue/bug because GRUB didn't detect their already present XP/Vista/Win7 installs (different OS depending on the friend), so I had just assumed that the issue still hadn't been resolved. I fixed their installs but was just curious if the issue had been resolved yet.

I wonder if their issue(s) was(were) something else? Interesting.......

Thanks for the update doas777.  :)

-Spydey :guitar:

---

### Post by spydeyrch on 2010-05-11
> **doas777 said:**
> well, they finished the respin before they released the iso's on the 29th. release was only delayed by a few hours. the bug was the result of a failure to reupdate the grub config after migrating data from a windows account. after that, any time grub was updated the correct entries would appear. they had initially considered jsut letting it go, since the first kernel update (which would appear immediately after install) would reconfigure grub and the other os boot options would then appear.

I see that you updated/edited your initial post. Thanks for that extra info! It clarifies some questions that I had. It makes sense now. Thanks a ton. :P

-Spydey :guitar:

---

### Post by doas777 on 2010-05-11
> **spydeyrch said:**
> I see that you updated/edited your initial post. Thanks for that extra info! It clarifies some questions that I had. It makes sense now. Thanks a ton. :P

-Spydey :guitar:
rock on. just have your friends run 
```
sudo update-grub
```  if it ever comes up again, and they shoudl be all set.

cheers

---

### Post by spydeyrch on 2010-05-11
> **doas777 said:**
> rock on. just have your friends run 
```
sudo update-grub
```  if it ever comes up again, and they shoudl be all set.

cheers

Yeah, I figured I could do it that way but wasn't sure if the bug would inhibit it so I did it a different way that works. A little more complicated but it gets them what they need.

But now that the issue has been resolved, I will just add that command to the list that I gave them for any possible issues/resolutions.

Thanks again for the input and info, I appreciate. :)

-Spydey :guitar:

---

