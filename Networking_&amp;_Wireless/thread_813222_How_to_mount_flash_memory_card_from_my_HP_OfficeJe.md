---
title: "How to mount flash memory card from my HP OfficeJet"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by MountainX on 2008-05-30
SOLVED NOW

I have an OfficeJet Pro L7680 all-in-one printer on my ethernet network. From a Windows computer I can access a flash media card that is in the printer. How can I do this from Ubuntu?

In Windows I open the file browser (Win Explorer) and enter the printer's IP address like this:
```
\\192.168.100.2\media_card\
```
immediately I have access to all photos or files on the flash memory card I have inserted into the printer.

I have tried using Nautilus to connect to a server with this IP address and I get an error like "Error: Failed to mount Windows share"

---

### Post by MountainX on 2008-05-31
So maybe no one has tried to mount the flash media drives on this printer under Ubuntu...

However, I am confused as to why the "SMB://" method gives me "Error: Failed to mount Windows share" in Nautilus when I can clearly mount this from Windows. Any thoughts? Ideas? Suggestions for troubleshooting?

---

### Post by MountainX on 2008-06-01
I could really use some help, please.

$ sudo mount -t cifs -vvv -o uid=myuser,gid=myuser,file_mode=0777,dir_mode=0777,rw //192.168.100.2/media_card /media/HpFlash
[sudo] password for myuser: 
mount: fstab path: "/etc/fstab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: spec:  "//192.168.100.2/media_card"
mount: node:  "/media/HpFlash"
mount: types: "cifs"
mount: opts:  "uid=myuser,gid=myuser,file_mode=0777,dir_mode=0777,rw"
mount: external mount: argv[0] = "/sbin/mount.cifs"
mount: external mount: argv[1] = "//192.168.100.2/media_card"
mount: external mount: argv[2] = "/media/HpFlash"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,uid=1000,gid=1000,file_mode=0777,dir_mode=0777"
parsing options: rw,uid=1000,gid=1000,file_mode=0777,dir_mode=0777
Password: 

mount.cifs kernel mount options unc=//192.168.100.2\media_card,ip=192.168.100.2,user=root,pass=,ver=1,rw,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 
retrying with upper case share name

mount.cifs kernel mount options unc=//192.168.100.2\MEDIA_CARD,ip=192.168.100.2,user=root,pass=,ver=1,rw,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 
mount error 6 = No such device or address

What else can I try. I can mount this flash drive without any effort from a Windows computer. Surely Ubuntu can mount it, right? What do I need to do? Thanks.

---

### Post by MountainX on 2008-06-03
bump

---

### Post by MountainX on 2008-06-03
how about any ideas... even if they are bad ideas. What else can I try? How can I troubleshoot this? Thanks.

---

### Post by tgalati4 on 2008-06-03
I have an older Officejet 7110 on ethernet.  I will try to look at reading CF cards on it.  

Have you tried the hp toolkit?  There are some printer-specific features such as ink level and cleaning.

The other thing to try is to log into the printer from a browser:

