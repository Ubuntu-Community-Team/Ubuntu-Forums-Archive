---
title: "SystemC installation"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by bharaths_jois on 2010-02-22
Hi,

I am trying to install systemC on my system and the getting stuck after 'make', during 'make install' where it pops an error in the examples directory.

```

Making install in examples
make[1]: Entering directory `/media/TechStuph/LiU/TDTS07/Tools/systemc-2.2.0/examples'
Making install in sysc
make[2]: Entering directory `/media/TechStuph/LiU/TDTS07/Tools/systemc-2.2.0/examples/sysc'
Making install in fft
make[3]: Entering directory `/media/TechStuph/LiU/TDTS07/Tools/systemc-2.2.0/examples/sysc/fft'
Making install in fft_flpt
make[4]: Entering directory `/media/TechStuph/LiU/TDTS07/Tools/systemc-2.2.0/examples/sysc/fft/fft_flpt'
make[5]: Entering directory `/media/TechStuph/LiU/TDTS07/Tools/systemc-2.2.0/examples/sysc/fft/fft_flpt'
make[5]: Nothing to be done for `install-exec-am'.
/bin/bash ../../../../config/mkinstalldirs .
for file in in_imag in_imag.1 in_imag.2 in_imag.3 in_imag.4 in_real in_real.1 in_real.2 in_real.3 in_real.4 out_imag.1.golden out_imag.2.golden out_imag.3.golden out_imag.4.golden out_real.1.golden out_real.2.golden out_real.3.golden out_real.4.golden  fft.cpp main.cpp sink.cpp source.cpp fft.h sink.h source.h; do \
		/usr/bin/install -c -m 644 ./$file ./$file; \
	done
/usr/bin/install: `./in_imag' and `./in_imag' are the same file
/usr/bin/install: `./in_imag.1' and `./in_imag.1' are the same file
/usr/bin/install: `./in_imag.2' and `./in_imag.2' are the same file
/usr/bin/install: `./in_imag.3' and `./in_imag.3' are the same file
/usr/bin/install: `./in_imag.4' and `./in_imag.4' are the same file
/usr/bin/install: `./in_real' and `./in_real' are the same file
/usr/bin/install: `./in_real.1' and `./in_real.1' are the same file
/usr/bin/install: `./in_real.2' and `./in_real.2' are the same file
/usr/bin/install: `./in_real.3' and `./in_real.3' are the same file
/usr/bin/install: `./in_real.4' and `./in_real.4' are the same file
/usr/bin/install: `./out_imag.1.golden' and `./out_imag.1.golden' are the same file
/usr/bin/install: `./out_imag.2.golden' and `./out_imag.2.golden' are the same file
/usr/bin/install: `./out_imag.3.golden' and `./out_imag.3.golden' are the same file
/usr/bin/install: `./out_imag.4.golden' and `./out_imag.4.golden' are the same file
/usr/bin/install: `./out_real.1.golden' and `./out_real.1.golden' are the same file
/usr/bin/install: `./out_real.2.golden' and `./out_real.2.golden' are the same file
/usr/bin/install: `./out_real.3.golden' and `./out_real.3.golden' are the same file
/usr/bin/install: `./out_real.4.golden' and `./out_real.4.golden' are the same file
/usr/bin/install: `./fft.cpp' and `./fft.cpp' are the same file
/usr/bin/install: `./main.cpp' and `./main.cpp' are the same file
/usr/bin/install: `./sink.cpp' and `./sink.cpp' are the same file
/usr/bin/install: `./source.cpp' and `./source.cpp' are the same file
/usr/bin/install: `./fft.h' and `./fft.h' are the same file
/usr/bin/install: `./sink.h' and `./sink.h' are the same file
/usr/bin/install: `./source.h' and `./source.h' are the same file
make[5]: *** [install-data-local] Error 1
make[5]: Leaving directory `/media/TechStuph/LiU/TDTS07/Tools/systemc-2.2.0/examples/sysc/fft/fft_flpt'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/media/TechStuph/LiU/TDTS07/Tools/systemc-2.2.0/examples/sysc/fft/fft_flpt'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/media/TechStuph/LiU/TDTS07/Tools/systemc-2.2.0/examples/sysc/fft'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/media/TechStuph/LiU/TDTS07/Tools/systemc-2.2.0/examples/sysc'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/media/TechStuph/LiU/TDTS07/Tools/systemc-2.2.0/examples'
make: *** [install-recursive] Error 1
bharath@reveredone:/media/TechStuph/LiU/TDTS07/Tools/systemc-2.2.0$ 

```

