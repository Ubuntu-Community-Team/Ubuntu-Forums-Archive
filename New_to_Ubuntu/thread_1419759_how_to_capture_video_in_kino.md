---
title: "how to capture video in kino"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by mafaldaspeaks on 2010-03-02
Could you help me please on how to capture from a digital video camera using kino?

I have the videocam connected to the laptop by firewire and when I open kino and choose capture, it gives a warning "raw 1394 kernel module not loaded or failure to read/write /dev/raw/1394" (please see bottom part of image attached). What does this message mean and how can I resolve it?

I'm using ubuntu 9.10 64bit.

---

### Post by cariboo on 2010-03-03
Have a look at [this]("https://help.ubuntu.com/community/Firewire"), page it helped me when I had the same problem.

---

### Post by chengmichael on 2010-06-21
> **cariboo907 said:**
> Have a look at [this]("https://help.ubuntu.com/community/Firewire"), page it helped me when I had the same problem.

i am using Ubuntu 10.04, and i am getting the same error message in kino at the bottom of the screen when trying to capture video through my firewire:

WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!

i looked at the page you suggested but being new to this i don't understand any of the information!

any help?

michael

---

### Post by lotharmat on 2010-06-21
I had this problem and got round it with the following command:

```
chmod 777 /dev/raw1394
```

Worked a treat after that.

Let us know how you get on and mark the thread as solved if it works. This will help others find the solution.

---

### Post by chengmichael on 2010-06-21
thanks for the quick reply -

i opened the terminal, and then typed 
[FONT=monospace]
[/FONT]chmod 777 /dev/raw1394

the response i got was:

chmod: changing permissions of `/dev/raw1394': Operation not permitted


is there something i'm missing?

michael

---

### Post by lotharmat on 2010-06-21
Sorry try sudo in front of the chmod command.

:oops:

---

### Post by chengmichael on 2010-06-21
you're a genius - seems to work, gonna try to capture video now.

sorry, stupid question #4 - how do i mark this thread as solved...?

---

### Post by lotharmat on 2010-06-21
It is in thread tools (at the top of the thread)

Or it may only be possible for the person who created the thread..

---

### Post by chengmichael on 2010-06-21
can't mark this thread...but thanks for all the help!!

m

---

### Post by maizuddin35 on 2010-06-21
better get this one solved, if don't nobody will know this is the right way. I don't know how to get this thing right. until o found this one. thanks to this post too..:)

---

### Post by no2498 on 2010-06-21
edit your first post
solved how to capture video in kino

---

