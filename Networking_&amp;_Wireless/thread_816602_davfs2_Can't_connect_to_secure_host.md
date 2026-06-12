---
title: "davfs2: Can't connect to secure host"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by dax2112rush on 2008-06-02
Hi,

I am trying to mount some secure webdav share with mount.davfs. I get the following error message:

Could not authenticate to server: ignored NTLM challenge, GSSAPI authentication error: Unspecified GSS failure.  Minor code may provide more information: No credentials cache found

I tried a few things including compiling davfs2 and libneon from source. My current config is : davfs2-1.2.2 (from src) and neon-0.28.2 (from source) on ubuntu 8.04.

I get the same message with davfs2 and libneon26 from ubuntu's repositories.

Full output of mount.davfs is

sudo mount -t davfs [https://some.server/some_share](https://some.server/some_share) /media/dav_share
Please enter the username to authenticate with server
[https://some.server/some_share](https://some.server/some_share) or hit enter for none.
Username: (username)
Please enter the password to authenticate user (username) with server
[https://some.server/some_share](https://some.server/some_share) or hit enter for none.
Password: 
/sbin/mount.davfs: the server certificate does not match the server name
/sbin/mount.davfs: the server certificate is not trusted
  issuer:      some.server
  subject:     some.server
  identity:    some.server
  fingerprint: 00:11:22:33:44:55:66:77:88:99:aa:bb:cc:dd:ee:ff:00:11:22:33
You only should accept this certificate, if you can
verify the fingerprint! The server might be faked
or there might be a man-in-the-middle-attack.
Accept certificate for this session? [y,N] y
/sbin/mount.davfs: Mounting failed.
Could not authenticate to server: ignored NTLM challenge, GSSAPI authentication error: Unspecified GSS failure.  Minor code may provide more information: No credentials cache found

Any help on how to get past this error message and how to remove the certificate warning would be appreciated!

Thanks
Eric:guitar:

---

### Post by kenklay on 2008-08-08
I was able to get a davfs2 working by follwoing this how to at [http://www.howtoforge.org/davfs_ubuntu](http://www.howtoforge.org/davfs_ubuntu)

There is a secrects file for the certificate but I do not know the format to enter a certificate.  It is located at /usr/share/davfs2 jfor system wide and in your home folder if you configured davfs2 for user access.

---

### Post by inoculator on 2010-09-28
Hello all,

I see this is very old, but I couldn't find any solution for this, as I experience the exact problem.

I have a fresh installed Ubuntu 10.04 full upgraded via Synaptics and installed DAVFS2 as descripted in many How-Tos.
The machine is behind a Proxy and if I type
mount /home/carsten/webdav/eagle
the process goes like this:
```

carsten@ubuntuplayground:~$ mount /home/carsten/webdav/eagle
Please enter the username to authenticate with proxy
[proxyIP] or hit enter for none.
  Username: [MyProxyUser]
Please enter the password to authenticate user [MyProxyUser] with proxy
[proxyIP] or hit enter for none.
  Password:  [MyProxyPassword]
Please enter the username to authenticate with server
https://[myHost]/[myPathToFolder] or hit enter for none.
  Username: [myWindowsAccount]
Please enter the password to authenticate user [MyWindowsAccount] with server
https://[myHost]/[myPathToFolder] or hit enter for none.
  Password:  [MyWindowsPassword]
/sbin/mount.davfs: the server certificate is not trusted
  issuer:      *******
  subject:     *******
  identity:    ********
  fingerprint: ********
You only should accept this certificate, if you can
verify the fingerprint! The server might be faked
or there might be a man-in-the-middle-attack.
Accept certificate for this session? [y,N] y
/sbin/mount.davfs: Mounting failed.
Could not authenticate to server: ignored NTLM challenge
carsten@ubuntuplayground:~$ 

```Here my FSTAB:
```

# Use 'blkid -o value -s UUID' to print the universally unique identifier
.
.[someDefaultStuff]
.
https://[myHost]/[myPathToFolder] /home/carsten/webdav/eagle davfs rw,noauto,user 0 0

```From the Synaptic I have installed and configured version 1.4.5-1

On the new source plattform [Savannah]("http://savannah.nongnu.org/forum/forum.php?forum_id=6316") I found a version from 1.4.6.
Is this already in progress for synaptics? 

Thanks for any help

carsten

---

