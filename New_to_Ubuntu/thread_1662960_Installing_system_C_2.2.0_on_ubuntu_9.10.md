---
title: "Installing system C 2.2.0 on ubuntu 9.10"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by rohitmakhija on 2011-01-08
i Everyone,

I am new to linux ubuntu, I would like to work on SystemC

I followed the following steps as mentioned in the thread above


[COLOR=Blue]Step1 : download systemC 2.2.0 from system.org 
    tar -zxvf systemc-2.2.0.tgz
     cd systemc-2.2.0 


Step2 : [/COLOR]       [COLOR=Blue]

If using SystemC version 2.2.0, and make errors out with the following:[/COLOR] [COLOR=Blue]

../../../../src/sysc/utils/sc_utils_ids.cpp: In function int  'sc_core::initialize()':[/COLOR] [COLOR=Blue]
../../../../src/sysc/utils/sc_utils_ids.cpp:110: error: 'getenv' is not a  member of std
../../../../src/sysc/utils/sc_utils_ids.cpp:111: error: 'strcmp' was not  declared in this scope

Then change the includes in the file  systemc-2.2.0/src/sysc/utils/sc_utils_ids.cpp to look like the  following: [/COLOR] [COLOR=Blue]


#include "sysc/utils/sc_report.h"[/COLOR]  [COLOR=Blue]
#include "string.h"
#include "cstdlib"



Step3:[/COLOR]  [COLOR=Blue]
  ./configure
   make install

[COLOR=Black]but after following these steps I get following errors

make[5]: *** [install-data-local] Error 1
make[5]: Leaving directory `/root/Desktop/systemc-2.2.0/examples/sysc/fft/fft_flpt'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/root/Desktop/systemc-2.2.0/examples/sysc/fft/fft_flpt'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/root/Desktop/systemc-2.2.0/examples/sysc/fft'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/root/Desktop/systemc-2.2.0/examples/sysc'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/root/Desktop/systemc-2.2.0/examples'
make: *** [install-recursive] Error 1


i need to install it urgently as i want to use eclipse which requires the installation of system C.

PLease help me...!

- Rohit
[/COLOR][/COLOR]

---

### Post by cariboo on 2011-01-09
You need to be root to install a a program eg:

```
sudo make install
```

---

