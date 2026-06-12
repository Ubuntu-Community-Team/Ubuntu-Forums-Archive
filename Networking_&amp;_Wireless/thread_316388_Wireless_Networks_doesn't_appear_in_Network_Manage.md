---
title: "Wireless Networks doesn't appear in Network Manager"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by gunst on 2006-12-10
Hi all.
Somewhat new to this lovely Edgy on my laptop. I've installed the gnome Network Manager, but the problem is that it doesn't detect the wireless networks. I can connect to them by going to System->Administration->Networking and then fill out the network name and so forth. So somethings working.

Do anyone know of this problem, and most importantly how to solve it? It would be nice if they appeared when i click the Network Manager icon in the panel.

My wireless is a PRO/Wireless 2915ABG Network

\Gunst

---

### Post by fredj on 2006-12-11
Edit the /etc/network/interfaces file and remove the lines that
refer to your wireless adaptor. Save the file and restart. Then
you should be able to network manager to connect to wireless 
networks.

---

### Post by matt_tee on 2006-12-12
There seems to be a lot of recent problems with wireless connection in network manager, I myself have just had the same thing happen, all working ok, then no wireless connection.....

has something happened on a recent software update?:-k

---

### Post by gunst on 2006-12-12
Hey
Just tried your tip fredj, and it worked perfectly! No probs!
TY TY TY :) But I'll probably be back soon with more problems.

\Smith

---

### Post by scubanator87 on 2006-12-12
I too recently updated my system and now my network manager is broken :-(

ill try what you suggested and post again on results

---

### Post by scubanator87 on 2006-12-12
After making a backup of the original, 


```
sudo cp /etc/network/interfaces /etc/network/interfaces_backup

```

I edited the file using nano and changed it from this:

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid dacheat

auto eth2
iface eth2 inet dhcp
```

to look like this 

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp
```

then rebooted and everything worked 

thanks for the tip fredj :-D

---

### Post by rts on 2006-12-14
I'm having the same problem, but the advice here (or here [http://ubuntuforums.org/showthread.php?t=317041&highlight=network-manager](http://ubuntuforums.org/showthread.php?t=317041&highlight=network-manager) or here [http://ubuntuforums.org/showthread.php?t=315268&highlight=network-manager](http://ubuntuforums.org/showthread.php?t=315268&highlight=network-manager) or ...) doesn't help me.

Whenever I try to get Network Manager to bring up my wired interface (ra0), it fails.  Attached is a log.

I'm using:

[17179593.244000] rt2500 1.1.0 BETA4 2006/06/18 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)

Configuring via System  | Administration | Networking it works fine.

I'm using plain old WEP.

Very puzzled...  :-k

---

### Post by tc10b on 2006-12-20
I have a similar problem, I tried editing my interfaces file, but it doesn't seem to make a difference. :(
I still can't acess the wireless network. However it does now find my wired network. :)

Cheers

Tom

---

### Post by tc10b on 2006-12-20
I figured out the problem I had, for some reason the interface was listed twice in the file. I just deleted the second entry and hey presto!

Cheers

---

### Post by kylevan on 2006-12-20
I personally comment-out everything but the loopback interface in /etc/network/interfaces when using NetworkManager

I'm pretty sure that this makes ifup and ifdown scripts non-functional, but I'm not too concerned, since if something gets really buggered, I can just switch everything back.

---

### Post by usererror on 2006-12-20
> **fredj said:**
> Edit the /etc/network/interfaces file and remove the lines that
refer to your wireless adaptor. Save the file and restart. Then
you should be able to network manager to connect to wireless 
networks.

I also had this problem, I found from another thread that disabling the wireless card in Network-Admin (System > Administration > Networking ) and clicking Properties on my wireless card and then unchecking **Enabled This Device** or whatever it says at the top, and then restarting networking (/etc/init.d/networking restart) then frees up the wireless card for NetworkManager to control the wireless card...works great in my WPA at home...

now if i could only get EAP-FAST with Dynamic wep keys to work at my office... ](*,)

---

### Post by tc10b on 2006-12-21
Hmm...

Now when I switch from wired to wireless I can't connect to the internet. :(

Any suggestions?

---

