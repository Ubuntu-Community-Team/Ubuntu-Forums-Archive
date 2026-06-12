---
title: "Edimax 7728ln pci wireless problem"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by attila_66 on 2008-03-03
Hello,

I bought Edimax 7728 pci card for a friends computer. I installed Kubuntu but it couldnt specify the card.
I downloaded driver from Edimax site. While trying to install there are some errors attached here.

karel@Karels:~/Desktop/2008_0108_RT2860_Linux_STA_v1.5.0.0$ sudo make
make -C tools
make[1]: Entering directory `/home/karel/Desktop/2008_0108_RT2860_Linux_STA_v1.5.0.0/tools'
gcc -g bin2h.c -o bin2h
bin2h.c:28:19: error: stdio.h: No such file or directory
bin2h.c:29:20: error: string.h: No such file or directory
bin2h.c:30:20: error: stdlib.h: No such file or directory
bin2h.c: In function ‘main’:
bin2h.c:34: error: ‘FILE’ undeclared (first use in this function)
bin2h.c:34: error: (Each undeclared identifier is reported only once
bin2h.c:34: error: for each function it appears in.)
bin2h.c:34: error: ‘infile’ undeclared (first use in this function)
bin2h.c:34: error: ‘outfile’ undeclared (first use in this function)
bin2h.c:42: warning: incompatible implicit declaration of built-in function ‘memset’
bin2h.c:45: warning: cast to pointer from integer of different size
bin2h.c:46: warning: cast to pointer from integer of different size
bin2h.c:49: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:54: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:57: warning: incompatible implicit declaration of built-in function ‘strcat’
bin2h.c:69: error: expected expression before ‘)’ token
bin2h.c:71: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:76: error: expected expression before ‘)’ token
bin2h.c:78: warning: incompatible implicit declaration of built-in function ‘printf’
bin2h.c:146: warning: incompatible implicit declaration of built-in function ‘sprintf’
bin2h.c:155: warning: incompatible implicit declaration of built-in function ‘exit’
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/karel/Desktop/2008_0108_RT2860_Linux_STA_v1.5.0.0/tools'
make: *** [build_tools] Error 2
karel@Karels:~/Desktop/2008_0108_RT2860_Linux_STA_v1.5.0.0$



Can anybody help with this problem.


Thank You Anyway.

---

### Post by nickmcg on 2008-06-30
Two things:

have you installed build-essential?

Download the latest driver source from [here]("http://www.ralinktech.com.tw/data/drivers/2008_0522_RT2860_Linux_STA_v1.6.1.0.tar.bz2")

Also, this thread may help [http://ubuntuforums.org/showthread.php?t=683085](http://ubuntuforums.org/showthread.php?t=683085)

Nick

---

