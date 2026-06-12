---
title: "WinXP Emergency"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-10-28
At school.  100 point essay is on my flash drive.  I can't print due to networking restrictions.  Is there any way I can get XP to recognize my storage?  The teacher doesn't accept late work.  O.O

---

### Post by sky_ceiling on 2010-10-28
> **TriBlox6432 said:**
> At school.  100 point essay is on my flash drive.  I can't print due to networking restrictions.  Is there any way I can get XP to recognize my storage?  The teacher doesn't accept late work.  O.O

If it is on a school system, you probably wont be able to make modifications to their computer. If you cannot plug it in and use, there may not be a lot you can do, unless you have access to your own computer?

---

### Post by TeoBigusGeekus on 2010-10-28
What is your flash drive's file system?

---

### Post by CharlesA on 2010-10-28
Shouldn't need to have admin access to get data off a flash drive.

That is, unless they disabled the use of USB devices (which is a good idea for a school tbh)

---

### Post by TriBlox6432 on 2010-10-28
I've always been able to use my flash drive before.  Here's a screenshot.

---

### Post by endotherm on 2010-10-28
are you saying that your flash drive is formatted as ext3/4 or another linux-only filesystem?

if so, this util may work, but google as there are probably others:
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by TriBlox6432 on 2010-10-28
would re formatting it from my Ubuntu laptop help?  I'll try.  =/

---

### Post by CharlesA on 2010-10-28
It's likely that they made it so that non admins cannot add new hardware (which a thumb drive is) - contact the IT guys and see if they can help you get your data off the thumb drive.

---

### Post by TeoBigusGeekus on 2010-10-28
> **TriBlox6432 said:**
> would re formatting it from my Ubuntu laptop help?  I'll try.  =/

Yeah, format it as fat32 (backup first).

---

### Post by TriBlox6432 on 2010-10-28
Filesystem type: msdos, so I doubt that's the problem.  I'll run to the IT manager quickly durring lunch.

---

### Post by CharlesA on 2010-10-28
> **TriBlox6432 said:**
> Filesystem type: msdos, so I doubt that's the problem.  I'll run to the IT manager quickly durring lunch.

That's the correct file system. The IT manager should be able to get it sorted for you. :)

---

### Post by TriBlox6432 on 2010-10-28
Alright.  It was a lack of driver, and students aren't allowed to install drivers.  The IT manager was able to drag and drop my file into My Documents folder, so now I can go to the library and print it off.  Thanks!! :D

---

### Post by CharlesA on 2010-10-28
Glad they got it working. :)

Don't forget to mark the thread as solved from the thread tools menu.

---

### Post by TriBlox6432 on 2010-10-28
Yeah, it was a huge relief.  Well, until the teacher gave me a test to do instead because my assignment wasn't "done".  Ugh.  I seriously regret taking Honors classes.

---

### Post by oldsoundguy on 2010-10-28
Think you are going to see more and more of USB blocking on Windows based networks as that is the quick down and dirty way to  stop the spread of thumb drive introduced malware that is becoming a real problem.

until there is an auto malware scan of the devices that the IT's can install, blocking will be the way they go.

---

### Post by CharlesA on 2010-10-28
Agreed. That definitely helps cut down the spread of usb-borne malware/virii.

---

