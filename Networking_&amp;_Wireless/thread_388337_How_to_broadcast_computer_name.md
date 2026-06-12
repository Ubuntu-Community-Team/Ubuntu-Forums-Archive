---
title: "How to broadcast computer name"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by joehill on 2007-03-19
When I used Mandrake, each computer on my network automatically broadcast its name, so I could connect to it with something like "ssh notebook".  After switching to Ubuntu, I have to connect using the IP address ("ssh 192.168.0.24").  I can name the computer using my router's firmware, but after a few minutes the computer seems to reset the name back to the IP address.  Is there a way to get Ubuntu to broadcast the computer's name

Thanks!

Joe

---

### Post by dbott67 on 2007-03-19
There are a couple of ways to accomplish this.  

**1. Using static IP addresses** and a manually maintained **hosts** file (for DNS-style name resolution) or **lmhosts** file (for Windows-like SMB name resolution).  Easy to setup, but can be a pain to manage if you have lots of computers or are using DHCP. This is probably not the way it was done in Mandrake *[COLOR=Blue](see the bottom of the post for details in setting up this way)[/COLOR]*.

**2. Install DNS (bind9 from the repos):** DNS requires a DNS server running on your network that will register each computer as it obtains an IP address.  Can be difficult to setup and configure for inexperienced users and again, is probably not the way Mandrake did it.

**3. Install Samba and winbind:**  Samba is a service that makes your computer behave like a Windows server.  It uses the SMB/CIFS protocol to announce computer names & shares (which is probably what you want). SMB requires a WINS server (which is called winbind in linux) to automatically register the "announced" computer names.  **This is probably the way Mandrake does it.**

_**Using Samba & winbind:**_

You need to install the following packages from the repos on one main computer:

```
 sudo apt-get install smbfs smbclient winbind
```On any other linux computers, just install smbfs and smbclient:

```
 sudo apt-get install smbfs smbclient
```[U][B]BACKGROUND AND SETUP INSTRUCTIONS

[/B][/U] (This is from another thread that I posted in regarding local name resolution. The full thread is for here: [http://www.ubuntuforums.org/showthread.php?p=1770797#post1770797](http://www.ubuntuforums.org/showthread.php?p=1770797#post1770797))

... some issues arise because of the way SMB shares "announce" themselves to the network. Generally, connecting via IP address works properly, but browsing by 'computer name' can occasionally fail. Windows uses WINS service to allow users to browse by computer name (also known in Windows-speak as Netbios name). WINS binds the computer name to the IP address. For the most part, this has been superceded by DNS, which binds the fully-qualified domain name to the IP address. The problem is that DNS resolution requires that:

a) You're running a DNS server (locally)
b) Each client is registered in the DNS server

The problem here is that most people don't run their own DNS server at home and if you have any Windows computers on the network (or Samba shares), you really should have a WINS server or 'winbind' installed.

There is a package in the repositories called 'winbind' that will allow you to browse by computer name.

This info is provided by 'featherking' from [this thread]("http://www.ubuntuforums.org/showthread.php?t=288022"): 

```
sudo gedit /etc/nsswitch.conf
```find this line (it may not be exactly that)

```
hosts:          files dns mdns
```and add **wins**, so now it looks like

```
hosts:          files dns mdns **wins**
```then install winbind
```

sudo apt-get install winbind
```The advantage to using winbind vs. static IPs is that I can add/remove PCs without worrying about editing the hosts file. There are also a few tools that can aid in discovery, such as **smbtree**:
```
dbott@thedrake:~$ sudo smbtree
Password:
WORKGROUP
        \\THEDRAKE                      thedrake server (Samba, Ubuntu) *[COLOR=Blue]<--- My Dapper desktop[/COLOR]*
                \\THEDRAKE\ADMIN$               IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\IPC$                 IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\dbott
                \\THEDRAKE\print$               Printer Drivers
        \\PIII-600 [COLOR=Blue]*<--- the kids XP PC; no firewall; no shares*[/COLOR]
        \\OMEGA-XP [COLOR=Blue]*<--- My laptop; Running XP firewall*[/COLOR]
Error connecting to 192.168.1.105 (No route to host)
cli_start_connection: failed to connect to OMEGA-XP<20> (192.168.1.105)
        \\NAS-160GB [COLOR=Blue]*<--- My NAS device*[/COLOR]
                \\NAS-160GB\IPC$
                \\NAS-160GB\Videos
                \\NAS-160GB\Music
                \\NAS-160GB\Archive
                \\NAS-160GB\Data
                \\NAS-160GB\PUBLIC
        \\JBOTT-PC [COLOR=Blue]*<--- My wife's laptop; Running Vista firewall; no open shares*[/COLOR]
timeout connecting to 192.168.1.101:445
timeout connecting to 192.168.1.101:139
Error connecting to 192.168.1.101 (Operation already in progress)
cli_start_connection: failed to connect to JBOTT-PC<20> (192.168.1.101)
dbott@thedrake:~$

```All of the discovered data is stored in **var/cache/samba/browse.dat**:
```
dbott@thedrake:~$ cat /var/cache/samba/browse.dat
"WORKGROUP"               c0001000 "THEDRAKE"                    "WORKGROUP"
"THEDRAKE"                40059a03 "thedrake server (Samba, Ubuntu)" "WORKGROUP"
"NAS-160GB"               40412003 ""                            "WORKGROUP"
"OMEGA-XP"                40011203 ""                            "WORKGROUP"
"JBOTT-PC"                40001003 ""                            "WORKGROUP"
"PIII-600"                40011003 ""                            "WORKGROUP"

```I hope this was useful and helps explain the difference between the various ways of setting up your network. You can use whatever method works, but I find the winbind package the easiest once it's setup.

