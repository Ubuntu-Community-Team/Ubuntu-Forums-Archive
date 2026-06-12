---
title: "loudness"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by abkarch on 2010-06-11
I had a issue with dual booting a little bit back so i installed  ubuntu right over the hard drive and its working. however with windows 7 i never had a heat issue, after it booted up it would be pretty silent. but  with ubuntu its pretty loud and the fan is always spinning fast. how do i fix this? i have a quad core 2.66 processor and 6GB of ram with a 1GB 256 bit graphics card, so it shouldnt be working this hard just to run the OS. help please? thx in advance.

---

### Post by nhasian on 2010-06-11
you need to setup fancontrol.

[HOWTO: Fancontrol]("http://ubuntuforums.org/showthread.php?t=42737")

---

### Post by abkarch on 2010-06-11
Eh thats all very confusing. im brand new to ubuntu, so using simple terms is there a way to do this?

---

### Post by abkarch on 2010-06-11
anyone...?

---

### Post by nhasian on 2010-06-11
if you want fancontrol, you will need to follow that tutorial.  as far as i know, there isn't another way.  I know it may seem daunting, but actually its not too hard.  first you install the lm-sensors, then you run the pwmconfig and hit enter a bunch of times as it already highlights the defaults.  you'll notice various fans turning on and off during the pwmconfig testing.  then when its all done you just run fancontrol and your system will be quiet again :)

---

