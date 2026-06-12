---
title: "ubuntu to mac"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by Digitallysick on 2007-04-02
I can connect from my mac to my ubuntu box, i have read/write access, but, from ubuntu, in networking i see "powerbook" when i double click it, it just displays nothing at all?? any idea what im doing wrong?

---

### Post by souki on 2007-04-03
I guess yo udon't have dns entry for your "powerbook"
try to ping it by name in a terminal window:
ping powerbook


if you know your ip address, you can use it with the "connect to server" menu entry
then you should see the share under "networks" and provide your login/password

---

### Post by Digitallysick on 2007-04-03
I can "ping powerbook" and i get a response with the ip i assigned (192.168.1.4) when i click "connect to server" i select windows share? and put in the ip, then it just says "0 objects"

---

### Post by dalziel_86 on 2007-04-03
Have you set up file-sharing on both machines? I'm presuming here that you're using Samba file-sharing. If you're only going to be using only Ubuntu and Macs on your network, you might look at AppleTalk instead.

---

### Post by Digitallysick on 2007-04-03
yeah im using samba , i will check into appletalk. I have a few windows pcs on my network (not that i own but friends that come over) that i would like to be able to access my files to. I assume they can from windows as of now

---

### Post by dalziel_86 on 2007-04-03
Stick with Samba if you want to share files with Windows machines.

Have you enabled Samba sharing on both machines? Have you set up accounts on both machines to access Samba sharing? Rememeber that Samba on OS X requires you to nominate accounts that can access the shares, and Samba on Ubuntu requires you to give each account a Samba password in addition to the account's system password. Are you sure you're entering the right accounts and passwords for the right machines? Have you made sure the firewall settings on both machines are set to allow Samba sharing?

---

### Post by Digitallysick on 2007-04-03
in osx i have "windows sharing " and "personal file sharing" enabled, is there something else i should do in osx to get it to work?

---

### Post by souki on 2007-04-05
I have the same problem and I guess you have to configure both desktop the same way (workgroup name and account name) to have it working this way
 
this means, you have to edit /etc/smb.conf under osx and adjust your workgroup name and your shares

but you can allways connect to any samba share following this steps :

from ubuntu,

- go to Menu > Shortcut > Connect to server
- choose Service Type : "Windows Share"
- server : the_mac_ip_address
- user name : the_mac_account_short_name
- click "Connect"

Now go to Menu=>Shortcut=>Network
you should see a volume named "the_mac_ip_address"
double click on it, and you should see a windows share  named "the_mac_account_short_name"

---

### Post by Digitallysick on 2007-04-05
Thanks! i finally got it working , when you use"connect to" it works, but for some reason just pulling up the powerbook in "network" it shows 0 items. Now i can connect and read/write to my powerbook thanks so much for your help!

---

### Post by souki on 2007-04-06
when you click on Network=>powerbook, you don't provide a login, you are logged as anonymous account
this account can't see any share

that's why

---

