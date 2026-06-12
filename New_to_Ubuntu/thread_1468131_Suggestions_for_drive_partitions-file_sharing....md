---
title: "Suggestions for drive partitions-file sharing..."
date: 2010-05-01
forum: New to Ubuntu
---

### Post by jfls45 on 2010-05-01
I would like some suggestions as to the best way to setup home network file sharing on my Ubuntu Server. I had MS Home Server installed and decided I wanted to try Ubuntu but having a little trouble making the transition. I have been googling for answers but don't have hours to spare to do this... My server is simply a  desktop with the following drives:

80GB  (currently have Ubuntu Server (added desktop gui)
160GB  (blank)
500GB  (blank)

500GB ext usb drive   (was my active file share under Home Server)
1TB ext usb drive  (I used this as a server backup-made backups of the 500 GB drives)

Here is my dilemma, the 1TB has backups of family photos, etc.. priceless, don't want to lose. The 500GB has share folders from the Home Server. My thinking is setup the 500GB internal and copy the shares from the 500GB ext drive. 

What is the best way to setup the 500GB drive? gparted or does Ubuntu have an utility built in to do this?

I don't mind doing a little reading just point me in the right direction. 

thanks

jte

---

### Post by Naitsirhc Hsem on 2010-05-01
gparted is good for formating drives. gadmin-samba is good for setting up samba shares

---

### Post by jfls45 on 2010-05-01
Whats your thoughts on saving a master copy of all files in NTFS EXT3 or 4? Is there any known issues backing up a Linux file system into NTFS drive?

I'm still in the experimental phase here so not 100% sure I am ready to go all Linux... my concern is being able to restore photo backups in case I screw up something, like I did in Home Server. 

What are your thoughts on all of this?

---

### Post by jfls45 on 2010-05-01
I download gadmin-samba   tried to open it.  get a "Gtk Warning, cannot open display   i'll try rebooting

---

### Post by Naitsirhc Hsem on 2010-05-01
were you in the gui?

---

### Post by jfls45 on 2010-05-01
No, I went ctrl alt F4   the terminal   i try sudo gadmin-samba   and still get cannon display error

what gives?

---

### Post by Naitsirhc Hsem on 2010-05-01
I don't know.  you are in the ubuntu-desktop gnome environment?

---

### Post by jfls45 on 2010-05-01
i was doing it from the black screen   not the gui    I didn't load the gnome version of the gui though   should I have? 

tell me how to do it from the gui...

---

### Post by Naitsirhc Hsem on 2010-05-01
if you installed ubuntu-desktop via apt-get(apt-get install ubuntu-desktop), you can log into the gui environment(gnome).  from there under either system > administration or Applications> System Tools  you should find gadmin-samba.  this will open up  a gui program for all of the samba options you need to configure, users, shares, ip addresses, dns servers, etc...  if you need any help setting up any of the options, I have become fairly acquainted with the program and samba configuration and would be willing to help with any problems you encounter.:)

---

### Post by jfls45 on 2010-05-01
Yes I could use some help. 

Here is my Windows setup:

Workgroup Name: JTE-NET
IPs are Static, DHCP is turned off in Linksys router.  Each PC has this 192.168.50.xx, 255.255.255.0 and I use the OpenDNS 208.67.22.222  208.67.220.220

I tried making some changes in Gadmin but still seeing "Workgroup" coming up in my windows network.

Is there a way in Linux gui to create a partition and format it, right now I have two internal drives that are "unallocated" from the initial install. Whats the best way to go, gparted? or someother utility in the gui I am not aware of?

thanks for all your help, most appreciated...

Jeff

---

### Post by Naitsirhc Hsem on 2010-05-02
Gparted is correct.  I think workgroup is defined on the first page, it is also on the last page in the smb.conf.

---

### Post by Morbius1 on 2010-05-02
I think it's time we get some facts so we can see what's up. Please post the output of the following commands:

```
net usershare info
testparm -s

```

---

### Post by Morbius1 on 2010-05-02
I've read thru your post again and I have more requests, sorry:

I don't know where you are in your partitions either, so if you could post the output of these commands it would be helpful:
```
sudo blkid -c /dev/null
cat /etc/fstab
mount

```One last question. How complicated are your sharing requirements on this server? Will all shares allow guest access across your LAN? Are you going to require usernames and passwords to access specific shares?

The reason I ask is that depending on your needs you may not need another application to create shares - you could do it from Nautilus ( assuming you're using Gnome - which isn't real clear either from your posts )

---

### Post by jfls45 on 2010-05-02
Ok, here is where I am at. I have the latest download of Ubuntu Server 10.04 installed.  I have not installed a gui for it. I would like to be able to do this from command line if possible. I will be running this server headless but I would like to be able to login remotely if necessary. My hunch is I will need a gui to be able to log in remotely?

I have three Internal drives in my server. 80GB, ext4 formatted, this has the server os loaded on it. The other two drives are 160 and 500GB formatted ext4 as well but they are empty. I have two Ext USB drives with all my stuff I don't want to lose. Both are formatted NTFS. So I need help but keep in mind I am going to run the server headless, but would like to login remotely if necessary without a gui. 

My other home computers will dual boot windows or linux, so I need to know what is the safest and best way to format the two drives in my server. ex4 or ntfs?  

Will I be able to run server without a gui as headless?  

I just installed Samba4 and starting down the learning curve by googling how to set it up.  
My file sharing is simple. Nothing special within the Lan, but want to keep hackers out from the outside world. I use Logmein on my windows computers and may want to setup a remote login for the server at some point. Right now my big this is setting up the drives, shares, and going headless. I would like to be able to just turn the thing on and not worry about it. 

thanks for all your help...

jte

---

### Post by Naitsirhc Hsem on 2010-05-03
for headless servers, use ssh remote login for the command line.  remote login gui needs a gui. samba can set up passwords and logins.  ext4 or ntfs will both work.

---

