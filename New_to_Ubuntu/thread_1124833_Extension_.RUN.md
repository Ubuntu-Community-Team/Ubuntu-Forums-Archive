---
title: "Extension: .RUN"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by rick astley on 2009-04-13
i have an ATI 2600 graphics card. i downloaded the linux drivers for it from the AMD website. the file extension is **.run**

where do i go from here?

thanks,
rick

---

### Post by skymera on 2009-04-13
a .run

ok open the terminal:

```
 cd /location/of/file.bin 
chmod +x file.bin
./file.bin 
```

OR install drivers using Envy (Easy, 1 step and it's easy :D)

```
 sudo apt-get update
sudo apt-get install envyng-core
sudo envyng -t 
```

Choose 3, it'll download the drivers, compile the kernel bits and then restart. Boom done :) Works a charm for me and my 4870

---

