---
title: "Adobe Flash cannot find camera"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by mr.big_gun on 2009-05-04
I have a intel pro pc camera  model # cs430 
when i try to get on cam in firefox   and i goto adobe flash settings, it says  Cannot find camera

how do i fix this??? please help

---

### Post by mr.big_gun on 2009-05-04
I have a intel pro pc camera  model # cs430 
when i try to get on cam in firefox   and i goto adobe flash settings, it says  Cannot find camera

how do i fix this??? please help me

---

### Post by elqbenzo on 2009-07-07
solution (works with firefox, skype, etc): you have to start appliaction like this:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox &

instead of just:

firefox &

:) worked for me; you can make a wrapper shell script of this

---

### Post by lionstone on 2009-11-10
Wow, that was genius. I've been super-frustrated with flash freezing and crashing randomly when I start to use a webcam - running firefox with the script you provided solves the issue completely! Thanks!!!!!

---

### Post by fitzgeraldpaul on 2010-06-14
What does that mean ? how do you start a programme with LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox &

---

### Post by no2498 on 2010-06-14
fitzgeraldpaul

you need to put that in a terminal

applications, accessories, look down the list click terminal


hope that helps

---

