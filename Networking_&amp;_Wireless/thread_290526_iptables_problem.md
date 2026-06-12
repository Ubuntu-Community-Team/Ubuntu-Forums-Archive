---
title: "iptables problem"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by mlalich on 2006-11-01
Hi have created a ruleset script (.sh file) for iptables. I tried entering "gedit /usr/local/sbin/firewall.sh" and paste in the code I wrote for the script, but when I goto save, it says I don't have permissions to save the file or something like that. I was told by a friend that I did not need to try "sudo /usr/local/sbin/firewall.sh" as when I would try and run the file as sudo it'll grant the file root perissions and I wouldn't be able to run it as my standard user account. Anyways how do I save the file that way I need to?

Thanks

---

### Post by sebastfr on 2006-11-01
> **mlalich said:**
> Hi have created a ruleset script (.sh file) for iptables. I tried entering "gedit /usr/local/sbin/firewall.sh" and paste in the code I wrote for the script, but when I goto save, it says I don't have permissions to save the file or something like that. I was told by a friend that I did not need to try "sudo /usr/local/sbin/firewall.sh" as when I would try and run the file as sudo it'll grant the file root perissions and I wouldn't be able to run it as my standard user account. Anyways how do I save the file that way I need to?

Thanks

Hello

You do need to sudo to edit the file. And you probably need to sudo to run as well (I hope one cannot change/start/stop the firewall rules without having root privs)

good luck

Seb.

---

### Post by mlalich on 2006-11-01
My friend also suggested that maybe the "/usr/local/sbin" folder has certain permissions set to it to not allow me to save to it as a regular user. Anywas I'll try saving it to my user desktop and running it from there.

---

### Post by sebastfr on 2006-11-01
> **mlalich said:**
> My friend also suggested that maybe the "/usr/local/sbin" folder has certain permissions set to it to not allow me to save to it as a regular user. Anywas I'll try saving it to my user desktop and running it from there.

As a normal user you should only be able to write (or create new files) to your home directory, and /tmp (that is, on a normal configuration).

You may save the script to your desktop, but still you won't be able to run 'iptables' as a normal user (I imagine your script calls 'iptables' one way or another).

Why not using sudo though?

Seb

---

### Post by harrysales on 2006-11-03
Has the script got executable permission? chmod +x filename.exe

---

