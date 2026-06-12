---
title: "KVM Bridging"
date: 2021-11-19
forum: Networking &amp; Wireless
---

### Post by Quarkrad on 2021-11-19
Getting myself into a state of confusion re trying to get kvm bridge working with my host - too many similar, but different, web/youtube pages explaining the same thing - doesn't help when latest version of virt manager is different to those on web pages.  I think I have set up a bridge connection on a ubuntu mate 20.04 kvm (but not sure!).  On the kvm machine the output of ip ad is:

```
dad@dadubuntu:~$ ip ad
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master bridge0 state UP group default qlen 1000
    link/ether 52:54:00:49:a6:1c brd ff:ff:ff:ff:ff:ff
3: bridge0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 52:54:00:49:a6:1c brd ff:ff:ff:ff:ff:ff
    inet 192.168.100.214/24 brd 192.168.100.255 scope global dynamic noprefixroute bridge0
       valid_lft 3345sec preferred_lft 3345sec
    inet6 fe80::53cf:8762:934d:4e4b/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```

So ... my understanding is the ip of this kvm machine is 192.168.100.214

On my host (using the Network Connections gui) I have a eth interface and a virbr0 bridge interface (I believe virbr0 is put there as a default when installing kvm/libvirt/etc - can I delete this Bridge virbr0 interface?)  The ip address of the eth interface is 192.168.1.150 (this is a static address).

I think I may have finally set is up correctly as I can ping 192.168.1.150 successfully from my KVM machine and also ping 192.168.100.214 successfully from my host machine.  Is this proof?

My main confusion is the bridge.  On the kvm machine under Network Connections I have under Ethernet -  bridge0 slave 1  and under Bridge - Bridge Connection 1.  This sort of makes sense to me as the kmv is bridging to my physical Ethernet on the host.  But as said - on the host I have Ethernet - eth and Bridge - virbr0.  If I can delete virbr0 on my host I think I do have little/some understanding.

---

### Post by Doug S on 2021-11-19
If I understand correctly, you have things messed up a little.

You do not need a bridge on your VM, you need it on the host. You also want your VM to be on the same sub-net as the host, namely on 192.168.1.0/24 (I have assumed the 24 bit sub-net mask).

Yes, you can get rid of virbr0, but there is a particular way to do so.

[Here]("https://ubuntuforums.org/showthread.php?t=2461631&p=14036896#post14036896") are some notes I made when I did this on my test 20.04.3 Ubuntu server.

And I have:

Host:

```
doug@s19:~/config/etc/libvirt/qemu/networks$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP group default qlen 1000
    link/ether 3c:7c:3f:0d:99:83 brd ff:ff:ff:ff:ff:ff
3: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 3c:7c:3f:0d:99:83 brd ff:ff:ff:ff:ff:ff
    inet 192.168.111.136/24 brd 192.168.111.255 scope global dynamic br0
       valid_lft 78322sec preferred_lft 78322sec
5: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:60:ea:5e brd ff:ff:ff:ff:ff:ff
```
and
```
doug@s19:~/config/etc/libvirt/qemu/networks$ brctl show br0
bridge name     bridge id               STP enabled     interfaces
br0             8000.3c7c3f0d9983       no              enp3s0
                                                        vnet0
```
and```
doug@s19:~/config/etc/libvirt/qemu/networks$ virsh list --all
 Id   Name      State
--------------------------
 2    desk-ii   running
 -    desk-ff   shut off
 -    desk-hh   shut off
 -    serv-xx   shut off
``` and ```
doug@s19:~/config/etc/libvirt/qemu/networks$ virsh net-list --all
 Name          State    Autostart   Persistent
------------------------------------------------
 host-bridge   active   yes         yes
``` and ```
doug@s19:~/config/etc/libvirt/qemu/networks$ sudo cat /etc/libvirt/qemu/networks/host-bridge.xml
<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh net-edit host-bridge
or other application using the libvirt API.
-->

<network>
  <name>host-bridge</name>
  <uuid>d474d859-8448-4055-9fc0-bb0b6cb83c34</uuid>
  <forward mode='bridge'/>
  <bridge name='br0'/>
</network>
```