It'd be great if anybody could help me with this.

---

### Post by bharaths_jois on 2010-02-22
Guys, I donno what really happened, but I have a successful 'make install'. I am reallly sorry about the thread creation. But, it would be good to know what was the problem and what solved it.

What did I do, because of which the problem got solved?
I just typed in 'make install' again (this was the 2nd time), and there... all was fine.

---

### Post by tipss on 2010-03-09
Step1 : download systemC 2.2.0 from system.org 
    tar -zxvf systemc-2.2.0.tgz
     cd systemc-2.2.0 
   
  
Step2 : 

If using SystemC version 2.2.0, and make errors out with the following:

../../../../src/sysc/utils/sc_utils_ids.cpp: In function int 'sc_core::initialize()':
../../../../src/sysc/utils/sc_utils_ids.cpp:110: error: 'getenv' is not a member of std
../../../../src/sysc/utils/sc_utils_ids.cpp:111: error: 'strcmp' was not declared in this scope

Then change the includes in the file systemc-2.2.0/src/sysc/utils/sc_utils_ids.cpp to look like the following: 


#include "sysc/utils/sc_report.h"
#include "string.h"
#include "cstdlib"


Step3:
  ./configure
   make install
  
If you get aclocal error ,Install  sudo apt-get install automake*
 make clean
 aclocal 
 automake
 autoconf

 ./configure
  make install
  
:popcorn:

Step4

export SYSTEMC=/home/srinu/systemC/downloads/systemc-2.2.0

---

### Post by apoorv_kumar247 on 2010-03-16
even i am stuck with the same problem -----

make[5]: *** [install-data-local] Error 1
make[5]: Leaving directory `/home/apoorv/OFFICIAL/systemc-2.2.0/examples/sysc/fft/fft_flpt'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/apoorv/OFFICIAL/systemc-2.2.0/examples/sysc/fft/fft_flpt'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/apoorv/OFFICIAL/systemc-2.2.0/examples/sysc/fft'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/apoorv/OFFICIAL/systemc-2.2.0/examples/sysc'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/apoorv/OFFICIAL/systemc-2.2.0/examples'
make: *** [install-recursive] Error 1
-------------------------------------------------------
my make and make check go on pretty well but make install creates errors. i tried the above steps using automake as well as the normal ./configure make make install method.
i have no idea how to get clear of it. i use ubuntu 9.10 and gcc 4.4. any help will be deeply appreciated.

---

### Post by hetal.borad on 2010-05-19
Hi Everyone,

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

[COLOR=Red]/usr/bin/install: `./source.h' and `./source.h' are the same file
make[5]: *** [install-data-local] Error 1
make[5]: Leaving directory `/home/hetal/systemc-2.2.0/examples/sysc/fft/fft_flpt'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/hetal/systemc-2.2.0/examples/sysc/fft/fft_flpt'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/hetal/systemc-2.2.0/examples/sysc/fft'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/hetal/systemc-2.2.0/examples/sysc'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/hetal/systemc-2.2.0/examples'
make: *** [install-recursive] Error 1[/COLOR]


I saw in this thread that someone faced the same problem, could anyone please help in solving this issue that I am facing. Do I need to do some seperate installation for gcc or something. 
I have just follwed the steps mentioned above till now.


Thanks,
Hetal.

[/COLOR][/COLOR]

---

### Post by bharaths_jois on 2010-05-20
Hi Hetal,

As far as I can remember, I followed the same steps and got stuck at the same place. Some people suggested changes to the Makefile, but all I remember is I did a make clean, make distclean and started all over again. It worked. But I will try to install it again and give a better answer.

/Bharath

---

### Post by rohitmakhija on 2011-01-08
Even I am having the same problems as described by hetal. Please anyone who can help me....

---

### Post by Alexir on 2011-03-06
Hetal, thank you for includes. To solve errors examples directory create some new directory in top of systemc. Run ./configure and makes from there. I have done it today and it work.
[COLOR=Blue]>>pwd
   /../../systemc-2.2.0[/COLOR]
[COLOR=Blue]>>mkdir objdir
>>cd objdir
>>.././configure
>>make
>>make install[/COLOR]

---