[http://192.168.100.2/](http://192.168.100.2/)

See what options are available.

---

### Post by MountainX on 2008-06-03
> **tgalati4 said:**
> I have an older Officejet 7110 on ethernet.  I will try to look at reading CF cards on it.  

Have you tried the hp toolkit?  

The other thing to try is to log into the printer from a browser:

[http://192.168.100.2/](http://192.168.100.2/)



Thank you. I have looked at the HP Toolkit. It has a "Unload Photo Card" feature, but I cannot get that to work.

I am able to access the printer from a browser. There is not an option to download files from the flash memory cards.

Thanks for the ideas. I still think the best solution is to mount the media_cards folder like I can do under Windoze.

---

### Post by tgalati4 on 2008-06-04
What size cards are you trying to use?  I as recall, HP has restrictive specs on the kind of cards that can be read.

The other issue may be permissions.  Have you tried mounting with read-only permission?

Is your printer listed in /etc/hosts?  It should have the same name as it is listed in the print dialog.

I haven't had a chance to play with my printer yet.

Check dmesg immediately after trying to mount:

>dmesg | tail

and also check /var/log for any messages that may help.

Does the mount point /media/HpFlash have 777 permissions?

---

### Post by MountainX on 2008-06-04
Here is some more info.

The error returned by the mount command is the same as what I posted earlier in this thread:
```
mount error 6 = No such device or address

```

```
dmesg | tail
[851799.724601]  CIFS VFS: No response to cmd 116 mid 4
[851799.855816]  CIFS VFS: cifs_mount failed w/return code = -6
[851799.868428]  CIFS VFS: RFC1001 size 39 bigger than SMB for Mid=4
[851799.868434] Bad SMB: : dump of 48 bytes of data at 0xf6b7b000
[851799.868439]  00000027 424d53ff 00000074 01008800 ' . . . &#65533; S M B t . . . . . . .
[851799.868443]  00000000 00000000 00000000 09780000 . . . . . . . . . . . . . . x .
[851799.868458]  00040000 0000ff03 34000000 00545b00 . . . . . &#65533; . . . . . 4 . [ T .
[851829.700631]  CIFS VFS: server not responding
[851829.700640]  CIFS VFS: No response to cmd 116 mid 4
[851829.832405]  CIFS VFS: cifs_mount failed w/return code = -6

```

I am accessing the device via IP address only, so I'm not using /etc/hosts.

There is nothing else pertinent to this issue in System Log Viewer (/var/log/ ...)

I've tried a couple different media cards in the HP OfficeJet. I can access all the cards from a Windows computer, but none of them from Ubuntu. Therefore, I don't think it is an issue with the kind of card.

The folder where I'm doing the mount has 770 permissions and my user is the owner. I have tried other permissions but it doesn't seem to make any difference.

---

### Post by MountainX on 2008-06-04
Oh, btw, changing the casing from media_card to Media_Card to MEDIA_CARD doesn't make any difference either. 

Under Windows, when mounted successfully, it is listed as media_card (CORRECTION: **memory_card**). See below.

---

### Post by MountainX on 2008-06-04
SOLVED! This whole problem turned out to be a stupid user error. I'm too embarrassed to even say what it was. :oops:

Ubuntu is accessing the media card just as easily as Windows now and everything is fine. Go Ubuntu!

---

### Post by MountainX on 2008-12-28
Someone asked for my solution.

I'm sorry for not posting exactly what the problem was when I resolved this.

The problem was simply spelling. Once I spelled the name "**memory_card**" correctly, it worked.

---

### Post by B34N on 2009-04-06
> **MountainX said:**
> Someone asked for my solution.

I'm sorry for not posting exactly what the problem was when I resolved this.

The problem was simply spelling. Once I spelled the name "mediacard" correctly (so my Ubuntu settings matched my printer's settings), it worked.

I'm a newbie so I guess I'm missing something.  What are the steps that I need to do in order to mount the SD Card on my HP printer if the IP address is 192.168.1.40?  

Thank you!

---

### Post by MountainX on 2009-04-06
> **st8ofmi9d said:**
> I'm a newbie so I guess I'm missing something.  What are the steps that I need to do in order to mount the SD Card on my HP printer if the IP address is 192.168.1.40?  

Thank you!

1. put SD card in printer (make sure there is no error shown on printer)
2. open Nautilus (e.g., places > home)
3. File > Connect to Server
4. Server: 192.168.1.40
5. Share: [COLOR=Red]**memory_card**[/COLOR]
6. click connect
7. enter username and password (depending on how you set your printer up)

A shorter way is to just open Nautilus and past this into the address bar:
```
smb://192.168.1.40/memory_card/
```And if you edit your /etc/hosts file, you should be able to just do this (I didn't test):
```
smb://hpprinter/memory_card/
```You can also add a bookmark to Nautilus for easy navigation in the future.

You can also browse to your printer using [http://192.168.1.40](http://192.168.1.40)

**And finally, there is a really easy option if you installed the HPLIP toolbox, you can simply open it and click "Upload Photo Card" (lower right button on "Functions" tab) and it will find your memory card.**

---

