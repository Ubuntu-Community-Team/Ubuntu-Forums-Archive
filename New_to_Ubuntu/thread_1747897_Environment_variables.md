---
title: "Environment variables"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Buleste on 2011-05-03
I've recently installed Ubuntu 11.04 as a total newbie and it works fine (to go from windows to Ubuntu takes some getting used too).

I've followed a tutorial to get an SDk up and running and that works fine. However after trying to compile some source code I got this message. 

```
make[1]: Entering directory `/opt/ds2sdk/ireader/ebook/obj'
makefile:4: *** "Please set DS2SDKPATH in your environment: export DS2SDKPATH=<path to>ds2sdk". Stop.
```
I would like to know which file I should edit to set up the DS2SDKPATH (the DS2SDK is in /opt/ds2sdk) and also what I should enter in to the file.

Do I put ```
export DS2SDKPATH=/opt/ds2sdk
``` into .bashrc or do I put something else somewhere else?

---

### Post by m_duck on 2011-05-03
Yep, that's the way I'd do it. After editing ~/.bashrc you will have to source the file to make Ubuntu aware of the changes:```
source ~/.bashrc
```From then on though, it will get automatically sourced on log in.

You can double check that it has worked by issuing the following from the terminal:```
env | grep DS2SDKPATH
```The ouput from that should just be ***DS2SDKPATH=/opt/ds2sdk***. That should work anyway!

---

### Post by Buleste on 2011-05-03
Thanks for the advice. 

I've tried all that and checked with the env code you gave and it gave the correct path etc. tried to complile the code again and got the same error.


EDIT: Found the problem. It's a problem in the makefile not Ubuntu

---