---

### Post by Quarkrad on 2021-11-20
Thank you - seems I am still way-off and confused.

```
dad@dadubuntu:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 2c:f0:5d:92:6d:9e brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.150/24 brd 192.168.1.255 scope global noprefixroute eno1
       valid_lft forever preferred_lft forever
    inet6 2a00:23c8:4185:2c00:287c:53d5:e229:9290/64 scope global dynamic noprefixroute 
       valid_lft 315359954sec preferred_lft 315359954sec
    inet6 fdaa:bbcc:ddee:0:1ccd:2fa:889b:e48f/64 scope global noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::4d90:c3de:344b:9959/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:55:17:b1 brd ff:ff:ff:ff:ff:ff
    inet 192.168.100.1/24 brd 192.168.100.255 scope global virbr0
       valid_lft forever preferred_lft forever
4: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr0 state DOWN group default qlen 1000
    link/ether 52:54:00:55:17:b1 brd ff:ff:ff:ff:ff:ff

```

```
dad@dadubuntu:~$ brctl show br0
bridge br0 does not exist!

```

```
dad@dadubuntu:~$ virsh list --all
 Id   Name                     State
-----------------------------------------
 -    haskinsmarine            shut off
 -    ubuntu20.04              shut off
 -    ubuntu20.04 base-clone   shut off
 -    ubuntu20.04-2            shut off
 -    win10                    shut off
 -    win10-2                  shut off

```

```
dad@dadubuntu:~$ sudo cat /etc/libvirt/qemu/networks/host-bridge.xml
[sudo] password for dad: 
cat: /etc/libvirt/qemu/networks/host-bridge.xml: No such file or directory
```

This confirms my worst fears - having spent hours on this. At least my host is still working!   My problem now is where do I go from here and what do I do?  I seem to be on a merry go round reading the same pages and watching the same video over and over again and still not getting it right.

---

### Post by Doug S on 2021-11-20
Please refer to the notes I made before, the process is detailed therein. [Link.]("https://ubuntuforums.org/showthread.php?t=2461631&p=14036896#post14036896")
Yes you don't yet have the /etc/libvirt/qemu/networks/host-bridge.xml file because either you didn't make it yet or you named it something else when you did.

---

### Post by Quarkrad on 2021-11-20
Followed your link and lost everything - no network connectivity at all.  Reluctant to re-build and forget bridging kvm (too difficult?) but having spent more than two days on this and never getting it to work perhaps it's time to admit it is beyond my capability.  At the moment, dangerously following pages I don't fully understand I have connectivity back but I'm sure I'm all messed up.  At the moment I'm looking like the attached.

---

### Post by Doug S on 2021-11-20
Well, you are not supplying us much information as to what you have done and what results you get at each step, so it is somewhat difficult to try to help.

What do you get for this:

```
doug@s19:~/config/etc/libvirt/qemu/networks$ [COLOR="#FF0000"]virsh net-list --all[/COLOR]
 Name          State    Autostart   Persistent
------------------------------------------------
 host-bridge   active   yes         yes
```

You seem to have odd stuff such as: netplan-eno1, eth, bridge-br0. Whereas I expected eno1, based on one of your previous posts. You still have virbr0 and still seem to be using it. Suggest you destroy and undefine the default stuff (keep a copy first) and modify your VM's to use bridging instead of NAT, as I thought that is what you were wanting to do.

---

### Post by Quarkrad on 2021-11-21
Doug - thank you for your help/support.  I really am too far in the dark with this and need too much 'hand-holding'.  Despite knowing that following script/config changes, without really understanding the consequences from web pages is dangerous, this is what I did(!) - hence the mess I got into.  So ... I copied a backed up copy of /etc/ to my host and got back to a base line. However, to my surprise, everything I wanted seemed to work - I could ping host/vm from each other and am now finishing off setting up shh coms (although my host and the vm are on different sub-nets).  I attached a picture of my network connections and to my understanding it doesn't make sense as there is no bridge (e.g. br0) that is binded to my eno1 ethernet.  I have decided to leave everything as it is and to 'play' with a laptop set up on this whole bridge/vm working to get a better understanding so I do not waste your time trying to help me.  I may well come back in the months to come but at least I will, hopefully, have a deeper understanding and hopefully be more specific about where I've gone wrong.  Thank you.

