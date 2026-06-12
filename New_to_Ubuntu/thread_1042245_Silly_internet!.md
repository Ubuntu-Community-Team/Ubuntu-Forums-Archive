---
title: "Silly internet!"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by beatrice on 2009-01-17
In the boarding school where I live during the week, my internet won't work. I was told I have to type user name and password somewhere in the System- Administration- Network tab. (well if I translate the tab would be called network, or something similar)
The thing is, I don't have it! The only internet related tab in System-Administration is Network Tools. In System- Preferences there is Network configuration and Network proxy. The thing I'm looking for looks like this:
[http://www.ubuntu.si/dokuwiki/doku.php?id=adsl_nastavitve](http://www.ubuntu.si/dokuwiki/doku.php?id=adsl_nastavitve)
I know the answer is simple! But I don't seem to be getting anywhere and it's really getting on my nerves specially because I remember I had this tab before I reinstalled Ubuntu!
(And it doesn't help if I try to edit menus. *Network something* seems to be hiding.)

:confused:

---

### Post by huwaw69 on 2009-01-17
Try typing:
gksudo network-admin
im still new to ubuntu so this is all i got if im wrong im sorry but thats how i managed that problem of mine....

---

### Post by cmnorton on 2009-01-17
> **huwaw69 said:**
> Try typing:
gksudo network-admin
im still new to ubuntu so this is all i got if im wrong im sorry but thats how i managed that problem of mine....

You are correct. Answer the sudo password request with your password (if you installed  Ubuntu).

---

### Post by beatrice on 2009-01-17
How is the code supposed to work? I tried and nothing really happens.... :)

---

### Post by cmnorton on 2009-01-17
You are supposed to have a menu choice under System --> Administration called Network. From there, you configure your network.

---

### Post by SanjoEel on 2009-01-17
Many questions need answered to help with this.
First, what type of internet connection are you using? Dial-up, DSL or cable?
Are you sure you are connected to a live internet connection?
Does the computer detect your network card? ( type "lspci" without quotes in a terminal, and see if it lists your card)
Is "network-manager" installed? You may have to install it. You can do so in a GUI with synaptic package manager.

Bring us some more info and we can help!

---

### Post by beatrice on 2009-01-17
It's still not there. I even tried rebooting. 
Any other ideas?

To SanjoEel
At home, internet works perfect (wired and wireless). Network card is fine. In a boarding school, it connects, but I can't browse. (it's an ADSL connection I think) I don't have a *network Manager* tab, but in Add/Remove Applications it says it is installed. So.... I'm just looking for something where I can type a username and password (at home my brother's computer is *the boss* and I connect via him, so I never needed typing username)

---

### Post by huwaw69 on 2009-01-17
> **beatrice said:**
> It's still not there. I even tried rebooting. 
Any other ideas?

Did you try being a root user before entering the code to terminal?
open terminal again
type:
su
then enter your password for root not the one your using in the login screen...
then type again
gksudo network-admin

-----------------------------------------------------------------
if you have not changed the root password yet
type this in the terminal

sudo passwd

then repeat the instructions above...


I hope im right about what i said, i hope someone correct me if im wrong...

---

### Post by beatrice on 2009-01-17
Jesus, when I tried that I got this...

```
root@MrEdgar:/home/kachar# gksudo network-admin
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(gksudo:6872): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

```

---

### Post by huwaw69 on 2009-01-17
> **beatrice said:**
> Jesus, when I tried that I got this...

```
root@MrEdgar:/home/kachar# gksudo network-admin
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(gksudo:6872): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

```

Yeah me too i got the same problem that shows but nothing will happen, did it show you the network thingy your looking for?

---

### Post by beatrice on 2009-01-17
No. :mad:

---

### Post by utnubuuser on 2009-01-17
Hi -- Is it not just a matter of clicking (right or left) on the network icon, selecting the desired network and entering the info in the pop-up window?

---

### Post by sailor2001 on 2009-01-17
try this: In synaptics, (system/administration) search wi-fi manager

---

### Post by beatrice on 2009-01-17
No. It connects automatically. Look, we have some strange internet connection I can't even explain in my own language. I called the service and they told me I have to enter the username and password in order to access the internet, the thing is, they didn't know why I don't have that famous network tab.

---

### Post by SanjoEel on 2009-01-17
This is puzzling. Hopefully an Ubuntu guru will come along to help with this. What do you mean by "a strange internet connection"?

---

### Post by sandip26879 on 2009-01-17
go to System-->Preferences-->Network Configuration

It is not there in Administration

---

### Post by Ben Page on 2009-01-17
> **sandip26879 said:**
> go to System-->Preferences-->Network Configuration

It is not there in Administration

Da, to ti je to, slovenka :)

---

### Post by albinootje on 2009-01-17
> **beatrice said:**
> Jesus, when I tried that I got this...

```
root@MrEdgar:/home/kachar# gksudo network-admin
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. 

You are logged in as root on that terminal ? Did you open a root terminal or did you use sudo before you entered that command ?

For network-admin you *have* to launch it as following, thus as *normal* user (no sudo or root user!) :
[code]
network-admin

```
Then it should show you the "unlock" button.
You can verify this as following (if you have it) :
1) Right click on the -> System -> Administration -> Network
2) Choose "add launcher to panel"
3) When it's on the panel, right click on it, and look at the "command" field.

---

### Post by beatrice on 2009-01-17
This is just getting more and more silly.

