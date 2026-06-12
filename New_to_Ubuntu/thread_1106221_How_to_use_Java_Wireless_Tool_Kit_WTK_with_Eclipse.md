---
title: "How to use Java Wireless Tool Kit WTK with Eclipse and Ubuntu??"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by mmaia on 2009-03-25
Hi,

I'm new to linux world. I was trying to configure Ubuntu 64bits + eclipse + JME toolkit.. It was impossible. 

I have a more complete thread about this here: 
[http://www.coderanch.com/t/437787/Java-Micro-Edition/Mobile/Ubuntu-bits-WTK#1946555](http://www.coderanch.com/t/437787/Java-Micro-Edition/Mobile/Ubuntu-bits-WTK#1946555)

My question is: 

1)Does anyone have a REAL project where you use Ubuntu + Eclipse +WTK working?  :confused: :(

tx in advance.

---

### Post by albandy on 2009-03-25
Have you all the system system requirements installed?

[http://java.sun.com/products/sjwtoolkit/download.html](http://java.sun.com/products/sjwtoolkit/download.html)

    * ibXpm (libxpm-dev)
    * libXt (libxt-dev)
    * libX11 (libx11-dev)
    * libICE (libice-dev)
    * libSM (libsm-dev)
    * libpthread (libc6-dev)
    * libm (libc6-dev)
    * libnsl (libc6-dev)
    * libstdc++6-dev

---

### Post by mmaia on 2009-03-25
Hi,

As I said I'm new to linux so... 

How do I check if the libraries are in place?

[]s

---

### Post by albandy on 2009-03-26
trought synaptic:

system --> Administration --> Synaptic Package manager

---

### Post by mmaia on 2009-03-26
Tx for helping..

Because of my tight dead line I just decided to go for Ubuntu 32bits . Took me ~6hours to configure it all to work. 

Worked perfectly.

Ubuntu 32bits + eclipse + EclipseME + WTK2.5.2 + Subclipse.

My final consideration is WTK 2.X doesn't work with Ubuntu 64bits.

regards.

---

### Post by albandy on 2009-03-26
Good Job

Well if in future you want to  use the 64 bits version on ubuntu you can get 32bit compatibility by installing the package ia32-libs

---

### Post by mmaia on 2009-03-26
Humm.. that would problably had work, too late now.. 

tx anyway...

I'm happy with 32bits for now!!!

---

