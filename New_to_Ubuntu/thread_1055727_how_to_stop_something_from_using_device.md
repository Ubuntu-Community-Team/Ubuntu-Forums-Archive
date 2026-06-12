---
title: "how to stop something from using device"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by mishathegoat on 2009-01-31
Hey everyone,

Is there a way to stop a program from using a device?
Something that in my mind would look similar to:

```
killall -program_that_is_using /dev/video0
```

Much help is appreciated thanks.

---

### Post by prshah on 2009-01-31
> **mishathegoat said:**
> 
Is there a way to stop a program from using a device?
Something that in my mind would look similar to:
```
killall -program_that_is_using /dev/video0
```


Since all devices in linux are treated as files, you can use the lsof (list open files) command, in a fashion similar to (untested)```
sudo killall `lsof | grep \/dev\/video0 | cut -f 1 -d " "`
```

More information on lsof with ```
man lsof
```

---

