---
title: "problem with ssh on wireless"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by paulus4605 on 2008-09-29
Hi 
I have the following problem,
when I want to connect to my server from my linux laptop through ssh I need to run this fix
The workaround for this in Intrepid (don't know if it will work for hardy) is to first see if you have the ioctls:

root@moltar:/home/pgraner# iwpriv
lo no private ioctls.

eth0 no private ioctls.

eth1 Available private ioctls :
set_leddc (8BE0) : set 1 int & get 0
set_vlanmode (8BE1) : set 1 int & get 0
set_pm (8BE2) : set 1 int & get 0

then actually set it:

pgraner@moltar:~$ sudo iwpriv eth1 set_vlanmode 0

Note this has to be done as root. 

when this is done I'm able to connect wireless to my my server using either local ip adress when I'm at home or over my dns account when I'm at work.

when I want to move files locally using scp it works like a charm however when I want to do this when I'm at work I get this error message after entering this command 
scp Pictures1.tar.gz [email]paul@carrebeanpirates.homedns.org[/email] -pxxxx: /home/paul/  

cp: `Pictures1.tar.gz' and `/home/paul/Pictures1.tar.gz' are the same file
cp: cannot stat `paul@carrebeanpirates.homedns.org': No such file or directory
ssh: scp -d -f .: Name or service not known

how do I solve this in order to make it work correctly

I work with ubuntu 8.04

thanks for your help>

Paul

---

### Post by paulus4605 on 2008-09-30
doesn't anybody have a clue here?

---

