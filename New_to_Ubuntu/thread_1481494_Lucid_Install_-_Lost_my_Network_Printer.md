---
title: "Lucid Install - Lost my Network Printer"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by BeeSharp on 2010-05-12
I had a network printer up and working, but since I went to Lucid it's gone. :(

It's a true network printer off a router, not a shared device off a PC.

I can pull up the Printing window, but the Add a Printer option is gray'ed out. I can see the Printer in the Network window PS-120C81 (Print Server), but it's coming up as an unknown device. It's an old HP 6L Laser printer.

Thanks

---

### Post by cariboo on 2010-05-12
Try restarting cups to see if that helps:

```
sudo service cups restart
```

---

### Post by BeeSharp on 2010-05-12
That did the trick - thank you!

---

