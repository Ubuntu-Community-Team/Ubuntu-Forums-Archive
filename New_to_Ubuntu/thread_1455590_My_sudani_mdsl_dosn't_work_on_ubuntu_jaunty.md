---
title: "My sudani mdsl dosn't work on ubuntu jaunty"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by toloykhan on 2010-04-16
Hello every one ...,
 
[SIZE=4]am totally new in linux and I use ubuntu 9.04 jaunty the problem I face that I cant access to the internet using my " sudani mdsl AC8700 800M modem" pleace help me.[/SIZE]

---

### Post by toloykhan on 2010-10-17
Hello there, I saw that is there is a lot of views for this page and I just want to put the answer that I had found for my problems and the steps to follow.
1/ install wvdial
sudo apt-get install wvdial
2/ open terminal and type
sudo gedit /etc/wvdial.conf

3/ then post the following into the wvdial.conf file
[Dialer Defaults]
Stupid mode = yes
Modem = "/dev/modem/ttyUSB2"
Modem type = Tone
Phone =*777#
Username = 
Password = 
New PPPD = yes

replace "/dev/ttyUSB2" with the path of your device

hope work

---

