---
title: "how to create lan with 2 machines, one for downloading"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by bs.jaze on 2009-10-23
hi,
i'm totally new to the computer world, but since i started to study AI i started using ubuntu, and i like it.
but now im using my laptop a lot and dont want it to be constantly writing and reading to my disk  (torrents) so i got this old computer and a router.
I want that old computer to download and share (torrents) but also wanna be able to get some selected files to my laptop over  a lan network, and i guess its also possible to get files from that old computer anywhere in the world. 
I am so far that i know im supposed to fix this with samba, but know nothing about internet/servers/clients/sharing/routers.  A little about ubuntu though
Somebody knows a good starting tutorial, the ones i found are not really clear.

---

### Post by Peter09 on 2009-10-23
Samba is basically for interfacing to Windoze shares. Try right clicking on a folder on one machine and setting it as shared. On the other machine go to the places menu and select network, you should find the shared folder there.

---

### Post by mapes12 on 2009-10-23
For internet access to files I guess you could consider [https://www.getdropbox.com/](https://www.getdropbox.com/)

For a LAN I guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved.

1.) Make sure the openssh-server and openssh-client are installed on both machines.

```
sudo apt-get install ssh
```Is a meta package and will install both applications. Or you can search for it in Synpatic and install it from there.

2.) Go to the machine you want to connect to. You need to find the machines IP address, so in Terminal:

```
ifconfig
```

This should give you an output just like this one

> eth0 Link encap:Ethernet HWaddr 00:50:da:e0:67:74
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:9 Base address:0xc000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:27 errors:0 dropped:0 overruns:0 frame:0
TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1732 (1.7 KB) TX bytes:1732 (1.7 KB)

wlan0 Link encap:Ethernet HWaddr 00:11:50:dd:a9:16
inet addr:**192.168.1.68** Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::211:50ff:fedd:a916/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1769 errors:0 dropped:0 overruns:0 frame:0
TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1661090 (1.6 MB) TX bytes:342426 (342.4 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-11-50-DD-A9-16-39-31-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - this the internal address of your network adapter).

So, in my case the address would be 192.168.1.68

3.) Access the computer
Now, when you want to access a computer from the other, go to places>connect to server.
- Choose SSH as the "service type" from the drop down list
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This is the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Click OK

You may get a message about keys on first time connection. Just OK it

You will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is Secure Shell which is designed to be just that i.e. secure.

Hope this helps.

---

### Post by bs.jaze on 2009-10-23
thanks for the fast reply,
it works till i get to ifcofig, there's just a eth0 information, at wlan there seems to be no connection.
the ssh is new to me though, thought that is what samba did..

---

### Post by bs.jaze on 2009-10-23
solved so far  thanks

---

### Post by undecim on 2009-10-23
You can set up that "old computer" as a file/torrent server.

Physical setup is easy: plug your router uplink (sometimes labeled "www" or indicated with a globe icon) to one end of a CAT 5 (network) cable, and the other end of the same cable to your modem (or wherever you would plug in your computer to get internet access)

Then download and install Ubuntu Server Edition on the your downloader machine. Once installed, make sure you have the lamp-server, openssh-server, and torrentflux packages by logging in and typing```
sudo aptitude install lamp-server openssh-server torrentflux
```

Then, from another Ubuntu computer (i.e. your laptop) you can go to a file browser and in the location bar, type "sftp://username@hostname.local/home/username" where  username is your username on the server and hostname is the server's hostname. (if the username on both computers is the same, you can leave out the "username@" part)

You will have to type your password that you log onto the server with. Your home folder on your server should now open up.

If you don't want to type in your password all the time, you can set up key-based authentication (which is considered more secure!): [https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Key-Based%20SSH%20Logins](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Key-Based%20SSH%20Logins)

Also, if you ever have to do this from a windows machine, you can use filezilla from the windows machine or set up samba on your server

To manage torrents for the server. go to [http://hostname.local/torrentflux](http://hostname.local/torrentflux) and log in with the same info you use to log into your server. From there you will have a nice html interface to manage torrents remotely.

---

### Post by bs.jaze on 2009-10-25
nice, certanly something i wanna do in the future!  thanx

---

