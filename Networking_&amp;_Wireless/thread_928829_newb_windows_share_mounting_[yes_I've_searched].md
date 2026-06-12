---
title: "newb windows share mounting [yes I've searched]"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by idledecz on 2008-09-24
Hey All, I have a XP SP3 machine for a media server. It hosts all my music/movies/etc. I recently moved from XP to Kubuntu for my primary workstation. I want to mount the media server share so I don't have to keep using the Dolphin share wizard every time I want to watch a flick or listen to music.

I've searched around and so far this, kinda, works

```
sudo mount -t cifs //192.168.1.120/share /mnt/mymount -o user=user,password=password

```

The thing is that will only work if I point to an exact share on the media server. I want to mount the 192.168.1.120 address so I can access ALL the shares it lists.

If I try 
```
sudo mount -t cifs //192.168.1.120 /mnt/mymount -o user=user,password=password

``` I get the following error:
> Mounting the DFS root for a particular server not implemented yet
No ip address specified and hostname not found

If I try 
```
sudo mount -t cifs //192.168.1.120/ /mnt/mymount -o user=user,password=password

``` I get the following error:
> mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

I'm really confused why it works when I specify a particular share on the server but won't work if I want to access the root of all shares. Yet if I use that handy share wizard in Dolphin I CAN specify the root share and everything I want.

---

### Post by McNils on 2008-09-24
Well, I use **autofs** to mount smb-shares. It can mount all shares from one server.

---

