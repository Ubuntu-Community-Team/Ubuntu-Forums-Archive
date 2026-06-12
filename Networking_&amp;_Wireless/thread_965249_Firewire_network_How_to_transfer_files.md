---
title: "Firewire network: How to transfer files"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by bostonvinnie on 2008-10-31
I'm trying to connect two computers, both running Ubuntu 8.04 (Hardy), via Firewire to transfer large digital video files from one to the other. I can get the network up, and I can ping between the two computers, but beyond that I can't figure out how to actually transfer a file. My preference is to use a graphical file manager (Nautilus or Konqueror) so that I can pick and choose the files more easily.

I've loaded the eth1394 module on each computer and brought up the Firewire interfaces in their own subdomain, 192.168.200.0 (the two computers were also on the same wireless network, 192.168.100.0, but I brought down those interfaces when trying to set up the firewire network):

On machine #1, the desktop:
> desktop $ sudo modprobe eth1394
$ sudo ifconfig eth1 192.168.200.1 up
On machine #2, the laptop:
> laptop $ sudo modprobe eth1394
$ sudo ifconfig eth2 192.168.200.2 up
(the laptop has a built-in wireless card which is eth1, so the firewire interface is eth2)

Once this is done on both machines, I can ping from one to the other. However, I'm not sure what to do next. 

I tried sharing a folder from Nautilus, which seems to use SAMBA, but for some reason could not get it to actually make the share available; the error messages I got seem to indicate some permission problems. 

Next I tried ssh. I have an ssh server running on both machines, and I have used ssh successfully to transfer files between these two computers over the wireless network, so I figured it should work for the Firewire connection as well. No dice. I tried the Gnome/Nautlius "Connect to Server" tool to connect from the laptop to the desktop, told it to connect to an SSH server, entered the ip address, and got an error message that it was unable to connect. 

I then tested ssh on the command line between the two, but the connection would hang silently until I gave up and hit CTRL-X:
> laptop $ ssh -lvinnie 192.168.200.1

laptop $

As I said, I could connect between the two computers and transfer files via SSH using Natilus (or Konqueror's fish:// protocol) over the wireless network, just cannot do it over the firewire network.

I thought this might have something to do with the settings necessary to establish a direct-cable network between two computers, e.g., I have the wrong netmask or default gateway or something, but if this is the case I presumably wouldn't be able to ping. My next guess is that there is some default in Ubuntu Hardy which blocks things like ssh over eth1394, but haven't the foggiest what setting would need to be changed. Really, though I have no idea.

Any suggestions?

---

### Post by arti! on 2009-12-16
Although this thread is quite old, i had the same problem and found the following solution:

I wanted to share a folder with Samba in ubuntu 9.10 via firewire.
I did all you described for configuring the interface, but samba didn't work.

The reason is, you need to tell samba which interfaces it should use.

so in /etc/samba/smb.conf simply add a line like
```
interfaces = lo eth0 eth1
```(where lo is loopback, eth0 is my ethernet and eth1 is my eth1394)
add the interface of your choice (by the way, this line is found in the "Networking" section of smb.conf, but commented -> uncomment and edit - whatever)

afterwards you have to tell the samba-daemon to reload the config-file
```
sudo smbcontrol smbd reload-config
```and everything should be fine :)

greetz

---

### Post by erjoalgo on 2010-07-12
I am also stuck where the OP is:
```

sudo modprobe eth1394
sudo ifconfig eth1 123.123.123.1 netmask 255.255.255.0 up

```After doing this in the other box, the 2 can ping each other.

But ssh connection times out:
```

user@desktop:~$ ssh 123.123.123.3
ssh: connect to host 123.123.123.3 port 22: Connection timed out

```I tried the above step, adding the line 
```
interfaces eth0 lo eth1
```I even added the ip
```
nterfaces eth0 lo eth1 123.123.123.3
```And nothing. If pinging works, then I SHOULD be able to transfer files, what am I missing? Did the OP  ever got this to work? I've been trying this for DAYS.

---

