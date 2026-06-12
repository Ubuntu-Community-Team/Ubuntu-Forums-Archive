---
title: "mount nfs after wifi connects"
date: 2023-12-22
forum: Networking &amp; Wireless
---

### Post by jessel on 2023-12-22
Hello,

Is it possible to mount network shares automatically (/etc/fstab) after the wifi connects? At present it appears that the system attempts to mount prior to wifi connection.

At present I can open a terminal and enter "sudo mount -a" and then my network shares will be available. The line in /etc/stab is:
```
192.168.23.10:/volume1/photo    /mnt/photo    nfs    auto,_netdev    0    0
```

A look at the /var/log/syslog and it appears that I connect to my wifi (I lookup the ssid which is TDS1704) on line 2250 but the nfs mount failed on line 1984

```
1984 Dec 22 08:52:02 mojo mount[803]: mount.nfs: Network is unreachable
1985 Dec 22 08:52:02 mojo systemd[1]: mnt-jesse.mount: Mount process exited, code=exited, status=32/n/a
1986 Dec 22 08:52:02 mojo mount[798]: mount.nfs: Network is unreachable

2250 Dec 22 08:52:08 mojo NetworkManager[512]: <info>  [1703253128.1894] policy: auto-activating connection 'TDS1704' (636b3713-91d0-45f4-919e-51e5b50fee10)

```
I searched for a solution and I came across a number of instructions on how to setup mount a network drive, how to mount a network drive using nfs...

I found this which looks like it would work... but I wonder if it is the accepted solution or if there is a better solution.
[https://ubuntuforums.org/showthread.php?t=1197864&highlight=wifi%2C+mount](https://ubuntuforums.org/showthread.php?t=1197864&highlight=wifi%2C+mount)

Thank you

---

### Post by jimmyrus on 2023-12-22
> **jessel said:**
> Hello,

Is it possible to mount network shares automatically (/etc/fstab) after the wifi connects? At present it appears that the system attempts to mount prior to wifi connection.

At present I can open a terminal and enter "sudo mount -a" and then my network shares will be available. The line in /etc/stab is:
```
192.168.23.10:/volume1/photo    /mnt/photo    nfs    auto,_netdev    0    0
```

A look at the /var/log/syslog and it appears that I connect to my wifi (I lookup the ssid which is TDS1704) on line 2250 but the nfs mount failed on line 1984

```
1984 Dec 22 08:52:02 mojo mount[803]: mount.nfs: Network is unreachable
1985 Dec 22 08:52:02 mojo systemd[1]: mnt-jesse.mount: Mount process exited, code=exited, status=32/n/a
1986 Dec 22 08:52:02 mojo mount[798]: mount.nfs: Network is unreachable

2250 Dec 22 08:52:08 mojo NetworkManager[512]: <info>  [1703253128.1894] policy: auto-activating connection 'TDS1704' (636b3713-91d0-45f4-919e-51e5b50fee10)

```
I searched for a solution and I came across a number of instructions on how to setup mount a network drive, how to mount a network drive using nfs...

I found this which looks like it would work... but I wonder if it is the accepted solution or if there is a better solution.
[: mount.nfs: Network is unreachable 1985 Dec 22 08:52:02 mojo systemd[1]: mnt-jesse.mount: Mount process exited, code=exited, status=32/n/a 1986 Dec 22 08:52:02 mojo mount[798]: mount.nfs: Network is unreachable2250 Dec 22 08:52:08 mojo NetworkManager[512]: [1703253128.1894] policy: auto-activating connection 'TDS1704' (636b3713-91d0-45f4-919e-51e5b50fee10)I searched for a solution and I came across a number of instructions on how to setup mount a network drive, how to mount a network drive using nfs...I found this which looks like it would work... but I wonder if it is the accepted solution or if there is a better solution. [https://ubuntuforums.org/showthread.php?t=1197864&highlight=wifi%2C+mount](https://ubuntuforums.org/showthread.php?t=1197864&highlight=wifi%2C+mount)Thank you."]https://ubuntuforums.org/showthread.php?t=1197864&highlight=wifi%2C+mount]("http://Hi,Is it possible to mount network shares automatically (/etc/fstab) after the wifi connects? At present it appears that the system attempt to mount prior to wifi connection.At present I can open a terminal and enter &quot;sudo mount -a&quot; and then my network shares will be available. The line in /etc/stab is: 192.168.23.10:/volume1/photo/mnt/photonfsauto,_netdev00A look at the /var/log/syslog and it appears that I connect to my wifi (I lookup the ssid which is TDS1704) on line 2250 but the nfs mount failed on line 19841984 Dec 22 08:52:02 mojo mount[803)

Thank you
dunno if this helps, but you can run a script after connecting  [https://askubuntu.com/questions/13963/call-script-after-connecting-to-a-wireless-network](https://askubuntu.com/questions/13963/call-script-after-connecting-to-a-wireless-network)

---

### Post by SeijiSensei on 2023-12-22
I've thought about this problem quite a bit and have concluded that it is not possible using Ubuntu. The network doesn't come up until after you have logged in (to accommodate wifi users). I even asked here once about whether it was possible to run a script automatically after log in with root privileges. As far as I know, it's not possible.

---

### Post by jessel on 2023-12-22
Thanks for the responses, I think that I have this working as desired.

I put this down this morning and after coming back to it I looked at the responses. In particular the link provided by jimmyrus I read and thought about, I think on that page there was a related thread or something and I came across instructions for using x-systemd.automount...

I changed the /etc/fstab so that it now reads:

```
192.168.23.10:/volume1/photo    /mnt/photo    nfs    auto,_netdev,x-systemd.automount,user    0    0
```

And when I restart, the network drive is available. It works for the non-sudo user account as well. I am very happy with this. Not that writing a script is such a big deal but using a built in feature is preferable.

Thanks again

---

