---
title: "Sharing Network Folders with NFS between 2 Ubuntu v6.10 Desktop PCs - Please Help!!!"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by dvarsam on 2006-12-05
Hello All!

I need your help!
I am trying to Share some Folders between 2 Ubuntu v6.10 _Desktop_ PCs.
And I am trying to do it by using **NFS**.

I followed all the steps provided here:

[http://nfs.sourceforge.net/nfs-howto/index.html](http://nfs.sourceforge.net/nfs-howto/index.html)


But I can't seem to get to Share a Folder!
I will start explaining every step taken so that hopefully I can get some help here...

**So, I performed the following steps:**

**1.** From the Menu, I selected "**System Administration\Shared Folders"**.

**2.** I then installed _just_ **NFS** - not Samba.

**3.** The following packages were installed:

a. libevent1_1.1a-1_i386.deb
b. libgssapi2_0.10-2_i386.deb
c. libnfsidmap1_0.16-3_i386.deb
d. librpcsecgss2_0.13-2_i386.deb
e. nfs-common_1%3a1.0.9-2ubuntu1_i386.deb
f. nfs-kernel-server_1%3a1.0.9-2ubuntu1_i386.deb
g. portmap_5-20ubuntu1_i386.deb

**4.** I then, decided to perform the rest of the set up by using the **Terminal** & NOT go by using the Menu's "**System Administration\Networking**".

_Note_:
I decided to go this way, because, when from the Menu I create a Shared Folder & then try to delete it, it does NOT get deleted...
And then I have to go & delete the line from the file "**/etc/exports**" to finally get the Shared Folder deleted from the Menus too!
I guess that this is a BUG (that needs some attention)!!!

**5.** I launched a Terminal window (from Menu, I select "**Applications\Accessories\Terminal**").

**6.** I typed "sudo -i" & then my password.

**7.** I typed "cd /" & then "**cd /etc**"

**8.** I typed "**nano hosts**" & added the following 2 lines:

> 192.168.1.2 dimitris-desktop.workgroup
# representing user "dimitris"

192.168.1.3 elena-desktop.workgroup
# representing user "elena"

_Notes_:
a. In the above, "dimitris-desktop" is representing the "Host Name" & "workgroup" is representing the "Domain Name".
b. I have assigned to my 2 Ubuntu v6.10 Desktop PCs Static IPs: 192.168.1.2 (to be the Server) & 192.168.1.3 (to be the Client)
c. I am working on the Server Side currently - i.e. 192.168.1.2
d. The is NO problem with these 2 PC's Network Settings, as they can both Access the Internet through a Router.

The way my "**/etc/hosts**" file looks like after saving is:

> 127.0.0.1 localhost
127.0.1.1 dimitris-desktop.workgroup

192.168.1.2 dimitris-desktop.workgroup
# representing user "dimitris"

192.168.1.3 elena-desktop.workgroup
# representing user "elena"

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

_Note_:
Also, in the above "/etc/hosts" file, make sure that the line "127.0.1.1 dimitris-desktop.workgroup" is in the correct format!
A format like "dimitris-desktop" or "ubuntu1" or else, would create problems. 

**9.** Now on the Terminal window, I type "**nano hosts.allow**" & add the following line:

> portmap : 192.168.1.3
# Here you type the IP of the Client PC.

# portmap : ALL
# If  "portmap : 192.168.1.3" does NOT do it, try using a 
# "portmap : ALL" instead.

The way my "**/etc/hosts.allow**" file looks like after saving is:

> # /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5), hosts_options(5)
#                   and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8 ), rpc.mountd(8 ) and
# /usr/share/doc/portmap/portmapper.txt.gz for further information.
#

portmap : 192.168.1.3
#Here you type the IP of the Client PC.

# portmap : ALL
# If  "portmap : 192.168.1.3" does NOT do it, try using a 
# "portmap : ALL" instead.

**10.** Now on the Terminal window, I type "**nano hosts.deny**" & add the following line:

> portmap : ALL

The way my "**/etc/hosts.deny**" file looks like after saving is:

> # /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5), hosts_options(5)
#                  and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper. See portmap(8 )
# and /usr/doc/portmap/portmapper.txt.gz for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

portmap : ALL

**11.** Now on the Terminal window, I type "**nano exports**" & add the following line:

> /home/dimitris/Desktop 192.168.1.3(rw,no_root_squash,sync)
# Here, the Client PC is permitted to access the Server PC.

_Notes_:
a. I would like to share my Desktop Folder with the Ubuntu Client PC with IP 192.168.1.3.
b. The word "Desktop", _must_ be typed with a capital "D".
c. I know that I could also use "elena-desktop.workgroup(rw,no_root_squash,sync)" notation instead of the IP one, but for some reason I feel better using an IP.
d. IF you are trying to access a Server's files (from the Client side) by being "**root**", your Server's "**/etc/exports**" file _must_ export the Shared Folder with the **no_root_squash** option. In general, being able to write to the NFS Server as "root" is a bad idea unless you have an urgent need - which is why Linux NFS prevents it by default. 


The way my "**/etc/exports**" file looks like after saving is:

> # /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#

/home/dimitris/Desktop 192.168.1.3(rw,no_root_squash,sync)
# Here, the Client PC is permitted to access the Server PC.

**12.** Since I have edited the file "**/etc/exports**", I _must_ force nfsd to **re-read** the file, by running the command:

> exportfs -ra

**13.** Even though this step might not be really needed, I decided to restart the "**nfs-kernel-server**" too, by running the command:

> sudo /etc/init.d/nfs-kernel-server restart

**14.** I _perform_ the above **same steps** on the other Ubuntu v6.10 Desktop PC but of course in reverse order (i.e. as if "elena-desktop" is now the Server, and "dimitris-desktop" the Client). 

**15.** It seems now that I am ready to access the NFS Shared Forder "**/home/dimitris/desktop**" on the other Ubuntu PC named "elena-desktop" with IP 192.168.1.3.

So, on the other PC, from the Menu, I select "**Places\Network Servers**" & see...

NOTHING!!!
NO SHARE!!!

**16.** I also tried to "**ping**" from the Client the Server, by using the name I used in "**/etc/hosts**":

> elena@elena-desktop:~$ **ping 192.168.1.2**
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=4.88 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=0.325 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=64 time=0.316 ms
64 bytes from 192.168.1.2: icmp_seq=4 ttl=64 time=0.313 ms
64 bytes from 192.168.1.2: icmp_seq=5 ttl=64 time=0.310 ms
64 bytes from 192.168.1.2: icmp_seq=6 ttl=64 time=0.303 ms
64 bytes from 192.168.1.2: icmp_seq=7 ttl=64 time=0.300 ms

--- 192.168.1.2 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6000ms
rtt min/avg/max/mdev = 0.300/0.965/4.889/1.602 ms

So, this seems to be successful!

Also, using the following notation:

> elena@elena-desktop:~$ **ping dimitris-desktop.workgroup**
PING dimitris-desktop.workgroup (192.168.1.2) 56(84) bytes of data.
64 bytes from dimitris-desktop.workgroup (192.168.1.2): icmp_seq=1 ttl=64 time=0.264 ms
64 bytes from dimitris-desktop.workgroup (192.168.1.2): icmp_seq=2 ttl=64 time=0.214 ms
64 bytes from dimitris-desktop.workgroup (192.168.1.2): icmp_seq=3 ttl=64 time=0.301 ms
64 bytes from dimitris-desktop.workgroup (192.168.1.2): icmp_seq=4 ttl=64 time=0.322 ms

--- dimitris-desktop.workgroup ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3008ms
rtt min/avg/max/mdev = 0.214/0.275/0.322/0.042 ms

Seems to a_lso_ work!

**What am I doing wrong?**

Thanks.

P.S.> By the way, _NO_ firewall program is installed in my Ubuntu...
So, you shouldn't worry about that...
However, I hope that it is not a Router related problem...
My Router provides _successful_ Internet access on _both_ Ubuntu v6.10 Desktop PC's.
Could it be due to the Router?
Please Help!!!

---

### Post by dvarsam on 2006-12-05
I also Noticed another NFS Networking BUG!!!

Even though, I edited through the Terminal the file "**/etc/hosts**", the data did NOT update on the Menus!!!
When on the Ubuntu Menu, I select "**System\Administration\Networking**", select "Wired Connection" & Click on the Tab named "General", under "Host Settings:", the "Host Name:" being preserved is an** old one** compared to the one stated inside the "**/etc/hosts**" file.
I can read a "**Host Name:**" value of "**ubuntu1**", while...
...the "**/etc/hosts**" file contains the value "**dimitris-desktop**".

That is NOT correct!!!

_Not_e:
This can also be noticed when a user Boots his Ubuntu v6.10 PC!
When the user is presented the Login Window, on the bottom right corner, a "Host Name:" value "**ubuntu1**" is shown, while the file "**/etc/hosts**" states a different value!!!
Oh dear... :)

