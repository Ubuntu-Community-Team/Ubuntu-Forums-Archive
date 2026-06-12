---
title: "[SOLVED] Network 2 ubuntu boxes using a crossover cable?"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by badguyanil on 2007-09-28
Guy I have no idea of networking. I read somewhere that it is possible to network 2 ubuntu (1 ubuntu and the other kubuntu) using a crossover cable. Can anyone provide me a tutorial or a step by step guide of doign the same. I also get from the threads that i need to install something called  "samba"! Can anyone just eloborate. I just need to be able to transfer files between the systems.
This is a bit urget and i have posted a similar post in the Absolute beginers section too! but not much help there.

Just to emphasise... i have no idea of networking so do explain things for me.... 

thanx in advance!

---

### Post by helgman on 2007-09-28
I'll try to explain it to you.

1. Connect the two computers using the crossover cable (an ordinary network cable might work, depending on the age of the network cards (NIC) etc but if you already have a crossover cable, use it).

2. For the computer to be able to communicate they'll need IP addresses. How IP works is a far to big subject to explain here but addresses are printed in the form of x.x.x.x where every x is a number between 0 and 255. These addresses are arranged in subnets and when you are trying to set up two computers the way you do it is essential that they are on the same subnet, else you will need a router between them. So let's set up the IP addresses ...

Just to make sure we know what we are talking about let's call one of the machines UBUNTU and the other one KUBUNTU and we'll assume that the NIC is eth0 on both.

3. Since I don't know how the GUI looks in Kubuntu we'll have to do this from the command line. On UBUNTU, open a terminal and give it the following command:```
sudo ifconfig eth0 192.168.0.1[/sudo] and then make sure that your command had the expected effect by typing the command:[code]ifconfig eth0
```That should give you output looking something like this```
eth0      Link encap:Ethernet  HWaddr 12:03:B0:84:B8:AF  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe81:b8c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:356395 errors:0 dropped:0 overruns:0 frame:0
          TX packets:272218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:263812022 (251.5 MiB)  TX bytes:28109990 (26.8 MiB)
          Interrupt:22 
```

