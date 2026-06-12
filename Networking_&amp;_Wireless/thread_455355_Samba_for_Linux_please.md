---
title: "Samba for Linux please"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by thelocust on 2007-05-26
For the life of me I can not find a tutorial on how to connect two Linux computers together using samba. All I get is how to connect to a Windows machine. I have 2 computers both running Kubuntu (1 Feisty and 1 Dapper) and I want to be able to share files between them. I know nothing about networking at all so I'm looking for a very basic step by step How-to. And also if there an easier way than samba I'm all ears. Thanks.

---

### Post by ruy_lopez on 2007-05-26
To install SSH on both computers, either search for it using synaptic package manager, or enter this on the command-line:

```
sudo apt-get install ssh
```

Then, using the network tool in System --> Administration --> Network, set up static IP addresses on each computer using the properties section for the interface. Once you've done that, add hostname to IP mappings, using the Hosts tab in the Network tool.

Once that is done, you should be able to use the Connect to Server tool, in Places --> Connect to Server, by choosing SSH as the service type and entering the hostname of the other computer, and filling out the fields.

You can probably omit setting up static IP addresses if your router assigns dynamic IPs in a predictable way (ie. you get the same IP every time you connect). In such a case, instead of entering the hostname, you would just enter the IP address of the other computer.

If you need clarification on any of the steps, just ask. Without knowing how you are connected (through a router, wireless, wired etc.) I can't really be more specific.

---

### Post by thelocust on 2007-05-26
I have the 2 computers set up on a switch. So they both have the same IP address.
> 
Once that is done, you should be able to use the Connect to Server tool, in Places --> Connect to Server, by choosing SSH as the service type and entering the hostname of the other computer, and filling out the fields.I can't find this option in KDE?

---

### Post by ruy_lopez on 2007-05-26
Silly me, I keep forgetting there's an Ubuntu version with KDE. You can do the same on the command line, to log into the other box (once you have ssh installed and running):

```
ssh username@other_box
```

it will prompt for your password, then you should be logged in remotely.

to copy a file from one box to the other:

```
scp localfile username@other_box:/path/to/put/file
```

or, to download a file from the other box
```

scp username@other_box:/remote/file/to/get /local/place/to/put/it
```

I'm sure someone who knows Kubuntu can tell you how to do this sort of thing with the GUI?

Oh, and there's "sshfs" which you can use to mount a remote ssh folder (once you have ssh setup).

To use it, first test to see if you have the fuse module:

```
sudo modprobe fuse
```

And if no errors occur:

```
sudo apt-get install sshfs
```

Then to mount a remote drive, create an empty folder somewhere, say in your home folder, then:

```
sshfs user@other_box:/ empty_folder
```

That command will mount the other machine's entire filesystem into the empty folder. To unmount it (come out of the folder, first):

```
fusermount -u empty_folder
```

---

### Post by thelocust on 2007-05-26
Thanks for all the help ruy. I think it's working but I get this error.

```
bob@tuxbox:~$ sshfs bob@XX.XX.XX.XXX:/ /dapper
bob@XX.XX.XX.XXX's password:
fuse: failed to exec fusermount: Permission denied
```Any ideas?

---

### Post by ruy_lopez on 2007-05-26
What about logging in using
```

ssh bob@xxxxx
```

Does that work okay?

---

### Post by thelocust on 2007-05-26
I think so this is what I get

```
bob@tuxbox:~$ ssh bob@XX.XX.XX.XXX
bob@XX.XX.XX.XXX's password:
Linux tuxbox 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Sat May 26 12:19:32 2007 from tuxbox.local
bob@tuxbox:~$  
```

---

### Post by ruy_lopez on 2007-05-26
All that looks fine. Are you sure you are connecting to the other box (and not just connecting to yourself?). Did you install ssh on both machines, modprobe fuse on both machines, and install sshfs on both machines?

---

