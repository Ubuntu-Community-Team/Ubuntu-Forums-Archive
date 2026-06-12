---
title: "Perplexing Samba Problem"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by stego_s_aurus on 2007-01-24
Hello all!

I am stuck: I am using 6.10 Edgy, and have set up a samba server using all the default settings, creating the samba user with smbpasswd, and enabling the homes folder. Here is a dump of my samba settings as listed by Testparm:

> 
[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        dns proxy = No
        passdb expand explicit = No
        invalid users = root

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0600
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


From the windows machine, I can log onto the users folder no problem, I can browse the directories no problem. I can create a folder, I can delete the folder. No Problem.

The problem is: Each and Every time I try copying a big file out from or into the share from a windows computer, ubuntu COMPLETELY locks up. Mouse freezes, I can't even ctrl-alt-F6 to get into another terminal. BAM. Stuck. It freezes just as bad as a flippin Windows box!! I've tried looking at logs: I set my log level to 3. It gets all the way to the point of showing how windows gets the file info for it, but no further.

I'm at a loss. Is there anything that I'm missing??

Help with this would Definitely be appreciated.

---

### Post by elst on 2007-01-24
The first step is probably to narrow down the cause a bit more. Try connecting the Ubuntu system to it's own Samba service (i.e. localhost), and doing the transfer. This goes over loopback, so it cuts out the network interface, the network connection, and XP, all of which are other potential causes.

---

### Post by stego_s_aurus on 2007-01-26
SOLVED!!!!

Allrighty: I had noticed someone on another forum that mentioned the Idea of using TWO nics in the Virtual Machine: the one that connects to the Net (and ultimately the Internet), and then another "Host Only" nic that Only communicates between VMware and your linux Host.

This solution worked nicely!!

Apparently, Samba just doesnt like the Idea of "Swallowing its own spit", if you will, where the physical NIC is trying to push the same data back through itself to the virtual NIC.

Instead, Have it communicate from a Virtual nic (the Host Only virtual nic on the VMware side) to the Virtual Nic on the Linux side (the vmnet1 nic that is created when you first install VMware).

To better describe my setup:

When I installed VMware and created my virtual machine, it set up the virtual machine with a Bridged NIC that communicates on the same physical network that the computer is connected to. At the same time, it created (on the linux side) a vmnet1 interface with the IP of 192.168.206.1 . (to see the IP assigned to Your virtual NIC, do an IFCONFIG in a terminal window and look at the IP address assigned to vmnet1)

For me to properly use Samba with this, before I "turned on" the virtual machine, I added another Network Interface to the virtual machine, selecting "Host Only" from the options.

Also: in my smb.conf, since I force samba to bind to specific interfaces, I made sure to include the interfaces 192.168.206.0/8, vmnet1 in my smb configuration and restarted the samba server.

Now, when I turned on the virtual machine and loaded up Windows, windows saw this new NIC, and an invisible DHCP server assigned it an IP of 192.168.206.x .

Lastly, I clicked start > run, and typed in \\192.168.206.1 and hit ENTER.

Since I was requesting specifically that IP address, it connected through the virtual nic to the other virtual nic, and suddenly I was connected to my linux host, and able to move large files flawlessly!!


This was SUCH a headache to find out, but once I found it and understood what was going on, it seems to be a Very easy setup! Think of it as two virtual NICs connected together via a virtual crossover cable.

---

