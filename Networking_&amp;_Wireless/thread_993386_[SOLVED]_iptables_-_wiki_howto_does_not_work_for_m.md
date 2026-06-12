---
title: "[SOLVED] iptables - wiki howto does not work for me"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by dryder on 2008-11-25
Hi,
Hardy
Using the wiki info [" [COLOR="Blue"]here[/COLOR]]("http://www.azureuswiki.com/index.php/NAT_problem") under "**4.1.4 Port Forwarding on Linux, specifically Ubuntu**", I have created the script my_iptables_azureus.sh and put it in /etc./init.d
As the wiki states, I have > sudo chmod +x /etc/init.d/my_iptables_azureus.sh succesfully.

However, > update-rc.d my_iptables_azureus.sh start 51 S to link the file into the startup sequence gives me this:> david@ubuntu-server:~$ sudo update-rc.d my_iptables_azureus.sh start.sh 51 S
[sudo] password for david: 
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults|multiuser [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
david@ubuntu-server:~$ 

I added .sh to the commands as it is a script file, though the wiki does not.

May I ask for help in this command please?

Many thanks,
David

---

### Post by SpaceTeddy on 2008-11-26
> **dryder said:**
> david@ubuntu-server:~$ sudo update-rc.d my_iptables_azureus.sh start**[COLOR="Red"].sh[/COLOR]** 51 S

the red bit is wrong. This is not a filename, this is a paramter telling that this is a start directive. leave the .sh out there and it should work... 

i have never used update-rc.d before... didn't even know it existed... but the man page helps :)

---

### Post by dryder on 2008-11-26
Hi,
Hmm ... didn't see that as much as I looked at my command.Yes, the man pages can help but I found no solution before I posted, unfortunately.

As I noticed a few script files without the .sh, I decided to delete that extension from my filename.

So, I > chmod +x /etc/init.d/my_iptables_azureus successfully but
> update-rc.d my_iptables_azureus start 51 S .
gives me the same error:
> david@ubuntu-server:~$  Adding system startup for /etc/init.d/my_iptables_azureus ...
   /etc/rcS.d/S51my_iptables_azureus -> ../init.d/my_iptables_azureus
update-rc.d: symlink: Permission denied



David

---

### Post by dryder on 2008-11-26
Problem solved - I didn't run it as sudo.

Thanks :-)

---

