---
title: "nfs with 9.04 server edition"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by Thocrun on 2009-09-26
I do not know how to install nfs, I have the /etc/exports file edited to what it said + I have it installed on the server, started it, but my client (also 9.04 (desktop)) couldn't read it and I installed the nfs-common- I tried to mount it but it said the mount point /local/ubuntu does not exist.

---

### Post by bodhi.zazen on 2009-09-26
From that error my guess is you simply need to, on the client,

```
sudo mkdir /local/ubuntu
```

Otherwise we need some additional information. Are you running a firewall on either the server or client ?

See also :

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html)

---

### Post by Jose Catre-Vandis on 2009-09-26
Installing NFS on server:
```
sudo apt-get install nfs-kernel-server nfs-common portmap
```
add your share to /etc/exports

Export your share
```
sudo exportfs -a
```

Restart the server
```
sudo /etc/init.d/nfs-kernel-server restart
```

Installing NFS on client:
```
sudo apt-get install nfs-common portmap
```

Mounting share:
```
sudo mount xxx.xxx.xxx.xxx:/share /media/share
```

Check out [this thread ]("http://ubuntuforums.org/showthread.php?t=249889")for more info

---

### Post by Thocrun on 2009-09-26
any idea what I should put for an IP on the server?

---

### Post by bodhi.zazen on 2009-09-26
On the client you put the ip address of the server.

If you do not know it, log onto the server and type:

```
sudo ifconfig
```

You can add your server to the clients /etc/hosts (or set up DNS) .

---

### Post by Thocrun on 2009-09-26
I was just wondering how to even set up the IP's, netmasks and stuff so I can run everything I want, I am installing it from live cd to an old pc that used to rum windows Me.

---

### Post by bodhi.zazen on 2009-09-26
Do you have a router ? If so are you wanting to use dhcp or a static IP ?

If you are running a GUI you can use network manager. If not you will need to manually edit /etc/network/interfaces.

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

If you do not know your network settings, either get them from your router, get them from windows, or boot a live CD and use the ifconfig command.

```
sudo ifconfig
```

---

### Post by Thocrun on 2009-09-26
I don't have a router, I want to use a static IP and be able to do anything I want with it, I think a good one would be 192.168.198.xxx or something like that.-I have the server on that IP now and been trying nfs but I cannot mount it from the client


I get this error:  mount.nfs: DNS resolution failed for (server name): no address associated with hostname

---

### Post by Thocrun on 2009-09-26
> **Thocrun said:**
> I don't have a router, I want to use a static IP and be able to do anything I want with it, I think a good one would be 192.168.198.xxx or something like that.-I have the server on that IP now and been trying nfs but I cannot mount it from the client


I get this error:  mount.nfs: DNS resolution failed for (server name): no address associated with hostname
  now I get this when I use the IP address for it (on the client) mount.nfs: mount system call failed

---

### Post by bodhi.zazen on 2009-09-26
I am sorry you are having problems. NFS is a bit tricky to figure out, but it works well.

What guide are you following ?

And what is the architecture of your network. You must have a router of some kind , no ?

If not how are your  computes physically connected ?

---

### Post by Thocrun on 2009-09-26
I am following this guide: [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889) and the mounting at boot part I get the error, I have only two computers (one server 9.04 and one desktop 9.04 both 32-bit) and have them connected by ethernet crossover, no router. I have been having the problem when I get to the mounting at boot part of the guide and typing mount /files.

---

