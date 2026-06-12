---
title: "python module problem"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by farhanshahid2009 on 2009-07-09
i have ubuntu 6.06 with python 2.4.3. Previously i downloaded a python tutorial from the internet which came with a module to make things simpler. by writing import module in python i could import that module. But now python says module does not exist. the same is the case with some other game examples i downloaded which came with their own modules.

---

### Post by d_liebscher on 2009-07-09
Hi,

can you post a link to one of these tutorials and to this module respectively?

Thanks
Daniel

---

### Post by farhanshahid2009 on 2009-07-09
[http://www.livewires.org.uk/_media/python/livewires-2.1-r2.zip?id=python%3Apackage&cache=cache](http://www.livewires.org.uk/_media/python/livewires-2.1-r2.zip?id=python%3Apackage&cache=cache)

---

### Post by d_liebscher on 2009-07-09
Hi,

I suppose, that your problem is the missing pygame library, which is uses by LiveWires Modules.

If this is the problem, you can solve it by installing the python-pygame package from Ubuntu repositories.

(alternatively: ```
 sudo apt-get install python-pygame
``` )

Daniel

---

