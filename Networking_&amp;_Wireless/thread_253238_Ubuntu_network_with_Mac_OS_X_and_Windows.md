---
title: "Ubuntu network with Mac OS X and Windows"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by MacPC on 2006-09-08
Hi,

Questions about networking Ubuntu to Mac and Windows machines. There are several issues here actually.

I have a LAN which consists of two Windows PCs, one runs Windows 2000 Pro and the other runs Windows XP Pro., and I also have a Mac runing OS X 10.4.6 All of them are networked, all can share files and printer.

Recently, I added another machine running Ubuntu 6.0.6, I want it to be on the network. I set it up and the following happened:

1.) On the Ubunto PC, it can see both Windows PCs  and can transfer files from the Windows machines to the Ubuntu machine without problem, but....

In the Network neighborhood on the two PCs, I can see the Ubuntu PC's icon, but when I try to access the Ubuntu PC, I can't pass the stage where the indows ask for username and password, it just keeps pop back up after I entered my info. No error message or warning of any sort, How can I set the Ubuntu PC as the server so that the Windows PCs can have access to it?

2.) Both the Mac and the Ubuntu can find each other, but on the Mac, it's the same thing, I once I typed in the username and password, the Mac says it can't connect to the Ubuntu, and on the Ubuntu PC, I can open the shared folder from the Mac but it doesn't show anything in the folder.

3.) About the printer, I have two printers, one connects to the Windows PC and the other one connects to the Mac. I set up print sharing on the Ubuntu, I can print to the printer that connected to the Windows PC but I can't print to the printer on the Mac. I have both printer drivers installed on the Ubuntu.

4.) I followed some instruction on this forum to configure the /etc/samba/smb.conf file, but it won't allow me to save it because it says the file is read-only. How can I change that?

I am a total newbie to this Unix/Linus thing so any help wil be appreciated.

Thanks in advance.

MacPC.

---

### Post by whistlerspa on 2007-05-25
Same here I keep getting asked to authorise access on the Mac but then I'm told to delete an 'Alias' whatever that  means. I can see the Mac on my Ubuntu boxes but can't access shared folders.

I find Samba pretty slow anyhow  even between my Ubuntu boxes, and i often have to fiddle with LAN settings on my router box to get it working under DHCP - definitely the worst aspect of Linux I feel

---

