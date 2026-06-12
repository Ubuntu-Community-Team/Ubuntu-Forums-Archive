---
title: "Automatic running of bash scripts"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-03-17
I have an entry in startup applications which runs this bash script, which will in turn run all bash scripts in the folder i specified, 
```

#!/bin/bash

for f in $(ls /home/mark/Documents/scripts/login_scripts/*)
do
bash $f &
done

```
I works flawlessly for all but one of the bash scripts which is the most basic one 
```

#!/bin/bash

amixer set Master 60%

```
I cant figure out why this one wont work, all its supposed to do is reset the volume to 60% and it works in the terminal, could it be something about the way amixer loads???

---

### Post by TeoBigusGeekus on 2011-03-17
Perhaps the script is executed before amixer loads.
Try putting a sleep command, ie
```
#!/bin/bash
sleep 5
amixer set Master 60%
```

---

