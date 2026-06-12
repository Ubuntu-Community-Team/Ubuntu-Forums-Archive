---
title: "DSL connection gets dropped repeatedly"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by abs7453 on 2011-03-25
Hi everyone ! ):P
First of all I would really say hats off to the open source community... Ubuntu is absolutely amazing !
I don't know why no one around me uses it ! Google led me from sh**ty Windows to Ubuntu (MS lovers please don't mind!)

This is the first time I have started using Ubuntu and it has been two days...
(HP Pavilion DV-6 with AMD Turion X2 64-bit currently using Ubuntu 10.04)

I have a broadband Internet connection that uses a user name and a password to connect. I googled it and connected it using DSL Connection. 

Now every time I turn on my laptop either after shutting it down or restarting it, the internet connects fine...
but if I log out or suspend from Ubuntu, after logging back in the connection drops and after that it just keeps dropping again and again

I am getting really frustrated because every time i leave my laptop idle for sometime, I have to restart it if I want to use Internet....

I would really like if you can give me a direct solution or else some way to bypass the logging out and suspending of my Admin account.....

Thanks a lot in advance ! ;)

---

### Post by Arijit_Kundu on 2011-03-25
welcome to ubuntu.

open a terminal (applications > accessories > terminal) and run

lspci

and post the output here. Also, similarly run after once suspending 

ifconfig

and post the output here.

---

