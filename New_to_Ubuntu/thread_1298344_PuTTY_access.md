---
title: "PuTTY access"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by smithwk2 on 2009-10-22
Is there anything that I need to do on my Ubuntu machine to access it with PuTTY?  Thanks.

---

### Post by MrWES on 2009-10-22
> **smithwk2 said:**
> Is there anything that I need to do on my Ubuntu machine to access it with PuTTY?  Thanks.

Install the ssh server:
```
sudo apt-get install openssh-server
```

And if you're behind a router, you'll need to forward port 22; unless you configure ssh for another port.

You might also look into WinScp (Windows Secure Copy)

[http://winscp.net/eng/index.php]("http://winscp.net/eng/index.php")


~Bill

---

### Post by smithwk2 on 2009-10-22
Bill:

That worked.  Thanks for the quick help!!  Have a great evening.

Wayne

---

### Post by kevdog on 2009-10-22
Putty keys and Openssh keys are not interchangeable just an FYI!

---

### Post by MrWES on 2009-10-23
> **smithwk2 said:**
> Bill:

That worked.  Thanks for the quick help!!  Have a great evening.

Wayne

No problem, glad to help. 

Of course forwarding a port from your router opens you up for potential attacks. Couple of things you can do to make yourself more secure.

1. Only allow sshkey logins:
[http://www.mtu.net/~engstrom/ssh-agent.php](http://www.mtu.net/~engstrom/ssh-agent.php)

2. Install and configure DenyHosts for your computer:
[http://ubuntuforums.org/showthread.php?t=254149]("http://ubuntuforums.org/showthread.php?t=254149")
Good idea to add your IP(s) to the /etc/hosts.allow file to ensure you don't lock yourself out of your box; been there done that :)

3. Lastly, if you're really paranoid, you can configure a couple of iptables (firewall) rules to help prevent brute force attacks.
[http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/]("http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/")

A lot of people now configure their sshd to run on an alternative port, say 2222 -- however, I've found people still knocking on my door with that port too.

Bill

---

### Post by Paddy Landau on 2009-10-23
You don't need PuTTY on Ubuntu.

Just open a terminal and enter the command *ssh*.

Or, you can do this as a menu option or from a script, as follows.
```
gnome-terminal --execute ssh -l *loginname* *hosturl*
```Read the manual for gnome-terminal if you want other options, e.g. a title or a different profile.

Read the manual for ssh if you want other options, e.g. a different port from the default.

Example:
```
gnome-terminal --tab-with-profile='myssh' --title='SSH to example.com' --execute ssh -p 1015 -l smithwk2 ssh.example.com
```

---

### Post by -=hazard=- on 2009-10-23
> **Paddy Landau said:**
> You don't need PuTTY on Ubuntu.

Just open a terminal and enter the command *ssh*.

Or, you can do this as a menu option or from a script, as follows.
```
gnome-terminal --execute ssh -l *loginname* *hosturl*
```Read the manual for gnome-terminal if you want other options, e.g. a title or a different profile.

Read the manual for ssh if you want other options, e.g. a different port from the default.

Example:
```
gnome-terminal --tab-with-profile='myssh' --title='SSH to example.com' --execute ssh -p 1015 -l smithwk2 ssh.example.com
```

Maybe he want to access on his box from a winzoz machine this is why he asked for putty, though the main goal was making his ubuntu ready for remote ssh control.

---

### Post by MrWES on 2009-10-23
> **-=hazard=- said:**
> Maybe he want to access on his box from a winzoz machine this is why he asked for putty, though the main goal was making his ubuntu ready for remote ssh control.

I was also assuming that.

~Bill

---

### Post by Paddy Landau on 2009-10-23
> **-=hazard=- said:**
> Maybe he want to access on his box from a winzoz machine this is why he asked for putty, though the main goal was making his ubuntu ready for remote ssh control.
Apologies for the misunderstanding.

---