The Ubuntu OS should _either_ use the value saved on the file "**/etc/hosts**" _OR_ the value saved on the Menu's "**System\Administration\Networking**" Tab "General", "Host Name:" value "**ubuntu1**".
Keeping **both** is a problem!!!
Anyway, I updated the Menus to reflect what the file "**/etc/hosts**" contains (e.g. "dimitris-desktop").

Finaly, performing an "**rpcinfo -p 192.168.1.2**" command on the Server side, gave the following results:

> root@dimitris-desktop:/# rpcinfo -p dimitris-desktop
rpcinfo: dimitris-desktop is unknown host
root@dimitris-desktop:/# rpcinfo -p 192.168.1.2
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32770  nlockmgr
    100021    3   udp  32770  nlockmgr
    100021    4   udp  32770  nlockmgr
    100021    1   tcp  36718  nlockmgr
    100021    3   tcp  36718  nlockmgr
    100021    4   tcp  36718  nlockmgr
    100005    1   udp    662  mountd
    100005    1   tcp    665  mountd
    100005    2   udp    662  mountd
    100005    2   tcp    665  mountd
    100005    3   udp    662  mountd
    100005    3   tcp    665  mountd
    100024    1   udp  32771  status
    100024    1   tcp  35122  status

I have NO clue what do all these mean...

