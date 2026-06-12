---
title: "installsation of trgraph in ubuntu 10.10"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by hossain258 on 2011-04-13
Hi
this is hossain i was trying to install trgraph in ubuntu 10.10. and I have installed trgraph using following site

[http://mzislam.net/](http://mzislam.net/) 

I followed the steps which were given in that site. but when I was try to use the command its showing like 

hossain@ubuntu:~$ export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/hossain/mgl/bin/glnx86
hossain@ubuntu:~$ cd mgl/bin/glnx86/
hossain@ubuntu:~/mgl/bin/glnx86$ ./trgraph
bash: ./trgraph: No such file or directory

Please can u help me n this .

thank you

---

### Post by rosencrantz on 2011-04-13
Hi hossain,
please post the output of
ls -l /home/hossain/mgl/bin/glnx86
It looks like trgraph ins't where it's supposed to be.

Cheers,
rosencrantz

---

