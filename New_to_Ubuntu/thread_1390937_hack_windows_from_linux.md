---
title: "hack windows from linux"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by kakashi_12 on 2010-01-26
Playing around with my home network, from another network, remoting in. Just want to test on my OWN network. Btw, I'm remoting from WIndows, into Linux, and trying to get into a Windows box on my home network. The windows box at home does have a shared folder. Here's my two ideas...

1. Access scheduled tasks of win pc. and do a run now of a file. How would i access scheduled tasks? does not show in linux. it will show sometimes in windows.

2. access hidden share and create file on desktop. how do i access hidden share from linux?

---

### Post by 3rdalbum on 2010-01-26
> **kakashi_12 said:**
> 1. Access scheduled tasks of win pc. and do a run now of a file. How would i access scheduled tasks? does not show in linux. it will show sometimes in windows.

If all your Windows system is doing is sharing a folder, then you cannot run commands on the Windows system unless you take advantage of some sort of security flaw in Windows' SMB system. Obviously we can't help you do that.

> 2. access hidden share and create file on desktop. how do i access hidden share from linux?

In Nautilus, press Control-L and type in the computer's name and the name of the share like this:

```
smb://computername/share/
```

Even a hidden share can be accessed this way. Of course, you'd be assuming that the attacker is looking for hidden shares and is willing to try guessing the name of such a share. And willing to guess a password too, if they find the share's name (as you should ALWAYS use a password, even on a hidden share).

While it's laudable that you want to take responsibility for your security, you might be going a little overboard with the testing. As long as your wireless network is WPA2 encrypted with a strong password, and you have a firewall in your network router, it's nigh-on-impossible to enter your network anyway. Having password-protected shares that are different to your WPA2 passphrase just seals the deal.

---

### Post by kakashi_12 on 2010-01-26
> **3rdalbum said:**
> If all your Windows system is doing is sharing a folder, then you cannot run commands on the Windows system unless you take advantage of some sort of security flaw in Windows' SMB system. Obviously we can't help you do that.
 
 Can't help me on my own network? okay.
 
In Nautilus, press Control-L and type in the computer's name and the name of the share like this:
 
```
smb://computername/share/
```
 
Even a hidden share can be accessed this way. Of course, you'd be assuming that the attacker is looking for hidden shares and is willing to try guessing the name of such a share. And willing to guess a password too, if they find the share's name (as you should ALWAYS use a password, even on a hidden share).
 
While it's laudable that you want to take responsibility for your security, you might be going a little overboard with the testing. As long as your wireless network is WPA2 encrypted with a strong password, and you have a firewall in your network router, it's nigh-on-impossible to enter your network anyway. Having password-protected shares that are different to your WPA2 passphrase just seals the deal.
 
I know that works for a shared name, but for hidden share, it's suppose to be c$ or $c. That doesn't work. There must be another way.
 
I am not testing. I am just playing.

---

### Post by mkvnmtr on 2010-01-26
If you are just playing then install zenmap. It is a front end for nmap. You can find the holes in your systems with that and it is fun to play with. It is in the repositories but you can also get it on Windows.

---

