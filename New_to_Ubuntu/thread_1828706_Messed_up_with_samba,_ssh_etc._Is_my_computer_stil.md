---
title: "Messed up with samba, ssh etc. Is my computer still safe?"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by Mikakko on 2011-08-19
Sorry if this has been asked before, I tried to search already.

So I wanted to share files between my two ubuntu laptops in my home network via wlan. I stumbled upon various forum threads which suggested installing samba, ssh and/or giver. I installed all three using ubuntu's own installer (applications -> software center) and messed up with their settings, never gaining remote access to my files on other laptop. Growing ever frustrated I tried to undo all i had done, resetting all settings and uninstalling every package i had installed.

However I am not sure what I did and what I didn't manage to undo and now I am unsure if my laptops are safe anymore? Is it enough that I uninstalled everything, or is it possible the apps left open ports or other security flaws behind? What should I do to make sure my laptops are still as secure as before and not open for everybody via wlan? Is it enough that I have gufw installed and set on enabled? Over-installing whole operating system for both computers seems quite rough and troublesome solution.

Please answer in layman's terms as I am quite an amateur with this stuff. I am running on Ubuntu 10.04 LTS, netbook edition on both computers.

---

### Post by smurphy_it on 2011-08-19
Well for starters you can look at your package managers history file.  In a terminal you can type:

```
cat /var/log/apt/history.log
```

If you are only interested on what was removed, you can search for the word remove, like so:

```
grep -i remove /var/log/apt/history.log
```

---

### Post by Morbius1 on 2011-08-19
If you install the following application:
```
sudo apt-get install nmap
```
And run the following command:
```
sudo nmap -sS -sU -T4 192.168.0.100
```
[COLOR=Blue]*Changing 192.168.0.100 to the ip address of your machine.*[/COLOR]

It will show you all open ports.

---

### Post by androssofer on 2011-08-19
> **Mikakko said:**
> Sorry if this has been asked before, I tried to search already.

However I am not sure what I did and what I didn't manage to undo and now I am unsure if my laptops are safe anymore? Is it enough that I uninstalled everything, or is it possible the apps left open ports or other security flaws behind? What should I do to make sure my laptops are still as secure as before and not open for everybody via wlan? Is it enough that I have gufw installed and set on enabled? 

doing stuff like tht I assume ur behind a router? which will prob hav a firewall in it, so i'd say u'd be safe enough. and, as i recently learnt, iptables (linux firewall) is installed by default and automaticly locks all the ports for incomming connections, so i'd say ur safe enough.

this brings me to the second point. They probably didnt work due to the firewall settings on sed router and ur ubuntu boxes. for example i use ssh on my router and i hav to forward the port on the router and then hav the ssh server box configured to accept connections on that port. could that have been the reason?

to get ssh working do this on ur "server" machine:

```
sudo apt-get install ssh
```

then test it with:

```
ssh username@127.0.0.1
```

(replacing username with your username)

if it connects ssh works on ur "server" comp :-). then open up port 22 to allow connections from your other comp, aka the "client". on your router, forward port 22 to the "server" comp. then on ur client machine do:

```
ssh serverusername@ipOfServer
```

(replacing serverusername with the username u use on your "server" machine, and ipOfServer with the ip of the "server" on ur local network, usually sumthing like: 192.168.0.3) it will ask for your password, then your in! if u do sumthing like: 

 ```
ls
```

it will show all the folders in the "server" home directory. then u'll know its working for sure!

then wen ssh works, sftp works and scp also work! u can google em for more info. then with ssh you can forward ports! so you could forward the samba ports. however if your using 2 ubuntu boxes i would recomend using NFS. its much simple to set up (in my opinion). then with ssh you can forward your NFS ports, so its encrypted and u dnt need to open up any more ports on your firewall and router as it will go through the ssh ports :-) .


info on NFS is [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

ssh port forward is [here]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding")

---

### Post by Mikakko on 2011-08-19
Thanks a lot for your help already.

I checked the install/uninstall history on both laptops and uninstalled every remaining package I had installed earlier.

The nmap thingy said following:

[I]Not shown: 1998 closed ports
PORT     STATE         SERVICE
68/udp   open|filtered dhcpc
5353/udp open|filtered zeroconf
Nmap done: 1 IP address (1 host up) scanned in 1.58 seconds[/I]

on both laptops so I take it it's ok for those two ports to be open continuously?

Also for my original problem, as androssofer suggested it was all about ufw. I disabled ufw using gufw and then, as I had read on one of the forums, went to locations->connect to server, chose ssh and filled the ip-address, folder and username of the other laptop, soon it asked me for password and after that gave me access. And yes, I am behind a router and I understand it should have a firewall in it.

So my final conclusion is that I should be pretty ok with my laptops' security now as I have removed everything I installed and there seems to be only those two ports open? The installed (and now uninstalled) apps can't have done any other changes or settings that would leave my comps vulnerable?

Also I think I continue using the firewall if it's truly that easy to gain access to the computer if on the same network. I wonder what would have happened if I had to use public networks or unencrypted home networks before I figured out how to enable ufw.

---

