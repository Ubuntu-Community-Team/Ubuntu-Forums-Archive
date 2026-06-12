---
title: "cannot SSH from internal network"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by stekole on 2007-04-06
Alright so I am currently running the server edition of edgy. 

I have the box acting as a file server in my basement. I can use SAMBA...and i can use Winscp to transfer files...but i cannot ssh from any non linux machine to this machine from my local network.
I also have a debian server running in my house. when i ssh to the ubuntu machine it works fine! now..i did have shorewall installed...i uninstalled it because it is not needed...I THINK i cleared the IP tables so it should work.. I was wondering if someone could give me a little help here:) 

Thanks

---

### Post by cookfromfrozen on 2007-04-06
When you say it doesn't work, do you not receive any response from the other machine?  If so, it probably sounds like there is still a firewall rule blocking that particular machine from connecting.  There may also be a deny entry in /etc/hosts.deny.

---

### Post by stekole on 2007-04-06
hosts.deny there is no rule. and as for firewall...how would i check the current rules and get rid of them

im pretty sure that has to do with IP tables and i did the commands to get rid of them all..i think

---

### Post by Jovec on 2007-04-06
Check the output of "sudo iptables -L", or post it if you want/need help

---

### Post by stekole on 2007-04-06
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 


:)

---

### Post by Jovec on 2007-04-06
> **stekole said:**
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 


:)

That output means you have no iptables rules in effect, so that is not the problem.  Probably related to the ssh daemon.  You can check for negated (!) entries in:

/etc/ssh/ssh_known_hosts
~/.ssh/known_hosts

but those might be stored as hashes so that won't help you, although you could try temporarily renaming those to see if that is your problem.

Edits:  A simple "telnet hostname ssh" should give you some clues to, like if you can even reach that host on the ssh port.

---

### Post by stekole on 2007-04-06
SSH-2.0-OpenSSH_4.3p2 Debian-5ubuntu1

Protocol mismatch.

so at least something came up when i telneted to it...

as for known hosts its fine...

I do not know wat the issue could be:S -- i have a dlink router..but that should not be the issue because its internal correct?

edit: if i connect from an outside IP it works....(i have port forwarding on..)

---

### Post by Jovec on 2007-04-06
> **stekole said:**
> SSH-2.0-OpenSSH_4.3p2 Debian-5ubuntu1

Protocol mismatch.

Well, looks like you found your answer then.

Your Ubuntu and Debian comps are running the same SSH protocol/version.  Your outside comp is too.  Your other computers inside aren't, and you'll most likely need to update the SSH software on those.

---

### Post by stekole on 2007-04-06
naw man thats not the issue for sure...first off because the Debian machine isnt on...second because that error means protocol missmatch because im trying to TELNET to SSH they are dfferent protocols. and third because it says debian ubuntu is because they are based of the same kernel. so that cant be the issue...
when i go to use putty it says "network connection refused" . therefore it must be something on the machine itself.

---

### Post by okej01 on 2007-04-13
> **stekole said:**
> SSH-2.0-OpenSSH_4.3p2 Debian-5ubuntu1

Protocol mismatch.

so at least something came up when i telneted to it...

as for known hosts its fine...

I do not know wat the issue could be:S -- i have a dlink router..but that should not be the issue because its internal correct?

edit: if i connect from an outside IP it works....(i have port forwarding on..)

stekole,

I am experiencing the same situation with a D-Link DIR-655 router.  Please post if a solution is available or pm to commiserate.

---

### Post by MrHorus on 2007-04-14
> **stekole said:**
>  
I have the box acting as a file server in my basement. I can use SAMBA...and i can use Winscp to transfer files...but i cannot ssh from any non linux machine to this machine from my local network.

Then you have a software issue on your Windows boxes.

It's not going to be an SSH problem as if it was, then you wouldn't be able to use an SSH tunnel to copy files using SCP, would you? :)

Out of interest, what SSH client software are you using?

Humour me and try PuTTY if you aren't doing so already...

---

### Post by rpjanaka on 2007-06-29
pleas can i know that how to start a new thread....?could not find any link for new thread...?:(

---

