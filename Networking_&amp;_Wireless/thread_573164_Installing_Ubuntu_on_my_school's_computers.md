---
title: "Installing Ubuntu on my school's computers"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by PmDematagoda on 2007-10-11
Ok, now all who read my previous thread will know that I have installed Xubuntu on one of my teacher's computers, now the thing is that he loves Xubuntu and is considering recommending Ubuntu to the teacher in charge of my school's IT division since all the computers contain viruses(Windows XP ofcourse). But before that happens he needs some information:-

1) Is Ubuntu very stable and will not crash for any normal stuff? If not what would be recommended as a server?

2) Whether the normal Ubuntu 7.04 installation can be used as the server OS.

3) How to set up the network which includes a printer.

Once again I would appreciate any feedback as it would be pretty awesome to have Ubuntu or any form of Linux on my school's computers.:)

---

### Post by kevdog on 2007-10-11
Ubuntu crashes if you do something wrong so dont get that misconception.  The desktop installation CD you use can act as a server, but for some of the programs (samba,winbind) etc, you will have to install the software from repository (no big deal on that one).  The printer might be a much bigger issue.  Linux only supports a small number of printers (HP comes to mind since I think they have released their printer drivers as open source).  Lexmark -- other than some very old models -- is a no-no.  Not sure about others but support is limited.

---

### Post by PmDematagoda on 2007-10-11
The apt-get thing won't be much of problem as we have ADSL, we have only one printer which is a Canon, we also have a Canon scanner, will these work properly?

Also is it easy to set up a completely Ubuntu network? Is there a good guide?

There is also another thing. Now if some one restarts the computer to use Windows XP which will dual boot with Ubuntu on the school computers, will the network accept this change properly?

---

### Post by kevdog on 2007-10-11
You are going to have to google or check the ubuntu guide to see if Canon printers are supported.  Something tells me they are not, but they could be -- the problem will be with your scanner -- very low probability that this will be supported unless its an HP.

Setting up an Ubuntu network?? Not sure what you mean.  Its fairly easy.  To share files between computers (Ubuntu to Ubuntu only) I would recommend CFS, if you are going to throw Windows computers in the mix try Samba.  Samba is easy to use, but sometimes it doesnt work for me.  I dont know why.  There are a lot of guides in the forum and the posts by dbott67 (or dbott69) are quite helpful in getting the samba server up and running.

If you dual boot and reboot windows/ubuntu/windows you shouldnt have a problem in most cases.  The only problem Ive seen are some computers with some rtl networking cards that windows sets the card in a state that ubuntu cant detect it.  noob12 has provided a post on this problem.

---

### Post by PmDematagoda on 2007-10-11
Thanks for all your help kevdog, I will tell my teacher this and we will decide how to advance though most probably it would be an "All systems go" by the teacher in charge.:)

---

### Post by magikx21 on 2007-10-11
I would try for a dual boot setup first that way you can see what problems you encounter before making a full switch and getting stuck. This may be an easier way to convince him as well since your not deleting what is there already and you won't be suggesting forcing the system over to Xubuntu but giving the user options.

---

