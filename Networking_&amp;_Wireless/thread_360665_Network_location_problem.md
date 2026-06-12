---
title: "Network location problem"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by MuhammadOfEgypt on 2007-02-13
hi there,
I am a complete new comer to the Linux/Ubuntu world, just installed Ubuntu 6.10 Edgy a few days ago and I like it so much.

I have a problem with the network location. I created a network location called "Home" with the DNS settings that are appropriate for me. But every certain amount of time, i find the Internet not working, and when i check the network location in System->Administration->Networking, i find that it has changed from the location that i set(Home) to a location with no name, and with DNS = 192.168.1.1. So i have to set the location again to "Home" for the Internet to work .

I don't know if this problem is because there are some kind of settings that i didn't set properly, or if this problem is because of a bug in the network manager. I'd say it's because of my ignorance with the Linux O.S.

Can anyone please help me?

Thanks in advance.

---

### Post by dannyboy79 on 2007-02-13
if you post the output from cat /etc/network/interfaces
we can make sure that we append a dns server within there so that even if this does happen you won't lose interenet access. just so you are aware, I experience the same issue where the "profile" doesn't stay when I click on it within the networking gui.

add a line at the end of the interface that you are using that looks like this:
dns-nameservers 192.168.1.1 192.168.1.2

that is documented here: [http://www.shallowsky.com/blog/linux/resolvconf.html](http://www.shallowsky.com/blog/linux/resolvconf.html)

also, make sure that your /etc/resolv.conf file contains your dns servers as well, like this:

search test.com
nameserver 192.168.3.2 

that is documented here: [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

---

### Post by MuhammadOfEgypt on 2007-02-13
hi,
First of all, thanx a lot for the quick reply.

Here are the entries in the /etc/network/interfaces file:
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0

iface dsl-provider inet ppp
provider dsl-provider


These are the entriesin the file. I am afraid i dont undersand what they mean exactly.

Also I checked the file /etc/resolv.conf. I changed the DNS IPs entries to the ones i want, and after a while they were reset back again to 192.168.1.1.

I read the articles u sent in ur reply, they were pretty helpful and taught me some nice stuff about the Linux O.S., but am afraid they didnt solve the problem yet.

May be the only solution is as u said to mention the name-servers in the /etc/network/interface file. But can u please show me where exactly in the file to include these DNS entries??

Thanx again for the help.

---

### Post by dannyboy79 on 2007-02-14
well, here is a thread devoted to your exact problem. [http://www.ubuntuforums.org/showthread.php?t=282034&highlight=dns+changing](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=dns+changing)

also, if I were you I would comment out (using this, #) or just delete ALL the interface entries you don't even have on your computer. so for example here is mine:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers xx.xxx.xx.xx

i only have 1 interface, which is an ethernet card, that's defined as eth0. but you also want to leave the 
auto lo
iface lo inet loopback
entry as well. basically you only want your interfaces file to contain interfaces that your machine has. so if you also have a wireless card, you might need wlan0 or ath0 depending on the chipset of the wireless card. you would be able to see all your interfaces by typing in 
ifconfig
at the command line.

I use static ip's so my interfaces file has everything spelled out whereas yours will most likely only need 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

if you're using dhcp. the problem with the dns servers is because of the dhcp ip address renewal or request. if you read the link I posted you'll see this and there is a fix. it may or not be adding this to the end of your interfaces file
dns-nameservers xx.xxx.xx.xx

just make you read it. so after you read it, your interfaces file **may** look like this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
dns-nameservers xx.xxx.xx.xx

BUT make sure you read it. you'll get it going for sure. good luck

---

### Post by MuhammadOfEgypt on 2007-02-14
:)  Problem Solved!!

Thanks a lot for the great help u offered, i really appreciate it.

And i'd like to say that, although am kinda new to the Ubuntu/Linux community, but i think i am loving it, You guys r great.

Thanks again.

---

### Post by dannyboy79 on 2007-02-15
please try to get in the habit of writing down HOW you solved it, this way when other's come to this thread, they'll know what to do to solve it as well. this way they don't have to read thru tons of threads to find an answer like you did. they can just come here, read the last post, and read what you put about how you solved it. I would thank you if you did this as well as the entire community would like it if you did also. thanks

---

### Post by MuhammadOfEgypt on 2007-02-15
**Problem:**
Every a specific amount of time, i found out that i lose Internet connection, after a little search, i found that in the System->Administration->Networking the network location is changed from the one i defined to another blank location, and so, all the DNS servers i defined were lost. So the problem of losing Internet connection was mainly a DNS problem. After that, and by the help of the community, i was introduced to the two files /etc/network/interfaces, and the file /etc/resolv.conf. The first file contains some info about the network interfaces i am using, but it didn't have any thing related to the DNS, so that was not the problem. For the second file, it contained the DNS servers i defined, and when i lost internet connection i found that the DNS servers entries in this file were erased and replaced with 192.168.1.1. So i found out that the problem was with this file. So the obvious solution was to stop this process of erasing and replacing the file entries. But i didn't find a clue how to do that. But after checking out this thread:

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=dns+changing](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=dns+changing)

i was introduced to another solution, it is very clear and introduces an easy procedure to solve the problem, u really should check it out.

**Solution:**
The problem was solved by following the thread i mentioned before, in brief, do the following:

1. open the file:  "/etc/dhcp3/dhclient.conf" for editing, u can do that by typing the following command in your terminal:
                      sudo gedit  /etc/dhcp3/dhclient.conf

2. Just before the request line in your dhclient.conf file that you are looking at in gedit, add the following line, or remove the comment # from the start of the line if it is allready exists):
                      prepend domain-name-servers 208.67.222.222, 208.67.220.220;
ofcourse, u'll replace the mentioned DNS IPs, with urs.

3. Restart your interface by typing the following command in your terminal:
                       sudo /etc/init.d/networking restart

That's it. And that's exactly what was mentioned in the thread i mentioned before, no more and no less. 
So what happened?? The line you added to the /etc/dhcp3/dhclient.conf file, pre-appended your DNS server IPs to the /etc/resolv.conf file, so if the network location was changed automatically to the blank location with the DNS IP=192.168.1.1 again, then u'll find the DNS IPs u want pre-appended to the /etc/resolv/conf file just before the 192.168.1.1, which prevent the loss of the internet connection.

That's all i think.

---

