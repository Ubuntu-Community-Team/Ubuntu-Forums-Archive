---
title: "Floppy access in Intrepid"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by nifty542 on 2009-02-14
Hi, all

Could anyone tell me if there is a fix yet for the above?
Absolute beginner, so don't know what "modprobe" is...

Thanks, in advance.
Regards
Nifty:confused:

---

### Post by philinux on 2009-02-14
You could try installing fdutils from synaptic. I dont have a floppy any more and these utils wont work with a usb floppy.

---

### Post by Elfy on 2009-02-14
floppy doesn't get added by default anymore it seems - is it there in your /etc/modules
file?

From a terminal 

```
cat /etc/modules
```

---

### Post by nifty542 on 2009-02-14
Thanks a lot! Will try that.
Thanks for the very quick reply!
I am used to just clicking on the word thanks, in Mepis. Is there an equivalent here?

Regards
Nifty

---

### Post by nifty542 on 2009-02-14
Hi

Forestpixie, thanks. No, there are fd entries, but none of them work. I will try fdutils.
Thanks
Nifty

---

### Post by Elfy on 2009-02-14
I believe it needs to have

floppy 

in /etc/modules


There was a thanks - but there's a problem - so it's gone for the moment

---

