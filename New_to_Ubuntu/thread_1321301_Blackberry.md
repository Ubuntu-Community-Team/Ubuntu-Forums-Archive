---
title: "Blackberry"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by jinxs1591 on 2009-11-09
Can someone make a very easy to understand sticky or post on how to get blackberry support in ubuntu or how to use barry and where to get it.There are a few of us that really need this more than anything.

---

### Post by lavinog on 2009-11-10
```

p   barry-util                                                                       - Command line utilities for working with the RIM BlackBerry Handheld                       
p   barry-util-dbg                                                                   - Command line utilities for working with the RIM BlackBerry Handheld                       
p   barrybackup-gui                                                                  - GTK+ based GUI for backing up the RIM BlackBerry Handheld                                 
p   barrybackup-gui-dbg                                                              - GTK+ based GUI for backing up the RIM BlackBerry Handheld                                 
p   libbarry-dev                                                                     - Development files for libbarry                                                            
p   libbarry0                                                                        - Library for using the BlackBerry handheld on Linux                                        
p   libbarry0-dbg                                                                    - Library for using the BlackBerry handheld on Linux                                        
p   opensync-plugin-barry                                                            - Opensync Blackberry plugin, based on the Barry project                                    
p   opensync-plugin-barry-dbg                                                        - Opensync Blackberry plugin, based on the Barry project               

```
I would start by using synaptic to install barry-util, barrybackup-gui, opensync-plugin-barry
It looks like they are all in the universe repository (Community maintained open source software)

---

### Post by jinxs1591 on 2009-11-12
> **lavinog said:**
> ```

p   barry-util                                                                       - Command line utilities for working with the RIM BlackBerry Handheld                       
p   barry-util-dbg                                                                   - Command line utilities for working with the RIM BlackBerry Handheld                       
p   barrybackup-gui                                                                  - GTK+ based GUI for backing up the RIM BlackBerry Handheld                                 
p   barrybackup-gui-dbg                                                              - GTK+ based GUI for backing up the RIM BlackBerry Handheld                                 
p   libbarry-dev                                                                     - Development files for libbarry                                                            
p   libbarry0                                                                        - Library for using the BlackBerry handheld on Linux                                        
p   libbarry0-dbg                                                                    - Library for using the BlackBerry handheld on Linux                                        
p   opensync-plugin-barry                                                            - Opensync Blackberry plugin, based on the Barry project                                    
p   opensync-plugin-barry-dbg                                                        - Opensync Blackberry plugin, based on the Barry project               

```
I would start by using synaptic to install barry-util, barrybackup-gui, opensync-plugin-barry
It looks like they are all in the universe repository (Community maintained open source software)

I must need a new repository list because I have search for barry in synaptic and I come up empty

---

### Post by Tahakki on 2009-11-12
It may be in the Medibuntu repo. Check you've that enabled, yeah?

---

### Post by steveneddy on 2009-11-12
Looks like it is in the universe repos for Jaunty and above.

Here is the ppa for barry:

[https://launchpad.net/~doctormo/+archive/barry-snapshot](https://launchpad.net/~doctormo/+archive/barry-snapshot)

but looks like it is only released for jaunty and karmic.

It may run on Intrepid, but there will be dependency issues, I'm sure.

Read this also:

[http://ubuntuforums.org/archive/index.php/t-1054698.html](http://ubuntuforums.org/archive/index.php/t-1054698.html)

---

### Post by jinxs1591 on 2009-11-12
> **steveneddy said:**
> Looks like it is in the universe repos for Jaunty and above.

Here is the ppa for barry:

[https://launchpad.net/~doctormo/+archive/barry-snapshot](https://launchpad.net/~doctormo/+archive/barry-snapshot)

but looks like it is only released for jaunty and karmic.

It may run on Intrepid, but there will be dependency issues, I'm sure.

Read this also:

[http://ubuntuforums.org/archive/index.php/t-1054698.html](http://ubuntuforums.org/archive/index.php/t-1054698.html)
updated my whole system to 9.10. and got barry is there anywhere that will tell me how to use it, hook up my blackberry and nothing happen, not even a charge up

---

### Post by jinxs1591 on 2009-11-12
> **steveneddy said:**
> Looks like it is in the universe repos for Jaunty and above.

Here is the ppa for barry:

[https://launchpad.net/~doctormo/+archive/barry-snapshot](https://launchpad.net/~doctormo/+archive/barry-snapshot)

but looks like it is only released for jaunty and karmic.

It may run on Intrepid, but there will be dependency issues, I'm sure.

Read this also:

[http://ubuntuforums.org/archive/index.php/t-1054698.html](http://ubuntuforums.org/archive/index.php/t-1054698.html)
updated my whole system to 9.10. and got barry is there anywhere that will tell me how to use it, hook up my blackberry and nothing happen, not even a charge up

---

### Post by lavinog on 2009-11-13
What are you wanting to do?
What blackberry do you have?

---

### Post by jinxs1591 on 2009-11-13
I have the 8330m curve,So far I have it charging on its own that always seem to work without btool from my laptop. syncing and backup and anything else you can do just wont work
the backup I kinda guess the command...lol but I got this error (I have mass storage support off)
Desktop: error getting command table
Sent packet:
    00000000: 06 00 0a 00 40 00 00 01 00 00                    ....@.....

Response packet:

Sent packet:
    00000000: 00 00 08 00 0b 06 00 08                          ........

Response packet:
 this is where I hit a brick wall at ](*,)

---

### Post by steveneddy on 2009-11-14
A simple Google search revealed this answer:

[http://www.linux.com/news/embedded-mobile/mids/8210-syncing-your-blackberry-on-linux](http://www.linux.com/news/embedded-mobile/mids/8210-syncing-your-blackberry-on-linux)

---

### Post by jinxs1591 on 2009-11-20
still cant get sync to work

---

### Post by compeng on 2009-12-17
> **jinxs1591 said:**
> I have the 8330m curve,So far I have it charging on its own that always seem to work without btool from my laptop. syncing and backup and anything else you can do just wont work
the backup I kinda guess the command...lol but I got this error (I have mass storage support off)
Desktop: error getting command table
Sent packet:
    00000000: 06 00 0a 00 40 00 00 01 00 00                    ....@.....

Response packet:

Sent packet:
    00000000: 00 00 08 00 0b 06 00 08                          ........

Response packet:
 this is where I hit a brick wall at ](*,)
From what I have read you need the Blackberry on with mass storage support ON.  Try that.  I am going to install this weekend on 9.04 for a 8330.  Hopefully I find a way to sync with evolution too.  Good luck.

---

