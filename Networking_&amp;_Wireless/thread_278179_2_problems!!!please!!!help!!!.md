---
title: "2 problems!!!please!!!help!!!"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by finalreckoning on 2006-10-15
help with 2 things.:( ](*,) :confused:  :redface:
         1.   i have a dell xps m1210. i have an intel wifi card. i opened the wifi thing and it says it is connected (i think) but it wont hook up to the internet.

         2. i have a verizon wireless broadband card. (it works like cell phone internet.) i want to know how i can use it. ( i really like to have access to the world when i am on vacation) 

                        if you have a possible sollution, post it and send me an email at [email]john.finalreckoning@gmail.com[/email]


ps. i want to know if there is a way to use windows media player w/ linux. (emulator, perhaps;) )

---

### Post by tubasoldier on 2006-10-15
Windows Media Player? WTF M8? I dont even know windows users that use it.

---

### Post by capn_hector on 2006-10-15
1:  for the verizon card, contact verizon and see if they have a linux verison of there software

2:  check out vlc  [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)  a much better player than windows media player.  i even use it on my windoze.

---

### Post by mips on 2006-10-16
> **capn_hector said:**
> 1:  for the verizon card, contact verizon and see if they have a linux verison of there software


They are just going to tell you, "We don't support Linux"

You will have better luck if you posted info like Brand,Model etc here. Also a google search will help.

---

### Post by tturrisi on 2006-10-16
howto: verizon wifi & linux:
[http://kenkinder.com/evdo-pc5740/](http://kenkinder.com/evdo-pc5740/)

---

### Post by dannyboy79 on 2006-10-16
> **finalreckoning said:**
> help with 2 things.:( ](*,) :confused:  :redface:
         1.   i have a dell xps m1210. i have an intel wifi card. i opened the wifi thing and it says it is connected (i think) but it wont hook up to the internet. 
Are you getting an ip address from the router or access point? Are you using security, turn it off to see if you can connect, then turn it on.
Have you tried the following?
sudo dhclient wlan0 (or whatever interface your wifi card is at, eth0, ath0,) if and that didn't work, 
Please post output of the following
ifconfig
iwconfig
iwlist
dmesg | grep eth
lscpi -v

---

