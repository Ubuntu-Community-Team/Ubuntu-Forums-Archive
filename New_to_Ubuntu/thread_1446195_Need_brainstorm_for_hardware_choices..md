---
title: "Need brainstorm for hardware choices."
date: 2010-04-03
forum: New to Ubuntu
---

### Post by LoveJoyDK on 2010-04-03
Hi all.
 

 I am very new to Linux / Ubuntu, but not so new to networking and domain in Microsoft systems.
 

 I want to make some use of Linux/Ubuntu at home for private use, but know no people with insights in Linux. So am hoping to lend some eyes and ears here, for some Oh NO and Oh YES comments on my plans and ideas.
 

 I want to lay out what I have of dreams for the use of Linux. Tell what I have learned and done so far. And I hope to get some reply to help be know where I go wrong and where I go right.
 

 I hope I am doing this the right place. And thanks in advance.
 

 

 What I want to end up with:
 

 A Linux/Ubuntu server as PDC, file-server and DNS primarily.  
 With loads of space on it disks for filesharing on the local LAN.
 

 Window and Ubuntu desktops on the LAN able to use the shares on the Linux/Ubuntu server
 

 Also thought of making it a firewall and internet sharing box. But I think it would be unvise to make a PDC and file-server to be the front end box to the internet.
 Comments welcome on this as on everything else here.
 

 For now I have 3 CPU/motherboards
 

 1: Intel E8500 8GB DDR. Windows 7.  
 Used for windows gaming, movies, Vmware, 3D rendering and normal internet activities. Reading news/youtube etc.
 Motherboard has 4 SATA connectors
 

 2: AMD Athlon 64 X2 4 GB DDR. Windows 7.  
 Used for movies, internet programs/Downloads AND windows gaming when I have guests visiting and we play on LAN.
 Motherboard has 2 x 4 SATA connectors
 

 3: AMD Athlon(tm) 64 Processor 3200+, 1 cores. 1 GB DDR.  
 Was laying around and considered used for a media center.  
 Motherboard has 2 SATA connectors.
 

 I have now tried installing Ubuntu desktop and server on VMware machines. The desktop version I have not been able to make a working CD to install from. But the Ubuntu server I manage to get a disk working. I tried  to install it on machine 2 and 3.
 On machine 2 I added Ubuntu desktop.

 On machine 3 Samba is now running the PDC and file-server. DNS runs fine as well.
 The PDC was made following these two links.  
 

 [http://www.steve-lacey.com/blogarchives/2006/11/linux_as_a_wind.shtml](http://www.steve-lacey.com/blogarchives/2006/11/linux_as_a_wind.shtml)
 [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)
 

Fitted there setups lightly to fit me using Ubuntu server resources on Ubuntu.com. Webmin is running also.
 My tests with adding a VMware XP machine works as a charm except:
 

 In smb.conf there is:
 

 

    [FONT=Courier New, monospace][SIZE=2]#logon script = scripts/logon.bat[/SIZE][/FONT]
    [FONT=Courier New, monospace][SIZE=2]logon path = \\%L\profiles\%U\%a[/SIZE][/FONT]
    [FONT=Courier New, monospace][SIZE=2]logon drive = H:[/SIZE][/FONT]
    [FONT=Courier New, monospace][SIZE=2]logon home = \\%L\home\%U[/SIZE][/FONT]
 

 Can anyone tell me what the function of ”logon drive = H:” should be?
 Where can I find more about what the %L %U and so on stands for.?
 

 Have not yet come to testing with a Win 7 machine. But what I realy need comments on now, comes here.
 

 My dream is a box like this
 

 HD1  
 sda1    /boot        50 MB
 sda2    /swap        1 GB
 sda3    /        50 GB    
 sda4    /home        Rest of drive 100+ GB
 /home will hold the user profiles and private shares  
 

 HD 2 – 5 (4 x 1 TB)
     RAID (RAID 5 if possible) (Linux soft RAID if needed)
 sda5        /share        about 3 TB with RAID 5
         /share/*     (*different shares I  would want on my LAN)
 

 Comments needed on the sanity about this setup please.
 

 

 Here is my first problem. Machine 3 has only 2 SATA connectors. Not 5.
 

 I have a RAID controller a FastTrak S150 SX4-M  
 [http://www.promise.com/product/product_detail_eng.asp?segment=RAID%20HBAs&product_id=124](http://www.promise.com/product/product_detail_eng.asp?segment=RAID%20HBAs&product_id=124)
 

 But besides it only has SATA-150 I am not sure how it will run with 1 TB disks. And what little I have found about this controller and Linux it does not seem to work well. Specialy when it comes to 64 bit. So my plan about adding the controller to machine 3 and get 4 more SATA connectors seems to fail.
 

 I then thought of buying some cheap CPU and motherboard with more SATA connectors. But it seems like the price on CPU/RAM/Motherboard for old stuff with enough SATA connectors is not that far from new-on-the-market CPU/RAM/Motherboard. So the idea now is to buy a new set for my machine 1 and downgrade it to guest machine. Freeing up machine 2.
 

 Motherboard on machine 2 is A8N-SLI Premium
 [http://www.asus.com/product.aspx?P_ID=nbulqxniNmzf0mH1](http://www.asus.com/product.aspx?P_ID=nbulqxniNmzf0mH1)
 

 it has  
 **Southbridge** 
2 xUltraDMA 133/100/ 
4 xSATA 3 Gb/s ports Support RAID 0,1,0+1,JBOD 
**Silicon Image® 3114R RAID controller** 
4 xSATA with RAID0, 1, 10, 5  
 

 A good comment here would be something about if the Silicon image controller will give any problems. If it shoud use it's RAID option, or if I should let Linux do SOFT RAID and just treat the connectors as 8 equals.
 

 I have not had best luck with it under windows. When using the raid controllers, it would not let me boot from anything else than from the Silicon RAID drive. And making this box, I would want to boot on HD1 wich is not part of the raid. Might not be a problem this time as HD1 this time will not be part of a RAID.
 

 

 So to sum up and add final quistions:
 

 Is the above setup of disks on a fileserver a good or bad idea?
 

 Thinking here about placing shares under a /share mount and in one big partition. The files are going to be 99.9% static. Be both larger image files as well as small photo .JPG files. Files the users will most likely edit will be in there private /home dir.
 There might be needed to run some internet services on it as well. Teamspeak and FTP server are already requested by friends.
 I think I am so much a noob, that should something happend to my server installation, I am more likely to succed with reinstall HD1 than fixing what had gone wrong with the install. That is main reason for OS on HD1. And I also like to keep it seperate from main shares. Disk images as backup is also easier.
 

 Is machine 2 a good choice, will it be able to handle the disks. Or should I stick with the idea about buying some new CPU/motherboard for this box?
 

 I still need to buy the 1 TB disks. What I realy would like is the WD RE3 disks.
 [http://www.westerndigital.com/en/products/products.asp?driveid=503](http://www.westerndigital.com/en/products/products.asp?driveid=503)
 

 But they are almost twice the price of other 1TB disks. Do anyone know them and are they the extra money worth?
 Any other 1TB disk to recommend I check out?
 

 The server install ISO is named amd64. Ehm sorry to ask, risking to sound more stupid than I hope to be, but does that mean it does not work well or at all on Intel machines or what does the AMD refer too?
 

 And finaly an almost non Linux quistion. Would Phenom II X4 965 6 MB CPU be a good choice to build a new Windows gaming PC around? Keeping in mind that someday in the futher it will be the old machine and might be needed to make a new Linux something box.
 

 I know it is a long piece this one. But I hope somebody reach the end and have a thought or two to share. Any brainstom and feedback will be of big help.
 

 Thanks in advance  
 LoveJoyDK

---

### Post by undecim on 2010-04-03
Here's what can help with:

> **LoveJoyDK said:**
> Window and Ubuntu desktops on the LAN able to use the shares on the Linux/Ubuntu server
Both Windows and Ubuntu should be able to access Samba shares


> **LoveJoyDK said:**
> Also thought of making it a firewall and internet sharing box. But I think it would be unvise to make a PDC and file-server to be the front end box to the internet.
As long as you set up anything such as SSH and Samba to only listen on the Ethernet card that is connected to the local network, you will be fine. Once you have it all set up, it wouldn't be a bad idea to port scan your IP from another internet connection.

> **LoveJoyDK said:**
> In smb.conf there is:
 

 

    [FONT=Courier New, monospace][SIZE=2]#logon script = scripts/logon.bat[/SIZE][/FONT]
    [FONT=Courier New, monospace][SIZE=2]logon path = \\%L\profiles\%U\%a[/SIZE][/FONT]
    [FONT=Courier New, monospace][SIZE=2]logon drive = H:[/SIZE][/FONT]
    [FONT=Courier New, monospace][SIZE=2]logon home = \\%L\home\%U[/SIZE][/FONT]

 Can anyone tell me what the function of ”logon drive = H:” should be?
 Where can I find more about what the %L %U and so on stands for.?
 
Look at manual for smb.conf. In a terminal, type "man smb.conf" You can press the / key to search. (ie. "/logon drive" will search for "logon drive)


 > **LoveJoyDK said:**
> Is the above setup of disks on a fileserver a good or bad idea?
 
Sounds fine to me. I don't think you will need 50GB for /. 10GB is usually enough, unless you plan on running a squid server with a very large cache.

> **LoveJoyDK said:**
> Thinking here about placing shares under a /share mount and in one big partition. The files are going to be 99.9% static. Be both larger image files as well as small photo .JPG files. Files the users will most likely edit will be in there private /home dir.
 There might be needed to run some internet services on it as well. Teamspeak and FTP server are already requested by friends.
 I think I am so much a noob, that should something happend to my server installation, I am more likely to succed with reinstall HD1 than fixing what had gone wrong with the install. That is main reason for OS on HD1. And I also like to keep it seperate from main shares. Disk images as backup is also easier.

You can keep the shares in /home/shares/. That keeps them on your home partition, which has lots of space.
 

 Is machine 2 a good choice, will it be able to handle the disks. Or should I stick with the idea about buying some new CPU/motherboard for this box?[/QUOTE]
Just make sure you have the hardware to do what you want to do. Ubuntu will run on almost any hardware. 
 

> **LoveJoyDK said:**
> I still need to buy the 1 TB disks. What I realy would like is the WD RE3 disks.
 [http://www.westerndigital.com/en/products/products.asp?driveid=503](http://www.westerndigital.com/en/products/products.asp?driveid=503)

 But they are almost twice the price of other 1TB disks. Do anyone know them and are they the extra money worth?
 Any other 1TB disk to recommend I check out?
As far as I can tell, the cheaper WD disk just have features disabled. TLER for example keeps your disks from dropping out of RAIDS due to the drive's own error correction. I bought some disks without that feature, on the advice that downloading the old TLER confugation utility from WD would be able to activate TLER, but I've had no luck with it.


> **LoveJoyDK said:**
> The server install ISO is named amd64. Ehm sorry to ask, risking to sound more stupid than I hope to be, but does that mean it does not work well or at all on Intel machines or what does the AMD refer too?

It will work fine on 64 bit intel machines. The amd part doesn't really mean much. You see that architecture referred to as amd64, ia64, and x86_64.

Also, if you have any questions that don't get answered here, you will probably get better results from starting a new thread for each situation.

---

### Post by LoveJoyDK on 2010-04-04
> **undecim said:**
>  
 
Sounds fine to me. I don't think you will need 50GB for /. 10GB is usually enough, unless you plan on running a squid server with a very large cache.
 
You can keep the shares in /home/shares/. That keeps them on your home partition, which has lots of space.
 
As far as I can tell, the cheaper WD disk just have features disabled. TLER for example keeps your disks from dropping out of RAIDS due to the drive's own error correction. I bought some disks without that feature, on the advice that downloading the old TLER confugation utility from WD would be able to activate TLER, but I've had no luck with it.
 
 
 
 

 
Very much thanks for the comments.
 
Just one thing I am not clear on.
 the 50 GB / is just because I do not plan on using plenty of space on HD1. It will be a 200 GB disk or so. but I can move the 40 GB to the /home partition.
 
You say I can keep my shares on /home on main disk. But I have already about 1.2 TB of files I want to share from this box, and still growing collection.
 
So am not sure what shares you mean I can keep on /home. The usershares will be there, but for the allusers share I will need more space than a single disk can hold.
Therefore the RAID function of disks on SDA5. And with about 3 TB of files. backup is not going to be a main feature here. Which again is the reason for RAID to secure the data that way.
 
On the other hand. The system disk wich only will be about 200 GB max. backup is more easy. I plan on using disk cloning as backup before/after each mayor change to the server setup.
 
If anyone knows a better way to secure the setups and settings of a linux server I would be happy to know.
Would love a feature that could make a script from a running server to use for a reinstall later. Including the different conf and dB's used in the setup.
 
 
Another thing I have been thinking about is the KB of block on my partitions. The TB of files I am to share is ISO files, movie files. Which all are likely to be bigger than 100 MB each. On the other hand I also have a growing foto collection. But those files are more likely small in comparisson. Will it be worth the trouble to make two partitions. with different block sizes like 64 KB  for movies and 16 KB for photos?
 
Tried that before but ended up with no space left on one partition and plenty on the other. So ended up mixing the files anyway. 
So I gues my real quistion is. What KB blocks should I make for a partition with many large as well as many small files?
 
again thanks in advance

---