---

### Post by TheFu on 2021-11-21
brctl has been deprecated in 20.04, right? networkctl is the new way.
Next, the host NIC eth-whatever, shouldn't have an IP.  The bridge will provide the IP for the host.
Next, the host NIC should have a static IP. No DHCP.  Static.
Next, forget/ignore the libvirt settings. Those create NAT junk. You don't want that.  You want a manually created, static bridge for the host.

In 20.04, we use netplan files.
```
# #################################
#   [ for bridge + static - KVM ]
network:
 version: 2
  renderer: networkd
  ethernets:
     [COLOR="#FF0000"]eth0[/COLOR]:
       dhcp4: false
       dhcp6: false
  bridges:
      br0:
        interfaces: [[COLOR="#FF0000"]eth0[/COLOR]]
        dhcp4: false
        dhcp6: false
        addresses: [192.168.[COLOR="#008000"]55[/COLOR].15/24]
        gateway4: 192.168.[COLOR="#008000"]55[/COLOR].1
        nameservers:
           addresses: [192.168.[COLOR="#008000"]55[/COLOR].1]
```
Change the IP and subnet and gateway and "interface" (eth0) to match the interface you have.  Then:
```
sudo netplan generate
sudo netplan apply --debug
```

That should do it for the host setup.
For each VM setting, change the network to point at br0.  I like to make the pseudo-fake MAC for each guest machine have the last 2 characters map to the last 2 IPv4 numbers.
ens3 is the normal virtio NIC provided.
52:54:00:1d:4c:[COLOR="#8B4513"]43[/COLOR] --> 172.22.22.[COLOR="#8B4513"]43[/COLOR]
Makes an easy way to know the other if you have 1 of those - say you're looking at ARP tables ... now you know the IP too.  Of course, it makes setting up DHCP reservations easier too and easy to validate when looking at that table.  I prefer to use DHCP reservations only for devices that are difficult to make static so phones, tablets, tv-tuners, streaming devices and the occasional raspberry-pi.  I consider my network "well managed", since every device gets an IP that is set and in DNS.  Guest devices are put on the internet wifi subnet in a specific range that prevents access to the other LANs ... unless it is a public service for the entire world.

Forget setting this up using any GUI.

---

### Post by Doug S on 2021-11-21
> **TheFu said:**
>  Next, the host NIC should have a static IP. No DHCP.  Static. Disagree. DHCP works fine. But yes, static preferred.

> **TheFu said:**
> Forget setting this up using any GUI.Agree.

---

### Post by TheFu on 2021-11-21
> **Doug S said:**
> Disagree. DHCP works fine. But yes, static preferred.

Just trying to keep it simple.  I've attempted to teach university CS students how to do this using DHCP and only 20% "got it."  Too many moving parts when things aren't working.  

