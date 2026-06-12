---
title: "Webmin vs Ebox on Lucid"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by CharlesA on 2010-04-29
Since I cannot get Webmin to install on Lucid, I guess the only other option is to go with Ebox.

Does anyone know of any major differences?

EDIT: I was able to get webmin installed by installing webmin_1.510-2_all.deb instead of webmin_1.510_all.deb.

Different dependencies.

---

### Post by arrrghhh on 2010-04-29
Webmin installed perfectly for me, I prefer it but people on here will recommend eBox, because evidently Webmin is naughty and does bad things to your system... a) no one have ever said what exactly it does poorly or wrong, and b) I've been using it since 8.04, I love it.  Although I've never used eBox, I can't comment on it.

BTW, I downloaded Webmin 1.510 from their site.

---

### Post by CharlesA on 2010-04-29
You probably got the updated version then. I was running a script I wrote back in 9.10, but I guess I forgot to point it to the correct webmin version.

I don't know why it's "naughty" either, I haven't found any proof of it being bad.

eBox looks like it does way more things then I would even need to use.

---

### Post by arrrghhh on 2010-04-29
> **CharlesA said:**
> You probably got the updated version then. I was running a script I wrote back in 9.10, but I guess I forgot to point it to the correct webmin version.

I don't know why it's "naughty" either, I haven't found any proof of it being bad.

eBox looks like it does way more things then I would even need to use.

eBox definitely looks like overkill... sometimes that can be good, I guess I should give it a shot.  No reason you can't run both I don't think...?  So long as they're not on the same port I would assume haha.

---

### Post by CharlesA on 2010-04-29
> **arrrghhh said:**
> eBox definitely looks like overkill... sometimes that can be good, I guess I should give it a shot.  No reason you can't run both I don't think...?  So long as they're not on the same port I would assume haha.

You are probably right about that. I suppose, if you just want to play around with it, you could always run Ubuntu Server in a VM, that way you aren't messing up the working server. ;)

I might do that sometime, just for the hell of it.

---

### Post by DouglasAWh on 2010-10-23
> **CharlesA said:**
> 

EDIT: I was able to get webmin installed by installing webmin_1.510-2_all.deb instead of webmin_1.510_all.deb.

Different dependencies.

Are these in the repos?  I don't seem to have them, but then again I'm trying to set up an apt-mirror install, so I may have just junked it up.

---

### Post by CharlesA on 2010-10-23
> **DouglasAWh said:**
> Are these in the repos?  I don't seem to have them, but then again I'm trying to set up an apt-mirror install, so I may have just junked it up.

Webmin isn't in the repos. You would need to grab it from [webmin.com]("http://webmin.com/")

---

