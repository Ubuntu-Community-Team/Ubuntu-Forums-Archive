---
title: "SSH Slow To Start"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by timhaughton on 2007-06-09
When I made the switch from Edgy to Feisty, a problem arose with SSH. Whenever I try to start an SSH connection, Feisty just sits without activity for around 10 seconds before starting the connection.

This occurs whether I run SSH from the shell, or if I access a SSH server stored in my network places. When I access my server via GNOME's sshfs, I still see the same problem - 10 seconds of inactivity before trying to connect.

When I say inactivity, I mean no CPU, disk or network activity.

I've already disable ipv6 with no effect.

Needless to say this is a frustrating problem with what should be a bread and butter Linux application.

Some details - running Feisty x86 on a Lenovo 3000 N100 laptop.


Regards,

Tim Haughton

---

### Post by timhaughton on 2007-06-10
In the absence of a reply - I'll post a couple of solutions I've found:

1) Turn off "Automatic Service Discovery" in your Network Settings in GNOME.

or

2) Open /etc/ssh/ssh_config and comment out these 2 lines - 

GSSAPIAuthentication yes
GSSAPIDelegateCredentials no

Both these solutions fix the bug.

Regards,

Tim Haughton

---

### Post by dmizer on 2007-06-10
thank you.

---

### Post by salvador24 on 2007-12-16
> **timhaughton said:**
> In the absence of a reply - I'll post a couple of solutions I've found:

1) Turn off "Automatic Service Discovery" in your Network Settings in GNOME.

or

2) Open /etc/ssh/ssh_config and comment out these 2 lines - 

GSSAPIAuthentication yes
GSSAPIDelegateCredentials no

Both these solutions fix the bug.

Regards,

Tim Haughton

Thanks for the tip - used #2 in my home setup with Gutsy desktop connecting to a headless box running Gutsy server.  Not only did it resolved my issues with ssh asking for passwords slowly, but it also resolved an issue I was having with Nautilus where it would not connect to SSH folders and timeout waiting for a password cue.

---

### Post by ftmichael on 2008-07-12
Just a quick question: after editing config files like the ones mentioned above, does X need to be restarted before changes will take effect?  Is a reboot needed?  My understanding was that a reboot wasn't needed for anything except changes to the kernel or on a similarly deep level, and that when you edited a config file, you didn't need to restart X - the changes would take effect immediately.  Can anyone confirm?

Michael

---

### Post by dmizer on 2008-07-12
> **ftmichael said:**
> Just a quick question: after editing config files like the ones mentioned above, does X need to be restarted before changes will take effect?  Is a reboot needed?  My understanding was that a reboot wasn't needed for anything except changes to the kernel or on a similarly deep level, and that when you edited a config file, you didn't need to restart X - the changes would take effect immediately.  Can anyone confirm?

Michael

it has been so long since i've done this that i don't remember.  i don't think it required a restart of the x server, nor did it require a reboot, but i don't recall for sure.

i haven't needed to use this fix for a while.

---

### Post by ftmichael on 2008-07-13
My partner's having a related problem on his Hardy laptop - Nautilus won't connect via SSH, but the terminal will; Nautilus keeps giving a timeout error - and the fix is apparently the same, but neither setting **GSSAPIAuthentication no** nor disabling mDNS from /etc/nsswitch.conf (see below) helped at all, so we're a bit baffled.

In **/etc/nsswitch.conf**, he replaced:

```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```

with

```
hosts: files dns
```

as advised on [https://answers.launchpad.net/ubuntu/+question/9146](https://answers.launchpad.net/ubuntu/+question/9146) (comment from Neal McBurnett on 2007-07-03).

Michael

---

