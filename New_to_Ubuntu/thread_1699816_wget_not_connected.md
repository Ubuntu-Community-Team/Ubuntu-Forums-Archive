---
title: "wget not connected"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-03-04
Whatever site i put in wget, it says "Not connected". I do not what the problem is. Whenever I do sudo apt-get, it first tries to connect to the server of my college. How do i change it?

---

### Post by PunkLV on 2011-03-04
I am no sure I got you right, but...
Post the
```
cat /etc/hosts
```
```
cat /etc/apt/sources.list
```
```
cat /etc/network/interfaces
```

---

### Post by Paddy Landau on 2011-03-04
In addition to the previous post, do you have a proxy set?
System > Preferences > Network Proxy

---

### Post by RobikShrestha on 2011-03-04
Whenever I do sudo apt-get update, it tries to connect to 10.200.0.1 which is the server of my college. I do not know how to remove this address. I checked my proxy settings, both through browser and through system->network proxy, neither of them has this IP.

---

### Post by PunkLV on 2011-03-04
Please refer to what is written in my previous post. Post the output of those commands and you will get the help you require. As for now, you are not being helpful to yourself enough.

---

### Post by RobikShrestha on 2011-03-04
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	suzuki-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


suzuki@suzuki-laptop:~$ cat /etc/apt/sources.list

# deb-src [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main #deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic universe
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic multiverse
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-security main restricted
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-security universe
deb [http://archive.mitra.net.np/ubuntu/](http://archive.mitra.net.np/ubuntu/) karmic-security multiverse
deb [http://lgp203.free.fr/ubuntu/](http://lgp203.free.fr/ubuntu/) gutsy universe





suzuki@suzuki-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


additionally, I emptied apt.conf which stored 10.200.0.1

---

### Post by PunkLV on 2011-03-05
According to /etc/network/interfaces your network connection in not configured at all, therefore:
1) is it connected to internet through a router?
 1.1) if not, what IP/GW/mask addresses it used earlier?
 1.2) is it on the same network as the PC you are posting from?
2) what network device does the PC use/have?

---

### Post by RobikShrestha on 2011-03-05
Yes it is connected through a router for ADSL connection. But, earlier I took my laptop to college and used the IP address: 10.200.0.1 which is that provided by the college server. Then I again changed LAN settings to 'automatically detect settings' google chrome. Internet is running but i can't get updates. It uses ethernet card. I have got absolutely no idea what wrong I did.

---

### Post by TeoBigusGeekus on 2011-03-05
Your college firewall probably blocks the ubuntu repositories as spam/non trusted sites.
Try to use a proxy: [https://help.ubuntu.com/community/AptGet/Howto]("https://help.ubuntu.com/community/AptGet/Howto") (scroll down to "Setting up apt-get to use a http-proxy")

A good site with free proxies is this: [http://nntime.com/]("http://nntime.com/")

---

### Post by RobikShrestha on 2011-03-06
My main concern is not using it in college but at home. Will it work for home? I will try it.

---

### Post by RobikShrestha on 2011-03-06
Even if my college blocks ubuntu updates why can't i do them at home? I was able to do them before I took my computer to colg

---

### Post by RobikShrestha on 2011-03-06
I do not know what to do with those proxies. I changed my  Network Proxy settings from Direct Internet Connection to Manual proxy configuration and typed in ip and port addresses. But when I do sudo apt-get update it still says Connecting to 10.200.0.1 . I have removed this IP from every place possible. It's really frustrating

---

### Post by RobikShrestha on 2011-03-06
thanks it worked (the temporary proxy worked) but how do i completely remove that: trying to connect to 10.200.0.1. I don't know why it tries to connect to it when I haven't mentioned it anywhere i can possibly imagine

---

### Post by RobikShrestha on 2011-03-06
Please explain to me why those proxies were for free. What do they do? Why do we need them? Are they sources for the updates?

---

### Post by TeoBigusGeekus on 2011-03-06
The proxies are used whenever we want to hide our pcs and/or the sites we're visiting.
You connect to the internet via the proxy address, which means two things:
1)The sites you visit appear to be visited by the proxy address, not by you.
You can imagine where this could be useful (I won't tell you :P)
2)Your pc seems to connect only to the proxy address and nowhere else. If a site is blocked by a firewall, you enter a proxy and visit the site - the firewall thinks you're visiting the proxy address, whereas in fact you're visiting the site you want _through_ the proxy address.

As for the 10.200.0.1 problem, could it be your college's gateway?
Click your network settings (ethernet setup) and see if you encounter this address again.

---

### Post by RobikShrestha on 2011-03-06
Where is "Network settings". I looked at everything concerned with network. through system->preference and system->administration and auto eth0, but 10.200.0.1 is nowhere to be found.

---

### Post by The Cog on 2011-03-06
It might be worth running the command
> grep -R 10.200.0.1 /etc 2>/dev/null
and see if that address is mentioned in a configuration file somewhere. Maybe in /etc/apt for instance.

---

### Post by RobikShrestha on 2011-03-06
Thanks. Finally the problem is solved. Thank you very much!

---

### Post by TeoBigusGeekus on 2011-03-06
> **RobikShrestha said:**
> Thanks. Finally the problem is solved. Thank you very much!

Glad to hear that, but could you spare a minute and tell us how you solve it?
Others could benefit from your case.

---

### Post by The Cog on 2011-03-06
Yeah, I'm curious to know, too. The reason I suggested a recursive grep is that I don't know where proxy settings get hidden.

---

### Post by RobikShrestha on 2011-03-06
The IP address was in /etc/apt/environment
/etc/apt/apt.conf
and also /etc/apt/apt.conf~ (I guess it is a backup file or sth )

then in terminal I went as super user by
terminal> su
then entered password

then 
gedit environment
Then I deleted the IP address
 
I also deleted from every other file shown , but the ones with ~ recovered the IP (I don't know why)
Solved!

---

### Post by RobikShrestha on 2011-03-06
By every other file shown I mean those shown by
grep -R 10.200.0.1 /etc 2>/dev/null

---

### Post by Paddy Landau on 2011-03-07
> **RobikShrestha said:**
> then in terminal I went as super user by
terminal> su
then entered password

then 
gedit environment
Note: avoid su if possible. Rather use sudo (for CLI) and gksu (for GUI). In your case, you would use "gksu gedit environment".
 
> **RobikShrestha said:**
> the ones with ~ recovered the IP (I don't know why)
By default, gedit automatically creates a backup file when saving. You were correct that the files with ~ on the end are backups. So, when you saved the file, it created the ~ file as the pre-change backup. Don't worry about those files.

---

### Post by RobikShrestha on 2011-03-07
Is there a risk in using su ? are sudo and gksu for single commands? Anyways thanks!

---

### Post by Paddy Landau on 2011-03-07
> **RobikShrestha said:**
> Is there a risk in using su ? are sudo and gksu for single commands? Anyways thanks!
Correct, sudo and gksu are for single commands. Use su only when you have a set of root commands all in a row, a very unusual situation. It is easy to forget you have gone into su, making it rather dangerous.

---

### Post by PunkLV on 2011-03-07
```
sudo su
```
Would be preferable. Elevates to multi-command root shell, however you do not have to type root passw in and all your actions in this shell are considered as Roots doings by the system.

---

