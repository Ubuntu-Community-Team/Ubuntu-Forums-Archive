---
title: "closing terminal after opening app (script)"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by luvgirl12345 on 2011-02-11
Well I'm running a script because something doesn't work with my tor program... if someone knows why that is please tell me. My question would be how do I run this script:

```
#!/bin/bash
sudo /etc/init.d/privoxy restart
pithos 

```

then close the terminal but keep pithos open. adding & after pithos doesn't work... just exits without opening program then...

thanks in advance
sorry about my english (im german)

---

### Post by robsoles on 2011-02-12
If the script is in a file at /home/some-user/scripts/this-script.sh then```
cd /home/some-user/scripts
./this-script.sh
``` will start and the following line should start it from anywhere (but I've been wrong before)```
/home/some-user/scripts/this-script.sh
```Add '&' to the call to your script rather than in the script in the call to pithos - should give you a terminal you can close and leave pithos running no probs.```
/home/some-user/scripts/this-script.sh &
```


This might be of interest to you too: [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

### Post by Crusty Old Fart on 2011-02-12
In addition to what Robsoles wrote (Howdy Rob...been a while.), you can use the following line at the end of your calling script to end the calling script's process and thus, close the terminal window:
```

kill $$

```So, your complete script could look something like this:
```

#!/bin/bash
sudo /etc/init.d/privoxy restart
/full/path/to/pithos &
kill $$

```

---

### Post by DougieFresh4U on 2011-02-12
> **luvgirl12345 said:**
> Well I'm running a script because something doesn't work with my tor program... if someone knows why that is please tell me. My question would be how do I run this script:

```
#!/bin/bash
sudo /etc/init.d/privoxy restart
pithos 

```

then close the terminal but keep pithos open. adding & after pithos doesn't work... just exits without opening program then...

thanks in advance
sorry about my english (im german)

**nohup pithos**
then you can close terminal

**EDIT:** I know that the **nohup** works with apps but not sure how well with scripts

---

### Post by Crusty Old Fart on 2011-02-12
> **DougieFresh4U said:**
> **nohup pithos**
then you can close terminal
Nice. I never knew about the nohup command before now. Thanks.

---

