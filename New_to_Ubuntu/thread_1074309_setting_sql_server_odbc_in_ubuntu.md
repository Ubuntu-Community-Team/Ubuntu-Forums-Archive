---
title: "setting sql server odbc in ubuntu"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by cholidah on 2009-02-19
how setting sql server odbc on ubuntu 8.04 with wine 1.1.14, help me
thank u

---

### Post by igknighted on 2009-02-19
You'll want to use virtualbox or some other virtualiztion tool to run windows in a VM.  I don't think you can install SQL Server via wine.

---

### Post by cholidah on 2009-02-19
sql server on windows server 2003,odbc i will setting in computer client

---

### Post by igknighted on 2009-02-19
Try using a native OBDC conection and driver.  See here to get started: [http://www.unixodbc.org/](http://www.unixodbc.org/)

---

### Post by cholidah on 2009-02-19
i was install unixodbc , then install freetds but error like this :

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by igknighted on 2009-02-19
it's in the repo's.  Just use 'sudo apt-get install unixodbc-bin'

---

### Post by cholidah on 2009-02-20
ok succesfully 'sudo apt-get....',then what i can do? (soryy i dont know all about linux, its first experience)

---

