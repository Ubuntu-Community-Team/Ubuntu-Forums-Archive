---
title: "Having a problem opening and extracting data from a .img file"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-07-01
I'm running Ubuntu 10.04 and have an image that I made using dd earlier today. I imaged an entire disk that was NTFS file system. Now I need to open up that image and copy out the data inside. When I try to use Archive Manager I'm given the following error message through a gui window.

```

Could not create the archive

Archive type not supported.

```

What can I do to deal with this? I don't want to install windows on anything (even as a vm) and I don't know what to do with a nearly 80 GB image that 77 GB of it is unused space.

Can anyone suggest something that will help?

I have Wine . . .

I can install something Linux, even if it cli only.

---

### Post by wolfen69 on 2011-07-01
Installing p7zip-full may help.

---

### Post by ClientAlive on 2011-07-01
Oh-my-goodness. There is such an easier way to do this. It's called the cp command. Turns out Linux will mount and access ntfs. I don't know why I put myself through all that.

1 drive down, 2 to go.

Thanks for your help man. I don't think I would have thought of that or even come across the information had I not run into you.

Have great 4th of July weekend!

---

### Post by jtarin on 2011-07-02
RAR will do it too.

---

### Post by ClientAlive on 2011-07-02
> **jtarin said:**
> RAR will do it too.


I'm about to try the craaayzeee @$$ script I think will do something really cool. I got the idea from a guy on another thread showed me how to use dd to zero out the unused space. I don't know if I've got it right but I got the data safely off there already, so, might as well give it a try.

The guy said

```

dd if=/dev/zero of=./zero
rm ./zero

```

That's exactly how he wrote it but I think he intended that, that be two separate codes run one after the other. He said after that you can image it like normal and the gzip it to get crazy compression.

I'd like to try:

```

dd if=/dev/zero of=./zero; rm ./zero | dd if=/dev/sda of=/path/to/destination/filename.img notrunc,noerror bs=8 | gzip filename.gz /path/to/file/filename.img

```

Or maybe it should be:

```

dd if=/dev/zero of=./zero | rm ./zero | dd if=/dev/sda of=/path/to/destination/filename.img notrunc,noerror bs=8 | gzip filename.gz /path/to/file/filename.img

```

If that's right (don't know if rm or dd take std in) then a guy could just as easily use zip instead of gzip. That might be more suitable for passing it to someone who uses windoze.

:D
------------------

Edit:

I don't think rm takes std in. Maybe I need to look into xargs? Idk.
------------------

Edit:

I think it has to go:

```

dd if=/dev/zero of=./zero | xargs rm ./zero&& dd if=/dev/sda of=/path/to/destination/filename.img notrunc,noerror bs=8k | gzip filename.gz /path/to/file/filename.img

```

But I'm using my 250 GB external. The only one I have. My baby! I think I'll see fi someone comes and comments on that script before I try running it.

Not sure about that value for bs either. I saw "bs=8k" in another thread. I think that means 8 kilobytes (or 8000 bytes)?

:)

---

