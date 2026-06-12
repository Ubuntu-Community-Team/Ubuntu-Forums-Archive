---
title: "Guest session data"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by JayD2 on 2009-10-25
When I let someone use my computer under the guest session option are there any temporary files which get saved (and may accumulate) or is everything, including any files downloaded, deleted once the session ends?

Sorry if this is an overly simple question I didn't find a clear answer. Thanks.

---

### Post by cguy on 2009-10-25
Why don;t you try it yourself and see what happens? :D

---

### Post by nitro_n2o on 2009-10-25
I agree with cguy, 

try it and let us knw what happens, we can help you fix it. it could be that things get cleaned up after a reboot so try that as well. 

Even if not, you can put together a small script to clean up after your guests :)

---

### Post by JayD2 on 2009-10-25
I did and I know if I'm just going back and forth between my account and guest the changes remain but if I restart they are gone. What I don't know is if the files have been deleted or if they are still in a temporary folder somewhere in the file system.

---

### Post by mcduck on 2009-10-25
> **JayD2 said:**
> When I let someone use my computer under the guest session option are there any temporary files which get saved (and may accumulate) or is everything, including any files downloaded, deleted once the session ends?

Sorry if this is an overly simple question I didn't find a clear answer. Thanks.

Everything will get removed when the guest logs out. Everything users do, including temporarily files and stuff like that, is kept inside user's home directories since that's the only place where users have write privileges anyway). And guest session's home directory is completely destroyed after the guest user logs out, and created anew when guest login is used again.

edit: Of course if you *switch* between guest session and other user session the guest session is not destroyed. Just like your own session isn't destroyed either. The guest session remains active until the guest logs out, exactly like with any other user session.

---

### Post by QLee on 2009-10-25
> **JayD2 said:**
> When I let someone use my computer under the guest session option are there any temporary files which get saved (and may accumulate) or is everything, including any files downloaded, deleted once the session ends?

Sorry if this is an overly simple question I didn't find a clear answer. Thanks.

You might want to have a look at this document in the Ubuntu wiki. I doubt things have changed much since it was written, specifically, it states that the home for the guest account is on a temporary filesystem which seems to fit with what you have observed when you switched back and forth and then rebooted.
[https://wiki.ubuntu.com/DesktopTeam/Specs/Intrepid/GuestAccount](https://wiki.ubuntu.com/DesktopTeam/Specs/Intrepid/GuestAccount)

---

### Post by JayD2 on 2009-10-25
> **QLee said:**
> 
[https://wiki.ubuntu.com/DesktopTeam/Specs/Intrepid/GuestAccount](https://wiki.ubuntu.com/DesktopTeam/Specs/Intrepid/GuestAccount)

Thanks everyone and I'll read through that.

---

