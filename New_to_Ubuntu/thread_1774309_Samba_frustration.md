---
title: "Samba frustration"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by cgjrdl on 2011-06-03
I've been trying to set up a basic samba share on my 10.10 server installation (which runs as a VM on top of Xen 5.6).

I've been using both the command line and webmin and have tried every simple combination I can think of when it comes to a simple, security-free (for test purposes) smb.conf file.  I have tried accessing the share from both windows and OS X.  When I attempt to connect with a username and password (which has been added to the Samba settings) I get a message saying "error connecting to the server".  When I try to connect as a guest, I get a message saying "the server [IP] does not allow Guest access".

I'm sorry to pose such a basic query but I've been going at this for hours now and I've probably missed something really obvious 'cause I'm so close to it.  What do I need to do to enable this basic share and allow users or guests to connect?

Here's the conf file:

[global]
    netbios name = ubuntu
    workgroup = WORKGROUP
    os level = 20
    interfaces = 10.0.1.0/30 eth0
    username map = /etc/samba/user.map
    null passwords = yes
    encrypt passwords = yes
    security = user
    bind interfaces only = No

[data]
    guest account = [user]
    writeable = yes
    public = yes
    path = /home/[user]/dat

---

### Post by robsoles on 2011-06-03
Welcome to UF.

As you have webmin installed I will try to 'cook' this for you via webmin.

Due you are using user level access you need to set up users, Have you made webmin's "Convert Unix users to Samba users" to users - are users listed in a box in the page that opens when you click "Edit Samba users and Passwords"?

Alternatively, if you've been venturing into terminal I might only need to mention:```
man smbpasswd
```to get you somewhere.

---

### Post by cgjrdl on 2011-06-03
robsole, thanks a lot for your response.  To answer your questions:

(i) prior to using webmin, I was doing everything via the CLI and I added the test user [user] via 'smbpasswd -a [user]'
(ii) I checked "edit samba users and passwords" on webmin and [user] is listed there
(iii) I made sure to map [user] to a corresponding unix account
(iv) I also checked that the UIDs matched (OSX vs Ubuntu).

I just did one other test which was to disable the password requirement for [user] via "edit samba users and passwords".  I then tried to connect and again, the server asked for a password and again it was rejected.

Given it appears that all the samba permissions/passwords are in place, I'm wondering whether there's something else going on with the server that's rejecting an external attempt to connect.  FYI, I have iptables disabled at the moment and both the server and clients are on the same LAN.

Any further thoughts would be very welcome.

---

### Post by robsoles on 2011-06-03
After using the 'edit samba users and passwords", did you restart Samba to apply the changes?


It might be easier for you to just 'synchronise' users, manually set the Samba password (for whatever user you wish to access 'as') and then restart Samba - try again.

any good?

---

### Post by bichamar on 2011-06-03
Hi, Im also a really new for Linux environment but just fought with same kind of problem setting samba shares up and to be honest I'm not sure what did the trick, but my 2 cents would go to smpasswd -e [user], give it a try.

---

### Post by 3rdalbum on 2011-06-03
Does it work if you specify the IP address like so:

(in Nautilus' location bar)
smb://192.168.0.10/sharename

Also for a simple server you don't need to manually edit the smb.conf file, you can just use "gksudo shares-admin" or install system-config-samba.

---

### Post by cgjrdl on 2011-06-03
Thanks for your responses everyone!

robsoles: I did what you suggested and it worked, many thanks.

3rdalbum: thanks for the tip about the X Windows config tool.  One other thing which seems a bit weird: when I try to login from a client using an IP address (smb://10.0.1.29/sharename for OS X or \\10.0.1.29\sharename in windows) it doesn't work.  I guess it's not the end of the world but I'm curious as to why not.

Again, thanks everyone.

---

### Post by robsoles on 2011-06-03
> **cgjrdl said:**
> ... but I'm curious as to why not.

Again, thanks everyone.

Most welcome.

Have you verified the IP address your server is listening on? It is most likely listening on all interfaces at the moment and the 'eth#' or 'wlan#' (or awfully similar) from the output of "ifconfig -a", into terminal, will have the currently assigned public (on your LAN at least) IP address associated with it.

---

### Post by cgjrdl on 2011-06-03
robsoles: apart from the loopback address, the only IP I get from ifconfig -a is "eth0 10.0.1.29" which is the one I'm trying to connect to.  Also, if I enter "nmblookup [server]" into the CLI it also returns 10.0.1.29

As I said, I can live with this but it's always good to get to the bottom of these questions :)

---

### Post by grants on 2011-06-03
Run this command
```
root@ubuntu-server:/etc/samba# testparm -s
```
then post the results

---

### Post by Morbius1 on 2011-06-03
> When I try to connect as a guest, I get a message saying "the server [IP] does not allow Guest access".That is a statement of fact. Someone here stated that because you are using user level security you have to create users with samba passwords. That is not true if you only have a guest share which is what you posted. 

The reason you got that error is because you are missing a line in the [global] section of your smb.conf file:
```
map to guest = Bad User
```The unauthenticated remote user will be tagged "Bad User" then converted to the guest account ( which BTW is "nobody" with a group: "nogroup" ). Your use of "guest account = [user] will work now that "map to guest" is in place but I would recommend you do one of two thing:

(1) Put that line in the global section.
OR
(2) Remove the line completely, have the remote user come in as nobody, then convert him to [user] in the share definition using "force user".

 So your smb.conf would look something like this:

[global]
    netbios name = ubuntu
    workgroup = WORKGROUP
os level = 20
    interfaces = 10.0.1.0/30 eth0
    username map = /etc/samba/user.map
    null passwords = yes
    encrypt passwords = yes
    security = user
[COLOR=Blue]**map to guest = Bad User**[/COLOR]
    bind interfaces only = No

[data]
[COLOR=Blue]**     force user = [user]**[/COLOR]
    writeable = yes
    public = yes
    path = /home/[user]/dat

I should note that "map to guest = Bad User" is the default smb.conf so there's a lesson here somewhere.

---

### Post by cgjrdl on 2011-06-03
Morbius1: "map to guest = Bad User" worked like a treat!  I tell you, one can spend hours reading manuals but it's never as effective as asking the question directly to people who know what they're doing!  Many thanks.

---

### Post by cgjrdl on 2011-06-03
grants: here's the output of testparm -s:

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[data]"
Global parameter guest account found in service section!
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    interfaces = 10.0.1.0/30, eth0
    map to guest = Bad User
    null passwords = Yes
    username map = /etc/samba/user.map

[data]
    path = /home/[user]/data
    read only = No
    guest ok = Yes

---

### Post by crispy_420 on 2011-06-03
Question: Maybe I am reading this wrong but doesn't 10.0.1.0/30 suggest you are on a class A network with only 4 hosts available? (in relation to the interfaces line). If not that maybe a/the issue. Shouldn't that match the subnet you have?

[http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

---

### Post by cgjrdl on 2011-06-03
crispy_420: you're right, I had the wrong interface in there.  I've changed it to a class C network.

---

### Post by crispy_420 on 2011-06-03
Working now?

So you are on a 192.x.x.x?

From the documentation you can either use the cidr or directly put in the subnet, it's all the same. So 10.0.0.0/8 is the same as a 10.0.0.0/255.0.0.0 as far as the samba config is concerned.

---

### Post by cgjrdl on 2011-06-04
crispy_420: yes it's all working now.  I'm actually on 10.x.x.x and yes, it does seem that one can either put in the full subnet or use the abbreviated format.

Thanks for your help!

---

