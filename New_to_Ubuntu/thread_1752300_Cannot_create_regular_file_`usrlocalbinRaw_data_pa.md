---
title: "Cannot create regular file `/usr/local/bin/Raw_data_parse': Permission denied"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by subrataghosh on 2011-05-07
When I am installing a tar.gz file named miRExpress through terminal (command prompt), it shows the message 




"sghosh@ubuntu:~/miRExpress$ make
Making all in src
make[1]: Entering directory `/home/sghosh/miRExpress/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sghosh/miRExpress/src'
make[1]: Entering directory `/home/sghosh/miRExpress'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/sghosh/miRExpress'
sghosh@ubuntu:~/miRExpress$ make install
Making install in src
make[1]: Entering directory `/home/sghosh/miRExpress/src'
make[2]: Entering directory `/home/sghosh/miRExpress/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c Raw_data_parse Trim_adapter alignmentSIMD analysis statistics_reads '/usr/local/bin'
/usr/bin/install: cannot create regular file `/usr/local/bin/Raw_data_parse': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/Trim_adapter': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/alignmentSIMD': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/analysis': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/bin/statistics_reads': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/sghosh/miRExpress/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/sghosh/miRExpress/src'
make: *** [install-recursive] Error 1
sghosh@ubuntu:~/miRExpress$ ^C
sghosh@ubuntu:~/miRExpress$"




Now what should I do to resolve the problem? I could not install the software at all!
Please reply positively.
Thank you.

---

### Post by andrewthomas on 2011-05-07
sudo make install

---

### Post by subrataghosh on 2011-05-07
TILL NOW, THE PROBLEM HAS NOT BEEN RESOLVED, SIR! PLEASE FIND THE ATTACHMENTS. I TYPED "sudo make install". BUT THERE ARE SOME ERRORS. KINDLY RESOLVE THE PROBLEM!
IT SHOWED




Making all in src
make[1]: Entering directory `/home/sghosh/miRExpress/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/sghosh/miRExpress/src'
make[1]: Entering directory `/home/sghosh/miRExpress'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/sghosh/miRExpress'
sghosh@ubuntu:~/miRExpress$ sudo make install
Making install in src
make[1]: Entering directory `/home/sghosh/miRExpress/src'
make[2]: Entering directory `/home/sghosh/miRExpress/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c Raw_data_parse Trim_adapter alignmentSIMD analysis statistics_reads '/usr/local/bin'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/sghosh/miRExpress/src'
make[1]: Leaving directory `/home/sghosh/miRExpress/src'
make[1]: Entering directory `/home/sghosh/miRExpress'
make[2]: Entering directory `/home/sghosh/miRExpress'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/sghosh/miRExpress'
make[1]: Leaving directory `/home/sghosh/miRExpress'
sghosh@ubuntu:~/miRExpress$





PLEASE REPLY URGENTLY.
THANK YOU.

---

### Post by andrewthomas on 2011-05-07
You need to start over. 

./configure
make
sudo make install

---

### Post by Paqman on 2011-05-07
According to the website you also need to install the following dependencies before you compile:
```
sudo apt-get install g++ libglib2.0-dev
```

---

### Post by subrataghosh on 2011-05-07
> **andrewthomas said:**
> You need to start over. 

./configure
make
sudo make install
HELLO SIR, IT DOES NOT WORK. SAME MESSAGE SHOWN. THE SOFTWARE IS "KINDLY EXPLAIN AND GIVE ME THE SOLUTION.   	 	 	 	pre { font-family: "Liberation Serif"; }p { margin-bottom: 0.08in; }   miRExpress: The package of Constructing miRNA expression profile by next generation sequencing data  
   	 	 	 	pre { font-family: "Liberation Serif"; }p { margin-bottom: 0.08in; }  Wang, W.C., et al., miRExpress: Analyzing high-throughput sequencing data for profiling microRNA expression. BMC Bioinformatics, 2009. 10(1): p. 328. 
ABOUT THE SOFTWARE: 
THANK YOU.

---

### Post by subrataghosh on 2011-05-08
Dear Sir,
              Till now it is not working!
I installed  "
sudo apt-get install g++ libglib2.0-dev


Then again I started over. 


./configure
make
sudo make install
But no solutiom at all!
Kindly go through the matter and give me the solution!
Thank you.

---

