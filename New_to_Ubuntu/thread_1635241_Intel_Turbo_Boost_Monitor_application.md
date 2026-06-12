---
title: "Intel Turbo Boost Monitor application"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by fwin on 2010-12-01
Hi all,

I recently purchased a laptop with an i7 processor and I want to check if turbo boost is working, 

1. is there an application similar to the "intel turbo boost monitor" for gnu/linux?

2. if there are not any applications like this, how can I check  if  Turbo Boost is working?

3. Should I just run a bunch of programs, movies, music, etc at the same time when I'm ready for the test?

Note: I have not received the laptop yet, but as soon as I get it I plan to install ubuntu 10.04.  So I guess I will need a turbo boos monitor  for 10.04.

Thanks in advance

---

### Post by NCLI on 2010-12-01
It should just work, as it is supported by the kernel. Try [this tool]("http://code.google.com/p/i7z/") to make sure. You'll need to compile it though.

---

### Post by fwin on 2010-12-02
thank you very much NCLI, I will try this as soon as I have my laptop

---

### Post by fwin on 2010-12-16
I checked turbo boost with this program:

[http://www.kernel.org/pub/linux/kernel/people/lenb/acpi/utils/pmtools-latest/turbostat/turbostat.c](http://www.kernel.org/pub/linux/kernel/people/lenb/acpi/utils/pmtools-latest/turbostat/turbostat.c)

in case someone doesn't know how to compile it I did the following:

1. copy the text from the link above and paste it in gedit then save as turbostat.c

2. open terminal and enter this:    gcc -o turbostat turbostat.c

To run the program I did this:

3. in the terminal:   sudo modprobe msr

4. in the terminal:     sudo ./turbostat

Note: make sure you do steps 2 and 4 in the directory where you saved the turbostat.c file.


I checked my processors and yes turbo boost starts working after the processors reach 100%

---

