---
title: "SAMBA mount.cifs not working after clean install 18.04"
date: 2018-12-29
forum: Networking &amp; Wireless
---

### Post by twan2 on 2018-12-29
Hi, 
I recently did a clean install of LUBUNTU 18.04. When this machine  was still on 16.04 I had figured out a mount command that would mount a  shared drive on a WIN7 machine. This worked great. Now on LUBUNTU 18.04 I  try the same command and it does not work. I am not very experienced in  this area so I want to reach out for help. What can I do to figure out  what the problem is?

My command-line looks like this:
mount.cifs //192.168.1.116/data2 /home/twan/mnt/lan -v -o credentials=.smbcredentials

My .smbcredentials look like this:
workgroup=WORKGROUP
username=<my-id>
password=<my-pw>

The result that I get is this:
Credential formatted incorrectly: WORKGROUP
mount.cifs kernel mount options:  ip=192.168.1.116,unc=\\192.168.1.116\data2,iochars   et=utf8,sec=ntlm,uid=1000,gid=1000,user=<my-id>,pass=********
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

I really have no idea what is wrong here.
My second system is still on 16.04 and it works fine with this setup.

---

### Post by twan2 on 2018-12-29
I found a solution. I did two steps:

1) Change credential file
I changed the line workgroup=WORKGROUP to domain=WORKGROUP
In itself this does not solve the problem, but at least I got rid of the error 22 message.

2) Change fstab file
I noticed that while experimenting and leave the workgroup= statement out of the credential-file I still got the same error. Strange that I would get an error about an argument that is not even in the command, right? This led me to comment out the line in /etc/fstab that would try to make the same mount during system boot. This had the desired effect. For some reason, the mount.cifs command seems to reference the options in fstab, even when the command is given standalone in a terminal.

Now my next step is going to find out how to get the same share mounted during system boot. If needed I will post a new thread if I run into trouble.
Thanks.

---

### Post by Morbius1 on 2018-12-29
Your original post was driving me crazy because I couldn't figure out how this mount:
>  mount.cifs //192.168.1.116/data2 /home/twan/mnt/lan -v -o credentials=.smbcredentials
Created this comment:
>  mount.cifs kernel mount options:   ip=192.168.1.116,unc=\\192.168.1.116\data2,iocharset=utf8,sec=ntlm,uid=1000,gid=1000,user=<my-id>,pass=********
If I was as smart as I think I am I should have asked if you had an fstab entry.

Me thinks the issue was [B]sec=ntlm

[/B]It works in 16.04 because the default version of smb in the Linux kernel was SMBv1. Depending on the kernel in 18.04 it's SMBv3 or negotiated between SMBv2.1 and SMBv3. SMBv2 and up is incompatible with sec=ntlm.

WHen you have nothing else to do try adding another option to your fstab line:
```
vers=1.0
```
That will set the smb version back to where it was in 16.04 and it might just work.

---

### Post by boucherja4784 on 2019-01-31
Setting version to 1.0 worked for me thanks for the tip!

---

