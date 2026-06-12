---
title: "dd command - skip and iseek options"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by newbuntuxx on 2011-03-07
Hey,

I was imaging my laptop using this command:

```
sudo dd if=/dev/sda of=laptop.img
```

But I needed to stop before the imaging was complete. This is the output that I got when I stopped the process:
108748530+0 records in
108748530+0 records out
55679247360 bytes (56 GB) copied, 77347.8 s, 720 kB/s

Now, I want to resume from where i left off, however, I don't know how to do that exactly.

I do understand that it is possible to use the "skip" or "iseek" option. But it takes blocks and not records/bytes.

I have searched for a way to convert records into blocks, but to no avail.

Can anyone help?

---

### Post by rbc on 2011-03-07
How about this?

sudo dd if=/dev/sda >> /path/to/img/file skip=55679247361 count=1

Second opinions anyone?

---

### Post by gmargo on 2011-03-07
You can't do redirection in the middle of the dd command.  And skip is in blocks, not bytes.
How about this instead?
```

sudo dd if=/dev/sda of=laptop.img skip=108748530 oflag=append conv=notrunc

```
> 
I have searched for a way to convert records into blocks, but to no avail.

records == blocks

---

### Post by newbuntuxx on 2011-03-09
> **gmargo said:**
> You can't do redirection in the middle of the dd command.  And skip is in blocks, not bytes.
How about this instead?
```

sudo dd if=/dev/sda of=laptop.img skip=108748530 oflag=append conv=notrunc

```

records == blocks


Records == blocks! ehehe...I guess I should've known that.

Thank you!

A quick question, and this is just to help me understand the dd command more:

can your line:
```
sudo dd if=/dev/sda of=laptop.img skip=108748530 oflag=append conv=notrunc
```

be written like this:

```
sudo dd if=/dev/sda of=laptop.img skip=108748530 seek=108748530 conv=notrunc

```

Is yours faster? 

Thanks again,

---

