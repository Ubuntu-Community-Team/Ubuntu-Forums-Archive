---
title: "ssh server? new to linux networking"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by Balinsky on 2007-05-13
Ok so here is the story. I have been using a laptop with fiesty at school for a while now. I got home yesterday. Recently I bought a dell n series for my little brother and put fiesty on that as well. I am semi familiar with the ways of ssh since i have been using it with my school server (fedora core 5) with my CS classes.

At school i had a external hard drive i plugged directly into my laptop. when i got home i plugged the drive into my bros computer figuring it would be no big trick to access the files around the house remotely.

so i go into the terminal and type in the ssh command and get the following error:
```
$ ssh uname@PCname
ssh: PCname: Name or service not known

```

thinking ssh might be the problem i try my schools server and it works perfectly.

now i am baffled do i have to configure a fiesty computer to be a ssh server or what?

the ultimate goal of this little adventure is to mount the drive on plugged into my bros pc in my /media directory using fstab or something and "trick" amarok and BT so that i dont need to reconfigure anything.

any pointers would be awesome
jeBsky

---

### Post by chili555 on 2007-05-13
So you want to ssh computers on the network by name instead of an ever-changing IP address? You could install winbind and configure it, a process that's a bit complex but certainly do-able. If you had 4-5 machines on your network, that's probably what I'd suggest. However, you have two, you and brother. 

The quick and easy way to handle a small network is to give brother a statis IP address, let's say 192.168.1.105. Then, *sudo gedit /etc/hosts* to add a new line:```
192.168.1.105   PCname
```Save and close gedit and you will then be able to ssh, ping, etc. by name: ssh brother@PCname.

---

### Post by bukwirm on 2007-05-13
You also need to have the ssh-server installed on your brother's computer.

---

### Post by Balinsky on 2007-05-13
with both of your ideas now it works perfectly thanks

---

