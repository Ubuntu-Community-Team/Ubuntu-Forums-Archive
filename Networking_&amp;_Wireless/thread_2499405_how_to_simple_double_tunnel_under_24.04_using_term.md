---
title: "how to: simple double tunnel under 24.04 using terminal or nautilus-Files"
date: 2024-07-25
forum: Networking &amp; Wireless
---

### Post by Claus7 on 2024-07-25
Hello,

here I will describe the steps with examples in order for someone to connect from a linux computer (home), first to a linux remote computer (host1) and via host1 to a different linux remote computer (host2) either via terminal or gui.

In other words: home->host1->host2

Go to file ~/.ssh/config and add the information:

> Host "host1" "ip number like xx.xx.xx.xx" (here host1 is a name we give to differentiate each host) e.g. Host "test1" "12.34.56.78"
HostName ip number (here it needs the actual ip address as added above) e.g. HostName 12.34.56.78
User "username1" (the name of the user of host1) 
Compression yes
Protocol 2
Port xxx
HostKeyAlgorithms=+ssh-dss (these were not needed in old versions of ubuntu)
 
Host "host2" "ip number of host2"
HostName ip number (same pattern as host1)
User "username2"
Port xxx
HostKeyAlgorithms=+ssh-dss

Host "host3" "ip number -again- of host2"
HostName ip number of host2
ProxyJump host1 (this is the same as what you wrote in the first line after Host as host1) 
User username2
HostKeyAlgorithms=+ssh-dss

Terminal
```
ssh host3 
```
or
```
ssh -J username1@ip_host1:port_host1 username2@ip_host2
```

Gui via nautilus-Files
open Files and go to other locations
there add the line:
```
sftp://host3/
```
which will ask for username2 and password2 
or
```
sftp://username2@ip_host2/
```
it will ask both passwords pswd1 and then pswd2

Regards!

---

### Post by TheFu on 2024-07-26
Hard to follow without code tags and prompts, at least for me.  Indentation in the ~/.ssh/config file really helps break up stanzas too.

Why are any passwords requested?  Use ssh-keys and ssh-agent, so this happens just once, then not again until the user logs out of their local workstation and back in again.  Using passwords over the internet is really poor security.

---

### Post by Claus7 on 2024-07-27
Hello,

> **TheFu said:**
> Hard to follow without code tags and prompts, at least for me. 
Well mentioned, tags added.

> **TheFu said:**
> 
Indentation in the ~/.ssh/config file really helps break up stanzas too.
Again full path provided.

> **TheFu said:**
> 
Why are any passwords requested?  Use ssh-keys and ssh-agent, so this happens just once, then not again until the user logs out of their local workstation and back in again.  Using passwords over the internet is really poor security.
Passwords are requested every new login. I just pointed out the passwards, since I saw different behavior using the two different methods mentioned above: I found out that one method requires only one password, yet the other requires two. Unless I hadn't logged out in between and password was "remembered", yet I doubt it.

Regards!

---

### Post by TheFu on 2024-07-27
With ssh-keys and ssh-agent setup, only the initial key unlock should prompt for a password.  All other uses should use ssh-agent and handle passing authentication between systems automatically.
```
NAME
     ssh-agent — OpenSSH authentication agent

 DESCRIPTION
     ssh-agent is a program to hold private keys used for public key authenti&#8208;
     cation.  Through use of environment variables the agent can be located
     and automatically used for authentication when logging in to other ma&#8208;
     chines using ssh(1).
```

If ssh-agent isn't automatically started for you, you can add it to your .login file. Just check for the non-existence of  "${HOME}/.gpg-agent-info"

---

### Post by currentshaft on 2024-07-27
> **Claus7 said:**
> Host "host1" "ip number like xx.xx.xx.xx" (here host1 is a name we give to differentiate each host) e.g. Host "test1" "12.34.56.78"
HostName ip number (here it needs the actual ip address as added above) e.g. HostName 12.34.56.78
User "username1" (the name of the user of host1)
Compression yes
Protocol 2
Port xxx
HostKeyAlgorithms=+ssh-dss (these were not needed in old versions of ubuntu)

Host "host2" "ip number of host2"
HostName ip number (same pattern as host1)
User "username2"
Port xxx
HostKeyAlgorithms=+ssh-dss

Host "host3" "ip number -again- of host2"
HostName ip number of host2
ProxyJump host1 (this is the same as what you wrote in the first line after Host as host1)
User username2
HostKeyAlgorithms=+ssh-dss


90% of that is pointless.

Protocol 2 has been the default option for decades. So has Compression.

HostName should be a ... hostname and not an IP address, so you can get SSHFP DNS records to confirm the server you're talking to isn't being man-in-the-middled.

Also, why are you explicitely turning on ssh-dss as a host key algorithm? It was literally deprecated almost a decade ago.

On top of that you're recommending password-based authentication which is an awful security anti-pattern.

It is nice of you to share your workflow (I guess; it's still not clear why one would need to go through another host to access remote files), but you do not seem well qualified to be advising other users. Sorry.

---

