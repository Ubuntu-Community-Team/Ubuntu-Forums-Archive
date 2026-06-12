---
title: "Samba 3 weirdness on my laptop with gutsy"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by fireman71 on 2007-12-01
I kow that I am probably missing something extremely simple, but it's getting late and my head hurts from banging it against this problem for way too long today.

The scenario as it currently stands:

I have a home office lan with a few computers on it as follows
#1 - Windows XP for use by my better half who also acts as my secretary and handles my scheduling, contacts and bookkeeping.

#2 - Windows XP for my son who needed a computer for school but only seems to play games for hours on end.

#3 - Ubuntu Gutsy Server which is setup as a Samba file server / print server / local lan web server

#4 - Laptop dual booting Windows Vista and Ubuntu Gutsy Desktop.

Every computer can see and connect to the main Samba file server fine. All the windows machines can see it in network neighborhood, print to it etc. This includes the laptop when booted into Vista. The main samba server can see every share including the laptop when booted into Vista and all is good in the world.

When I boot the laptop into Gutsy, I can only access samba/windows shares from the command line with smbclient -L IPADDRESS -U username. I cannot browse the network using any GUI tools nor can I scan the workgroup in pyNeighborhood and gnome's browser shows "Windows Network" and when I go into that it acts as if nothing is out there and stubbonly continues to display a plain empty screen.

When I try to access a computer from the laptop in gutsy with smbclient -L COMPUTERNAME -U username it appears that the laptop is trying to access my public ip address (67.77.2xx.xxx which is closed to netbios requests) instead of my private ip addresses (192.168.1.xxx) which is assigned by DHCP from my router to every machine except for the main samba file server (#3).

I have tried configuring samba on the laptop with webmin, swat, by hand reffering to several different howtos and finally by just copying smb.conf from the main samba server to the laptop. All of which generate the same result.

So I am thinking the problem is not in smb.conf as I have suspected for the past several hours but is hiding somewhere else. For the life of me though I have no idea where or what the problem may be.

Does anyone have any ideas? And, yes, you can poke fun at me if I have missed the totally obvious \\:D/ but for th elife of me I cannot figure out which way to go next.](*,)

Many thanks in advance,
Ian

***MORE INFORMATION 12-02-2007***

smbtree reports the following information:

MYGROUP
        \\XPWIN                         xpwin
Error connecting to 67.77.231.141 (Connection refused)
cli_start_connection: failed to connect to XPWIN<20> (67.77.231.141). Error NT_STATUS_CONNECTION_REFUSED
        \\UBUNTUSERVER                  ubuntuserver server (Samba, Ubuntu)
Error connecting to 67.77.231.141 (Connection refused)
cli_start_connection: failed to connect to UBUNTUSERVER<20> (67.77.231.141). Error NT_STATUS_CONNECTION_REFUSED
        \\JAMIE          
Error connecting to 67.77.231.141 (Connection refused)
cli_start_connection: failed to connect to JAMIE<20> (67.77.231.141). Error NT_STATUS_CONNECTION_REFUSED
        \\FIREMAN71-LAPTO               fireman71-laptop server (Samba, Ubuntu)
Error connecting to 67.77.231.141 (Connection refused)
cli_start_connection: failed to connect to FIREMAN71-LAPTO<20> (67.77.231.141). Error NT_STATUS_CONNECTION_REFUSED

As you can see samba is trying to lok at my public IP address from my router instead of my private IP addresses which are assigned by a dhcp server on my router.

When I go into /etc/hosts and add an entry for the only computer on my network with a static IP address (which is ubuntuserver) I get the following:

MYGROUP
        \\XPWIN                         xpwin
Error connecting to 67.77.231.141 (Connection refused)
cli_start_connection: failed to connect to XPWIN<20> (67.77.231.141). Error NT_STATUS_CONNECTION_REFUSED
        \\UBUNTUSERVER                  ubuntuserver server (Samba, Ubuntu)
                \\UBUNTUSERVER\fireman71        Home directory of fireman71
                \\UBUNTUSERVER\OfficeJet_6100   OfficeJet_6100
                \\UBUNTUSERVER\PDF              PDF
                \\UBUNTUSERVER\print$           Printer Drivers
                \\UBUNTUSERVER\usbhd          
                \\UBUNTUSERVER\IPC$             IPC Service (ubuntuserver server (Samba, Ubuntu))
        \\JAMIE          
Error connecting to 67.77.231.141 (Connection refused)
cli_start_connection: failed to connect to JAMIE<20> (67.77.231.141). Error NT_STATUS_CONNECTION_REFUSED
        \\FIREMAN71-LAPTO               fireman71-laptop server (Samba, Ubuntu)
Error connecting to 67.77.231.141 (Connection refused)
cli_start_connection: failed to connect to FIREMAN71-LAPTO<20> (67.77.231.141). Error NT_STATUS_CONNECTION_REFUSED


Any ideas on where I need to look in my network configuration to fix this problem?

Thanks again!

---

### Post by handydan918 on 2008-01-28
Not a single response since December? I have the same error message....

---

### Post by swerdna on 2008-01-28
Maybe I can start the ball rolling by exposing some more of your underlying network data. Please post the dialogue you get in a terminal with these commands:
cat /etc/samba/smb.conf
cat /etc/resolv.conf
sudo route
sudo ifconfig
sudo iwconfig

Swerdna

---

