---
title: "linux to linux"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by jtravnick on 2008-02-22
ok so why is linux to linux network seem so hard to set up?

What I have is three systems:
My desktop running      UBUNTU7.10
wifes desktop running   Fedora8
laptop running              Fedora5

All systems can ping each other and see the internet. both desktops can see and access the laptop. No system can see a desktop. When I pull up network I have two icons one says SFTP File Transfer on localhost (this is the laptop). The other icon says Windows Network it does nothing.

So I know I must have done something to the laptop to get the network working on it but that was back when I first started using linux so have no idea what I did and cant seem to find anything on there that is different than the desktops. 

So until I can get the desktops to see each other I cant do anything with the laptop and I was really wanting to try ubuntu on it or at least update it since fedora5 is no longer supported.

So far I have tried Samba and NFS but neather seems to be working but than I don't seem to be setting them up right. Every where i look all I can seem to find is how to setup a network with linux to windows. Dont want that as the only system with windows is the laptop and I never boot to it anymore.

What I want right now is to be able to share files between all systems. Eventually I would like to be able to do admin. on all systems from my desktop but thats not as important right now.

Thanks
Jim

---

### Post by Discov3ry on 2008-02-22
You already picked a good approach with SMB and NSF. It's just a matter of configuring one of those the right way.

On the other hand you could opt for a temporary solution for sharing files using a SSH server and gFTP client on each of your workstations.

---

### Post by jtravnick on 2008-02-22
Not really sure witch way to go as I don't do a lot of networking. I do know I want what will work for the long haul. Don't think I need to worry to much about being able to connect windows to the network as of right now have no plans for adding windows to any of the systems. Only reason I still have it on the laptop is it came with the laptop and every now and than run into something that wont run on linux.

Right now I am trying to goggle fstp to see if I can find out what I did to the laptop to get that working. But I'm not totally locked into using that. I will also search more on how to set the others up 

But I've been getting kinda frustrated as I have never been able to get this network running right from day one. Even when I had fedora on all three systems and cant do anything with the laptop until at least the desktops see each other since the laptop winds up acting as a server.

Jim

---

### Post by jtravnick on 2008-02-23
So far this request for help has been looked at 33 times in almost 24 hours  and so far the only reply has been that I picked a good approach with SMB and NSF.

Is there nobody that can help me get it up and running? Everything I have read so far does not make much scents . The books I have here at home all cover fedora and those are not really helping. 

All I'm looking for right now is to be able to share files between systems it needs to be with a GUI as the wife has no idea how to use CLI.

Am I looking in the wrong place?

---

### Post by Rucas on 2008-02-23
Well i have a small home setup running 2 Ubuntu machines, and after much trial and error, finally got Samba to work.
I do believe that NFS seems to be the better option, but im still trying to get that one right,lol...
Anyhows. What i can now do in Ubuntu is share files, entire folder contents from machine to machine in my LAN and both still have their own access to internet and so on.

The steps: (have to be done on all machines)
Basically to first get SAMBA running in the Ubuntu Machine:
Got to System> Admin> Shared Folders: When you try to create a share it will tell you to install NFS/Samba if they are not already installed (if they are installed then this message would not appear.)

So you got Samba set up, now for the terminal:

1)type sudo smbpasswd -a username(username beeing the user of the machine you are on)
2)Terminal will ask for Sudo Password (ur password)
3)Terminal will now ask for a New Passw for the Samba share (this password can be whatever you want, but do remember it co's you will need it.)
4)Retype the passwrd
5)Thats it!!!
6)Reboot the machine.

Now on the Fedora Machines i suppose that the Procedure would be the same.
To share a folder:
In Ubuntu go into the Nautilus (computer) and basically if you right click on any foulder, it will pop up a menu and at the bottom there should be the option to share. this will then upon up a new dialog where you can choose NFS or Samba (choose samba) and also you can choose to give Read only access or full access by not selecting Read Only.

Now on the other machines you simply go to network and if your LAN is set up correct the Ubuntu Workgroup should show up. Click to see it and it will bring up a Login windon.
Username: The name of your Ubuntu Account
Password: The password you created in the Terminal for the SMB

If all is entered right, then you now have access to the shared folder/files from the Ubuntu machine.
Note after doing this once you dont need to redo the entire proccess again, from now on you simply create shares and they will be accesible.
Now to have Ubuntu access the other machine/s you need to do the same from each machine.
Hope this helps.

---

### Post by Eiríkr on 2008-02-23
For setting up NFS, one key is how NFS uses UIDs and GIDs -- the numerical values -- rather than the user and group names that we're used to seeing.  Thus, you can have the same user and group names on all machines, but if the numerical IDs don't match, any NFS connection attempt will fail, or at least behave strangely.  

SMB is great for Lin-Win networks, and can be made to work for Lin-Lin networks.  However, as some folks have noted, it's best to use a Unixy sharing service for Unixy clients, rather than forcing Unixy clients to jump through the many hoops related to Windows filesystems that are necessarily built into SMB.  :(

Have a look at the first half of [post=4387032]this post[/post] for advice on how to set up NFS with UIDs / GIDs mapped (so you don't have to go through the process of manually changing any UIDs / GIDs).  The second half of the post might be helpful if you hope to access NFS shares via a GUI (such as through Konqueror's [font=courier]zeroconf:/[/font] ioslave, or via Mac's Finder).  :)

Cheers,

Eiríkr

---

### Post by jtravnick on 2008-02-23
Well thats it I now give up. Everything I read makes less sense than what I read before it.

Tried doing the steps Rucas and seams to work lest dont get anything yelling at me until I try to see the desktop from another system.

Looked over the link that Eiríkr and I felt like I was reading greek. 

Guess the laptop will just have to run fedora6 forever as thats the only one any other system can see, and I have no idea what I did there.

---

### Post by blu3ness on 2008-02-23
Approaching it from a windows perspective as if you can make the desktops magically "see" each other is still a bit difficult on linux right now. The best way for LAN file sharing is NFS. But NFS requires you to have a central file-server (which is probably going to be your desktop), and through that file server, you can mount one of its directories like it's on your own hard drive through proper fstab configuration.

more information is probably on the ubuntu wiki, here's an official document tho:
[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

Good luck :P

---

