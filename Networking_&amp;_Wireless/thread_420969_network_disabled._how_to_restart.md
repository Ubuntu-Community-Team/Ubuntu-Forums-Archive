---
title: "network disabled. how to restart"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by auditory on 2007-04-24
i am using Feisty.

network worked good, but whenever copying files from windows share,
the network closed.
small files copied good. but copying a big file(>100MB) is terminated by time-out
and then every network functions are disabled.
I even can't reach to dns server. 

And then i never can reuse network unless reboot the machine.

first of all, I like to use network again.
Now i cannot shutdown my machine for a while.
plz let me know how to make network reusable without rebooting

I tried /etc/init.d/networking restart, then the message shows [OK],
but it doesn't work.

and what is problem with my network?
i connected windows share folder using smb://ipaddress in file browser.
i gave username and passwd, but the domain name is left default(maybe WORKGROUP)
and i don't know the domain name of window machine..
is that a cause of problem??

---

### Post by auditory on 2007-04-24
ping from the machine to itself is ok.

but it can not ping even the gateway.

ifconfig looks fine.

what more info would be helpful??

---

### Post by wieman01 on 2007-04-24
Do you have a wireless or wired network?

---

### Post by auditory on 2007-04-24
wired network.

---

### Post by auditory on 2007-04-24
network lived again even though i did nothing.
everything looks fine.

For the testing purpose,
i copied files by same way (via smb, using file browser)
the network dies again.

I hope it will work again in about 1 hour.
but i don't know why..

the amount of file copied before failure seems irregular.

---

### Post by Alekc on 2007-04-24
well you can try 
sudo ifconfig eth0 down
sudo ifconfig eth0 up

where eth0 is your network interface

---

### Post by auditory on 2007-04-24
sudo ifconfig eth0 down
sudo ifconfig eth0 up

doesn't work too.
whole network doesn't work, 

i was home with network dead and this morning,
i can ping the gateway and the nameserver.
but name resolving failed so i can't access web pages without ip address.

after /etc/init.d/networking restart
the network disabled again.

i can't ping gateway and nameserver.

---

### Post by auditory on 2007-04-24
now i guess i found out the cuase of the problems and
how to restart networks.
but not how to fix the problem.

i guess this is related to soft lockup and sky2 driver with Marvell onboard network card.

i could reuse network without rebooting by doing followings:

rmmod sky2
insmod sky2.ko

many thanks..

---

