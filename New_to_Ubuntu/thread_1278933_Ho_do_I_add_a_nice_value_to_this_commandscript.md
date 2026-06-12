---
title: "Ho do I add a nice value to this command/script?"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by ankspo71 on 2009-09-30
Hi,

I am setting up my 2nd hard drive to to seed linux distros in Transmission automatically on start up. I already have the drive set up to mount automatically at start up, and I found a workaround to delay the start of Transmission until the drive is mounted. Everything works as is, but I need to change the nice value so that Transmission will use a little less system resources. I want to be able to seed and watch flash videos smoothly at the same time.

I have this entry in my startup applications list:
```
sh /home/james/autostart-transmission.sh
``` 

And the shell script is this:
```
#!/bin/bash
sleep 15 && transmission -m ;
```

"man nice" and "man --help" says this:
-n, --adjustment=N   add integer N to the niceness (default 10).

Does this mean I change my start up script to this?
```
#!/bin/bash
sleep 15 && transmission -m -n, --adjustment=3 ;
```
I tried with and without the comma but Transmission wouldn't start. I am a bit confused on this one. :P
Thanks,
James.

---

### Post by ankspo71 on 2009-09-30
Hi Again,

Nevermind, I found out I was doing it backwards. :D

What I needed was this...
```
#!/bin/bash
sleep 15 && nice -n 3 transmission -m ;
```

Hmm, I see sudo is required to make negative values... that kind of ruins my next idea lol. Anyways, problem solved.

Thanks again,
James

---

