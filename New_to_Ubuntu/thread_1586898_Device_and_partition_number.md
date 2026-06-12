---
title: "Device and partition number"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by jhaveri.hiral on 2010-10-02
Hello,

How do I get the device and partition number in which my ubuntu is present using a shell script???

I want to use this device and partition number to generate another shell script, so also guide how to generate another shell script file which has this device/partition number using shell script..

Thank you..

---

### Post by sisco311 on 2010-10-03
Try something like:

first_script:
```
#!/bin/bash

second_script "$(awk '{if ($2=="/") print $1}' /etc/mtab)"

```

second_script:
```

#!/bin/bash

echo the root partition is "$1"
```

---

### Post by PapaNerd on 2010-10-04
Here is another option:

```

#!/bin/sh
DEVICE=`df -h | awk '{if ($NF=="/") print $1}'`
echo $DEVICE
exit

```

---

