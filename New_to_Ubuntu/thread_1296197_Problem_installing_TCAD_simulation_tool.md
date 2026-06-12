---
title: "Problem installing TCAD simulation tool"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by veereddy on 2009-10-20
I have been trying to install GSS, a TCAD simulation tool for semiconductor device modeling for last 1 week. I have been successful in compiling all the other required packages like **cgnslib**, **petsc**  and when I tried to compile **GSS** folder, it's throwing me the following error after executing the **make** statement.

/usr/bin/ld: cannot find -lmpiuni
collect2: ld returned 1 exit status
make[3]: *** [dumptif] Error 1
make[3]: Leaving directory `/home/nxadmin/GSS_dev/src/utils/tif2cgns'
make[2]: *** [ALL] Error 2
make[2]: Leaving directory `/home/nxadmin/GSS_dev/src/utils'
make[1]: *** [objs] Error 2
make[1]: Leaving directory `/home/nxadmin/GSS_dev/src'
make: *** [All] Error 2

I am aware that I may need to install an extra package so that to have lmpiuni in that specific location, but not sure about what might be that package. I am very new to LINUX/UBUNTU. Please let me know the appropriate solution if any of you is familiar with this issue. I appreciate your help.

---

### Post by homer.hauser on 2010-02-08
Hi,
I have a similar problem,
did you find a solution?

Best Regards,

Hubi

---

