---
title: "Open GL applications over SSH"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by mynicka on 2006-09-11
Hey all, 

I am trying to run an OpenGl example that my teacher created on my schools network by using ssh.  Im trying to run Xwindows so that the program will pop up once I run it from the commandline that I used for ssh.  It seems that X windows runs ok when using programs such as emacs or simple tools, but whenever I compile and try to example I get an error as follows...

bash-3.00$ simple1
GLUT: Fatal Error in (unamed): visual with necessary capabilities not found.

I don't know if I used ssh with X windows enabled wrong or not; This was the first time I ever tried to use X-windows on an ssh'ed machine.  I used this to login...

ssh -l ****** p2.cs.ohiou.edu -X

I'd appreciate any advice that you could give me on this problem.

Thanks

---