-Dave

If you only have 1 Linux computer and don't want to go through the hassle of installing samba & winbind, just create an lmhosts file and add the appropriate details

Connecting by hostname alone (i.e. notebook), as opposed to the IP address (i.e. 192.168.0.24) requires the **/etc/hosts** file or **/etc/lmhosts**:
 
**The LMHOSTS File Way:**

 1. Create the **lmhosts** file:
 ```
sudo gedit /etc/lmhosts
```2. Add your client hosts:
 
         ```
# Sample Samba lmhosts file.
 #
 127.0.0.1    localhost        
 192.168.0.24 notebook
 192.168.0.25 another-computer
```3. This file needs to be replicated on each computer and requires you to use static IP addresses for each computer (probably not what you want).

**The HOSTS File Way:**

  1. Create the **hosts** file:
  ```
sudo gedit /etc/hosts
``` 2. Add your client hosts:
  
          ```
# Sample hosts file.
  #
  127.0.0.1    localhost.mydomain.local localhost        
  192.168.0.24 notebook.mydomain.local notebook
  192.168.0.25 another-computer.mydomain.local another-computer
``` 3. This file needs to be replicated on each computer and requires you to use static IP addresses for each computer (probably not what you want).

---

### Post by chili555 on 2007-03-19
There is another way: ```
chili@LAPTOP:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       LAPTOP

192.168.1.116   MBR2.linux
192.168.1.118   GBR1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
bill@LAPTOP:~$ ssh sylvia@GBR1
sylvia@gbr1's password: 
Last login: Mon Mar 19 13:18:15 2007 from 192.168.1.113
[sylvia@GBR1 ~]$
```
Set static IP's on all the macines you want to ssh to and then amend your hosts file to simply tell your computer who has what number.

You didn't say if this is a mixed network, linux, windows, mac, etc. but this is what we do in our all linux household.

---

### Post by joehill on 2007-03-19
Thanks!  I decided to go with the Samba option, which seems to have worked.

---

### Post by joehill on 2007-03-19
What I can't figure out, however, is that it seems to expect a password (not my own apparently) to connect to Samba shares.  At first smbtree didn't work at all, now it works with any random password.  Mounting shares doesn't work at all, although I can browse them with Nautilus.  I guess there's some Samba password somewhere that I can't find.

---

### Post by dbott67 on 2007-03-19
You've got to create some smb accounts.

The details are in this thread (first post):

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

-Dave

---

### Post by joehill on 2007-03-20
Thanks Dave!  Everything seems to be working now.
Joe

---

### Post by FITorion on 2007-03-24
after installing winbind... is there anything I have to do to make it bind the name?...

I ask because I have installed winbind and yet from my windows machine I can only ssh into the linux machine with the IP address...

My linux machine is named Relativity.  I'm on a college campus.  In my room with both computers connected to the schools network... on the windows machine I can search for relativity and find it.  when I go to somewhere else on campus and search for relativity I can't find it.

Someone else I know has windows sharing set up on their windows machine and I can see his computer no matter where I am on campus...

This is the last thing that's hanging me up... I need to make the name be able to be found campus wide.  Help!

---

### Post by joehill on 2007-09-25
For future reference, this stopped working for me for a while, and I finally realized that the avahi-daemon package somehow got removed.  I just reinstalled the "ubuntu-desktop" package, which reinstalled avahi-daemon, and my computer's name is again being broadcast.  So add that to the things you apparently have to do: have avahi-daemon running along with samba and winbind.

---

