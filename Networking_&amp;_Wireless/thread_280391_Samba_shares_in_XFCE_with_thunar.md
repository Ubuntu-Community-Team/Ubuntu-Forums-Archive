---
title: "Samba shares in XFCE with thunar"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by Keshyden on 2006-10-19
I have recently set up Xubuntu on my laptop to speed things up a bit. My problem is not having a nice graphical way to browse my windows network (and one other ubuntu machine). Do I have to install Nautilus for this or is there a better way?

Thanks.

---

### Post by dbott67 on 2006-10-19
There's a package in the repos called 'linneighborhood'.

> Description:
An SMB network browser for Linux and X11.
This package allows users to browse SMB (e.g. Windows Network Neighborhood)
networks under X, and mount/unmount SMB shared filesystems via a graphical
interface.  It is somewhat more network-efficient that other similar tools
because  it uses the proper protocol for identifying network shares rather
than simply scanning IP address ranges.

In order for LinNeighborhood to work properly,  you must have the
smbfs filesystem compiled into your kernel and have a working Samba
setup.

-Dave

---

### Post by Keshyden on 2006-10-19
Cool. How do I go about setting up samba properly in Xubuntu?

---

### Post by dbott67 on 2006-10-19
Depends if you want to create a server or just connect to one.  If you just want to connect to one, you'll need 'smbfs' (SMB file System) and 'smbclient' (SMB client).  Install those, plus 'linneighborhood' as noted above.

```
sudo apt-get intsall smbfs smbclient linneighborhood
```

You should be able to browse SMB shares from the command line (just substitute 192.168.1.2 with the IP address or hostname of your SMB server), using the following command:

```
smbclient -L 192.168.1.2 -U%
```

```
dbott@thedrake:~$ smbclient -L 192.168.1.2 -U%

        Sharename       Type      Comment
        ---------       ----      -------
        PUBLIC          Disk
        Data            Disk
        Archive         Disk
        Music           Disk
        IPC$            IPC

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
```

If that command works, you should be all set with 'LinNeighborhood'.  I just installed it & everything seems to work... just type **LinNeighborhood&** from the terminal to get started (the trailing '&' puts the process in the background and returns control to the terminal window).  See attached screenshot.

If you want to mount SMB shares, read this thread:

[http://www.ubuntuforums.org/showthread.php?t=280473](http://www.ubuntuforums.org/showthread.php?t=280473)

-Dave

---

### Post by Wangsta on 2006-10-20
what if you want to create a network?

---

### Post by dbott67 on 2006-10-20
Just click on **SYSTEM > ADMINISTRATION > SHARED FOLDERS**.

Click **ADD** and select a folder to share... pretty easy.  Now, if you really want to create a dedicated server for work or something, then you may want to dedicate a computer to the task and lock it down (remove unwanted/unneeded services, etc.)

-Dave

---

### Post by Wangsta on 2006-10-20
I've already done that. But how do i get OTHER computers to access these files?

---

### Post by dbott67 on 2006-10-20
Depends on the other computers.
[B][U]
Windows XP:[/U][/B]
Click **START > RUN > \\IP.ADDRESS.OF.SERVER\SHARENAME**

**_Linux:_**
Follow instructions from above.

Note:
You may want to set the server IP to static, as using DHCP may cause issues for client PCs trying to connect if the IP address keeps changing.

-Dave

---

### Post by Wangsta on 2006-10-21
```
xubuntu@ubuntu:~$ smbclient -L 192.168.1.104 -U%
Error connecting to 192.168.1.104 (Connection refused)
Connection to 192.168.1.104 failed

```
this is what i got. 
the laptop where i'm sharing my folders from uses a wireless card.
so i assume that this must be the "server."

```
xubuntu@ubuntu:~$ ip address
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
    link/ether 00:10:a4:0f:88:fc brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:0d:88:65:05:34 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.104/24 brd 192.168.1.255 scope global wlan0
    inet6 fe80::20d:88ff:fe65:534/64 scope link
       valid_lft forever preferred_lft forever
4: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0

```

when you say substitute it with your ip address, that means my ip address is the one under wlan, right?

---

### Post by dbott67 on 2006-10-21
If I understand correctly, you have a laptop running Xubuntu with IP 192.168.1.104, correct?

Using the same laptop, you issue the command **smbclient -L 192.168.1.104 -U%**, but get an error.  I would suspect that you may have the firewall (iptables/firestarter/etc.) turned on.

When I issue the same command from my Ubuntu desktop with a shared folder, I get:
```
dbott@thedrake:~$  smbclient -L 192.168.1.106 -U%
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.22]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          IPC       IPC Service (thedrake server (Samba, Ubuntu))
        IPC$            IPC       IPC Service (thedrake server (Samba, Ubuntu))
        dbott-P4        Disk
        print$          Disk      Printer Drivers
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        THEDRAKE             thedrake server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        MSHOME               THEDRAKE
        WORKGROUP            PIII-600

```

So I'm guessing that you've got a firewall enabled on your laptop.

-Dave

---

### Post by Wangsta on 2006-10-21
well, the ip for the wireless card is 192.168.1.104. and i use the wireless card to connect to the internet. well, im not sure if this is "the" ip address of my computer.

so how do i turn off the firewall?

---

### Post by dbott67 on 2006-10-21
I'm not quite sure, as I don't have it installed (or XFCE).

Check in some of the program or system menus for 'Firestarter' and see if you can just disable it.  If you don't find anything in the menus, type the following from the terminal"

```
ps aux | grep iptables
```
```
ps aux | grep firestarter
```

If you see a process with one of the preceding names, it's installed. Firestarter is just a GUI front end for iptables (which is the firewall) --- if either or both are present it means that you have a firewall installed & running.

If you can't find anything to disable it, you can always uninstall via synaptic.

-Dave

---

### Post by Wangsta on 2006-10-23
i got this, and i have noo idea what it means:
```
xubuntu@ubuntu:~$ ps aux | grep firestarter
xubuntu   7936  0.0  0.6   2876   792 pts/0    R+   19:38   0:00 grep firestarter
xubuntu@ubuntu:~$ ps aux | grep iptables
xubuntu   7944  0.0  0.6   2876   796 pts/0    R+   19:38   0:00 grep iptables

```

i checked syanptic and it showed i didn't have it installed.

---

### Post by kalikiana on 2006-10-27
I am not shure if you are still looking for an appropriate client, but I recommend [pyNeighborhood](http://pyneighborhood.sourceforge.net). It can browse shares and mount folders automatically.

---

### Post by deshpak on 2008-01-06
You explanation was perfect.  You don't know how long I was looking for a solution to access my NSLU2 slug with attached drive.  I was amazed at how easy it was to follow your directions and everything worked on the first try.  I am very new to the Linux world and with the help of people like your self I am getting more and more confident with using it.  Thank you!

---

