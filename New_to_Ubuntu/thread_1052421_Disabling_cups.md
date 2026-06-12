---
title: "Disabling cups?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by S0m3th1ngw13rd on 2009-01-27
Is there a way I can disable cups?  I don't think I need it(not 1 printer in the house). I might be wrong ,not sure. Can someone please advise?

Thanks ahead of time.

---

### Post by tdayal on 2009-01-27
If you go to Preferences > Sessions, you can uncheck services you don't want at startup, so you probably want to uncheck the printing services. 

Next time you reboot, no more printing services.

---

### Post by yeats on 2009-01-27
I would think that unless there's a specific reason you don't need CUPS, you would want to leave it alone.  With no active printers, it can't be using much in the way of resources. . . 

But, since you're asking :-)  . . . have you considered a complete removal?  Reinstalling later is no sweat, especially if you don't have it configured already.

UPDATE: tdayal posted at the same time - that suggestion might be better :-)

---

### Post by bwang on 2009-01-27
Why would you want to disable it? Is CUPS causing you any trouble?

I think that 
```
sudo apt-get remove cups-pdf cupsys cupsys-bsd cupsys-client cupsys-common cupsys-driver-gutenprint libcupsys2
```
will remove CUPS, however, I don't recommend removing it.

---

### Post by S0m3th1ngw13rd on 2009-01-27
Don't have a printer at all and don't plan on buying one so don't need cups.  Unless it is used for something else also?

---

### Post by cariboo on 2009-01-27
One other way to accomplish what you want is to stop cups from starting at boot up, open a Applications-->Accessories-Terminal and type:

```
sudo update-rc.d -f cups remove
```

That way if you ever need to connect a printer, you don't have to reinstall cups, you can just start the service as needed.

Jim

---

### Post by S0m3th1ngw13rd on 2009-01-27
> **cariboo907 said:**
> One other way to accomplish what you want is to stop cups from starting at boot up, open a Applications-->Accessories-Terminal and type:

```
sudo update-rc.d -f cups remove
```

That way if you ever need to connect a printer, you don't have to reinstall cups, you can just start the service as needed.

Jim

Thanks Jim, this disabled it from starting at boot.

---