### Post by thelocust on 2007-05-26
Sorry for the confusion I was using the IP address because it would not connect when I used the host name (I think thats what it's called) so I've been connecting the same computer to it's self because they both have the same IP.

I original put ssh bob@MYBOX and got this
```

bob@tuxbox:~$ ssh bob@MYBOX
ssh: MYBOX: Name or service not known
```I probably doing it wrong. Where do I find he part you said was the "other_box"

> ssh username@other_boxI installed everything on both machines like you said.

---

### Post by psusi on 2007-05-26
Both computers can not have the same address.  I think what you mean is that you are using a router, not a switch, and the router presents a single public IP address to the Internet.  The computers themselves are assigned unique local addresses.

---

### Post by ruy_lopez on 2007-05-26
On both boxes run this command

```
ifconfig
```

look for the part that says "inet_addr XXX.XXX.XXX.XXX". ignore the one which says "127.0.0.1".

Make sure both boxes have unique IP addresses. Take note of them. Then edit this file on both boxes, and add the lines shown (supplying the IP addresses from above, and whatever hostnames you want to use):

/etc/hosts

```
XXX.XXX.XXX.XXX     hostname.for.box.a
XXX.XXX.XXX.XXX     hostname.for.box.b
```

Then when you login using SSH, you use the hostname for the box you want to connect to.

i.e.

```
ssh bob@hostname.for.box.you.want
```

Note: I'm asking you to try logging into the other machine for testing purposes. Once you've logged in, you should log out again, by typing "exit." Once that works, we'll try "sshfs" again. Since that is probably what you are wanting.

---

### Post by meng on 2007-05-26
If you want to use Samba, then you should be able to follow the same steps you would with Windows, but you would also have to specify on each computer which folders were to be shared.
If you want to use SSH instead, then you need to learn a few new tricks, but it is worth it for the security.

---

### Post by thelocust on 2007-05-26
I did the ifconfig and they both have the same address assigned by dhcp. I tried to change it but when I put it in manual and change the last number and apply, it just switches back to the old address but stays in manual. They are connected with a Linksys 5-port workgroup switch.

---

### Post by ruy_lopez on 2007-05-26
Before you can do any kind of networking you need unique IP addresses. I'm not familiar with your hardware switch. That's your homework. Find out how to get unique IP addresses. You might be able to assign them statically, using /etc/network/interfaces, but I'm wary of telling you to do that, in case you lose your internet connection.

Sorry, couldn't get you up and running. At least now you know what you need.

---

### Post by thelocust on 2007-05-26
I'll look in to it thanks for all the help.

---

### Post by psusi on 2007-05-26
You must be mistaken.  DHCP assigns each computer a unique address.  Linksys should allocate one an address of 192.168.1.1 and another 192.168.1.2.  They will have the same default gateway, which will be the address of the linksys router, which should be 192.168.1.100 IIRC.  

If they both have the same address then either one is not using DHCP or the linksys is broken.

---

### Post by dolphin_oracle on 2007-05-26
is the switch connected to a router as well as the two computers?

also, does the ip address assigned look like 192.xxx.xxx.xxx ?

Do you happen to have a static ip address from your internet service provider?

---

### Post by thelocust on 2007-05-26
My switch is connected to my DSL box in the uplink port and then each computer is connected. My IP address is set by the dchp and is 75.XX.XX.XXX

---

### Post by dolphin_oracle on 2007-05-26
Does your ISP allow for more than one IP address to be assigned to you?  Your ISP's system is assigning your IP addresses.  My suggestion is to get a Router and plug your DSL modem into that.  The router will take over LOCAL dhcp duties to your network and your ISP will only need to assign one EXTERNAL ip address for internet access.  My guess is that which ever computer you are using is getting the IP addresses your ISP is assigning you.

In effect, you are sharing an external address, and you have no internal network.

You could also setup your server to do local dhcp duties and act as a gateway.  It will involve two network cards in the server box, and I don't know how to set it up, but it can be done.

---

### Post by thelocust on 2007-05-27
Yea thanks for all the help I'll go out and get a router tomorrow.

---

### Post by psusi on 2007-05-28
Hrm... sounds like your isp is broken then... they should only give the address to one computer... when you bring the second one up it should fail to get an address.  You will need a router to grab that address and then assign internal addresses to each computer on the network.

---

