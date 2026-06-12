---
title: "How do I print?"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by jhsu802701 on 2009-12-08
I installed Ubuntu from command line for a minimal installation.

I downloaded and installed cupsys, but I cannot get into CUPS.

When I go to System -> Administration -> Services, I can see "Printer Service (cupsys)", but it's grayed out.  (In fact, everything in the "Services Settings" window is grayed out and inaccessible.)

---

### Post by LeifAndersen on 2009-12-08
Hmm...what printer do you have?

---

### Post by cariboo on 2009-12-08
Is cups running? Open a terminal and type:

```
ps ax | grep cups
```

to see if it is running. If it is you can access cups via the web interface at:

```
http://localhost:631
```

---

### Post by jhsu802701 on 2009-12-08
> **LeifAndersen said:**
> Hmm...what printer do you have?

My printer is a Brother MFC-240C.

---

### Post by jhsu802701 on 2009-12-08
Thanks for your help.  The localhost:631 suggestion worked.

My procedure for printer installation is:

[LIST=1]
[*]Download and install the package cupsys.
[*]If you are using a Brother printer, look at the brother-cups-wrapper-* packages for the one pertaining to your particular model. Download and install that particular package.
[*]Once cupsys and (if applicable) the brother-cups-wrapper-* packages are installed, go to [http://localhost:631/](http://localhost:631/) and follow the instructions.
[/LIST]
Of course, my printer is a Brother MFC-240C.  The procedure will be slightly different for other printers.

---

