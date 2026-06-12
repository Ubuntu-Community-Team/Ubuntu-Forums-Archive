---
title: "Need help setting up home network."
date: 2015-07-17
forum: Networking &amp; Wireless
---

### Post by dtree46 on 2015-07-17
Is anyone here willing to help an older person with minor brain damage set up a home network? It isn't a complicated system, it's just that I get confused trying to follow 'how to's' or 'tutorials'. I am willing to let someone in the system as a guest. All I ask is a way to contact you. I do not want name, address, phone number, only an email address. I also have Skype.

Thanks,
dlw

---

### Post by TheFu on 2015-07-18
Can you list the all the devices and what you hope to accomplish?  Not sure I have all the needed skills, that's all.

---

### Post by dtree46 on 2015-07-18
Thank you for replying.

There are 2 PC's, a printer and router.
Main PC: In office - spare bedroom. Move to den.
HP 4gb ram, 80gb hd, 1tb hd.
Ubuntu 15.04

Second PC: Keep in office.
Whitebox Mini, 2gb soon to be 16gb ram, 64gb SSD.
Ubuntu 15.04

Laptop: Wifi to Main PC
Dell Studio 1558, 8gb ram, 500gb HD.
Ubuntu 15.04, W7 dual boot. W7 is needed for cell phone use.

Maxtor external HD, 250gb for backup.

Printer:
HP Laserjet 1536 MFP

Router:
Netgear WPN824N

Both PC's and laptop are on a VPN.

What I want to do:
Change main PC to Mini PC 
I will increase ram to 16gb.
Add 1tb HD from main PC externally via USB.

The old main PC would keep the 80gb. Use to test other distros, etc.

I want the ability to share, move, etc between the 2 PC's and laptop and all 3 to share the printer.

I simply can not grasp networking and Samba is....
I hope this is clear. I'm happy to answer any questions I can.

dlw

---

### Post by TheFu on 2015-07-18
For linux migrations - just move the HDD. Provided the new system has the same sort of BIOS as the old one, it should be fine. Going from BIOS to UEFI is an issue. Also, network cards might need a little tweaking.

RAM changes don't matter.

I don't know anything about networked printers. If nothing changes about the printer and things are working, it will keep working.

