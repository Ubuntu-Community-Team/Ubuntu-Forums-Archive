---
title: "Network - triangle///please help"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by powel212 on 2009-02-20
Hi

Having intermittent trouble with my network configuration. Need help.

I have 2 computers - one win7 / one ubuntu

Win 7 is daily use running through a router to an ADSL box and out to the internet.

Ubuntu is for file share. it also has its own router to the same ADSL box and out to the intenet.

Win 7 is 192.168.0.1

Ubuntu is also 192.168.0.1

So far no problems.......

However

Both computers have a second network card which connect the 2 computers directly through a switch. This connection runs 168.254.0.1

Here is where the problem lies.

On the 168.254.0.1 connection I want to assign my address manually but I don't know what the complete configuration should be.


address ?.?.?.?
netmask 255.255.0.0
gateway ?.?.?.?

DNS 168.254.0.1

Question marks represent what I don't know.

please see attached jpg for more clarity on my setup.

Thanks

---

### Post by Kellemora on 2009-02-20
Hi Powell

Different machines NEED their OWN IP addresses!

And it cannot be one used by your Router or Modem too.

My machines range from 192.168.1.100 to 192.168.1.108 using dynamic rather than static IP numbers, but they never change, even though we pulled one machine out of service, the 192.168.1.102 machine and replaced it with a new machine that automatically became 192.168.1.108

When looking for a machine using Go/Location it would be smb://192.168.1.105 for example.  TWO slashes, not three!

I suggest that installed should be Samba, smbclient and smbtree, and if smbfs is installed, uncheck it, it causes problems with seeing shares.

IF you have smbtree installed, you can always (from Terminal) type in smbtree and make sure that all of your shares are showing.  If you see them there, can ping them, and get to them using Go/Location, there is a BUG in Nautilus that sometimes causes shares NOT to appear in Places/Network.  I thought they fixed that, but obviously not, because even here Places/Network has not shown shares on 5 machines for over 2 weeks now.

Good Luck

TTUL
Gary

---

### Post by powel212 on 2009-02-20
Thank you for your reply. I will look into that.

I am looking for the address range of

169.254.0.1
255.255.0.0

as in 
DNS 168.254.0.1
address range: ?.?.?.? to ?.?.?.?
netmask 255.255.0.0
gateway ?.?.?.? what is the gateway with this DNS?

---

