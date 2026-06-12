---
title: "connect computers at home"
date: 2016-06-01
forum: Networking &amp; Wireless
---

### Post by pedro_rodriguez2 on 2016-06-01
Actually what  I want is to connect 4 laptops at home. I'm starting with 2, then want to add more.

I started with 2, plugged an ethernet cable in to connect both, followed some instructions here and other places.

[http://askubuntu.com/questions/245406/how-to-make-a-home-server-using-ubuntu-desktop](http://askubuntu.com/questions/245406/how-to-make-a-home-server-using-ubuntu-desktop)

I can now successfully browse my new laptop from my old laptop, which is great progress for me! 

The other way around does not work. In the nautilus window I clicked connect to server. I entered ssh://pedro-bedro2 but I only get this computer, pedro-schule
On the old computer, I can browse pedro-schule. I do not understand why I cannot get to the old computer. Must it be a server too?

Do I have to set the old laptop to be a server too? The address of the old laptop is pedro-bedro 10.42.0.96,  and the new one is pedro-schule 10.42.0.1 I have set these values in /etc/hosts

I checked with ifconfig that the values were correct

I can ping both ways, but I can't browse the old laptop from the new laptop. 

pedro@pedro-schule:~$ ping -c 5 10.42.0.96
PING 10.42.0.96 (10.42.0.96) 56(84) bytes of data.
64 bytes from 10.42.0.96: icmp_seq=1 ttl=64 time=0.408 ms
64 bytes from 10.42.0.96: icmp_seq=2 ttl=64 time=0.294 ms
64 bytes from 10.42.0.96: icmp_seq=3 ttl=64 time=0.589 ms
64 bytes from 10.42.0.96: icmp_seq=4 ttl=64 time=0.323 ms
64 bytes from 10.42.0.96: icmp_seq=5 ttl=64 time=0.386 ms

--- 10.42.0.96 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3997ms
rtt min/avg/max/mdev = 0.294/0.400/0.589/0.103 ms
pedro@pedro-schule:~$

What else do I need to be able to browse both ways??

---

### Post by Dennis N on 2016-06-01
SSH: If they all use Ubuntu family OSes, then each needs openssh-server installed. Then assuming they are on your LAN, you can connect from Computer A to any or all of the others - all at the same time if you want. I like to use GUI connection manager gigolo to make connections.

---

### Post by pedro_rodriguez2 on 2016-06-02
All the laptops run Ubu 14.04 at the moment, my old laptop, my new laptop and the girlfriend's old and new laptops.

So in fact, each computer has to be a client and a server, is that right? 

At the moment, the ips are not fixed. What's the best way to assign fixed ips to each laptop on my little homenet, so I do not have to check each time I want to connect to computer A, B, C or D??

---

### Post by Morbius1 on 2016-06-02
You may not need to have fixed ip addresses. 

All of your machines can access each other using mDNS which is your host name with a ".local' attached at the end. So for example pedro-schule becomes pedro-schule.local

In fact if you use either SSH or Samba you can make it so it shows up under Browse Network if you are interested.

For SSH do this on all your Linux machines:

** Create a file:
```
gksu gedit /etc/avahi/services/ssh.service
```
** Then add this to it:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SSH</name>
   <service>
       <type>_sftp-ssh._tcp</type>
       <port>22</port>
   </service>
</service-group>

```
When you go to Browse Network you should see the hosts show up as something like "pedro-schule SSH"

You can do the same thing with Samba:
```
gksu gedit /etc/avahi/services/samba.service
```
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SMB</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```
All the hosts will show up as something like "pedro-schule SMB"

The only requirement is that avahi is running on all systems - and it should be by default:
```
sudo service avahi-daemon start
```
And you haven&#8217;t blocked it's port - 5353

[COLOR=#0000cd]**Note**[/COLOR]: The content of the *.service file is kind of picky. The first line of the file ( starting with <?xml version ... ) cannot have any leading spaces in front of it.

*I should also note that the avahi service announcement will be visible to Linux and OSX clients but not by Windows. Windows 10 can access and be accessed ( with a firewall rule update ) with a hostname.local but it cannot "browse"  or "discover" these avahi announcements.*

---

### Post by pedro_rodriguez2 on 2016-06-02
Thank you very much! I will try that on the weekend.

I am using ssh (I think, I really don't know anything about this) 

Samba is something that can access Windows? I try to avoid Windows, it is awful and here in China at least cannot be controlled. Programs install themselves, ads pop up everywhere!Not that I try with Win, I have been using Linux since Red Hat 9 I believe. 

I just think, this networking can't be so difficult, I just need to know the ropes. I have often thought, "how come I can get on the net and connect to computers all over the world, but the computer in the next room is inaccessible"

I'd like to not have to think that.

---

### Post by Morbius1 on 2016-06-02
> Samba is something that can access Windows? I try to avoid Windows,
Samba is a file sharing mechanism. Although it was originally created so Windows clients could access UNIX servers it's become ubiquitous as it runs on just about anything.

In fact Apple replaced it own file sharing mechanism ( afp ) with it's own brand of SMB ( compatible with samba ) a few years ago:
> When you connect from a Mac using OS X Mavericks or OS X Yosemite to  another computer using file sharing, your Mac automatically tries to use  the Service Message Block (SMB) protocol to communicate. If SMB is not  available, OS X tries to connect using Apple File Protocol (AFP).

Besides the way I'm suggesting using it pretty much removes most of the Windows specific stuff since we aren’t using netbios but mDNS to resolve host names on the network.

I'm not trying to convince you to use samba. There’s nothing wrong with ssh. I just wish people would stop saying that Samba is a Windows thing.

---

