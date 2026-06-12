---
title: "How to configure winscp to connecto ubuntu 8.04"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by jchurtado on 2010-07-29
I want to transfer a csr file from Ubutnu 8.04 to my windows pc to request a SSL certificate to a CA. I already download WinScp to get the files but don't know how to configure. I know that SSH is already installed on the ubuntu server. Can you help me??? Any help would be appreciated. Thanks :)

---

### Post by pricetech on 2010-07-29
Host Name is the Host name or IP of your Ubuntu machine, port 22 is correct if you didn't change it.
UserName and Password will be the credentials of your account on the Ubuntu machine.
Use PuTTYgen to generate the key you will use.
(Start - Programs - WinSCP - Key tools - PuTTYgen
and save the key in a safe place, then use the browse button to locate and load the key in WinSCP.

You'll be prompted to verify that you want to connect, but since both computers are yours, you'll want to OK that.

---

