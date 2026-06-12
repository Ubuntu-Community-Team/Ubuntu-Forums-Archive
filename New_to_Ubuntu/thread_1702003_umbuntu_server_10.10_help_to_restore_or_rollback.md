---
title: "umbuntu server 10.10 help to restore or rollback"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by cptblue on 2011-03-07
Hi
 
first very sorry if post elsewhere, i did a search but couldnt find anything specific to my query
second thanks to anyone who takes the time to reply
 
So long story short, had a little shuttle pc land on my doorstep and i decided to turn it in to a linux server for web access, print, media, security camera if poss and email server if poss.
 
i followed this tutorial
[http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-2)
but it was the one with ispconfig3
 
everything has gone really well and i am enjoying learning command line. I have had some snags that havent been helped by the install of ispconfig so i am going to remove it as i prefer to use the command line via ssh
I had the server running for 2 weeks with 2 domain names pointed at it and a media server using mediatomb, it was up all the time with no load or memory issuses
 
all came apart tho this weekend when i thought i would try to install and configure zoneminder a linux security camera suite
 
i followed this tutorial for that 
[http://www.zoneminder.com/wiki/index.php/Ubuntu_9.10_Server_32-bit](http://www.zoneminder.com/wiki/index.php/Ubuntu_9.10_Server_32-bit)
 
I installed all the Prerequisites and zoneminder and did a reboot as in tutorial on reboot i found that all my other services didnt work i.e. apache, mediatomb and ispconfig
 
aaarrrggghhh :(
 
My skillset is mostly based in mac os x and im not sure now how i can 'rollback' or 'restore' the server to its original base install so i can 
a. start again and get rid of ispconfig
b. clear up the mess i made with zone minder
c. sort out a few other things that ispconfig makes harder
 
ive learnt alot of stuff already but i cant find any text on how to restore a server without having to do a whole new reinstall
 
to be honest i havnt used the 10.10 install disk to 'repair a broken system' yet but i will try tonight, i was just wondering if there was a command to undo the things done by root user sort of like an undo button on most apps?
 
also as this is in beginners talk has anyone got any suggestions on hardware upgrades. its not yet maxed out on memory which i was going to do first but i also only have 1 pci slot and one apg slot so im think probably best to get a sata card to run more internal HD's but with the apg slot is it even worth me getting a graphics card as i have no desktop GUI or will it take some of the load from the cpu when using mediatomb?
 
thanks again for any help :)
 
cheers
 
cptblue

---

### Post by cptblue on 2011-03-07
ok so ive tried the install disk/rescue mode 
but this just gives you a shell to do commands in, no sort of gui type of rollback or restore

hmm ive reverse followed the zoneminder install to uninstall it but still no joy

i think its messed with the apache config ill have a look

---

