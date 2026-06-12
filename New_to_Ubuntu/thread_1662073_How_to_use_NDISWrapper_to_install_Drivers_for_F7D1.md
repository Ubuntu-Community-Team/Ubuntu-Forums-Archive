---
title: "How to use NDISWrapper to install Drivers for F7D1101V1"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by RichieB07 on 2011-01-07
I read that you can use NDISWrapper to install drivers for Wifi adaptors, and specially a lot of cases with the F7D1101V1 Belkin Basic Adaptor.   The problem is I never found out how exactly.  

NDISWrapper is installed on the computer and the CD for the drivers is inserted, what do I do now?

Any help would be awesome!

---

### Post by Hippytaff on 2011-01-07
try installing the GUI for ndiswrapper, makes life easier - it's called ndisgtk

---

### Post by RichieB07 on 2011-01-07
I found out how to do it here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart)

---

### Post by wep940 on 2011-01-07
That link is the hard way to do things.  Ndisgtk takes care of all of that for you without all the command line typing.  Start ndisgtk, select new, point it to the driver .inf file.  That's it.  Couldn't be simpler.

---

### Post by RichieB07 on 2011-01-07
> **wep940 said:**
> That link is the hard way to do things.  Ndisgtk takes care of all of that for you without all the command line typing.  Start ndisgtk, select new, point it to the driver .inf file.  That's it.  Couldn't be simpler.

Yeah, down near the bottom it talks about the Ndisgtk.  However it never hurts to learn the hard way sometimes.

---

