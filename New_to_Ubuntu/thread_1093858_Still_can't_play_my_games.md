---
title: "Still can't play my games"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by peggyarmstrong on 2009-03-12
I still have not figured out how to update java, but now am wondering if my nvidia card drivers need updated after I upgraded to 8.04?   any thoughts?  I did get an email saying the had an updated driver for linux users.

Either way I still cannot play my pogo games!  applets won't load.:(

---

### Post by teamcoltra on 2009-03-12
Make sure you are closed out of firefox and all other programs, and enter into terminal
sudo apt-get install ubuntu-restricted-extras

---

### Post by peggyarmstrong on 2009-03-12
that is in my synaptic pkg marked as installed, let me try your way

---

### Post by linuxuser21 on 2009-03-12
Are you trying to play games that you would on Windows?

---

### Post by peggyarmstrong on 2009-03-12
I have been strictly ubuntu on this computer, could play the games in gutsy.  This computer was custom built for me, but still learning the ubuntu way.  Have not used windows in 4 years.   The guy who built my system was helping me update it, but I'm not in cali anymore and he is hard to get on the phone when I have time for him to help. :(

---

### Post by peggyarmstrong on 2009-03-12
:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for peggy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-23-generic linux-headers-2.6.24-23
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
peggy@peggy-desktop:~$ 

I have been strictly ubuntu on this computer, could play the games in gutsy. This computer was custom built for me, but still learning the ubuntu way. Have not used windows in 4 years. The guy who built my system was helping me update it, but I'm not in cali anymore and he is hard to get on the phone when I have time for him to help.

---

### Post by peggyarmstrong on 2009-03-12
I must be an idiot, I keep getting abandoned!

---

### Post by Miljet on 2009-03-12
I had the exact same problem as you. Pogo games played fine in Gutsy, but when I upgraded to Hardy, they would not work. I tried for months to get it working. I finally created a new partition and re-installed Gutsy there just to play Pogo.

Then I bit the bullet and installed Intrepid and Pogo worked as soon as I installed java.

I have read that some people have had some success getting pogo to work with Hardy by removing Sun-java6 and installing Sun-java5. You might try that if you don't want to upgrade.

---

### Post by peggyarmstrong on 2009-03-12
UPGRADE TO 8.10?  Ihave the cd

---

### Post by hobo on 2009-03-13
I too have had problems running POGO games in 8.04 after upgrading from 6.06. What I found was **TWO JAVA plugins** resident in a Firefox subdirectory. Anyways, what I did was remove all JAVA from the system and downloaded the newest JAVA from SUN and installed. Then I deleted the OLD plugin and now POGO works just fine in 8.04 for me.

---

