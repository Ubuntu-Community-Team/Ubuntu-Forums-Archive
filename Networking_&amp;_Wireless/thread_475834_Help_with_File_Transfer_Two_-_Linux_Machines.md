---
title: "Help with File Transfer Two - Linux Machines"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by Ingla on 2007-06-16
Hello.

I have never set up a network between two Linux machine (mostly need file transfer). After checking the Internet, I'm left with various possibilities, but need a bit of help getting this to work.

I have three computers:

Computer 1: 2 hard disks. One running Ubuntu Dapper, one running Windows XP.

Computer 2: 2 hard disks. One running Xubuntu Edgy, one running Windows 98 (older machine so keeping OS's          light).

Computer 3: One HD running Windows XP

All three are networked OK on Windows.

Not long ago, with the help of someone on this forum, I set up a network from Computer1, running Dapper, to Computer 3 and can transfer files either way. This was done using smbfs plugin, and all transactions are initiated from Computer 1.

Now, I want to transfer files between Computer 1 and Computer 2, while both are running Linux. 

I set up shared folders on both. On Computer 1, in Network Servers, I can see the shared folder on Computer 2 under Windows Network. I cannot transfer anything either way ... access denied. On both machines, the shared folder is read only and the owner is "unknown".  This is also true of the shared folder on Computer 3 (Windows), but that doesn't prevent transfer ... Linux may differ because of permission issues??

On Computer 1, the folder is shared by NFS, and on Computer 2 by SMB. I have no option to change computer 1 to SMB (greyed out). When I changed Computer 2 to use NFS, I could no longer see its files while I was on Computer 1 ( the folder is there, but with no contents).

Interestingly (to me, as a newbie at this), the connection with the Windows machine just worked (already had shared folders on the windows machines and they both transfer to and from Computer 1 under Linux).

I don't know why I can't set Computer 1 to use SMB (maybe that would mess up my connection with the Windows box?), or why I can't see Computer 2 when it's set for NFS (something not installed?). Also don't know about ownership and permissions. As I say, I've never done this before.

Can someone tell me how to get this working (even if only initiated from Computer 1) between the two Linux boxes (WITHOUT ruining my connection to Windows)?

Any help appreciated.

Thanks very much.

---

### Post by bigken on 2007-06-16
sudo aptitude install samba 

sudo smbpasswd -a (your name )

sudo smbpasswd -e (your name )

just right click the files you want to share

---

### Post by Ingla on 2007-06-16
Thanks for the reply.

Please remember I don't know what I'm doing with this yet.

Do I do aptitude install or apt-get install?

Do I run these commands on Computer 1 or on both machines? 

I put in my user name twice?

I right click on a folder to share in both machines ... or did you mean right click on individual files each time? 

From where do I right click ... Network Servers? Shared Folders? Nautilus?

Sorry to be so dumb.

Thanks a lot.

---

### Post by bigken on 2007-06-16
you only run the commands on the linux machines 

you will find your shares in  places network ;)

---

### Post by Ingla on 2007-06-16
Thanks.

I enter the same user name twice?

---

### Post by bigken on 2007-06-16
> **Ingla said:**
> Thanks.

I enter the same user name twice?


yep u got it 

you may need to reboot

---

### Post by Ingla on 2007-06-16
OK, I did it all. Terminal seemed to indicate everything go.

I still cannot send a file from Computer1 to Computer 2 ... access denied.

I WAS able to pull a file from Computer 2 to Computer 1.

The shared folder on computer 1 is now SMB. Computer 2 now shows two shared folders of the same name. Both set themselves for NFS whenever  I close the GUI. I change them to SMB, but it won't save. Is there some way to set the shared folder to use SMB with the command line?

Computer 2 is running Xubuntu (Xfce instead of Gnome) and I can't even find how to view Computer 1 to try to pull a file over from there. There doesn't seem to be any equivalent of Network Servers. The file browser is Thunar and I can't find anything like that there either.

Any ideas?

---

### Post by link141 on 2007-07-11
[quote=Ingla]Computer 2 now shows two shared folders of the same name. Both set themselves for NFS whenever I close the GUI. I change them to SMB, but it won't save.[/quote]
You don't have samba installed on Xubuntu (or some other packages are missing, etc.).  How exactly did you view the shared folders?  Are they local mount-points on your machine?  How were you able to set-up Samba shares on Computer 2? 

[quote=Ingla]Computer 2 is running Xubuntu (Xfce instead of Gnome) and I can't even find how to view Computer 1 to try to pull a file over from there. There doesn't seem to be any equivalent of Network Servers. The file browser is Thunar and I can't find anything like that there either.[/quote]
The equivalent of Gnomes "Network Servers" (now I don't use Gnome, so I assume your talking about where you set your shared network folders) in Xfce is called "Shared Folders" and it's located under "Applications->System-> Shared Folders".  

These instructions have some overlap with how-to I'm going to point you to  at the end of my post, so read both, and decide what to do.
  
When you open the "Shared Folders" dialog, it will ask you for your password, inform you that you don't have NFS or Samba installed, and ask you if you want to install them-- check the samba box *if you want to be able to access your shares from computer 2 via SMB on the other computers on your network.  Installing a samba server will give you unnecessary  overhead.  The samba server is required for making the files on computer 2 available via SMB*.  It will then use synaptic to install them automatically for you, if you chose to install one of the packages.  You will then be provided with the settings dialog for shares.  Click on the add button, and specify the folder you want to share, tell it to share it using "Windows (SMB)", name the share, and uncheck the read only box if you want to be able to modify the share from your other computers.  Click ok, and click on the windows tab.  Enter your domain, and make sure "wins server" is checked.   Click close, and your Xubuntu box should be visible from Computers 1 and 3 8-).  

Thunar can't view Samba shares out-of-the box like Konqueror can, but you can mount them to a local folder on your filesystem using a program called "fusesmb" (read following link for more info), or you can use a program called pyNeighborhood to view the Samba shares on your network.

Here is the promised how-to that explains setting up Xubuntu to read Samba shares through Thunar: [thread=304131] How to: Xubuntu - Thunar Native Windows Network Browsing[/thread]

If you already have Computer 1 shared with windows(comp. 3) properly via Samba, you should  be able to see it from Computer 2 (along with the shares on Computer 3) with no extra effort when you setup fusesmb.  

I was really tired when I posted this, so it is probably poorly written and hard to follow.  Please leave a post if anything doesn't make sense to you.

p.s.:It's funny, I recently decided to setup shares between the three computers in my house:
Comp. 1 Kubuntu only 
Comp. 2 Xubuntu only
Comp.3 winxp only

---