### Post by Jose Catre-Vandis on 2009-09-27
There is something basic going wrong here :(

Can you / do you have connectivity between the two PCs, i.e. they are on the same subnet (e.g.192.168.1.0) and you can ping each PC for the other?

Test the nfs server on the server, by setting up a test mountpoint and mounting one of your nfs shares there. Use the IP address of the server to do this, so for example:

Say you have a share in your /etc/exports file called /home
```
sudo mkdir /media/testnfs
sudo mount 192.168.0.xxx:/home /media/testnfs
```

If this works then nfs is doing its job so we can now move to the client and keep testing

---

### Post by bodhi.zazen on 2009-09-27
> **Thocrun said:**
> ...  have them connected by ethernet crossover, no router.

He is trying to connect without any kind of router.

So, when you connect via crossover, you assign the server an IP address manually and you assign the client an IP address manually.

You can add them to /etc/hosts if you wish.

Your first step is to establish the connection between the two computers with your crossover.

Please get your crossover up and running such that you can ping the client form the server and you can ping the server from the client.

Then tell us the IP address of the server and the client, the name of your share, and where on the client you want to mount it.

I suspect the problem is your crossover is not working.

In addition networking is complex. Since you have no router and you have not installed a DHCP server, as I mentioned above, you probably should add your boxes to /etc/hosts This is not necessary, but it helps.

---

### Post by Thocrun on 2009-09-27
I am pretty sure I have th ethernet working, I got the  crossover cable from my computer support teacher, but I have no idea how to set them up to ping each other. since my computer support teacher doesn't use debian I have no clue on any commands other then vi and cd. I just want to know which IP address do you want: lo one or the eth1 one?

---

### Post by Thocrun on 2009-09-27
oh, and how do I make it scrollable when I use ifconfig?

---

### Post by bodhi.zazen on 2009-09-27
For you r crossover cable see these links :

[http://www.ax697.org/sharing-internet-connection-with-a-crossover-cable-2008238.html](http://www.ax697.org/sharing-internet-connection-with-a-crossover-cable-2008238.html)

[http://ubuntuforums.org/showthread.php?t=1259667](http://ubuntuforums.org/showthread.php?t=1259667)

It is fairly straight forward (usually).

to see the output of a command pipe it to less

ifconfig | less

or pipe it to a text file

ifconfig > ifconfig.out

then nano or vi ifconfig.out

---

### Post by Thocrun on 2009-09-27
I get to mounting the client again and I get this: mount.nfs: mount to NFS server '192.168.xxx.xxx:/ubuntu' failed: RPC Error: Program not registered

---

### Post by bodhi.zazen on 2009-09-27
Is your crossover connection working ?

can you ping the server from the client ?

---

### Post by Thocrun on 2009-09-27
I got it to ping now at 100% successful packets, I lose my internet connection every time I connect using it tho.

---

### Post by bodhi.zazen on 2009-09-27
You basically have two problems / issues. One is your crossover cable and the other is NFS.

It is difficult to know the source of the problem.

If your crossover is not working, fix that first.

Next, mount your NFS share on the server. If you can not mount the share on the server you will not be able to mount it on the client either.

Once that is working try connecting to the server via ssh.



I assume you have the nfs server kernel installed on the server, and port mapper on the client ?

Have you looked at /etc/hosts.allow ?

Firewall ?

you can see if this thread helps at all :

[http://ubuntuforums.org/showthread.php?t=78100](http://ubuntuforums.org/showthread.php?t=78100)

Other then that your posts are not specific enough as to what you have done exactly, step by step, what you have installed on the server or client, how your shares are configured, etc.

---

### Post by Thocrun on 2009-09-27
ok, I guess I checked one thing off on the list
1. My crossover works, I can ping
when I get to mounting on the server that doesn't seem to work at all though.
Is there a firewall that comes with the 32-bit ubuntu desktop/server edition by default-if not I do not have a firewall on either.

---

### Post by bodhi.zazen on 2009-09-27
Well if mounting on the server is not working, start there.

review or post your config files including /etc/hosts.allow and /etc/hosts.deny

You can check your firewall with 

```
sudo iptables -L -v
```

---

### Post by Thocrun on 2009-09-27
1. I installed the nfs-kernel-server on the server
2. I installed the nfs-common on the client
3. I configured the etc/exports file as such:
/ubuntu 192.168.xxx.xxx(rw,sync,no_root_squash)
4. I started the server :
**sudo /etc/init.d/nfs-kernel-server start**
5.I made directories /local/ubuntu on both pc's with mkdir
6.I edited the /etc/fstab file as such:
(IP of the other other pc):/ubuntu /local/ubuntu nfs rsize=8192,wsize=8192,timeo=14,intr

---

### Post by Thocrun on 2009-09-27
under chain forward there are no bytes but the rest have bytes I'm guessing my firewall is not on then? (I am using it on the client pc)

---

### Post by Thocrun on 2009-09-27
oh and I did do the manual thing under network connections.

---

### Post by Thocrun on 2009-09-27
the server has 0 bytes how do I change that?

---

### Post by bodhi.zazen on 2009-09-27
I can not tell from what your posted, or at least nothing obvious =)

[http://tldp.org/HOWTO/NFS-HOWTO/troubleshooting.html](http://tldp.org/HOWTO/NFS-HOWTO/troubleshooting.html)

---

### Post by guga31bb on 2009-09-28
> **Jose Catre-Vandis said:**
> There is something basic going wrong here :(

Can you / do you have connectivity between the two PCs, i.e. they are on the same subnet (e.g.192.168.1.0) and you can ping each PC for the other?

Test the nfs server on the server, by setting up a test mountpoint and mounting one of your nfs shares there. Use the IP address of the server to do this, so for example:

Say you have a share in your /etc/exports file called /home
```
sudo mkdir /media/testnfs
sudo mount 192.168.0.xxx:/home /media/testnfs
```

If this works then nfs is doing its job so we can now move to the client and keep testing

I'm also having NFS problems. I did this test, and that went fine (so NFS seems to be running fine). I can also mount directories on the client using the server using SSH, so I don't think I have any networking problems. However, when I try to mount using the client, I get "mount.nfs: mount system call failed". Why might this be happening?

---

### Post by Jose Catre-Vandis on 2009-09-28
> **Thocrun said:**
> 1. I installed the nfs-kernel-server on the server
2. I installed the nfs-common on the client
3. I configured the etc/exports file as such:
/ubuntu 192.168.xxx.xxx(rw,sync,no_root_squash)
4. I started the server :
**sudo /etc/init.d/nfs-kernel-server start**
5.I made directories /local/ubuntu on both pc's with mkdir
6.I edited the /etc/fstab file as such:
(IP of the other other pc):/ubuntu /local/ubuntu nfs rsize=8192,wsize=8192,timeo=14,intr

Did you install portmap, and did you also:
```
sudo exportfs -a  <<-- on the server
```

What IP addresses are you using for your client and server? The IP addresses in 3. and 6. above should be the same?

Does your user have permission to access/read/write the directory /local/ubuntu?

---

### Post by Thocrun on 2009-09-28
I'm thinking it's firewall by the troubleshooting page I get so far and get this:
Remote system error - No route to host

I have all rights as sudo (if I want to) on both pc's

the server address is 192.168.1.2 the IP DNS is 192.168.1.1
the client is 192.168.1.1
gateway on both is 255.255.255.0.

---

### Post by guga31bb on 2009-09-28
Anyone have any thoughts on my problem? (see above post)

---

### Post by Jose Catre-Vandis on 2009-09-29
> **guga31bb said:**
> Anyone have any thoughts on my problem? (see above post)

Some things to check (in no particular order!):

1. Run through the howto again
2. Ensure you have portmap installed on both client and server
3. Check portmap is running with "/etc/init.d/portmap status"
4. Ensure you have nfs-common installed on the client too
5. Check your user settings and permissions on both client and server. I usually opt for an easy "low security" setup, I have the same user with the same UID on boht client and server, and set everything in the share to read/write. If I want to tighten up I can work back from there.
6. Try "showmount -e IPofServer" on your client, to check you get the output of your nfs share. For example, my servers IP is 10.10.10.70 and all my exports are to 10.10.10.1/24.
7. Try this command "mount -t nfs IPofServer:/share /mnt/share/"
(replacing the IP and share info)
8. Try "sudo dpkg-reconfigure portmap" and choose "No"
9. Try "sudo mount -t nfs -o nolock IPofServer:/share /mnt/share/"

---

### Post by guga31bb on 2009-09-29
> **Jose Catre-Vandis said:**
> Some things to check (in no particular order!):

1. Run through the howto again
2. Ensure you have portmap installed on both client and server
3. Check portmap is running with "/etc/init.d/portmap status"
4. Ensure you have nfs-common installed on the client too
5. Check your user settings and permissions on both client and server. I usually opt for an easy "low security" setup, I have the same user with the same UID on boht client and server, and set everything in the share to read/write. If I want to tighten up I can work back from there.
6. Try "showmount -e IPofServer" on your client, to check you get the output of your nfs share. For example, my servers IP is 10.10.10.70 and all my exports are to 10.10.10.1/24.
7. Try this command "mount -t nfs IPofServer:/share /mnt/share/"
(replacing the IP and share info)
8. Try "sudo dpkg-reconfigure portmap" and choose "No"
9. Try "sudo mount -t nfs -o nolock IPofServer:/share /mnt/share/"

Thank you! Is the following output from the server a bad sign?
```
ben@ben-server:~$ /etc/init.d/portmap status
open: Permission denied
 * Usage: /etc/init.d/portmap {start|stop|force-reload|restart}

ben@ben-server:~$ sudo /etc/init.d/portmap status
[sudo] password for ben: 
 * Usage: /etc/init.d/portmap {start|stop|force-reload|restart}

```

Also, from the client:
```
ben@ben-vostro:~$ /etc/init.d/portmap status
 * portmap is running

ben@ben-vostro:~$ showmount -e 192.168.1.100
rpc mount export: RPC: Timed out
```

EDIT: more output--
```
ben@ben-vostro:~$ mount -t nfs 192.168.1.100:/home/ben /files
mount: only root can do that
ben@ben-vostro:~$ sudo mount -t nfs 192.168.1.100:/home/ben /files
[sudo] password for ben: 
mount.nfs: mount system call failed
```

My /etc/exports has ```
/home/ben 192.168.1.100(rw,no_root_squash,async) 192.168.1.101(rw,no_root_squash,async)
```
(where the server is [...].100 and client [...].101.

I reconfigured portmap and have the same login/UID on both machines. I'm really at a loss.

---

### Post by Jose Catre-Vandis on 2009-09-30
Well that first one doesn't match with what I get as i have a "portmap running" returned on both server and client.

Check  the installation of portmap on your server, and reinstall if necessary.

You can start it manually with:
```
sudo /etc/init.d/portmap start (or restart)
```

and again check status with:
```
/etc/init.d/portmap status
```

Hopefully this may be where the problem lies? Also try a reboot on the server to ensure that portmap is starting up OK.

---

### Post by bodhi.zazen on 2009-09-30
> **Jose Catre-Vandis said:**
> Well that first one doesn't match with what I get as i have a "portmap running" returned on both server and client.

Check  the installation of portmap on your server, and reinstall if necessary.

You can start it manually with:
```
sudo /etc/init.d/portmap start (or restart)
```and again check status with:
```
/etc/init.d/portmap status
```Hopefully this may be where the problem lies? Also try a reboot on the server to ensure that portmap is starting up OK.

Or for the lazy typer :

```
sudo service portmap restart
```

---

### Post by guga31bb on 2009-09-30
Okay, I reinstalled everything, restarted portmap and rebooted my server. I think I'm still in the same place. Here's some more output, from the client, giving info of server:

```

ben@ben-vostro:~$ rpcinfo -p 192.168.1.100
   program vers proto   port
    100000    2   tcp    111  portmapper
    100024    1   udp  32784  status
    100024    1   tcp  45296  status
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  53274  nlockmgr
    100021    3   udp  53274  nlockmgr
    100021    4   udp  53274  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  46908  nlockmgr
    100021    3   tcp  46908  nlockmgr
    100021    4   tcp  46908  nlockmgr
    100005    1   udp  38977  mountd
    100005    1   tcp  36151  mountd
    100005    2   udp  38977  mountd
    100005    2   tcp  36151  mountd
    100005    3   udp  38977  mountd
    100005    3   tcp  36151  mountd
```

Client:
```
ben@ben-vostro:~$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100024    1   udp  35099  status
    100024    1   tcp  54954  status
    100000    2   udp    111  portmapper
```

But I still get 
```
ben@ben-vostro:~$ showmount -e 192.168.1.100
rpc mount export: RPC: Timed out
```

Also, 
```
ben@ben-vostro:~$ tracepath 192.168.1.100
 1:  ben-vostro.local (192.168.1.101)                       0.269ms pmtu 1500
 1:  no reply
 2:  no reply
[...]
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500 
```

```
ben@ben-vostro:~$ ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=64 time=0.464 ms
[...]
64 bytes from 192.168.1.100: icmp_seq=5 ttl=64 time=0.339 ms
--- 192.168.1.100 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3996ms
rtt min/avg/max/mdev = 0.339/0.445/0.492/0.055 ms
```

Why would I be able to ping but not tracepath?

---

