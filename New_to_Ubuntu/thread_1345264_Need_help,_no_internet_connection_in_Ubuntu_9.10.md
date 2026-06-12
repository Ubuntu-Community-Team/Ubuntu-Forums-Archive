---
title: "Need help, no internet connection in Ubuntu 9.10"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by newbieinubun on 2009-12-03
I have upgraded my OS from Ubuntu 9.04 to Ubuntu 9.10..but when i restarted my laptop, i cant connect to the internet..

---

### Post by suzypeppercorn on 2009-12-03
are you trying to connect with a wire or through wireless?

---

### Post by jquest68 on 2009-12-04
Same here I can't connect to the Internet. I'm trying the wireless way. But I do t want to mess up the wireless on my girl friends laptop(windows) my laptop is on ubuntu.

---

### Post by mikewhatever on 2009-12-04
Have you checked under System->Admin->Hardware Drivers? If that doesn't work, provide info about your wireless hardware.

---

### Post by suzypeppercorn on 2009-12-05
Some wireless cards don't work correctly in Ubuntu and need a proprietary driver to be enabled. The person above me has posted how to enable a proprietary driver. Try connecting to the internet through a wire before checking the list. If there is nothing in the list of drivers to use, there is still more to try.

Open a terminal and use the command lspci. Then post the output here.

---

