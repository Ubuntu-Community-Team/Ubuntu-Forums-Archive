---
title: "tellico issue jaunty"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by chilimac02 on 2009-06-09
I get this error when I try to start Tellico

[I]There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not read network connection list.
/home/justin/.DCOPserver_justin-laptop__0

Please check that the "dcopserver" program is running![/I]

Then when I close that box I get:

[I]Could not find mime type
 application/octet-stream[/I]

Can someone point me in the right direction??

---

### Post by duanedesign on 2009-06-09
from what I can tell it is a permission problem. 

Open Terminal and run the following while in your Home folder /home/justin/  

```
ls -l .K*
```

and see what the permissions are on your .KDE folder. You want to make sure they are not root.


If you get something like below, where it says root, you need to change that.

```
 drwxr-xr-x  4 root        root            4096 2009-04-09 08:14 .KDE 
```

While in your Home directory run the following in Terminal:

```
sudo chown -hR [your login name] .kde
```

---

### Post by chilimac02 on 2009-06-11
yup that did it. Thanks!!

---

