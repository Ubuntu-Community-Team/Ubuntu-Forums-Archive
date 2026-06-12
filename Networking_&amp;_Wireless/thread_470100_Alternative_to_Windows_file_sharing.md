---
title: "Alternative to Windows file sharing"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by drhiii on 2007-06-10
This is an endless blackhole of lost time I know, discussing Netbios.  I dunno how many people I have talked with over time, and just in the last week alone, who are having these network problems, irrespective of what they are running... NT, 2000,  XP, Vista, Ubuntu, RedHat, etc etc etc.

Here's the situation.  An associate has a networked enviroment.  He has a hybrid of 2000 and XP machines, and an NT machine (this is required to run a printer).  After endless cursing while trying to get things to talk to each other shares, some work, some don't, and all of it is sometimes anyway, it is futile. 

I have a wonderful, fantastic, Ubuntu box also on the same network.  It is the ONLY thing that I can rely on of course.  

My question is, anyone have ideas on how to share files in this environment... NOT using Netbios.  I am really interested in hearing if others have had similar file sharing problems and just resorted to another method.  I've considered setting up an FTP server, using Usermin that allows file transfers through a browser, using a browser to access an ftp server, using SSH to transfer files... all using the Ubuntu server as a file server.

But, has anyone else worked around Netbios and created a solution to share files across windows boxes without using windows file sharing.  Trust me, using Netbios is really broken.  

Anyone have a solution for this?

And, will tell you how dire it is getting... this is a print lab and there is a lot of WIndows specific stuff, but the guy is so agitated with how crummy Windows works for networking, he is considering letting me flatten everything, reinstall into Ubuntu clients, and then bringing up his windows apps too.  This is drastic and I don't want to go there, yet.... but still....   it is a twinkle in the eye at this point.

tx.  This is a great community and I have learned a tremendous amount by just hanging out.

---

### Post by scrooge_74 on 2007-06-10
I not sure if it is the solution for your problem, but this is my two cents.Maybe replace the NT machine with a Linux server using SAMBA for the shares.

Also your Netbios problems could be firewall related, to give you and idea you should read about the problems Ubuntu has when using Firestarter and SAMBA to share on a network.

Here is the[ thread]("http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138")

---

### Post by Gary.M on 2007-06-10
> **drhiii said:**
> Here's the situation.  An associate has a networked enviroment.  He has a hybrid of 2000 and XP machines, and an NT machine (this is required to run a printer).  After endless cursing while trying to get things to talk to each other shares, some work, some don't, and all of it is sometimes anyway, it is futile. 


Has this network got a server? A router? Something with a DHCP server? It should be very easy to make the machines talk to each other. I think you need to get to the fundamental problem.... the network and protocols, before adding fuel to the fire. This should be easy, even with MS products.

---

### Post by Mr. C. on 2007-06-10
Improperly configured Windows networking is challenging.

The trouble is likely a result of using a home-network setup, for an office/workgroup situation, and not understanding the requirements for successful Windows networking.  Without proper understanding and configuration of a PDC or Active Directory, your network will be subject to the poor network resource convergence.  Windows networking was designed to work with a PDC or equivalent.

If you properly setup a PDC (Windows or Samba) or Active Directory, you will reduce your troubles to almost nil.  If you use a peer-to-peer style of workgroup setup, you will have endless troubles as workstations are rebooted, shutdown, etc.

Since you have a NT system acting as a print server, configure it to always become and win the master browser election.  Also configure it to act as a WINS server.

MrC

---

### Post by drhiii on 2007-06-11
> **scrooge_74 said:**
> I not sure if it is the solution for your problem, but this is my two cents.Maybe replace the NT machine with a Linux server using SAMBA for the shares.

Also your Netbios problems could be firewall related, to give you and idea you should read about the problems Ubuntu has when using Firestarter and SAMBA to share on a network.

Here is the[ thread]("http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138")


Thank you for your response.  The problem here is the NT server is tied to a Frontier printer.  It cannot be changed out for something else.  Trust me, I would like nothing more than to move the NT out of the environment, but it is a fixed, proprietary application that is physically connected to the Frontier printer.

And, as it turns out, you are correct.  The new PC did have a firewall issue.  Once removed, it began working.  So you win the prize for speculating this.  

tx for your response.

---

### Post by drhiii on 2007-06-11
Tx everyone for your responses.  The core problem on the newest machine was solved by altering a firewall.  I'd instructed the person to do it, but a tech arrived for a different problem and he ended up disabling the firewall function and things began working.  

Still, I cringe when dealing with Windows anymore.  I handed an Ubuntu cient CD to my brother who has a home network and he had been yanking his hair out with all the problems.  He ran the system in test mode and was floored to find it 'saw' his entire network without having to do battle.   Needless to say, he is in the process of migrating over now.  I have an increasing number of people who are just fed up and making the change as well... to Ubuntu.

---

### Post by scrooge_74 on 2007-06-11
Nice to hear you made some progress.  I am also one of those that got fed up with windows.  All my PCs run Linux and I am starting to tell people not to ask me how to solve their problems in windows.

I am in the middle of making a mirror image of all my data on another PC (a couple of GBs), where else can you do this wireless, be able to still do work and surf the net at the same time without using to many resources.

---

