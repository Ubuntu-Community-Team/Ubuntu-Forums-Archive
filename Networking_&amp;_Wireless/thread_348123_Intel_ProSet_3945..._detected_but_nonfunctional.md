---
title: "Intel ProSet 3945... detected but nonfunctional"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by V for Vitriolic on 2007-01-28
Alright, I've been trying to figure this one out for a week or so now.  I've got a Lenovo N100 laptop with Edgy installed on it and everything seems to work fine EXCEPT the proset 3945.  For whatever reason, it is correctly recognized and associated with the right driver under the device manager but does not have any sort of a network interface associated with it (backed up, of course, by its complete absence from iwconfig).

Anyone got any ideas?

---

### Post by V for Vitriolic on 2007-01-28
I take it I'm not gonna get any help with this one, then.

*No one* has anything?

---

### Post by mrpeenut24 on 2007-02-02
I've got the same problem.  I'm using a Velocity Micro Notemagix L80 Ultra and have the same chip with the same problem.  I thought it might be the wireless switch on the front of my laptop, but I completely reinstalled Ubuntu, making sure the switch was in the 'on' position.  Help would be greatly appreciated, as I need this laptop for school.

---

### Post by xfce1952 on 2007-02-10
> **V for Vitriolic said:**
> Alright, I've been trying to figure this one out for a week or so now.  I've got a Lenovo N100 laptop with Edgy installed on it and everything seems to work fine EXCEPT the proset 3945.  For whatever reason, it is correctly recognized and associated with the right driver under the device manager but does not have any sort of a network interface associated with it (backed up, of course, by its complete absence from iwconfig).

Anyone got any ideas?

Here are my notes for getting the ipw3945 working on a Thinkpad z61m. Running edgy eft (6.10) Xubuntu.

The ipw3945 driver comes with the ubuntu 6.10 installation, but the regulatory daemon ipw3945d is missing. It's contained in the restricted modules package, which is installed at the command line with:

aptitude install linux-restricted-modules-$(uname -r)

start the daemon thus:
/sbin/ipw3945-$(uname -r)
If there is an error message that ipw3945d is aleady running, but in fact it's not, delete /var/run/ipw3945.pid and try again (seems to be a bug that pid is left over).

Applications/system/networking (in Xubuntu, at least) will produce the network adaptor config dialog  and the wlan adaptor should now show there.  Insert your essid and key details, ip address etc.

Only WEP is available without further installations to enable WPA, so save some bother and use WEP security for the present on you wireless router.

The Firestarter firewall, if you use it can be troublesome, (you might find outbound pings are forbidden) but this can be sorted by opening the Firestarter GUI and doing File/Run Wizard. Seems to cure problem of false forbidden outbound traffic.

ifconfig -a should now report  the wireless lan adaptor as eth1 (eth0 being the wired connection), and iwconfig will show full details of wlan connection.

---

### Post by lavinog on 2007-02-10
> start the daemon thus:
/sbin/ipw3945-$(uname -r)

should it be:
/sbin/ipw3945d-$(uname -r)

with a 'd' after the 5?

---

### Post by Balinsky on 2007-02-11
apparently this i a very common problem. as i have the same problem on my dell inspiron 7something

i feel like a idiot for asking but what does:
-$(uname -r)
mean?

when i try just 
aptitude install linux-restricted-modules
in terminal i get the "you are not root" errors
so i assune it has something to do with that

i tried 
sudo aptitude install linux-restricted-modules
but there are no packages with that exact name just some other ones with that in the name

---

### Post by Nulifier on 2007-02-13
all -$(uname -r) does is sub in your linux version

if you don't belive me then type uname -r in

this worked for me and can be done easily in gnome without using aptitude

just search in synaptic for restricted and install the one that you get with uname -r in the console

then start the service

---

### Post by darwin_te on 2007-05-27
Kubuntu 7.04 (Feisty)
ASUS G1

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

WEP 104-bit (128-bit) setting connecting to Windows AP:

/etc/network/interfaces:

########################
#home - wifi
########################

auto eth1
iface eth1 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid youressidhere

# passphrase is test
# see [http://www.powerdog.com/wepkey.cgi](http://www.powerdog.com/wepkey.cgi) (Passphrase To Hexadecimal WEP Keys)
wireless-key1 9FDF3BFDFB10AFEB0925EF9605

wireless-defaultkey 1
wireless-keymode open

command line to bring wireless network up:

>ifup eth1

---

