---
title: "Workgroup Comp not visible in Ubuntu"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by metallicatony on 2008-02-03
Hi,
 Im using Ubuntu 7.10 and have my wireless connection setup with internet access working perfectly through it. My friends comp is running Vista with working internet connection through the same router. He has some of his folders shared in his windows which i need to access but im unable to see his computer at all in 
**Places -> Network -> Windows Network**
How come im unable to see anything though we both belong to the same workgroup?
Am i missing something here?
I would be grateful if someone can help me out?

Here are the details of windows machine
Hostname: tsb
Workgroup: MSHOME
IP(DHCP): 192.168.2.4

Here are the details of my ubuntu machine
Hostname: Zion
Workgroup: MSHOME
IP(DHCP): 192.168.2.3

Here is the global section of my samba
[B][global]
workgroup = MSHOME
server string = %h server (Samba, Ubuntu)
wins support = yes
;   wins server = w.x.y.z
dns proxy = no
;   name resolve order = lmhosts host wins bcast[/B]

and i have ensured samba is up and running

[B]metallicatony@Zion:/etc/samba$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons...                                                                                                                          [ OK ] 
 * Starting Samba daemons                                                                                                                             [ OK ] [/B]

[B]
metallicatony@Zion:/etc/samba$ ps -eaf | grep smb
root      6763     1  0 03:02 ?        00:00:00 /usr/sbin/smbd -D
root      6767  6763  0 03:02 ?        00:00:00 /usr/sbin/smbd -D
1000      6769  6652  0 03:02 pts/0    00:00:00 grep smb
[/B]

---

### Post by metallicatony on 2008-02-03
Still im not able to see the other comp thru samba.. after truncating smbd and nmbd logs in /var/log dir, i restarted smbd service and went to Places -> Network -> Windows Network
Still im not able to see anything listed there.. I can see the following in log.nmbd file..

[2008/02/03 11:09:01, 0] nmbd/nmbd.c:main(697)
  Netbios nameserver version 3.0.26a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2007
[2008/02/03 11:14:36, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396)
  *****
    Samba name server ZION is now a local master browser for workgroup MSHOME on subnet 192.168.2.3
    *****
[2008/02/03 11:14:36, 0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(396)
  *****
    Samba name server ZION is now a local master browser for workgroup MSHOME on subnet 169.254.5.86
    *****
[2008/02/03 11:14:36, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name MSHOME<1b> for the workgroup MSHOME.
  Unable to sync browse lists in this workgroup.
[2008/02/03 11:14:36, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name MSHOME<1b> for the workgroup MSHOME.
  Unable to sync browse lists in this workgroup.


Why is it not able to sync browse lists in this workgroup? Is this a BUG in ubuntu? really frustrates end users when these kind of straight forward configs don't work as expected in ubuntu!!

---

### Post by jetsam on 2008-02-03
It's definitely a troubled area.  Microsoft's closed protocols are as much to blame as anything. 

Very often, people are able to work around the lack of browsing by typing:```
smb://<ip_address_of_server>
``` into the location bar in Nautilus.  In the case of what you posted in #1, that would be```
smb://192.168.2.4
``` if you were trying to connect to the Windows machine.  

Since it seems like a temporary set-up for you, maybe if that works it will be enough for what you need?

If you really want to try to fix browsing, one of the better presentations of approaches toward the problem I've seen is at this web page by another forum poster: [http://www.swerdna.net.au/linux.html]("http://www.swerdna.net.au/linux.html") under "Network Browsing I' and 'II'.  It's written for Suse, but I think it's mostly translatable to Ubuntu and the general presentation is very clear.

One other thing that might be worth checking is a that an overzealous firewall on either the Ubuntu side or the Windows side can cause browsing to fail.

---

### Post by metallicatony on 2008-02-03
Thanks jetsam for your help. It was a very good tutorial.

I tried smb://192.168.2.4 in my nautilus. But it didn't display the shared contents of windows machine.

I followed the option 2 as advised in the tutorial. I added the following configs in smb.conf 
domain master = no
preferred master = Yes
local master = yes
os level = 65

I restarted the samba daemon. But didn't find it working as desired.
One last thing which i can try.. as you told..
I can see the windows machine (hostname: tsb) showing up under Network. I ensured in windows that firewall setting is off under control panel.
How can i ensure that there is no firewall blocking in ubuntu? I didn't install any firewall utilities on my own in my ubuntu.

---

### Post by jetsam on 2008-02-03
In a terminal,
```
sudo iptables -L
``` will spit out your firewall rules if you have any.

---

### Post by metallicatony on 2008-02-03
ok, i didnt find any firewall rules applied..

 sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Still not working! No more hope in me! :(

---

### Post by jetsam on 2008-02-03
It's interesting that you can now see and (I think) connect to the Vista machine, but can't see anything it's sharing.  I'm wondering if there's some detail of the way things are set up on the Vista machine that's off.  I don't use Vista myself, but Swerdna's web page has a Vista specific section.  Don't worry about any of the version stuff he talks about, but maybe when he gets into the Vista settings  it will give you an idea of some things to look at.  Here's his Vista page:
[http://www.swerdna.net.au/linhowtosambavista.html]("http://www.swerdna.net.au/linhowtosambavista.html")

I guess what I'm thinking is the share properties might not be set right to allow everyone to see the shares.

---

### Post by metallicatony on 2008-02-03
No im not able to see the windows machine from ubuntu samba. 
I was trying to mean that im just able to see the windows shared drives (permission given to everyone) under Network icon of WINDOWS.

i ensured that im able to ping windows computer from ubuntu.

The main reason is log.nmbd says
[2008/02/03 13:41:59, 0] nmbd/nmbd_browsesync.c:find_domain_master_name_query_fail(351)
  find_domain_master_name_query_fail:
  Unable to find the Domain Master Browser name MSHOME<1b> for the workgroup MSHOME.
  Unable to sync browse lists in this workgroup.

It is not able to reach the domain master browser of MSHOME workgroup and so ubuntu cudnt get the browse list of computers in that workgroup.
Anyways, im having a look at the link which you gave in your previous post now.

Thanks for your patient help!!

---

### Post by jetsam on 2008-02-03
> Thanks for your patient help!!
Sure, I wish it was more effective:-?

I wouldn't normally mess with this setting, but given your specific error message, it might be worth a shot to try setting 
```
domain master = yes
```
in the global section of your smb.conf and then restarting Samba.  If it doesn't work, take it out again.  It's a straw, and I am grasping at it....

Do you get anything if you type ```
smbtree
```
in a terminal?  You can just hit <enter> when it asks for a password.

---

