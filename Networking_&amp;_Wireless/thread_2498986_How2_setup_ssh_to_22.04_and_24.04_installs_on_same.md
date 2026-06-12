---
title: "How2 setup ssh to 22.04 and 24.04 installs on same computer"
date: 2024-07-06
forum: Networking &amp; Wireless
---

### Post by him610 on 2024-07-06
There are no problems *ssh* into 10.0.0.60 on the 22.04.4 side; however, attempting to* ssh* in to 24.04 side gives me an advisory message.
```

hugh@b450m:~$ ssh -x hugh@10.0.0.60
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ED25519 key sent by the remote host is
SHA256:+(a long string of characters).
Please contact your system administrator.
Add correct host key in /home/hugh/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /home/hugh/.ssh/known_hosts:6
  remove with:
  ssh-keygen -f "/home/hugh/.ssh/known_hosts" -R "10.0.0.60"
Host key for 10.0.0.60 has changed and you have requested strict checking.
Host key verification failed.

```
The distro to boot into is chosen from the Grub menu.
Rather not remove an existing key, but add a new one.
What is the most sensible way to *ssh* into either 22.04.4 or 24.04 when either is running?
Would unique URLs manually assigned to each installation work? 
Or is there a better way?

---

### Post by &amp;KyT$0P# on 2024-07-06
If you are the admin of the remote system, copy the SSH keys in [FONT=monospace]/etc/ssh[/FONT] from the 22.04 install into [FONT=monospace]/etc/ssh[/FONT] in the 24.04 install.  If doing this while booted into 24.04, restart sshd for the change to take effect.

---

### Post by him610 on 2024-07-06
> If you are the admin of the remote system, copy the SSH keys in /etc/ssh from the 22.04 install into /etc/ssh in the 24.04 install. If doing this while booted into 24.04, restart sshd for the change to take effect.
I will try that. Thanks

---

### Post by him610 on 2024-07-06
> If you are the admin of the remote system, copy the SSH keys in /etc/ssh from the 22.04 install into /etc/ssh in the 24.04 install. If doing this while booted into 24.04, restart sshd for the change to take effect.
I will try that. Thanks

Added:
@halogen It works. Thanks for the elegant solution.

---

### Post by currentshaft on 2024-07-06
> **him610 said:**
> There are no problems *ssh* into 10.0.0.60 on the 22.04.4 side; however, attempting to* ssh* in to 24.04 side gives me an advisory message.
```

hugh@b450m:~$ ssh -x hugh@10.0.0.60
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ED25519 key sent by the remote host is
SHA256:+(a long string of characters).
Please contact your system administrator.
Add correct host key in /home/hugh/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /home/hugh/.ssh/known_hosts:6
  remove with:
  ssh-keygen -f "/home/hugh/.ssh/known_hosts" -R "10.0.0.60"
Host key for 10.0.0.60 has changed and you have requested strict checking.
Host key verification failed.

```
The distro to boot into is chosen from the Grub menu.
Rather not remove an existing key, but add a new one.
What is the most sensible way to *ssh* into either 22.04.4 or 24.04 when either is running?
Would unique URLs manually assigned to each installation work? 
Or is there a better way?

The output of the command provided the solution:
ssh-keygen -f "/home/hugh/.ssh/known_hosts" -R "10.0.0.60"

Perfectly safe to do so on a private network where you control all the hosts. It is also much more "elegant" and secure than duplicating/impersonating another host's identity.

If you're paranoid, run "ssh-keygen -lf /etc/ssh/ssh_host_rsa_key.pub" or whatever to get the fingerprint and compare them.

---

### Post by TheFu on 2024-07-06
Use different static IPs for the different booted OSes on the same hardware.

---

### Post by him610 on 2024-07-06
@halogen2
@currentshaft
@TheFu

You all have suggested three different solutions. Maybe this thread will help someone else.

Many thanks.

---

### Post by &amp;KyT$0P# on 2024-07-07
> **currentshaft said:**
> It is also much more "elegant" and secure than duplicating/impersonating another host's identity.

> **TheFu said:**
> Use different static IPs for the different booted OSes on the same hardware.

:confused:

Could you please explain why copying the host's identity across a dual-boot setup is bad and insecure?

It's clear why it would be a bad idea across independent systems (including individual VMs), and I don't do it even when erasing+reinstalling.  But dual-boot seems different from those other cases? -

[LIST]
[*]It's the same host
[*]Both OSes won't be simultaneously booted
[*]SSH is actively used on both OSes of the host, neither OS is being decommissioned from SSH
[/LIST]

What am I missing?

---

### Post by TheFu on 2024-07-07
> **halogen2 said:**
>  What am I missing?

One hack, gets 2 systems.  Please go with 2 different static IPs, two different hostnames and think of them as two completely different systems.

OR .... use KVM/QEMU and run them both concurrently on the same hardware.  Pretty much anything that isn't a FPS game or heavy video editor will work great these days.

---

### Post by &amp;KyT$0P# on 2024-07-07
> **TheFu said:**
> One hack, gets 2 systems.

Isn't that always true in a dual-boot setup regardless of SSH host identification?  How would having different SSH host identification isolate a hack to only one of the two systems?

> use KVM/QEMU and run them both concurrently on the same hardware.

+1

---

### Post by currentshaft on 2024-07-07
> **halogen2 said:**
> :confused:

Could you please explain why copying the host's identity across a dual-boot setup is bad and insecure?

It's clear why it would be a bad idea across independent systems (including individual VMs), and I don't do it even when erasing+reinstalling.  But dual-boot seems different from those other cases? -

[LIST]
[*]It's the same host
[*]Both OSes won't be simultaneously booted
[*]SSH is actively used on both OSes of the host, neither OS is being decommissioned from SSH
[/LIST]

What am I missing?

If one system is compromised, it will allow the attacker to compromise the other by impersonating its SSH identity.

It's not necessary "bad" to share SSH host keys, but generally we try to build defenses in depth, and rekeying systems is part of that strategy.

---

### Post by TheFu on 2024-07-08
> **halogen2 said:**
> Isn't that always true in a dual-boot setup regardless of SSH host identification?  How would having different SSH host identification isolate a hack to only one of the two systems? 

I was thinking of remote hack for both systems, but I suspect you are thinking that if either system has access to the storage for the other system, then both can be cracked with just one of them successfully attacked. There is a strong possibility of that.

For my suggested solution, having 2 different static IPs, it means that DHCP reservations can't be used, unless the DHCP server honors hostnames to provide the static IP, not just the MAC on a NIC.  Of course, having multiple NICs in the system could work as another workaround to the DHCP problem.  Or just setup the static IPs on the two OSes directly.

---

### Post by &amp;KyT$0P# on 2024-07-08
> **TheFu said:**
> I suspect you are thinking that if either system has access to the storage for the other system, then both can be cracked with just one of them successfully attacked. There is a strong possibility of that.

Yes exactly.

It sounds like the downside of sharing SSH host identification across a dual-boot is a defense-in-depth thing: shared SSH host identification is an *additional* vector by which a hack could spread to both systems, and better to have fewer such vectors where possible.

Thanks TheFu and currentshaft for the clarification! :KS

---

