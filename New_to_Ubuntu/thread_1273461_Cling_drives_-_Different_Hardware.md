---
title: "Cling drives - Different Hardware"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by dmcdaniel on 2009-09-23
So I am new to this cloning drives. 

I have a system set exactly how I like it. I want to clone it:

Problem: I have different hardware. 

Question: Will this work? I don't know how Ubuntu "drivers" work. Does Ubuntu have all "drivers' installed so I can do this sucessfully?

Thanks,
dmcdaniel

---

### Post by LewRockwell on 2009-09-23
> **dmcdaniel said:**
> So I am new to this cloning drives. 

I have a system set exactly how I like it. I want to clone it:

Problem: I have different hardware. 

Question: Will this work? I don't know how Ubuntu "drivers" work. Does Ubuntu have all "drivers' installed so I can do this sucessfully?

Thanks,
dmcdaniel

While cloning an operating system which was initially installed on one set of hardware for usage on a separate machine with different hardware might appear to work initially...

It is not recommended

.

---

### Post by nhasian on 2009-09-23
as long as you are not cloning from an LVM or RAID hard disk, to another system, i think you will be okay.  all of the drivers are auto-detected on startup.  that's how the liveCD works you know :)
the only issue is that if you have a different graphics adaptor like if you went from ATI to Nvidia or something you will need to install the restricted driver manually.

---

### Post by dmcdaniel on 2009-09-23
> **nhasian said:**
> as long as you are not cloning from an LVM or RAID hard disk, to another system, i think you will be okay.  all of the drivers are auto-detected on startup.  that's how the liveCD works you know :)
the only issue is that if you have a different graphics adaptor like if you went from ATI to Nvidia or something you will need to install the restricted driver manually.

Thanks for the information. I believe they are both ATI. The Motherboards are almost the same, its just a newer version and same with the processor. Going from an Intel 8200 to an Intel 8400. 

Thanks again,
dmcdaniel

---

