---
title: "Direct connect to XP machine"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by jwlawson on 2008-09-27
I am new to Linux.  I have installed Xubuntu on an old PC to try it out.  The install work well.  After fighting a bit with the nVidia drivers, all seems to work.  The old machine has a Win modem, so I decided to try and use internet connection sharing (ICS) from my XP machine.  I purchased a Netgear FA311 NIC for the old machine and connected it to the XP machine with a crossover cable.  After installing the NIC, upon start up, Xubuntu recognized the card.  The internet sharing works great.

My problems started when trying to get the Xubuntu to see the shared folders on the XP machine.  I have configured the MSHOME workgroup as most postings suggest.  The XP machine is set with an IP of 192.168.0.1 and the Xubuntu machine with an IP address of 192.168.0.2 and both having a subnet mask of 255.255.255.0.  With these settings, ICS does not work nor can I access the XP shared folders.  To get the ICS to work again, I set Xubuntu to use roaming mode.  Under roaming mode,the IP address is 192.168.0.228.  I still cannot see the XP machine.

While under roaming mode, ICS works great.  I do have smbfs installed and the XP machine shows the local area connection as connected.  Why can't I see the XP shares?  I have disabled the XP firewall.  My understanding is that I should see a Windows network option under the Application-Network.  The XP machine does not show the Xubuntu machine under the workgroup computer listing either.

Apparently I am missing something.  Any advice to resolve this issue will be greatly appreciated.

Thanks,

---

### Post by SecretCode on 2008-09-27
I may be confused as to which machine has the internet connection - presumably the XP machine? But since ICS is working, that's not a problem.

Can you ping each computer from the other? (From XP command window / linux terminal window. This confirms your network is connected.) Can you ping web sites by name from each computer?

I have Ubuntu with the Nautilus file browser so I'm not sure what commands connect to a network share under Xubuntu.

On XP do you have file and printer sharing enabled on the 'local area connection'?

---

### Post by jwlawson on 2008-10-05
You were correct; the XP machine has the internet connection.  When i pinged the computers, they were found so the problem had to be configuration.  After a bit of searching, I found some needed changes to the smb.conf file.  All works great now.  Thanks,

---

