---
title: "accessing local drives"
date: 2013-10-18
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2013-10-18
What is the easiest way to connect to another machine's drive assuming the only connection is via the ethernet ports of an ADSL router?

I have only 2 computers both connected only via the ADSL router's  ethernet ports. I would like the one which is connected to my TV,  via hdmi, to be able to pull files from the other computer. What is the simplest way to do it?

Do I have to use NFS or is there a less complex way?

Robin

---

### Post by houstonbofh on 2013-10-18
With a file browser (nautilus) open click on File, and choose "Connect to Server."  I connect via ssh, but you do have to install ssh.  However, I consider that a requirement anyway.

---

### Post by Robbyx on 2013-10-19
Thank you. Could you please comment a bit more.

I guess the file is clicked on at the computer that is hoping to access it ie the one that does not have the file. 

At present I can not see any of the contents of the other machine. Nothing is being shared by my main (non tv connected) computer. So there is nothing to click. Sharing has not been set up, if that is needed. 

I did a search here on network sharing and did not find anything directly relevant to me. What I did find was this comment, but it looks like overkill as a 20 machine system was being discussed:

[I]
Enable file sharing amongst ubuntu, xubuntu, lubuntu ?

    With that many computers, you really need to consider building a central server, presumably using one of the existing machines. For an all-Linux system, you should be using NFS. Designate one machine as a server (it can also function as a workstation if necessary, though it's not recommended), attach sufficient storage either by installing a hard drive or attaching an external USB device, then create a folder where the shared files will reside. Make the folder world-writable (sudo chmod uga+rwx /path/to/the/folder). Next install nfs-kernel-server from the repositories and follow the instructions in the linked article above to create the /etc/exports file.

    On all the machines you will need to install the nfs-common package so they can communicate with the server. You can add an entry into /etc/fstab on the client machines to mount the shared folder automatically at boot.

    Files created in the shared folder will have the ownership and permissions of the person who created them. That means that, by default, only the file's owner can edit the file. If you want to allow people to alter other peoples' files, read this. 

[/I]

---

### Post by coldraven on 2013-10-19
This article is using wifi to share but the process should be the same for cable.
[http://askubuntu.com/questions/310180/how-to-share-files-using-a-wireless-network](http://askubuntu.com/questions/310180/how-to-share-files-using-a-wireless-network)

---

### Post by Robbyx on 2013-10-19
> **coldraven said:**
> This article is using wifi to share but the process should be the same for cable.
[http://askubuntu.com/questions/310180/how-to-share-files-using-a-wireless-network](http://askubuntu.com/questions/310180/how-to-share-files-using-a-wireless-network)

Following the article I have done the following which has not solved my access problems:

Using synaptec I have Installed ssh on both machines. This should have resulted in both the server and the guest versions put on both machines.

Can not find the option to "Connect to server" in nautilus. 

What have I done wrong?

---

### Post by coldraven on 2013-10-20
> Can not find the option to "Connect to server" in nautilus.
Select from the file menu at the top of the screen File>Connect to Server or press Alt+F then S

---

### Post by Robbyx on 2013-10-20
I am stuck at trying to access the main computer from the TV connected one.  I can do it the other way around. I can see the name in the router and set up the server address via nautilus. The other direction is not working because I can only see an entry called unknown in the router via a cable connection.  I do have a firewall on the primary machine and wonder if that is blocking the details of its server.  I made it from a template provided by firewall builder.>  This is taken from the begining of the script: 
# Similar to fw 1, but the firewall is used as DHCP and DNS server for internal network.
# This firewall has two interfaces. Eth0 faces outside and has a dynamic address; eth1 faces inside.
# Policy includes basic rules to permit unrestricted outbound access and anti-spoofing rules. Access to the firewall is permitted only from internal network and only using SSH. The firewall can send DNS queries to servers out on the Internet. Another rule permits DNS queries from internal network to the firewall. Special rules permit DHCP requests from internal network and replies sent by the firewall.


Is it possible this is the reason why the details of the machine are not appearing in the router config page?

---

### Post by houstonbofh on 2013-10-22
You are making this massivly more complex than it needs to be.  You have ssh installed, correct?  First, try to ssh from the command line to each system.  "ssh user@192.168.x.x" with the correct IP address, of course.  If both work, then to the "Connect to Server" using IP address.  The router never has to enter into it.

---

