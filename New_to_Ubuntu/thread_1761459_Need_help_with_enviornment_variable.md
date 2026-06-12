---
title: "Need help with enviornment variable"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by hrushi.397 on 2011-05-18
Hi all,
 
I have a problem. I downloaded and installed Intel Fortran on my PC. Problem is, my IFort was installed in /opt/intel. Everytime I have to compile fortran program, I have to run following command:
 
$/opt/intel/bin/ifort sample.f
 
I tried including this path in .bashrc in PATH variable and export it but it didn't work. Is there any way to include this path in ./bashrc?

---

### Post by Plueonic on 2011-05-18
Are you exporting /opt/intel/bin/ or /opt/intel/?
```
export PATH=$PATH:/opt/intel/bin/
```

---

