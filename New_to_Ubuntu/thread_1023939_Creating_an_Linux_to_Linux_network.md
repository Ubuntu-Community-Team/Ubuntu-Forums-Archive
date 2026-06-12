---
title: "Creating an Linux to Linux network"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by OutOfReach on 2008-12-28
I am going to create a pure Linux network between several PCs, all of them have Ubuntu except one which has Arch Linux (my computer).

Which software should I use? How would I go about actually creating the network?

I have heard several things about NFS but I am not sure if that is the answer. I am also behind a router, might that cause some problems?

Thanks. :)

---

### Post by scorp123 on 2008-12-28
> **OutOfReach said:**
>  How would I go about actually creating the network? By "create a network" do you mean enabling the computers so they could easily share files with each other ... or are we indeed talking about cabling, wiring, routing, TCP/IP addressing, and so on?

---

### Post by OutOfReach on 2008-12-28
Yes, by creating a network I meant enabling the computers to share files with eachother. Something like Samba but for Linux networks.

---

### Post by scorp123 on 2008-12-28
> **OutOfReach said:**
> Yes, by creating a network I meant enabling the computers to share files with eachother. Something like Samba but for Linux networks. Why not use SSH? On Ubuntu the package is called "openssh-server". Other distributions might use a similar name. This is straightforward and simple. You'd then be able to get into each other computer by using the username and password already in use there (basically the same user information that you'd use to login locally). To exchange files you could simply access each others file system. On Ubuntu and with GNOME you can do it e.g. like this:
**Places > Connect to Server > ...**
[LIST]
[*]Service Type: SSH
[*]Folder: /home
[*]User Name: yourusername (on the remote system!)
[*]Use "add bookmark" and give it a name, e.g. "ArchLinux"
[/LIST]

=> this will give you the remote system's "/home" folder as icon on your desktop and you could easily drag and drop files between your local system and the remote system.

---

### Post by dragos_iliescu_2005 on 2008-12-28
For sharing files you can just declare for the desired folder the sharing options to "YES" or you can install a FTP server, Apache server,...

---

### Post by jerome1232 on 2008-12-28
> **scorp123 said:**
> Why not use SSH? On Ubuntu the package is called "openssh-server". Other distributions might use a similar name. This is straightforward and simple. You'd then be able to get into each other computer by using the username and password already in use there (basically the same user information that you'd use to login locally). To exchange files you could simply access each others file system. On Ubuntu and with GNOME you can do it e.g. like this:
**Places > Connect to Server > ...**
[LIST]
[*]Service Type: SSH
[*]Folder: /home
[*]User Name: yourusername (on the remote system!)
[*]Use "add bookmark" and give it a name, e.g. "ArchLinux"
[/LIST]

=> this will give you the remote system's "/home" folder as icon on your desktop and you could easily drag and drop files between your local system and the remote system.

I'm going to second this idea! I've gotten faster speeds using ssh vs samba. And it's very easy to work with.

The thing about Linux is you have so many options in this area, ftp, ssh, nfs, samba. They all have their various advantages and disadvantages.

---

### Post by mapes12 on 2008-12-28
I guess what you want is file sharing between linux boxes - there is NO WINDOWS involved. This works for me: 

1.) install the openssh-server
to do that, type this command in both computers and let them run through. They may ask you to confirm the installation - say yes !

```
sudo apt-get install openssh-server
```

2.) find out the IP addresses of your computer
this is important to address the computers. use the following command to obtain your computers IP-Address

```
ifconfig

```
this should give you an output just like this one

> eth0 Link encap:Ethernet Hardware Adresse 00:13:77:04:cd:26
UP BROADCAST MULTICAST MTU:1500 Metrik:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 Sendewarteschlangenlänge:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Basisadresse:0x6000 Speicher:d2800000-d2820000

lo Link encap:Lokale Schleife
inet Adresse:127.0.0.1 Maske:255.0.0.0
inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
UP LOOPBACK RUNNING MTU:16436 Metrik:1
RX packets:992 errors:0 dropped:0 overruns:0 frame:0
TX packets:992 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 Sendewarteschlangenlänge:0
RX bytes:30392 (29.6 KB) TX bytes:30392 (29.6 KB)

wlan0 Link encap:Ethernet Hardware Adresse 00:13:02:0f:83:56
**inet Adresse:192.168.18.143** Bcast:192.168.18.255 Maske:255.255.255.0
inet6-Adresse: fe80::213:2ff:fe0f:8356/64 Gültigkeitsbereich:Verbindung
UP BROADCAST RUNNING MULTICAST MTU:1500 Metrik:1
RX packets:237037 errors:0 dropped:0 overruns:0 frame:0
TX packets:200628 errors:0 dropped:0 overruns:0 carrier:0
Kollisionen:0 Sendewarteschlangenlänge:1000
RX bytes:208782489 (199.1 MB) TX bytes:22525126 (21.4 MB)
your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine so, in my case the address would be 192.168.18.143.

