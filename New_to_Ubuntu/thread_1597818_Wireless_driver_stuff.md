---
title: "Wireless driver stuff"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by Uruk-hai on 2010-10-15
Ok, So I have Ubuntu installed but It doesn't automaticlly download the right driver for the wireless. I'm not sure how to get the right driver for my card. I have a dell inspiron 1545 and I heard The wireless card doesn't have a common ubuntu driver. 

P.S. I have already installed Ubuntu on this machine and I got the wireless working through someone else helping me. He reinstalled some driver and then installed it again. He also typed in something on the command line...I cant remember what it is though.

---

### Post by TBABill on 2010-10-15
I have the same machine. If you type lspci into a terminal (that command line window you watched him type in) it will tell you which wireless adapter you have in that big list of stuff. You should have a Broadcom BCM4312. All you have to do in order to activate is plug into a router and run updates. The machine should prompt  you to install proprietary drivers, but if it does not you can click System>Applications>Hardware and see if it prompts you to install one. The STA driver is the one for your card if it's the model I identified.

Post back if you need clarification :)

---

### Post by earthpigg on 2010-10-15
if you open a terminal and press the up arrow key, it will go in reverse historical order and you can find what your buddy typed to get wireless up and running. try and make some sense of what is going on before you start entering the commands again, to ensure you don't make things worse.

---

### Post by earthpigg on 2010-10-15
actually, we can help you make sense of it.

type this command into a terminal, please, and copy/paste the output:

> history

if you can make enough sense of any of hte 500 lines to isolate which ones you think your friend typed, you can paste just that and make things easier on us. if not, no biggie.

---