Thanks.

P.S.> Even though I fixed this, I can still NOT Share any Folders between those 2 PCs...

---

### Post by dvarsam on 2006-12-05
Hello again!

I have managed to "**mount**" an NFS share!

To do this, on the Client's side, I launched a Terminal window & did the following:

1. Typed: "sudo -i" & typed password

2. Typed: "cd /" & "**cd /mnt**"

3. Typed: "**mkdir nfsshare**"

4. Typed: "**mount 192.168.1.2:/home/dimitris/Desktop /mnt/nfsshare**"

5. Typed: "**cd nfsshare**.

6. Typed: "**ls**.

You should now be able to see a list of your Server's Desktop files on your Client's "**/mnt/nfsshare**" folder.

**However, this was NOT my original intention...**

[quote=dvarsam]I wanted to be able to see my NFS Shared Folders inside the Menu's "**Places\Network Servers**" as an icon!!![/quote]

Is this NOT possible?

Thanks.

P.S.> And I thought that NFS would look like SAMBA's Shared Folders...???
**This sucks!!!**

---

### Post by dvarsam on 2006-12-06
Hello again!

I am facing the following problem:

When I am trying to connect with a "**mount**" command:

**a.** From the PC "**elena-desktop**" (IP 192.168.1.3) to the PC "dimitris-desktop" (IP 192.168.1.2), I do NOT have a problem - the connection is successful. 

But:

