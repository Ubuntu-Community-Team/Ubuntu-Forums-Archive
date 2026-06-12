---
title: "Slow boot with verbose text"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by Jaraxle on 2009-10-23
I don't think this has been asked before, but is there a way to actually slow down the system boot (so that it takes longer) and make the text displayed even more verbose. As in, more detailed information.

In my never-ending quest of learning linux, I would like to be able to read more easily what is outputed to the screen. I also know that there is a lot more going on beyond the scenes that Ubuntu doesn't show, even with the boot quiet option off.

Thanks!

---

### Post by alphaniner on 2009-10-23
The majority of the information seen is during a non-quiet, non-splash boot stored in the /var/log/dmesg file.

---

### Post by Jaraxle on 2009-10-23
Thanks, I didn't know how to do that. I looked at that file and that should tell me all I need to know.

Just out of curiousity though, is there a way to do it in real time, at bootup? I'm asking because I remember that Red Hat had something like quiet, non quiet, and *really* non quiet boot. I think it was called verbose. 

I searched and searched, but apparently there doesn't seem to be a way to do this with Ubuntu. I'm just a little surprised that it wouldn't be an option.

---

### Post by alphaniner on 2009-10-23
Someone once told me you could pause the process by hitting, appropriately enough, the Pause key, but I tried it and it didn't work.  I could swear I was able to pause the process on another distro though.

It does seem to make sense to have a more verbose boot, though.  Did you try debug?  I just found [this]("http://www.tldp.org/HOWTO/BootPrompt-HOWTO-3.html") linked from an Ubuntu Documentation page. It says

> Specifying debug as a boot argument will set the console loglevel to 10, so that all kernel messages appear on the console.

Also, I forgot to mention that you can access /var/log/dmesg simply by typing **dmesg** in the terminal.  And dmesg is not just a record of the boot process, it can be updated after the system is up and running.  Just FYI.

---

