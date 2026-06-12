---
title: "Access Multiple windows shares"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by adwatkin19 on 2007-03-26
Hi all, hope this is in the right section

I have a laptop running edgy connected to my companies Windows based network.  (i say company its actually a school)

The internet is run through a proxy and i have got this to work no problem over the wireless network.

What i am having problems with is accessing the shared drives on the network to get important document i need access too. i have tried googling for hours, tried all sorts of different methods and i just cant get it to work. 

so here are the details:

domain is: ossettschool.co.uk

server where everything is: server1

then the shares i am looking for is: pupils$, aw, pupilshared and staff shared

I dont want to make this computer a client of the network, i just want it to be able to access these shares, i could do it no worries with my xp laptop, but my linux is having a hissy fit about doing.

I will be more than greatful for any help that anyone could give me. 

Many thanks

Adwatkin19

---

### Post by kidders on 2007-03-26
Hi there and welcome,

> **adwatkin19 said:**
> my linux is having a hissy fit about doing.

What kind of problems are you having? Any useful error messages, logs, or other information would be helpful ... we have to find out what your problem *is*, before we can solve it.

---

### Post by adwatkin19 on 2007-03-26
i have got through the inital stage now, i got round the network manager and found out the IP address of the server, but the problem now comes with mounting the shares all the time, I.E. when i turn on my computer.

i have tried some things but nothing seems to work

i added this to the bottom of my fstab: 

//10.126.160.30/Aw$ /mnt/Awhome smbfs

which finds the share on the server and mounts it to /mnt/Awhome

im not sure what the last but is, but i read that it was neede

when i run the command mount -a (i havent restarted the machine) i get the error message:


cli_negprot: SMB signing is mandatory and we have disabled it.
6358: protocol negotiation failed
SMB connection failed

whats happening? is my coding correct in fstab?

many thanks for the help

---

### Post by kidders on 2007-03-26
> **adwatkin19 said:**
> cli_negprot: SMB signing is mandatory and we have disabled it.
6358: protocol negotiation failed
SMB connection failedHave you disabled client signing somewhere?

> **adwatkin19 said:**
> is my coding correct in fstab?No, not quite. You should be using something like **//10.126.160.30/Aw$ /mnt/Awhome smbfs defaults 0 0** (or at least something with that many parameter groups in it).

---

### Post by adwatkin19 on 2007-03-26
Hi

thanks for the swift reply

I am fairly new to the whole linux thing, as far as i am aware i havent switched off siginalling, i dont even know how i would go about solving this, i will try and adjust the statment in fstab to match what you have listed,

thanks again for your help, i appreciate it

adwatkin19

---

