---
title: "external hard drive"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by phim12 on 2009-01-03
try to connect my external hard drive but says cannot mount volume can anyone help

---

### Post by Paqman on 2009-01-03
What format is the external drive formatted in? What happens when you open a terminal and enter:
```
sudo mount -a
```

---

### Post by phim12 on 2009-01-03
i havent opened a terminal yet so i open terminal type in what u said then. do i plug my hd in before i open terminal

---

### Post by Paqman on 2009-01-03
Yep, plug it in. If it doesn't automount then go to Applications > Accessories > Terminal and paste in that command followed by your password. It should spit out an error message, if you could copy and paste that it your reply it would be very helpful.

---

### Post by Bölvaður on 2009-01-03
You did not post the error message here so there is no way of knowing what is wrong. But it seems like you are having the popular bug with not unmounting the removable hdd when you used it last time in windows.

If you read the error message it might contain the solution to your problem.

Here is my solution though:
Connect the hdd in windows and unmount it (eject/saftly remove).


Disconnecting a hdd without unmounting it can have damaging effects.

---

### Post by phim12 on 2009-01-03
typed sudo mount -a came back with dbus error

---

### Post by phim12 on 2009-01-04
hi just to say thx for advice did want u said its now working fine thx again

---

