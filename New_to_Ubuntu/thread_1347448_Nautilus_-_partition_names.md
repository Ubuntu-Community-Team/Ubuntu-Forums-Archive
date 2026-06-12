---
title: "Nautilus - partition names"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by rex4u on 2009-12-06
Hello all,

I got a simple problem.
I updated my system recently and after that nautilus shows my partitions as "500 GB Hard Drive : Linux(and other labels)" whereas earlier it would show only "Linux". Whats wrong ?

Kindly guide me.....

Thanks.........

---

### Post by laidback on 2009-12-06
This probably doesn't directly answer your question but it may help:-

I've used the following to (re)name volumes:-

Changing volume labels
$ mount (to get dev id)
$ sudo e2label /dev/sda? newlabel

obviously replace the ? with the correct number as per the mount output.

---

### Post by rex4u on 2009-12-06
Thanks laidback...
Its not about labels of the partition but only when I click "Computer" on desktop and it shows me all my drives & partitions where it is happening...

---

### Post by laidback on 2009-12-08
Try relabelling one of them and see what happens...

---

