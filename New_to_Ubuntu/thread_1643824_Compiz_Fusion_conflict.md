---
title: "Compiz Fusion conflict"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by coolmego on 2010-12-12
I have successfully downloaded the package and enabled the 3D cube and wobbly window but they aint working so what should i do..!!

---

### Post by toupeiro on 2010-12-12
sometimes, compiz can crash when turning off and on certain features.

Please open a terminal window (Applications -> Accessories ->Terminal) and type:

> ps -ef | grep compiz

You should see at least one line like the one below, although the numbers may be different, it should say **/usr/bin/compiz**

```

toupeiro@mobius:~$ ps -ef | grep compiz
toupeiro  1862  1782  0 10:45 ?        00:00:22 /usr/bin/compiz
toupeiro  2978  2956  0 11:42 pts/0    00:00:00 grep --color=auto compiz
toupeiro@mobius:~$ 

```

If you **don't** see this line there in any way/shape/form, please type the following command in that same terminal window to restart compiz manually:

> compiz --replace &

To manually control compiz from the GUI, I recommend installing *Compiz Fusion Icon* from the software center.  You can perform restarts of compiz without needing to access the terminal if you are uncomfortable doing so.

Hope this helps.

Cheers!

-T.

---

