---
title: "What a mess I made of my Ubuntu Server 9.10"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by ehlenfeld on 2009-12-20
I'm not the brightest bulb by any means when it comes to Linux. I've used Windows for years but with increasing dissatisfaction in their product and even more so in their pricing. The last upgrade for Windows and Office cost more than my PC, that's just not right.

Anyhow my problem started by installing SAMBA in an attempt to share physical disks between virtual PC's having Windows 7 and Windows Vista, the host is Ubuntu 9.10 obviously.

I made several changes to users and groups but could never share a physical hard drive. I decided to start from scratch so I removed anything having to do with SAMBA or networking and that is where I made my mistake.

The gnome desktop was also removed along with other critical files for running Ubuntu.

I did manage to get a XUBUNTU desktop installed but the core files are a mess and I can't open VMplayer or VMconverter Standalone or any of my virtual PC's because the kernel headers need rebuilt, whatever that means.

I've tried repairing packages but no help, I used the 9.10 server dvd and tried rescue a broken system and that proved useless (for me, I just don't know enough about the terminal, give me a DOS shell and I know my way around, the language and commands in Linux are cryptic to me).

So anyhow I have a broken UBUNTU 9.10 server installation that has a lot of important information in it and things tweaked to just how I like them. I hate to just trash the whole OS because of that.

I set up another Ubuntu 9.10 Server and did manage to transfer a lot of my important documents but since that system had ownership of some disks I can't access them in this new OS and I'm not about to start making the same mistakes of changing user and group policies.

So, I need to know how I can salvage my old Ubuntu and continue using it (part of the reason for that is that I also activated Windows 7 and Windows Vista and Microsoft Office on those virtual machines and I'm not sure if that will transfer to the new Ubuntu OS or if Microsoft spyware will sniff out that it is on a different drive and require a new license).

Any thoughts would be appreciated.

---

### Post by Temposs on 2009-12-20
Most settings, and your user data, are kept in the home directory. Generally when you want to transfer things from one install to another, you just transfer the entire home directory(including all the hidden files and folders that start with a dot). 

I would not bother transferring anything else.

---

### Post by indytim on 2009-12-20
I'm a little bit confused by your original posting.  One the one hand you say you broke Ubuntu Server.  Later you're referencing Gnome.  Are you saying that you broke your server(s) installed within a desktop environment (Gnome..)?

Looks like you smashed your installation pretty well.  As was mentioned above, you should see if you can copy the contents of "/home" to a safe off-line storage area.  This can be done by booting to a LiveCD and mounting the partition that contains your "/home" and copying ALL of the contents to, say a usb stick or a CD etc.

Beyond that, I would recommend that the easiest course for you would be to go through a complete re-install.  Do the "Manual" partition thing when the installer comes to that point.  Identify your existing partition(s) to install to.  Make sure that you select the "format" checkbox for the "/" partition as this is a requirement of the installer.

Once you have successfully re-built your core installation, then mount the device that you stored "/home" on and copy / overwrite the contents to your new "/home".  Re-install any special apps you post installed from your original installation and you should be good-to-go.

IndyTim

---

### Post by ehlenfeld on 2010-01-01
I'll try to clarify IndyTim;
I first installed Ubuntu desktop 9.10 and later upgraded to server 9.10.
On the original install of the OS it was on a second hard drive, I wanted to keep my Windows installations apart in case of problems with GRUB.
Anyhow, I used VMWare to migrate my Windows to a virtual machine which would run under Ubuntu server 9.10. By the way, Microsoft's spyware detected that the installation was not on the original machine so I had to get new license keys for Vista Ultimate and MS Office 2007 so anyone wanting to do this should keep that in mind.
I wanted to be able to share disks with the host (Ubuntu) and the virtual client (Windows) and thought SAMBA would work nicely. As it turned out it is more complicated than I want to try and set up and beyond my abilities as I am just starting with Linux.
So, I decided to "uninstall" SAMBA using synaptic package manager so I entered SAMBA in the search, marked all that came up and clicked on Apply. When I restarted Gnome was pretty much wiped out which is when I did "sudo apt-get install xubuntu-desktop" thinking I might repair Gnome.
Gnome never would install again, I kept getting an error saying that it was missing some file but that it would not be installed. So, I gave up and did a fresh install and transferred all the documents I needed from the busted Ubuntu to the fresh Ubuntu.
I still can't share files between the host and virtual clients, I can see the host in the virtual client network but it won't let me access anything.
I've tried setting up so that a user on the virtual client can logon to the host and reading the documentation on setting this up is very involved, for me, so I decided to give up.
I can get access to the drive I want through VMWare Workstation 7 because it allows you to add a physical drive, of course the problem with that is that the host can't use it then.
If anyone has a simple explanation on how to set this up, remembering I'm a long time Windows user, then I would appreciate your help.
For now, I just mount and unmount the drive as needed which tends to be a hassle but one I can live with as long as I don't have to worry about the OS getting messed up again.

---

