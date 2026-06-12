---
title: "Printing to Windows XP printer - getting started"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by windmill77 on 2009-01-05
I am trying to set up Printing to Windows XP printer from Ubuntu.

I have samba installed and can share files etc and see the printer via the network server browser

When I go set up the printer in Ubuntu the "new" button is disabled so I can't get to 1st base.

I have read the how to document but it does not help me with this issue. It does not seem to be a permissions issue as I tried it while logged in as root, or is it?

CUPS is installed.

Any help would be great.

---

### Post by pytheas22 on 2009-01-05
You're talking about the program available at System>Administration>Printing, correct?  That's weird that the 'New' button is grayed out.

Does it work if you launch it from the command-line by typing:
```

sudo system-config-printer
```

---

### Post by windmill77 on 2009-01-05
Thanks pytheas22,

Yes Thats correct

System>Administration>Printing

Its greyed out.

Trying via Terminal does not work either.

Should I uninstall all the CUPS related stuff and reinstall?

---

### Post by pytheas22 on 2009-01-05
Reinstalling CUPS might help, but really this should not be necessary because by default CUPS should work.  Is this a fresh install of Ubuntu or have you been using it for a while and possibly mucked something up?  If you boot to the live CD, can you set up a printer there without a problem.

Also, have you tried playing around with the various settings in the file menu of the print manager?

I googled a bit but nothing came up about the 'New' button being grayed out.

---