Add in the VPN stuff (which shouldn't matter) and it is easy to compound the confusion.  I use a VPN (ovpn) from time to time with one of my KVM hosts.  It doesn't allow WAN inbound connections - just outbound.

---

### Post by Quarkrad on 2021-11-21
@TheFu     Thank you for your help - I followed your instructions (apart from the pseudo mac addresses) and all went well - although I had some fun with  yaml indentation after my changes!   The GUI Network Connections is not showing anything different (just a single eth connection) but I'm assuming this is OK; a consequence of using netplan(?).  The ip of my host is 192.168.1.150 and the output of ifconfig on my vm is:

```
dad@dadubuntu:~$ ifconfig
bridge0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.181  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2a00:23c8:4185:2c00:32fc:e925:e1b:1e5  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::7099:1e16:b5b:63dd  prefixlen 64  scopeid 0x20<link>
        inet6 fdaa:bbcc:ddee:0:5e96:202:e5d8:2b2  prefixlen 64  scopeid 0x0<global>
        ether 52:54:00:d6:b2:86  txqueuelen 1000  (Ethernet)
        RX packets 21577  bytes 18761835 (18.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16546  bytes 3202728 (3.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 52:54:00:d6:b2:86  txqueuelen 1000  (Ethernet)
        RX packets 21661  bytes 19074309 (19.0 MB)
        RX errors 0  dropped 3  overruns 0  frame 0
        TX packets 17530  bytes 3253894 (3.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3922  bytes 383256 (383.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3922  bytes 383256 (383.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

This is starting to make sense - I configured the vm Network Source to be: Bridge br0:Host device eno1 and indeed from the output above my vm ip address is 192.168.1.181 (the same range as my host).  I can ping each way between host and vm using those addresses but I'm having trouble setting up basic ssh.  Not sure at this point whether to set up another thread or stay here as it might be related to this bridging issue. 

I intend to use ssh keys to establish the connection but before I get to that stage I'm hitting a block at the very first connection:

```
dad@dadubuntu:~$ ssh dadubuntu@192.168.1.181
The authenticity of host '192.168.1.181 (192.168.1.181)' can't be established.
ECDSA key fingerprint is SHA256:8k8NfoNHiU32EiJj+330QG7YRyG82UIvmANg1PatjpI.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '192.168.1.181' (ECDSA) to the list of known hosts.
dadubuntu@192.168.1.181's password: 
Permission denied, please try again.
dadubuntu@192.168.1.181's password: 

```

I have turned firewalls off and the default port 22 is being used.   As said, I intend to change the port being used and use ssh keys but I first need to get over this first step.

---

### Post by Quarkrad on 2021-11-21
I might be confusing a little as I'm using dad@dadubuntu on both machines.  I read this afternoon on a server forum that you need/it helps if the user/host name is the same on both machines - although I don't think is actually true.  But I did it in case it helped with my permission error.

---

### Post by Doug S on 2021-11-21
This:
```
dad@dadubuntu:~$ ssh dadubuntu@192.168.1.181
```
Should be this (I think):
```
dad@dadubuntu:~$ ssh dad@192.168.1.181
```

---

### Post by Quarkrad on 2021-11-22
Doh .... thank you.  Setting up ssh now

---

### Post by TheFu on 2021-11-22
> **Quarkrad said:**
> I might be confusing a little as I'm using dad@dadubuntu on both machines.  I read this afternoon on a server forum that you need/it helps if the user/host name is the same on both machines - although I don't think is actually true.  But I did it in case it helped with my permission error.

What?  No. That is incorrect. Not any help.

The username can be the same, but doesn't need to be.
The hostnames cannot be the same between the 2 systems.

ssh logins look like email addresses  {username}@{servername} - the servername can be the IP, if you don't have name resolution setup.

I've posted how to setup ssh here probably 50 times - with keys.  I also have an ssh troubleshooting link posted here lots of places.  Setting up ssh after installing the "ssh fail2ban" packages is 2 steps the first time, then 1 step from the client (already did the keygen) to any other ssh servers using ssh-copy-id.  If you search these forums for that command, be it will be clear.

If you really want to make this stuff easier, after you get the basics down ... use the ~/.ssh/config file to setup host-aliases.  Then you won't need to remember different userids or any IP addresses or a non-standard port or any other specialized connection settings.  Every libssh based tool honors ssh-keys and the config file, so when you want to use rsync or sftp or scp or remote vim over rsync or x2go or .... the other 50 tools. This is valid for every Unix-like OS as a client.  Only MS-Windows doesn't have ssh-copy-id for some reason.  MSFT just wants to make things hard, I suppose.

Why install fail2ban?  Because, it blocks brute force attacks for nearly zero overhead. The defaults only address ssh on port 22/tcp, which is likely what we want in a LAN.

---

