---
title: "[SOLVED] HP F380 suddenly not printing"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by trekguy on 2008-12-18
Ubuntu 8.04
HP F380

It has worked flawlessly up til I installed the HP Toolbox earlier this week.  Now, it won't print.  I've tried uninstall/reinstall... but it seems that it remembers it, or something... when I restart, it's there again.  I've gotten "printer is not connected", I've gotten print jobs in the queue, that never print, and flashing error codes on the printer itself.

I think I need to get rid of it, and install it fresh... not sure how to exactly go about it.

Help, I need to print the Christmas letter!

---

### Post by trekguy on 2008-12-18
As of right now, it sends the print job.... print job box says "processing".... then the flashing panic lights go off the printer.  I push the power button on the printer, to reset it, then the print job is gone.

---

### Post by kansasnoob on 2008-12-18
> **trekguy said:**
> Ubuntu 8.04
HP F380

It has worked flawlessly up til I installed the HP Toolbox earlier this week.  Now, it won't print.  I've tried uninstall/reinstall... but it seems that it remembers it, or something... when I restart, it's there again.  I've gotten "printer is not connected", I've gotten print jobs in the queue, that never print, and flashing error codes on the printer itself.

I think I need to get rid of it, and install it fresh... not sure how to exactly go about it.

Help, I need to print the Christmas letter!

How did you install the hp tool box?

Did you install the hplip-gui from synaptic?

---

### Post by trekguy on 2008-12-18
> **kansasnoob said:**
> How did you install the hp tool box?

Did you install the hplip-gui from synaptic?

I think so.  The HP Toolbox is gone now... I thought that might fix my problem.  Still getting the error on the printer...

---

### Post by trekguy on 2008-12-18
System> Admin> Printing> Print Test Page... printer icon appears for about 3-4 seconds... then disappears.  There is no print job in the queue for the "Print Test Page"... also, Print Test Page does not result in an error on the F380 itself.

---

### Post by kansasnoob on 2008-12-18
> **trekguy said:**
> I think so.  The HP Toolbox is gone now... I thought that might fix my problem.  Still getting the error on the printer...

Go to System > Administration > Synaptic Package Manager and in the search window search hplip.

Choose to reinstall hplip and install hplip-gui.

That should bring in the dependencies.

---

### Post by trekguy on 2008-12-18
> **kansasnoob said:**
> Go to System > Administration > Synaptic Package Manager and in the search window search hplip.

Choose to reinstall hplip and install hplip-gui.

That should bring in the dependencies.

This is what's installed now...

hpijs
hplip
hplip-data
hplip-gui

Also, the versions are 2.8.2-_Oubuntu8.1_   Is that right?????????


Oh yeah.... still get error on printer.

---

### Post by kansasnoob on 2008-12-18
> **trekguy said:**
> This is what's installed now...

hpijs
hplip
hplip-data
hplip-gui

Also, the versions are 2.8.2-_Oubuntu8.1_   Is that right?????????


Oh yeah.... still get error on printer.

But, did you click on reinstall? That may resolve any unmet dependencies.

---

### Post by kansasnoob on 2008-12-18
Or go to Terminal and:

```
sudo apt-get install --reinstall hplip
```

---

### Post by trekguy on 2008-12-18
> **kansasnoob said:**
> But, did you click on reinstall? That may resolve any unmet dependencies.

Ahhhh... "Mark For Reinstallation" !!!

[SIZE="5"]**Printing!!!**[/SIZE]

Christmas is saved!!

Thank you so much!

---

