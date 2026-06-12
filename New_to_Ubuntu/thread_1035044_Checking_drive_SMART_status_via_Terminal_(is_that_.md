---
title: "Checking drive SMART status via Terminal (is that possible)?"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by RichTJ99 on 2009-01-09
Hi,

I would like to check my hard drive SMART status through the terminal. 

Is there a command to do that?

Thanks,
Rich

---

### Post by blueridgedog on 2009-01-09
```
smartctl -i /dev/hda
```

Change /dev/hda to your drive.

---

### Post by forger on 2009-01-09
```

sudo apt-get install smartmontools
sudo smartctl --help
sudo smartctl -i /dev/sda

```

---

### Post by widda on 2011-04-03
huh?? I dont know where this comes from

---

### Post by widda on 2011-04-03
think i'm lost here

---

### Post by CharlesA on 2011-04-03
smartmontools requires a MTA (mail transfer agent) as one of the dependencies.

Try running this:

```
sudo updatedb
```
```
locate smartctl
```

---

