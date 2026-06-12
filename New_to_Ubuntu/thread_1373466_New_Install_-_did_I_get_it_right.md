---
title: "New Install - did I get it right?"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by DannStarr on 2010-01-05
Did a bit of an upgrade on the laptop, went up to 4GB Ram, and also fitted a 500GB HDD.

My Old HDD was 100GB and I was dual booting with Vista.

If I can get hold of a free Windows 7, I may dual boot with that in my new set up, if I cant it's all Ubuntu.

Here's what I did so far;

I chose to manually partition the drive.
I made an extended partition of 400GB.
Within that I made a 4GB Swap area
I made a 15GB logical partition mounted at / using ext4
I then made another logical partition for the remaining space mounted at /home also using ext4

The rest is left as unused space which may one day be occupied with windows 7.

Do I appear to have done it right? how might it have been done differently, are there any benefits to what I have done, or have I balls'd it up completely?

All suggestions welcome

---

### Post by Cheesemill on 2010-01-05
Sounds good to me.

I'm not sure about Windows 7 but I know XP wanted to be installed on the first partition so ideally your free space should be at the start of the drive.
Someone who has 7 will be more informed though :)

---

### Post by Methuselah on 2010-01-05
Sounds fine to me.

---

### Post by gabo.cr on 2010-01-05
Vista likes to be install in the first partition too, I don't know about Win 7.

---

### Post by cartisdm on 2010-01-05
That looks great, I dual boot with Win 7 (on the first partition), but I'm pretty sure people have had success with putting it on the second partition like you will be doing

---

### Post by DannStarr on 2010-01-05
Hmmm, yeah good point, I forgot that windows likes to be over at the start, I cant see 7 being any different, but, if I do get it i'll give it a try

---

