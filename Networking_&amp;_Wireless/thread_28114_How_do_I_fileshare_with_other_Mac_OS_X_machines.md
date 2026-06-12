---
title: "How do I fileshare with other Mac OS X machines?"
date: 2005-04-18
forum: Networking &amp; Wireless
---

### Post by Tofu on 2005-04-18
Hi there,

I'm new to Linux and Ubuntu.

I've got a PowerPC with Ubuntu, and also a Mac OS X machine connected via a home router. I'd like to be able to share files between the Ubuntu machine and the Mac OS X machine.

There are no Windows machines on the network.

What method should I use on the Ubuntu machine?

How should I set up the OS X machine to see it?

Both machines are surfing the web OK, but not yet file sharing.

thanks.

---

### Post by diebels on 2005-04-18
install nfs-kernel-server on the ubuntu machine
define directories to share in /etc/exports
se this page [http://sial.org/howto/osx/automount/](http://sial.org/howto/osx/automount/)

---

### Post by Tofu on 2005-04-18
Thanks, diebels, that's great information and a really useful link. I'll give it a go right now.

---

### Post by luna6 on 2005-04-19
Samba works fine for me between my powerbook and Ubuntu servers...never could get nfs working correctly....will try again in the summer

---

### Post by Tofu on 2005-04-19
[QUOTE=luna6]...never could get nfs working correctly....[/QUOTE]
Looking at that website (linked above) it baffles me why NFS should be so difficult to set up on the Mac side, considering its UNIX heritage.

---

### Post by Tofu on 2005-04-19
When networking OS X machines to OS X machines via a home router, do they use SMB/Samba to do that?

OS X -> OS X seems so easy.   How is that easier?  OS X & Linux are both UNIX.

---

### Post by mike3k on 2006-10-01
> **Tofu said:**
> Looking at that website (linked above) it baffles me why NFS should be so difficult to set up on the Mac side, considering its UNIX heritage.

It's not difficult - there's just one trick: you need to specify 'insecure' on your export. Once you do that it will just work. You can fine-tune it a bit more. 'async' improves performance dramatically, and I find that I also need to specify no_auth_nlm or some applications will complain about locks not working.

---

### Post by sfwasabi on 2007-02-21
I have spent about 2 weeks trying to fileshare from my mostly Mac Workstations to an Ubuntu 6.10 Edgy Server which is replacing Windows Servers. My main Mac runs Tiger and is an Intel Mac. The others are PowerMacs on Panther. 

I could never get Samba to work or NFS. I have 2 large external drives, 1 USB Fat 32 for Network Files, and 1 Firewire NTFS for Music and Video.

 I FINALLY got NFS to work, just to be disappointed when it wouldn't load the NTFS external Firewire drive. I got it to work with my external USB drive, and jumped up and down when I could rename files, delete files, and download them using NFS, but that turned to pain when I couldn't upload files.

Personally, I can use SSH or command line, but I can expect others on the network to use anything other than a mounted drive.

BUT there is HOPE! After weeks of trying to accomplish this one task, and hours and nights spent tearing my hair out, I found MacFuse at the Google Code project.

MacFuse makes it so that you can connect to an SSHFS server. There are 2 downloads:   	MacFUSE-Core and sshfs. MacFUSE installs the guts. sshfs is a GUI window where you put in the ip address of your server, your username, and the folder that you want to mount, and it will connect and mount it as a drive on your desktop!

On the Ubuntu side, you have to install the SSHFS server. There is a great tutorial at:
[http://www.ubuntuforums.org/showthread.php?t=103860](http://www.ubuntuforums.org/showthread.php?t=103860)

The beauty of it all is that it WORKS! Also, it's using SSH so its encrypted. Finally, it only took me about an hour to set up. I hope this helps everyone who has been killing themselves trying to set up an Ubuntu Server with Samba or NFS and trying to get OS X Macs to connect to it.

---

### Post by sfwasabi on 2007-02-23
Sorry, I guess I was a little quick in my excitement with my last post. MacFUSE and SSHFS ARE awesome! They work great. Install quickly with little pain, and you can network Macs to Ubuntu in about an hour of setup and configuration.

HOWEVER...

MacFUSE is OS X Tiger 10.4+ or greater only, and I only have 1 workstation on Tiger, the rest are on Panther, and Leopard is coming out in 6 months or so, so I'm not going to spend the money upgrading OS X until Leopard is out.

SO, what's a guy to do?

I was able to set up Apple File Sharing (Netatalk) on the Ubuntu server, so you can just go to Go > Connect to Server in Finder, enter afp://YourUbuntuServerIpAddress, enter your Ubuntu User Name and Password, and you're good to go.

It takes a little more set up than MacFUSE/SSHFS, probably 2 hours the first time, but it actually works, unlike NFS and Samba - at least I couldn't get them to work for me and I spent weeks trying.

There is a tutorial here at ubuntu forums here, but it doesn't install secure password transmission. There is a short, step by step tutorial at:
[http://technically.us/n8/articles/2006/11/16/a-year-of-plaintext-afp-passwords-is-enough](http://technically.us/n8/articles/2006/11/16/a-year-of-plaintext-afp-passwords-is-enough)

If you follow those few steps, in about 20-30 minutes you will have Netatalk working on Ubuntu and you will be able to log right into your Ubuntu home folder. 

Then you have to configure your shares. Since, by default, it will allow you to connect to your home folder, and you have ownership and access to your home folder, I found it easiest to just put links in the home folder to the folders on the drives on the server that you want to connect to. You can probably do this in about 10 minutes. Here is the syntax:

From Applications>Accessories>Terminal, navigate to your home folder: cd ~
Then create a link to the folder or file that you want to access: sudo ln -s /path/ActualFolderNameOrFileName LinkNameToThatFolderOrFileName

This will create a link (Alias/Shortcut) to the /path/folder that you want to share and when you connect to your home folder, you will find a folder there with the Link Name. Clicking on it will give you access to that Folder or File that you created the link to. If its a folder, it will also give you access to all the folders and files beneath it.

Obviously, your login user needs to have permissions to access all the files and folder, or else...

For some reason I couldn't get links directly to the root of a hard drive to work. When I would click on them, they would disappear. Links only worked for me if I linked to a folder below the root of the hard drive. There are two solutions that I know to this problem. First, you can create a folder in the root of the hard drive, and move all of your subfolders into this Main folder, then you could make 1 link to this Main folder and have access to all of the subfolders or Secondly, and what I did, since the root of the hard drives that I wanted to share only had a few folders, and no files that I wanted to share, in my home directory I created a folder for each drive:
cd ~
sudo mkdir HardDriveName01
sudo mkdir HardDriveName02

Then I navigated into the folder that I made for the hard drive: cd HardDriveName01
and created a link to every folder in the hard drive that I wanted to share: sudo ln -s /path/ActualFolderNameOrFileName LinkNameToThatFolderOrFileName

That way, when I connected through Finder's Go To Computer in OS X, and connected to my home folder, there was a folder in there for every hard drive that I wanted to share, and a link to every root folder on that hard drive, and since all of the subfolders are accessible, it gives me access to the whole hard drive without having to wade through more configuration files.

Also, both hard drive that I'm sharing are external. 1 USB Fat 32 and 1 Firewire NTFS, so that may be problematic trying to share in itself, but by linking to them I rid myself of the configuration hassle.

If you want to share the drives directly or spend more time noodling with configurations, there's a good quick explanation of how to share drives at:[http://gentoo-wiki.com/HOWTO_Share_Directories_via_AFP#Configuring_AFP](http://gentoo-wiki.com/HOWTO_Share_Directories_via_AFP#Configuring_AFP)

And for tweakers, the whole manual with all the options is available at:
[http://netatalk.sourceforge.net/2.0/htmldocs](http://netatalk.sourceforge.net/2.0/htmldocs)

---

### Post by rbarrimond on 2007-03-06
I install netatalk on my ubuntu Edgy server and have yet to connect.  Keep getting connection failures despite providing proper credentials.  (I'd be happy with cleartext passwords if they didn't fail!)  Did a plain jane apt-get install and have only disabled atalkd and papd in the startup script since my network is strictly TCP.  What's gives?

> **Connection Failed**

Unknown user, incorrect password, or login is disabled. Please retype the name and password or contact the server's administrator.

---

### Post by edward4130 on 2008-01-29
rbarrimond-

I to have had the same issue, on both a edgy as well as a gutsy server.  Mac sees and tried to connect but just says the unknown user /pass and it is not the case.  I can connect and fileshare the other way around but not the way I would like with the linux being the server.  Did you get this working?

-Edward 4130

---

### Post by edward4130 on 2008-01-29
On a humorous note I can sit at the mac and share the mediacenter's screen (Feisty) and it works but I cant share the frikkin' files!! Aint that a Beeach!

-Edward 4130

---

### Post by sastian on 2008-02-07
> **mike3k said:**
> It's not difficult - there's just one trick: you need to specify 'insecure' on your export. Once you do that it will just work. You can fine-tune it a bit more. 'async' improves performance dramatically, and I find that I also need to specify no_auth_nlm or some applications will complain about locks not working.

you sound like you have some experience with this.. could you elaborate on the steps someone with out your experience should take to accomplish what you speak of?  :)

---

