---
title: "Fixed IP problem"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by starcastle on 2008-11-06
I am using Desktop 8.10 version and I trying to assign a fixed IP.

I make the necessary changes as well 'uncheck' the 'Seystem Setting' box and save.  The network config changes correctly.

However when I reboot the OS a second 'auto eth0' connection is created along with the fixed IP version that I had previously created.  The second interafce has the default DHCP config.

I dont know where to disable this behaviour.  I am running this as a vmware image and not sure if that could be contributing (I do have experience in running images and this is the first time I have seen this behaviour).

Anyone know how to diable this behaviour (I'm using the default GIU).

Thanks

Peter

---

### Post by superprash2003 on 2008-11-06
there seems to be a bug.. the only i think to fix this is manually editing /etc/network/interfaces file

---

### Post by RogerThompson on 2008-11-06
I also am having a problem assigning a fixed ip to my computer.  I tried using the graphical tool (Network Configuration under Preferences).  I opened to wired and what was showing was "Auto eth0"  I tried editing this under the IPv4 tab. I switched the method to Manual and added a set of fields to fill out.  I added the appropriate information in the fieldds, add DNS Server ips, as well as the search domain info. I clicked OK. and then Close in the main window.  I opened the whole thing up again to see that the information was retained which it appeared to be. I closed everything up and rebooted.  The system came back up I logged in and was informed that I was connected to the internet.  I opened the Network Connections tool again and it was back to getting the ip via DHCP.  What must I do? If this has been answered in another thread, please send me a pointer to the answer.

---

### Post by blackened on 2008-11-06
```
gksudo gedit /etc/network/interfaces
```

then make "#The primary network interface" section look like this (changing the addresses to what is appropriate for your network)

```
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.52
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

then

```
sudo /etc/init.d/networking restart
```

---

### Post by RogerThompson on 2008-11-13
I'm back again.  I did the above and the problem seemed to be solved.  I rebooted this morning and my machine did not come back up on the network.  I looked at the /etc/network/interfaces file and it appears to be as it should be (as above).  If I go to the GUI tool for network connections under Wired I see an entry for "ifupdown (eth0)" and an entry that says "never"

---

### Post by RogerThompson on 2008-11-13
Note the fix listed in this thread works, but it does not restore access to the DNS.  To do this, I had to manually edit the file /etc/resolv.conf
to add.

domain xxx.oclc.org
search <various domains>
nameserver xxx.yyy.zzz.aaa
for as many nameservers as there are on your system.

This may not survive a reboot though, so you might have to do it every time you reboot.

---

### Post by blackened on 2008-11-13
Doh, yeah that was my fault. I shoulda noted that you needed to add your dns entries to resolv.conf.

---

### Post by Gerrit1234 on 2008-11-26
I use 8.10 and in my work need to change IP often, using command line and editing the conf files is not practical, the previous wicd worked well, but I also like the 3G ability of the new Network manager. Please help

---

