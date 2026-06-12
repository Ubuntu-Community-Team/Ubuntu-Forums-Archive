---
title: "Domain setup"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by chucklesk on 2006-12-17
Ok here is my situation. I work for a small school with 8 windows workstations (win 98, 2000, xp). I have convinced the school administrator to let me setup a domain and convert all the workstations to Ubuntu. I want to do this for a few reasons first; I want to have a centralized place for adding user’s accounts (I’ve been adding all users to every computer on the workgroup). Second I want users to be able to login to any computer on and have access to saved preferences (desktop background, application launchers, gnome panels, that kind of thing) and files (their /home directory). I want to be able to automatically backup their /home folders as well. Mostly I just want to learn about this stuff. 

Right now I’m thinking at least one of the machines will need to stay windows for at least a couple of weeks. It is running QuickBooks and I will need to get it running on Linux before I can get rid of windows. Crossover looks like a good way to go, but would Wine work just as good? This particular machine is running XP home so it can’t join a domain anyway. I would like to setup a domain that is capable of connecting windows and Linux clients since some of the staff have windows laptops they sometimes use.

 It’s not a huge deal to have a mixed domain, but it would be nice. If it would make things to complicate to start out I would rather just stick to Linux. I keep getting confused about how to setup the domain and join it with Ubuntu. I’ve been trying to use samba which I know is for windows, but I don’t know what else to use.

I’m going to try and get it working in a test situation first. I would also like to eventually setup ftp, DNS (for the local domain), DHCP, and apache.

My main question is what I should use for the server software? Do I need to setup samba as the domain controller for authentication? If so how should that work for the Linux workstations? Would they still be able to logon to any machine and see the same things (desktop, files /home folder) and still have the same software in their path? Should I use NFS? Do I need both to run windows and Linux on the same domain? If there are any good articles, books, or websites for learning how to configure this kind of network i would also like to know about those to.

---

### Post by koenn on 2006-12-18
That's a big question, and answering it to completeness would be like writing the ubuntu domein mini-howto. furthermore, your choice of terms and the way you prase your questions suggest that you have a general idea of what you want to accomplish (and it's a good idea at that), but you turn to sollutions that you don't fully understand. 
Like, you want to be able to manage your users in a centralized manner (very good idea from a sysadmin's point of view) but while microsoft promotes the Active Directory Domain to accomplish that, it is not necessarily the only sollution, and trying to mimic it in a Linux environment is *not necessarily* a good idea. Then, giving users access to the same home directory no matter where they log on is also a good idea. In a windows environment this is called 'roaming profiles' and they are usually implemented within a AD domain - but only because they hardly make sense without a domein (local accounts don't roam). 

Here are a couple of pointers to get you going. You'll have to read and experiment a lot, and if you have questions, come back and we can have a further look. 

1-
Try and see of edubuntu gives you what you're after. It is ***not*** a domain-based sollution, rather a server-based sollution ("Terminal Server"). It does offer centralized user management (user accounts only exist on the server), a consistent user experience (home directories, including both user files and preferences, desktop settings etc  are stored on the server, the clients mount and access them via -i thing- NFS : Network File System), and, as in all TS sollutions, you also don't need to manage computers because they'd be thin clients : all configuration lives on the server, all software runs of the server, etc. 
Obviously, it's also dead easy to do a centralized backup : there's nothing else to backup except the server.
An Edubuntu server is almost just as easy to set up as a Ubuntu desktop, and for testing/experimenting you can easily run an Edubuntu server and one or a few thin clients in VMware (I've tried it on a 1.8 Ghz CPU, 1GB RAM and 4 GB free disk space  :-) )

2- The alternative sollution is to mimic a Microsoft AD domein with roaming profiles etc. Where a Windpows Server will come with most of the tools and features to set this up out of the box, you'll need to choose and combine several Linux programs to get something similar in a Linux environment

a/SAMBA is basically a 'Windows compatible' file server, i.e. it makes directories on a server accessible as "Windows shares" i.e; using smb protocol. Both Windows and Linux systems (with smb client) can use its shares.
 Samba was further devellopped to act as an "NT4" style domain controller so that would give you centralised user account management ("domain users"). I have no experience with it but you may wan't to check whether having a SAMBA domain controller will allow users to log on from any workstation - you *may* still need unix accounts on those machines as well - I'm not sure. 

b/ you'd need a sollution for the roaming profiles. any form of access to directories on a remote system would do (NFS, Samba share, ...) but you'd have to learn how to mount those as /home/ for the logged on user in question. In a mixed domain, you'd need 2 sollutions : the linux machines expect a home with both files etc and user specific preferences and configurations settings, while windows expects separate 'home' and 'profile' folders. With windows, you'd be limited to SAMBA, with linux, you can also look into other networked filesystems.

c/ for users to have the same software in their path no matter what machine they log on to - having a user-specific PATH, in addition to the systemwide PATH,  can probably be accomplished by editing the users profile or .bashrc file  (in home) but it wouldn't make much sense if the software is not present on the machine they log on to. This would only work if you have standardized work stations.  That's the same in a Windows domain, exept that they have "On demand" installation of software (with Active Directory Group Policies), which does not exist for Linux, at least not to my knowledge. (And  in a Windows environment, I'm not even sure it's that good an idea). 

d/ Where windows revolves around the registry , linux is much more based on the presense of config files and the execution of scripts. That, combined with the unix ways to mount remote filesystems **into** the local filesystem (as opposed the Windows way of  *adding* drive letters / shares to a file system) has probably everything you need to set up a centrally managed network - but it's going to take some work and creativity to pull it off.

And to answer your question; the software you require on your server depends on which way you want to go and how you want to implement it. 

(And *do* have a look at Edubuntu. It may already have all you want.

---

### Post by chucklesk on 2006-12-18
Thank you for taking the time to answer my questions. After reading your post and looking around more I've decided to use NFS. I picked up an O'Reilly book on NFS and NIS and I will have a look at Edubunt also. Thanks again.

---