**b.** From the PC "**dimitris-desktop**" (IP 192.168.1.2) to the PC "elena-desktop" (IP 192.168.1.3), I can NOT connect!!!

I have checked everything!

Every file:

1. "**hosts**"
2. **"hosts.allow**"
3. "**hosts.deny**"
4. "**exports**"

I also performed an "**exportfs -ra**" in the "**elena-desktop**" PC,

but I can NOT seem to be able to fix this!

I also decided to install the package "**openssh-server**" by Synaptic, in order to try to connect to the "elena-desktop" through **SSH**.

_Note_:
Installation of package "**openssh-client**" was not required because in Ubuntu v6.10 it is installed by default!

Anyway, the SSH connection was successful!

So I don't know what is the matter...

I have already shared with you my "**dimitris-desktop**" files before (e.g. hosts, hosts.allow, hosts.deny & exports)...
So, let me now provide the files inside the other Networked PC - "**elena-desktop**":

**1.** File "**hosts**", includes:
> 127.0.0.1 localhost
127.0.1.1 elena-desktop.workgroup

192.168.1.2 dimitris-desktop.workgroup
# representing user "dimitris"

192.168.1.3 elena-desktop.workgroup
# representing user "elena"

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

**2.** File "**hosts.allow**", includes:
> # /etc/hosts.allow: list of hosts that are allowed to access the
# system.
#             See the manual pages hosts_access(5), hosts_options(5)
#             and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap"
# for the daemon name. Remember that you can only use the keyword
# "ALL" and IP addresses (NOT host or domain names) for the
# portmapper, as well as for rpc.mountd (the NFS mount daemon).
# See portmap(8 ), rpc.mountd(8 ) and 
# /usr/share/doc/portmap/portmapper.txt.gz for further information.

portmap : 192.168.1.2
# Here you type the IP of the Client PC.

# portmap : ALL
# If "portmap : 192.168.1.2" does NOT do it, try using a
# "portmap : ALL" instead.

**3.** File "**hosts.deny**", includes:
> # /etc/hosts.deny: list of hosts that are _not_ allowed to access
# the system.
#             See the manual pages hosts_access(5), hosts_options(5)
#             and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap"
# for the daemon name. Remember that you can only use the keyword
# "ALL" and IP addresses (NOT host or domain names) for the
# portmapper. See portmap(8 )
# and /usr/doc/portmap/portmapper.txt.gz for further information.
#
# The PARANOID wildcard matches any host whose name does not match
# its address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs.
# In past versions of Debian this has been the default.
# ALL: PARANOID

portmap : ALL

**4.** File "**exports**", includes:
> # /etc/exports: the access control list for filesystems which may be
# exported to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
 
/home/elena/Desktop 192.168.1.2(rw,no_root_squash,sync)
# The number 192.168.1.2 refers to the Client PC.
# Here, the Client PC is permitted to access the Server PC.

# /home/elena/Desktop dimitris-desktop.workgroup(rw,no_root_squash,sync)
# You might be able to try this - it should be considered safer too!

Do you find anything to be wrong in these files compared to the files provided before for the user "dimitris-desktop"?

Also, according to this HowTo [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

> NFS user permissions are based on user ID (UID). UIDs of any users on the client must match those on the server in order for the users to have access.
Blah...blah...

Could this problem be related to UIDs?
How can I check that?

Thanks.

P.S.> I am trying to create 2 Folder Shares at the _same_ time:
**1.** On the PC named "**dimitris-desktop**", I want the user to be able to access the User's "elena-desktop" Desktop.
**2.** On the PC named "**elena-desktop**", I want the user to be able to access the User's "dimitris-desktop" Desktop.
And both of these shares are going to be "active" at the _same_ time!
Is that permitted by Ubuntu's v6.10 Shares through NFS or not?
But in any way, even if I "**umount**" the successful above case "2", I can still not create a successful "mount" for the above case "1" - even though an SSH connection seems to be working fine (it is achieved successfully)!
Please help!

---

