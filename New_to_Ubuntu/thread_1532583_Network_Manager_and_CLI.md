---
title: "Network Manager and CLI"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by A_M_S on 2010-07-16
Hello.


Anybody know if its safe to reconfigure some network parameters (IP, DHCP, DNS...) using the CLI with network manager running?


Tnx.

---

### Post by bodhi.zazen on 2010-07-16
> **A_M_S said:**
> Hello.


Anybody know if its safe to reconfigure some network parameters (IP, DHCP, DNS...) using the CLI with network manager running?


Tnx.

Define "safe"

You can do it, but it is better to disable NM if you are not going to use it.

Otherwise NM usually overwrites any changes you make.

I would not anticipate any breakage a reboot (if it even gets that far) would not fix.

---

### Post by A_M_S on 2010-07-16
Tnx for your reply.

> **bodhi.zazen said:**
> Define "safe"


What i was trying to know is: 

Does the network manager accept the changes made in the CLI (and the opposite).

> **bodhi.zazen said:**
> 
You can do it, but it is better to disable NM if you are not going to use it.

Otherwise NM usually overwrites any changes you make.


According to your answer that is not possible with NM.
Anybody know if the same problem occur with WICD?

---

### Post by bodhi.zazen on 2010-07-16
> **A_M_S said:**
> Tnx for your reply.



What i was trying to know is: 

Does the network manager accept the changes made in the CLI (and the opposite).



According to your answer that is not possible with NM.
Anybody know if the same problem occur with WICD?

Yes. You have a graphical application (NetworkMangaer or Wicd) both trying to configure your network and at the same time you are trying to over ride these applications.

So you will have conflicts. I doubt anything will "break" it is just that NM/WICD will over write your changes from time to time.

If you wish to configure your network from teh command line, stop NewtorkManager or Wicd first. When you are done playing with the command line, re-start network manager or Wicd.

---

### Post by A_M_S on 2010-07-17
> **bodhi.zazen said:**
> Yes. You have a graphical application (NetworkMangaer or Wicd) both trying to configure your network and at the same time you are trying to over ride these applications.

So you will have conflicts. I doubt anything will "break" it is just that NM/WICD will over write your changes from time to time.

If you wish to configure your network from teh command line, stop NewtorkManager or Wicd first. When you are done playing with the command line, re-start network manager or Wicd.

Ok. Tnx again for your reply. :)

---

### Post by nothingspecial on 2010-07-17
I`m not sure what your situation is or what you are trying to accomplish, but it might be useful to know that you can use wicd in the console using it`s ncurses interface.

```
wicd-curses
```

It`s the first thing I install after a minimal ubuntu install

It saves messing about with config files, but you don`t need X.

---

### Post by A_M_S on 2010-07-17
> **nothingspecial said:**
> I`m not sure what your situation is or what you are trying to accomplish, but it might be useful to know that you can use wicd in the console using it`s ncurses interface.


I was trying to know if i can configure my network using simultaneously some GUI application  and the CLI.

---

