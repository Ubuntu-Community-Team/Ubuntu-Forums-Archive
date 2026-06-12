---
title: "Can't resolve windows hostname."
date: 2011-08-16
forum: New to Ubuntu
---

### Post by leinad177 on 2011-08-16
I was using this guide [here]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") about mounting network drives and i get this error.

```
daniel@daniel-laptop:~$ sudo mount -a
[sudo] password for daniel: 
mount error: could not resolve address for daniel-computer: No address associated with hostname
No ip address specified and hostname not found
```This is the entry i put into /etc/fstab
```
//daniel-computer/Movies  /media/Movies  cifs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

I can ping the laptop via the hostname on the computer but not the other way around.

Can anyone tell me how to fix this?

---

### Post by bodhi.zazen on 2011-08-16
Add your windows box to /etc/hosts or add a dns server to your network.

---

### Post by leinad177 on 2011-08-16
Could you explain how to do that?

Thanks :)

---

### Post by bodhi.zazen on 2011-08-16
```
gksu gedit /etc/hosts
```

Add in your windows box, save the file.

The synatax is :

IP address   hostname
> 111.22.3.444     windows_host_name_goes_here

---

### Post by HermanAB on 2011-08-16
Edit the hosts file:
$ sudo gedit /etc/hosts

Then add a line like this:
192.168.1.100      daniel-computer

Get the IP address of the Windows machine with a DOS box:
C:\> ipconfig

---

