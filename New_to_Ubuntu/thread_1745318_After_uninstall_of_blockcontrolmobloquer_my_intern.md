---
title: "After uninstall of blockcontrol/mobloquer my internet traffic is blocked"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by spielball on 2011-04-30
I have a problem with moblock/mobloquer/blockcontrol. I had this installed in order to guard my p2p stuff and block bad peers. However, I found that blockcontrol caused more hassle than advantages, because it creates problems with all sorts of applications that need internet access (skype, etc). So I uninstalled it.

After the uninstall, I installed Uncomplicated Firewall (ufw) + gui to see what options it gives. I decided that I don't need it either. So I unstalled that too.

Everything worked normally after that. However, after a reboot this morning, my internet traffic was completely blocked. And I don't know what to do. This clearly must be a problem with the previously installed moblock/mobloquer/blockcontrol. But I have no idea how to fix it. And now I'm lost.

In order to try to fix it, I need info from the internet. Thus I have to boot into Windows inbetween, then boot back into Ubuntu and try possible solutions. If they don't work, again boot into Windows, check for info, etc. Sucks! ](*,)

Please, somebody help!

---

### Post by jre on 2011-05-01
To see what is happening check your iptables rules (This is the only place where something can go wrong from moblock/blockcontrol side. And I strongly guess this is what's happening with ufw, too.):
```
sudo iptables -L -nv
```

You should only get empty chains INPUT/OUTPUT/FORWARD without any rules in them, like that
```
$ sudo iptables -L -nv
Chain INPUT (policy ACCEPT 17 packets, 1126 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 26 packets, 1505 bytes)
 pkts bytes target     prot opt in     out     source               destination 
```        
If you get more then 6 lines output, post them and clean them up manually:
```
sudo iptables -F
sudo iptables -X
```
Also make sure that policy is ACCEPT.

> **spielball said:**
> This clearly must be a problem with the previously installed moblock/mobloquer/blockcontrol.
Come on, be fair :-)

My personal bet is that it is not blockcontrol's fault. Instead I guess, ufw used the "iptables-save" command, and these rules that were present once now get reapplied by "iptables-restore" on every boot again.

**Purge** everything instead of just uninstalling it:
```
sudo aptitude purge moblock mobloquer blockcontrol **ufw**
```

---

### Post by spielball on 2011-05-01
Damn, I was just about to edit my original post to tell people not to bother about it anymore. Because I have just re-installed Ubuntu. Needed desperately internet and thought I was stuck. Unfortunately, I can't test your solution anymore, as I'm on a fresh install now. But still, I do thank you very much for your kind help. I will mark this thread for possible future problems. Because I want to give UFW another shot. Hopefully I won't end up the same way again. I feel so dumb in Ubuntu, still have to struggle a lot to handle it. This morning I was so lost, I was really thinking about giving up and wipe Ubuntu from my harddisk. But then again, I already fell in love with Linux a bit. Above all, due to security issues. Ever since I had a trojan on my Windows, I am paranoid. And in the long run, I'd like to be able to get rid of Windows altogether.

---

