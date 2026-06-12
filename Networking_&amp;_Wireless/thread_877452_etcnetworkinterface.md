---
title: "/etc/network/interface"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by deepsman on 2008-08-01
Hi all,

I am new to Linux and Ubuntu is the 1st OS that I used. I need to edit the file /etc/network/interface because I would like to set up a computer with 2 network NIC. One to connect to internet while another one to connect to another switch/hub which has 2 computer. Some one told me to configure my etc/network/interface  file.

After reading so many forum and online materials, I do not understand what kind of command we can used and where we can find those command? How we know which command can be used? The most important thing is what this commands does? 

I am appriciate if any of you can direct me to the material that can explain what command i can used and what those command are use for. 

Thanks

---

### Post by TJCIB on 2008-08-01
I know this doesn't answer your question, but I'm curious (for my own learning):

Why not plug all three computer to the switch and put your router/modem directly into it as well?

Isn't having 2 NIC cards mostly used for servers through which other computers connect to the internet?

---

### Post by deepsman on 2008-08-01
I am try to play around server-client. The two computer will be client while the 3rd one will be server.

---

### Post by TJCIB on 2008-08-01
If you're trying thin clients, you could always use Edubuntu or the Ubuntu Alternate CD, which will set up both NICs at install for thin client setup.

check out this to get started
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)
Check out the links at the bottom of the page for more help

---

### Post by mrsteveman1 on 2008-08-01
The only time you need 2 NICs is when you are doing routing, you can still do all the server stuff by putting your boxes all on one switch and connecting that to a router.

---

