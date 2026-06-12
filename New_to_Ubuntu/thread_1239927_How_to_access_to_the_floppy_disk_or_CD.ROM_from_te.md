---
title: "How to access to the floppy disk or CD.ROM from terminal"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by mosquetero on 2009-08-14
Hi everyone!

I think it is a very easy question but surprisingly, I can't find it anywhere :(

How can I enter to the CD or the floppy disk using the terminal???

For the CD in Windows I used to type d:, for the floppy disk a:, but now it does not work with the ubuntu terminal. Any idea??

Thanks

---

### Post by credobyte on 2009-08-14
```
cd /media/cdrom

```

---

### Post by mosquetero on 2009-08-14
Thanks, but I am more interested in the floppy disk. Besides, I am starting to think that maybe I must mount them... :(

---

### Post by credobyte on 2009-08-14
```
mount /dev/fd0 /media/flopz
cd /media/flopz
```

---

### Post by colau on 2009-08-17
> **mosquetero said:**
> Hi everyone!

I think it is a very easy question but surprisingly, I can't find it anywhere :(

How can I enter to the CD or the floppy disk using the terminal???

For the CD in Windows I used to type d:, for the floppy disk a:, but now it does not work with the ubuntu terminal. Any idea??

Thanks
If the cdrom is mounted in /media/cdrom0
```

cd /media
ls
cd /media/cdrom0

```

---

