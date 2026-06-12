---
title: "TFTP , Transfer time out issues"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by kondrara on 2007-09-20
Hi,

I configured tftp on my ubuntu, which is running thru VMWare from a windows XP machine.

These are the steps i followed...

1. Install tftpd and related packages.

$ sudo apt-get install xinetd tftpd tftp

2. Create /etc/xinetd.d/tftp and put this entry:

service tftp
{
protocol        = udp
port            = 69
socket_type     = dgram
wait            = yes
user            = nobody
server          = /usr/sbin/in.tftpd
server_args     = /tftpboot
disable         = no
}

3. Make /tftpboot directory

$ sudo mkdir /tftpboot
$ sudo chmod -R 777 /tftpboot
$ sudo chown -R nobody /tftpboot

4. Start tftpd through xinetd

$ sudo /etc/init.d/xinetd start

After this i tried testing the tftp locally on my machine by get and put commands. It always shows that Transfer timed out.

even I  can see that xinetd, inetd, in.tftpd all running, and with 

netstat -a |grep tftp too I am able to see tftp running. Can any one help me in this issue. I was struggling with tthis issue from 2 days.

Thanks in Advance.

-Ravee.

---

### Post by rajan_rai on 2007-09-25
I had similar issue. I disabled firewall and now tftp is working fine. Other way is to add tftp in trusted service.

-Rajan

---

### Post by iyud on 2007-12-06
hi,

I have a similar issue of TFTP problem, I tried a simulation to send and receive a cisco IOS  beetween Ubuntu's tftp and TFTPD32 in Windows XP and it always succeed, but if I try to do the same beetween ubuntu and a real cisco router always get timeout, anyone can help me?

tks

---

### Post by davey.moore on 2008-06-21
Sorry to bump this, but there isn't much infor on the net on this.
I have exactly the same problem as kondrara, so if you see this and managed to solve it please answer!

thanks

---

### Post by VVarga on 2008-07-08
Hi every body!

I met with both problem with tftp service
1. No such file or directrory after put hda.txt
   This problem caused by selected directory where I have started tftp.
   My solution select directory cd /tftpboot   :)

2. Operation timed out error after put hda.txt
   after I istalled an other tftp package problem eliminated
   So I think try the following if you have same problem:

   sudo apt-get install tftp-hpa*
   sudo /etc/init.d/xinetd restart

I hope it will help :)

---