3.) Access the other computer
Now, when you want to access a computer from the other, go to places -> connection to server.
- Choose SSH as the at the service type
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank
- the username *must* be specified. This would be the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Most imporant - click ok
you will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine and away you go!

---

### Post by OutOfReach on 2008-12-28
Hmm well I'll go with SSH then.

But would I need to install the openssh-server package on each computer? Because, there will not be one 'main' computer, as I said several computers will be accessing each other.

---

### Post by albinootje on 2008-12-28
> **jerome1232 said:**
> I'm going to second this idea! I've gotten faster speeds using ssh vs samba. And it's very easy to work with.

The thing about Linux is you have so many options in this area, ftp, ssh, nfs, samba. They all have their various advantages and disadvantages.

+1
I agree. Samba can be a pain to tweak when you're having transfer speed issues with it. The "folder sharing" from Nautilus looks nice though.

Perhaps the OP can give some more details.
You want uploading and downloading for several users inside a LAN divided over different machines ?

And something that I like as a cool feature,
This is for ssh in the url-field in konqueror :
fish://username@other_machine_ip

For Nautilus and ssh :
ssh://username@other_machine_ip

If you try using a samba share *through* Nautilus you will find some problems (last time i checked, like OpenOffice repeatedly asking for passwords, and giving errors).
Not sure whether this applies also to ssh via Nautilus.
You can go around this problem by mounting the samba shares manually on the commandline or with autofs, and not via Nautilus.

And.. you can even use bittorrent for sharing data locally ;-)

---

### Post by mapes12 on 2008-12-28
> **OutOfReach said:**
> Hmm well I'll go with SSH then.

But would I need to install the openssh-server package on each computer? Because, there will not be one 'main' computer, as I said several computers will be accessing each other.

Yep. Then you can access each machine as I posted.

---

### Post by billgoldberg on 2008-12-28
You'll want ssh.

Easy to set up and to use.

---

### Post by albinootje on 2008-12-28
> **mapes12 said:**
> Yep. Then you can access each machine as I posted.

If you trust everyone in the LAN, you can even use sshfs + autofs + ssh-key-authentication, with the idea that after a machine boots the shared directory will be visible right away, without having to type in a password or click anything.

You could create a non privileged user on all those machines, and give the normal users enough permissions to read/write in the home dir of the new non privileged user.

---

### Post by OutOfReach on 2008-12-28
Ahhh, I love SSH now. I love the ability of having control over one machine while on another. :)
Thank you guys for recommending SSH, I've never had any experience with things like this but it was very easy to install and use.


But one more question, how can I copy or move files from the computer I am connection to, to my computer?

---

### Post by jerome1232 on 2008-12-28
Open nautilus, hit ctrl+L, type ssh://username@servers.ip.address/home/username

Then you can hit ctrl+d to bookmark it so it's in your places menu

---

### Post by OutOfReach on 2008-12-28
On all the computers I'll be using Xfce. (They're all Pentium III's with < 500MB of RAM, except my laptop)

But of course I can run nautilus with --no-desktop.

---

### Post by lswb on 2008-12-28
A nice addition to the ssh server package is sshfs. With sshfs installed you can create a mountpoint (empty directory) and mount a remote filesystem, or subdirectory of one, to the mountpoint, similar to how a local disk is mounted. Then the mounted filesystem can be accessed by any cli command or gui program as if it were mounted locally.

---

### Post by albinootje on 2008-12-28
> **OutOfReach said:**
>  But one more question, how can I copy or move files from the computer I am connection to, to my computer?

You have several options :

* GUI style *
-------------
Nautilus, Konqueror, gftp, and there's more.

Personally I like to use gftp for scp/sftp on my own machine ...

(See this image :
[http://www.linux.com/var/slashimages/12cd04f90c9d599324ddd69928856cf4.png](http://www.linux.com/var/slashimages/12cd04f90c9d599324ddd69928856cf4.png)
Select SSH2 instead of FTP at the top right, and if you want, change ftp to ssh2 as the default protocol in the gftp preferences)

... and Konqueror when I'm not at my own computer and in a hurry

* CLI style *
-------------
scp example for files :
```

scp username@ssh-server:~/somefile*.txt .

```

scp example for directories :
```

scp -r username@ssh-server:~/some-dir .

```

sftp example :
```

sftp username@ssh-server 

```

fill in your password, hit <enter>

use commands like ls, put and get, just like in ftp, and type : help for more options

See also : 
```

man scp
man sftp

```

---

### Post by OutOfReach on 2008-12-28
I'll try out both sshfs (looks interesting) and the ssh support in Nautilus, gftp looks alright but eh...

---

### Post by hyper_ch on 2008-12-29
sshfs is very simple to use :) I'd go with that.

---