```
kachar@MrEdgar:~$ network-admin
The program 'network-admin' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-network-admin
bash: network-admin: command not found
kachar@MrEdgar:~$ sudo apt-get install gnome-network admin
[sudo] password for kachar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-network is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gnome-nettool
E: Package gnome-network has no installation candidate 
```

Before I just follow the instructions someone mentioned it might work. (that was when I got the strange error)

By strange internet connection I simply mean I can't explain how it really works, but to simplify it, it's ADSL. It works on windows, so there's nothing wrong with the connection. (it even connects me, as I've said earlier, but I can't browse internet. Or ping. )

---

### Post by albinootje on 2009-01-17
> **beatrice said:**
> This is just getting more and more silly.

```
kachar@MrEdgar:~$ network-admin
The program 'network-admin' is currently not installed.

Please post the output of this :
[code]
sudo apt-get install gnome-system-tools
lsb_release -a
uname -a

```
Thanks.

---

### Post by beatrice on 2009-01-17
```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-system-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid


Linux MrEdgar 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux 
```
:oops:

---

### Post by albinootje on 2009-01-17
> **beatrice said:**
> ```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-system-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Thanks for the output!

What gives :
[code]
locate network-admin|grep bin
dpkg -l |grep gnome-system-tools

```

---

### Post by zika on 2009-01-17
right-click on menu (with Applications, Places, System)->Edit_menus->Preferences->check-Network_Configuration.

open System->Preferences->Network_Configuration and make changes as it is suggested in [http://www.ubuntu.si/dokuwiki/doku.php?id=adsl_nastavitve](http://www.ubuntu.si/dokuwiki/doku.php?id=adsl_nastavitve)

---

### Post by beatrice on 2009-01-17
The first code gives nothing, the second displays this:
```
 ii  gnome-system-tools                        2.22.1-0ubuntu1                         Cross-platform configuration utilities for G

```

I already have Network Configuration (as I've said in the very first post). Could that be the same as Network? I don't know, like it used to be called Network in previous versions or something like that.

---

### Post by zika on 2009-01-17
Nastavitve_omrezja jeste Network_Configuration. dalje je sve kao u [http://www.ubuntu.si/dokuwiki/doku.php?id=adsl_nastavitve](http://www.ubuntu.si/dokuwiki/doku.php?id=adsl_nastavitve) ...

(sorry for english speaking readers ... it might be quicker this way)

---

### Post by beatrice on 2009-01-17
Hja no, ne izgleda isto kot na tistem linku. Mam posebi ži&#269;ne, brezži&#269;ne, vpn pa dsl. Bom poskusla ko pridem nazaj v Ljubljano. :)

---

### Post by zika on 2009-01-17
> **beatrice said:**
> Hja no, ne izgleda isto kot na tistem linku. Mam posebi ži&#269;ne, brezži&#269;ne, vpn pa dsl. Bom poskusla ko pridem nazaj v Ljubljano. :)
da, na tom linku je slika iz Ubuntu 8.04 (Hardy Heron). kakva je vrsta veze koju zelite da uspostavite: modem, DSL ili bezicna?

---

### Post by beatrice on 2009-01-17
brezži&#269;na ali ži&#269;na, obe možnosti sta. Samo ne najdem obrazca za uporabniško ime in geslo, ker samo to nucam.

---

### Post by zika on 2009-01-18
> **beatrice said:**
> brezži&#269;na ali ži&#269;na, obe možnosti sta. Samo ne najdem obrazca za uporabniško ime in geslo, ker samo to nucam.
da, sada sam shvatio. 
za zicno povezivanje:
pretpostavljam da imate u vasoj sobi kabl kojim se povezujete na mrezu, internatsku. tada vam ni ne treba username i password. ako je drugacije, to cemo resiti naknadno (nisam imao takvo iskustvo ali mozemo se snaci). u tom slucaju bi trebalo da imate adsl modem ili nesto slicno (usb ...)
otvorite terminal i u njemu otkucajte:```
gksudo gedit /etc/network/interfaces
```
password koji vam zatrazi je onaj za vas racunar, ne za mrezu.
file koji se pojavi valjalo bi da izgleda (izmenite tako da bude kao):```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface DHCP
auto eth0
iface eth0 inet dhcp
```
sada restart-ujte mrezu sa (u terminal-u):```
sudo /etc/init.d/networking restart
``` i kada zavrsi sa drugim "krugom" i (mogucno) ceka, otkucajte "enter". probajte mrezu. ako ne radi otkucajte u terminal-u:```
ifconfig
``` i posaljite rezultat.
srecno!

---

### Post by rednano12 on 2009-01-18
I think that Intrepid doesn't have that tab thing. I know for a fact that when I upgraded, it dissapeared. That might help.

---

### Post by yknivag on 2009-01-18
If the network connects ok but the internet cannot be accessed without a username and password, surely this is the school restricting internet activity to go through a proxy?

I'm not running Intrepid here but there should be a "Network Proxy" option in the "System"-"Administration" menu which should allow this to be configured.

You'll need the username and password (of course) and also either the address of the proxy pac file or the address and port of the proxy server.

Hope this helps.

---

### Post by beatrice on 2009-01-20
Well I solved the problem by phoning the tech support for the internet service I'm using (I had to try many times, because they kept telling me they do not support Linux, blahblahblah, but I finally got someone who knew what he was doing. 
THe thing I needed to do was to type the router address in firefox, type the username and password of the router and changed some settings. Easy trick, big troubles.

Thanks everyone for patience. :KS

---