4. On KUBUNTU open the terminal and hit it with the command:```
sudo ifconfig eth0 192.168.0.2
``` and the repeat make sure that you've got an IP address with ```
ifconfig eth0
``` and look for inet addr: 192.168.0.2.

Short explanation: **ifconfig** is used to configure NIC, plain and simple. We tell UBUNTU to use 192.168.0.1 as its address and KUBUNTU to use 192.168.0.2. I spoke earlier on subnets and every IP address has a default subnet, that is, if nothing else is said it uses as default. In this case 192.168.0 is the network portion of the address and the last digit is the host specific part. Since that works fine for use we don't have to bother with using subnetmasks in the ifconfig command (type man ifconfig for more information).

5. Now make sure that the two machines can communicate. In the terminal of UBUNTU type:```
ping 192.168.0.2
```If you get a response looking like this:```
PING 192.168.0.2 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.2: icmp_seq=1 ttl=255 time=0.531 ms
64 bytes from 192.168.0.2: icmp_seq=2 ttl=255 time=0.462 ms
64 bytes from 192.168.0.2: icmp_seq=3 ttl=255 time=0.455 ms
``` Then can communicate. If it looks something like this:```
PING 192.168.0.2 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.2 icmp_seq=1 Destination Host Unreachable
From 192.168.0.2 icmp_seq=2 Destination Host Unreachable
From 192.168.0.2 icmp_seq=3 Destination Host Unreachable
``` then something is not setup right. Go over the first steps one more time, make sure that the cable is connected, that the addresses are configured etc and then try again.

To make it stop (the ping) just press Ctrl+C or it will go on forever.

Now here is the tricky part. I'm no master when it comes to SAMBA but I'll try to make an install on my machine to see if I can make a guide for you. If not I suggest you search the forum since I'm sure there is a lot of information about SAMBA around here already.

Regards,
Helgman

---

### Post by helgman on 2007-09-28
And now to the SAMBA part.

The installation instructions etc are for the UBUNTU machines since I can verify that it work in Ubuntu (don't know the exact menus in Kubuntu).

1. Navigate to **System -> Shared Folders** and when asked *Install Windows networks support (SMB)*. NFS is also a way to share folders but since it's SAMBA you want it's SAMBA you will get ... hopefully! ;)

It will now install SAMBA for you.

2. When the next menu opens up press "+ Add". In **Path** you navigate to the folder you want to share. I made a new one in my home folder called "share" by picking "Other ..." and then "Create Folder". The name of the folder is the name that will how up in the window of the connecting machine, I picked "share", plain and simple. Remove the mark in "Read only" if you want to allow computer that access the share from the network the right to place new files in the share or modify files already in it. Then hit "OK" (or what ever the button is named) and your share is ready for use ... almost.

3. To be able to access the share the one trying to use it need a password. Simplest way to do it (if it's only you that will use the share) is to use the same account as you use now, so that's what we'll do here. Open the terminal and write ```
sudo smbpasswd *username*
``` where *username* is the name of the user account that you are using. Then set the password. There is no need to use the same password that is used for the machine so you can pick any password you'd like. When that is done the user is set up and we can move over to KUBUNTU.

4. On KUBUNTU, open the file browers and type smb://192.168.0.1 in the address field. You'll be asked for credentials so you just type in the username from above and the password. You're in!

I hope you can take if from here ... but don't be afraid to ask.

Have a nice weekend,
Helgman

---

### Post by badguyanil on 2007-10-02
great walkthru!!!! reached the ubuntubox thru KBUNTU!! But facing problems in copying stuff.

as told above after typing smb://192.168.0.1 on my KUBUNTU box it takes me to the share folder. But does not ask for any password.  Also while creating any folder gives an error. Please help! have done eczactly as given above....

guys any help would be appreciated....just waiting for this to be complete!

---

### Post by badguyanil on 2007-10-02
guys any help for the above problem. Still not able to proceed....

> 4. On KUBUNTU, open the file browers and type smb://192.168.0.1 in the address field. You'll be asked for credentials so you just type in the username from above and the password. You're in!


it does not ask for any username or password. And when i try and create a file in the shared folder thru the KUBUNTU box throws me an error about permissions. What do i do!

---

### Post by helgman on 2007-10-02
I have no idea. Are you sure the folder is not set to read only?

I'll try to investigate this some and I'll let you know if I find anything - but I can't recreate the exact situation since I don't have to linux machines with GUI.

I'll let you know if I figure something out.

Regards,
Helgman

---

### Post by badguyanil on 2007-10-02
Hmm u r right the problem was with permissions. Actually KUBUNTU wasn't showing the exact error message. I tried the same given above using a live CD of ubuntu on the KUBUNTU laptop and it clearly said the user does not have permissions to access the files. Setting the permissions right on the shared folder does the trick! It was very good to c a 2.7gb file being transfered without a usb. Although it took quiet a bit of time for the transfer but i am happy it is working! Thanks a ton for you help! 

Cant wait for ubuntu 7.10 now!!!

---

### Post by sgtbob on 2007-11-16
OK - I finally got the 'ifconfig' set in both PC1 and PC2, so that when I 'ping' PC2 _from_ PC1, I got data similar to the following:


Code: PING 192.168.0.2 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.2: icmp_seq=1 ttl=255 time=0.531 ms
64 bytes from 192.168.0.2: icmp_seq=2 ttl=255 time=0.462 ms
64 bytes from 192.168.0.2: icmp_seq=3 ttl=255 time=0.455 ms

I also was able to ping PC1 from PC2 and got similar data, so I think I must (may be?) connected.(?????)

Now the $64 question is what do I do to view/see/access the files on PC2 if I'm on PC1 and vice-versa?:)

I've really enjoyed the feature in Ubuntu that permits me to see my Windows files in Ubuntu on the same PC - now what I would like to do is to use file on PC1 that are on PC2....

Bob

---

### Post by sgtbob on 2007-11-27
Anyone?](*,)

---

