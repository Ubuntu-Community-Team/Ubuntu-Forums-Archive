---
title: "install error in systemc 2.2.0"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by apoorv_kumar247 on 2010-03-16
hello guys,
i corrected the usual make error by including the library files and the make process goes on pretty smoothly but i face a new glitch now in the make install step. the error is below
-----------------------------------------------------------
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
----------------------------------------------------------
i use ubuntu 9.10 and gcc4.41.
i'm stuck and tried even the automake method but even that doesn't help. any help will be deeply appreciated.
thanx

---

### Post by apoorv_kumar247 on 2010-03-17
ol rite guys... it got the ans.... the trick is to provide an exception to the example folder in the make file since it is the folder creating the problem

---

### Post by amigabill on 2010-11-17
> **apoorv_kumar247 said:**
> ol rite guys... it got the ans.... the trick is to provide an exception to the example folder in the make file since it is the folder creating the problem

How does one make this exception?

Are we unable to do the examples?

How does one do the library include in the previous post?

---