For Linux-to-Linux file sharing on the same LAN, NFS is best for many reasons. CIFS (implemented by samba) is a "lowest common denominator" answer. You can use both NFS and CIFS at the same time to share the same storage.  For cross-platform, sharing from anywhere in the world, sftp is the best answer I know. It works over ssh with ssh-keys for authentication. sftp is part of the openssh packages (there's a client and server).

If you do that, samba won't be necessary.  

For printing, use the IPP protocol. Every networked desktop OS supports that. 

Is there a reason you don't use virtualization to test new distros? It makes life much easier and with 16G of RAM, it won't be an issue with any Core i3/5/7 CPU.

BTW - I have a 1558 myself (got it cheap with 1080p video about 5 yrs ago). I'm mirroring the 500G disk to a 750G disk right now and expanding the 50G for windows to 99G - started getting out of space warnings/errors.  Going from 512b sectors to 4K sectors is complicating the disk alignment.  Too bad Windows doesn't support GPT without UEFI booting. Would much prefer to use GPT.

You mention vpn, but not which vpn is being used.

I'm not a fan of netgear equipment. It does what it claims, but I've been burned by missing features that every other home router provides - like port translation and DHCP reservations. 

Which ports are open to the outside world? Do you deal with WAN DHCP or not?

Ubuntu 15.04 support ends in January. I only deploy LTS releases here. Need longer support periods.

Sounds like you have 3 PCs, a printer-scanner, and a router. That's a little more complex.  If you use [zeroconf]("https://help.ubuntu.com/community/HowToZeroconf") , all of them should be able to find each other, but there are security implications and access from the outside world may not work to a specific system. I dunno, don't use it myself.

Have you looked at the motherboards to be sure they will support 16G of RAM? Most of the time, a system that has 2G today **will not** be upgradeable to 16G - the firmware doesn't support it.  For example, the Dell 1558 only supports 8G of RAM.

---

### Post by dtree46 on 2015-07-18
> **TheFu said:**
> For linux migrations - just move the HDD. Provided the new system has the same sort of BIOS as the old one, it should be fine. Going from BIOS to UEFI is an issue. Also, network cards might need a little tweaking.

      So, just connect the 1tb hd externally to the mini and set it to boot up in BIOS instead of the 64gb ssd. Is this what you are suggesting?

For Linux-to-Linux file sharing on the same LAN, NFS is best for many reasons. CIFS (implemented by samba) is a "lowest common denominator" answer. You can use both NFS and CIFS at the same time to share the same storage.  For cross-platform, sharing from anywhere in the world, sftp is the best answer I know. It works over ssh with ssh-keys for authentication. sftp is part of the openssh packages (there's a client and server).

     Both pc's are formated ext4. Every thing important is backed up. Should I reformat to NFS?

  Is there a reason you don't use virtualization to test new distros? It makes life much easier and with 16G of RAM, it won't be an issue with any Core i3/5/7 CPU.

     Do not know what virtualization is, I'll research it.

BTW - I have a 1558 myself (got it cheap with 1080p video about 5 yrs ago). I'm mirroring the 500G disk to a 750G disk right now and expanding the 50G for windows to 99G - started getting out of space warnings/errors.  Going from 512b sectors to 4K sectors is complicating the disk alignment.  Too bad Windows doesn't support GPT without UEFI booting. Would much prefer to use GPT.

     A friend gave me the Dell or I would still have the EEE netbook. LOL


You mention vpn, but not which vpn is being used.

     PIA.

     Which ports are open to the outside world?   No idea.
     Do you deal with WAN DHCP or not?  Laptop connects via wireless as do cell phones.

Ubuntu 15.04 support ends in January. I only deploy LTS releases here. Need longer support periods.

    I ran 12.04 until it expired. Updated to 14.04 but had trouble with it. Updated to 15.04 hoping for better luck but that did not work. That is why I got the mini    to replace the main pc. The HP PC is getting old... like me.

Sounds like you have 3 PCs, a printer-scanner, and a router. That's a little more complex.  If you use [zeroconf]("https://help.ubuntu.com/community/HowToZeroconf") , all of them should be able to find each other, but there are security implications and access from the outside world may not work to a specific system. I dunno, don't use it myself.

Have you looked at the motherboards to be sure they will support 16G of RAM? Most of the time, a system that has 2G today **will not** be upgradeable to 16G - the firmware doesn't support it.  For example, the Dell 1558 only supports 8G of RAM.

    Yes, the mini will support 16gb.

---

### Post by TheFu on 2015-07-18
Based on what you've described, I am not the person to help. Sorry. 

I tend to do things the hard way with every device having a static IP which is hard to accomplish from a remote connection. There must be easier ways for a setup like yours. Hopefully someone else will respond.

I think you'd like to use **DHCP reservations** for your networking. [http://documentation.netgear.com/fvs336g/enu/202-10257-01/FVS336G_RM-05-07.html](http://documentation.netgear.com/fvs336g/enu/202-10257-01/FVS336G_RM-05-07.html) Couldn't find any more detailed instructions there.  The short version is MACs connect to hostnames and IP addresses.    Just pick some IPs that aren't in the DHCP dynamic range and everything will be OK. The MAC for each system is found with **ifconfig** or **ipconfig** on windows. **arp** should show all connected devices so you can copy/paste.

Oh - you are a VPN client, not running your own VPN. Doubt that changes anything.

For the things you want, I think you need someone local - have you checked with the local **Linux Users Group** for help? Most cities have 1 or 5.

---

### Post by dtree46 on 2015-07-18
Thanks for you time anyway.

dlw

---

### Post by Dylan_Langdon on 2016-05-07
You can identify the IP address of your router by typing “ipconfig” in the command prompt on your Windows computer. You may use a Mac operating system these days. You can find out the IP address of your router by typing “Terminal” in the search bar of your launch pad. 
Once the app on the subject of Terminal has opened, you have to type in netstat – nr 1 grep default command.  Now, you can take note of the IP address of your router from the second line of the output.  You may get the [ip address 192.168.0.1]("http://www.ipaddressdefinition.com/192-168-0-1-1/") when you use the Netgear or D-Link router.

---

### Post by dtree46 on 2016-05-07
Thank you for your reply.
The mini I purchased was not able to hold 16gb ram.
Returned to seller.
[TABLE="width: 100%"]
[TR]
[TD="colspan: 2"][/TD]
 [/TR]
 [TR]
 	[TD="colspan: 2"][/TD]
 [/TR]
 [TR]
 	[TD="colspan: 2"][/TD]
 [/TR]
 [TR]
 	[TD][/TD]
 	[TD="align: right"] 	. 	. 	. 	 	[/TD]
 [/TR]
 [TR]
 	[TD][/TD]
 	[TD="align: right"] 	. 	. 	. 	 	[/TD]
  [/TR]
 [TR]
 	[TD][/TD]
 	[TD="align: right"] 	. 	. 	. 	 	[/TD]
 [/TR]
 [TR]
[TD="colspan: 2"][/TD]
[/TR]
 [TR]
 	[TD="colspan: 2"][/TD]
 [/TR]
 [TR]
 	[TD="colspan: 2"][/TD]
 [/TR]
 [TR]
 	[TD="colspan: 2"][/TD]
 [/TR]
 [TR]
 	[TD][/TD]
 	[TD="align: right"] 	. 	. 	. 	 	[/TD]
 [/TR]
 [TR]
 	[TD][/TD]
 	[TD="align: right"] 	. 	. 	. 	[/TD]
[/TR]
[/TABLE]

---

### Post by him610 on 2016-05-07
Hello dtree46,
> 
I want the ability to share, move, etc between the 2 PC's and laptop and all 3 to share the printer.
This should not be difficult. I have a similar network: however, I have a dedicated *fileserver* accessible to all PCs. I do not use VPN though.
TheFu in Post #4 suggested using *zeroconf*, I followed his link and it seems like a reasonable solution for your needs.
I have a question about your laptop, > Dell Studio 1558,...Ubuntu 15.04, W7 dual boot. W7 is needed for cell phone use
Do you intend to use the laptop when running W7 to exchange files with your other PCs running Ubuntu?

Maybe we can work our way through this.

---

