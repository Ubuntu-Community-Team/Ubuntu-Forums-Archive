---
title: "Browsing to Windows Computers Stopped Working"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by freddyp on 2008-01-11
Need some help, I've spent hours reading various newsgroups and still have not found a fix.  First some background -- running Gutsy 7.10 (standard install) with wireless connection (built into Fujitsu Lifebook) on a home network via Linksys router.  (Network has three Windows computers/2 XP Pro 1 XP Home and the one Ubuntu laptop).  Can cruise the web and check E-mail etc. on all computers with no problems! 

The Ubuntu documentation says Ubuntu supports accessing shared folders, drives and printers on a Windows computer by installing the smbfs plugin.  Installed smbfs plugin and for the past month have been able to go to Places>Network>Windows Network> and successfully connect to shared folders on all of the Windows computers on the home network simply by double clicking the computer icon (with computer name).  Also installed Samba (used a great guide from [http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm](http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm)) and can successfully connect to a shared folder on Ubuntu from all of the Windows machines.

Now the problem -- all of a sudden when I go to Places>Network>Windows Network> and click on the computer name I'm getting the following error:  "The folder contents could not be displayed.  Sorry, couldn't display all the contents of "Windows Network: <computer name>". 

I can connect to the Windows shares on each Windows computer by entering the IP address of each computer directly in the file browser location bar i.e. SMB://192.168.1.105.  Samba is also working because I can connect to the shared Ubuntu folder from any of the Windows machines.  Yes, I am using DHCP on the router, but I have verified that the router has assigned the same IP address that was in use on each computer when things were working.  Hope that makes sense! (I do not want to use static IPs for other reasons, and like I said, in this case I don't think it matters....no change in assigned IPs to each computer name, right?).  

smbtree properly lists the home network and all of the shares on each Windows computer
findsmb lists the proper IP ADDR and NETBIOS NAME for each computer
Trace route by IP shows one hop to the Windows computer on the internal network.
Trace route by computer name shows one hop and then goes to the ISP DNS name resolution and then dead end (?)

Things I've tried:

1. Remove/install samba and smbfs.  Of course, ran sudo smbpasswd -L -a logname and sudo smbpasswd -L -e logname after Samba re-install.  Samba works.

2. Made sure /etc/samba/smb.conf has browseable = yes and writeable = yes in the Share Definitions section.  Everything looks normal in the [Shared] section at the bottom of the file.

3. Connected laptop to router with ethernet cable (reconfigured interface) and tried to make sure problem is not a wireless issue.  Still cannot successfully connect to shared folders on any of the Windows computers by going Places>Network>Windows Network> and double clicking on the computers (with computer name).

4. Tried winbind and no change....still broken.

5. Ran Gutsy from Live CD and no change....makes me wonder if it ever worked.

Don't see this as an internal network or router problem because....

I can run Mint 4.0 from Live CD on the Ubuntu computer (that way I'm using the same computer, cables, and router) and everything works perfect (of course after making the appropriate configuration changes, loading sambe etc.)!!!!  In Mint I can connect to all the Windows computers (by computer name or IP) using the file browser and all Windows computers can connect to Mint via Samba.  Works perfect.  (Yes, router assigned the same IP as under Ubuntu).  I'm really confused now, though Mint was based on Ubuntu 7.10 ?!?!?  Is there a Ubuntu bug?  What am I missing?  Any help will be really appreciated.

---

### Post by 5circles on 2008-01-12
As mentioned in [http://ubuntuforums.org/showthread.php?t=664282]("http://ubuntuforums.org/showthread.php?t=664282"), our problems are similar.  Here is my experience for some of the things tried in this thread. 

> I can connect to the Windows shares on each Windows computer by entering the IP address of each computer directly in the file browser location bar i.e. SMB://192.168.1.105.
This worked for me too.  I needed authentication for some systems, but not ones I'd accessed earlier when things were working.

 > Samba is also working because I can connect to the shared Ubuntu folder from any of the Windows machines. 
This works for me too.

> smbtree properly lists the home network and all of the shares on each Windows computer
I can see the Ubuntu machine, but don't see the others consistently.  Some servers show timeouts from an Internet address.

> findsmb lists the proper IP ADDR and NETBIOS NAME for each computer
This works only for a couple of systems, presumably before the Internet timeouts occur.

> Trace route by IP shows one hop to the Windows computer on the internal network.
Ditto

> Trace route by computer name shows one hop and then goes to the ISP DNS name resolution and then dead end (?)
Traceroute by name to the computer with a faked static IP shows one hop.  Traceroute by name to others appears stuck.  Using the 'mtr' command I can see lots of Internet hops.

Using the 'host' command, I can see 3 public internet addresses attempted (one repeated) when I try to access systems on the LAN that don't have a faked IP address in /etc/hosts.

Not sure if the preceding adds anything other than sharing the misery...

Mike

---

