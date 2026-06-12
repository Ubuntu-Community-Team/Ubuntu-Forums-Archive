---
title: "want to copy a few files form a http site"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by stinger30au on 2009-03-16
i have used wget -r [www.nameofwebsite/name/of/directory](www.nameofwebsite/name/of/directory)

and this command works *TOO* well

it wants to copy the ENTIRE web site to my hdd

there is a heap of directorys full of data im chasing and flashgot will not do it that i can see anyhow

any ideas?

---

### Post by hyper_ch on 2009-03-16
look at httrack or webhttrack. You can specify filenames/extensions there.

---

### Post by stinger30au on 2009-03-16
ah ha!!!

i found the answer, after doing some reading i found this



wget - r -np [www.website](www.website)


this will do all directorys below the one specefied and will not go above the directory specefied

yee-haw!!

---

