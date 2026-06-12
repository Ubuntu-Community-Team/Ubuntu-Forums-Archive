---
title: "Belkin Wireless Express f5d8073 rt2860 chipset help"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by LuvSulime808 on 2008-03-03
I thought I have done everything right, but I'm unable to connect to my router or even really scan for a network (probably doing it wrong anyways)

when I do a ndiswrapper -l I get:

rt2860 : driver installed
             device (1814:0681) present

When I look in the device manager, it shows up, but as unkown (ralink vendor, subvendor belkin)

I did the Windows Wireless Driver install, that part went fine....


am I doing something wrong, or is it because my router is set to N band only?


When I download the driver from RALink... and try to compile it, i get this:


luvsublime@JeremyLaptop2:~/drivers/RT2860$ make
make -C tools
make[1]: Entering directory `/home/luvsublime/drivers/RT2860/tools'
gcc -g bin2h.c -o bin2h
bin2h.c:28:19: error: stdio.h: No such file or directory
bin2h.c:29:20: error: string.h: No such file or directory
bin2h.c:30:20: error: stdlib.h: No such file or directory
bin2h.c: In function &#8216;main&#8217;:
bin2h.c:34: error: &#8216;FILE&#8217; undeclared (first use in this function)
bin2h.c:34: error: (Each undeclared identifier is reported only once
bin2h.c:34: error: for each function it appears in.)
bin2h.c:34: error: &#8216;infile&#8217; undeclared (first use in this function)
bin2h.c:34: error: &#8216;outfile&#8217; undeclared (first use in this function)
bin2h.c:41: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
bin2h.c:44: warning: cast to pointer from integer of different size
bin2h.c:48: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:51: warning: incompatible implicit declaration of built-in function &#8216;strcat&#8217;
bin2h.c:57: error: expected expression before &#8216;)&#8217; token
bin2h.c:59: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:64: error: expected expression before &#8216;)&#8217; token
bin2h.c:66: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
bin2h.c:134: warning: incompatible implicit declaration of built-in function &#8216;sprintf&#8217;
bin2h.c:143: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/luvsublime/drivers/RT2860/tools'
make: *** [build_tools] Error 2

---

### Post by zadok the priest on 2008-03-20
I just bought a new laptop, a zepto znote 3415W and its wireless card is a RT2860
I have tried to install its drivers to no avail, can anyone please help?

Secondly, would anybody know if the chipset can be used for packet injection?

Cheers

---

