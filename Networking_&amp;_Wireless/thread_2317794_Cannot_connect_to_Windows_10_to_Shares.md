---
title: "Cannot connect to Windows 10 to Shares"
date: 2016-03-19
forum: Networking &amp; Wireless
---

### Post by jdhamric on 2016-03-19
I recently had to replace a Windows Vista computer with one containing Windows 10 Home. I also have a laptop running Ubuntu 15.04 with which I would be able to connect wirelessly to shared partitions & printers on the Vista computer through Samba. I set up the Windows 10 computer with the same user name, workgroup name, shared partition names and IP address as the Vista box. I made sure my user name was added to all shares and full control of the shares was enabled. However when I attempt to connect to the shares I am unable to do so. The shares have always been mounted at boot time through fstab. As an example:

//192.168.1.2/Data /home/jeff/Barsoom_Data  cifs  auto,user,rw,x-systemd.automount,username=Jeff,password=*********,uid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777  0  0

Running "sudo mount -a" in a Terminal results in the cursor just blinking after entering the command.
Entering "smbclient -L //192.168.1.2 -W Zebedee -U Jeff" gives the following output:


Domain=[BARSOOM] OS=[Windows 10 Home 10586] Server=[Windows 10 Home 6.3]

    Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$          Disk      Remote Admin
    C$              Disk      Default share
    Canon MX882 Printer Printer   Canon MX882
    Data            Disk      
    E$              Disk      Default share
    F$              Disk      Default share
    G$              Disk      Default share
    HP Photosmart D7300 series Printer   HP Photosmart D7300 series
    IPC$            IPC       Remote IPC
    Media           Disk      
    Media2          Disk      
    My Documents    Disk      
    print$          Disk      Printer Drivers
    Users           Disk      
Connection to 192.168.1.2 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
NetBIOS over TCP disabled -- no workgroup available

I've Googled the error but can't find anything that seems to relate to my problem.

Nothing has changed on the Ubuntu machine. I've disabled Homegroup on Windows 10 and enabled NetBIOS over TCP in Windows. The only other difference I can see is McAfee IS/Firewall on Windows 10. Before I was using the Comodo suite. If I have to I can/will uninstall Mcafee & install Comodo; but I have disabled McAfee with no result.

Any help resolving this issue is appreciated.

---

### Post by weatherman2 on 2016-03-20
Have you tried this?

[https://lists.samba.org/archive/samba/2015-September/193886.html](https://lists.samba.org/archive/samba/2015-September/193886.html)

FYI, unless you love Mcafee (or Comodo), you can simply use the built-in Windows Defender (formerly called Security Essentials) which is built into Windows 8 and Windows 10 and disables itself if you have another anti-virus installed.  Remove Mcafee, reboot, search for Defender then update it and that's all you need for anti-virus.

---

### Post by jdhamric on 2016-03-20
> **weatherman2 said:**
> Have you tried this?

[https://lists.samba.org/archive/samba/2015-September/193886.html](https://lists.samba.org/archive/samba/2015-September/193886.html)

FYI, unless you love Mcafee (or Comodo), you can simply use the built-in Windows Defender (formerly called Security Essentials) which is built into Windows 8 and Windows 10 and disables itself if you have another anti-virus installed.  Remove Mcafee, reboot, search for Defender then update it and that's all you need for anti-virus.

Weatherman2-- I did come across that article & I have considered it. But since Ubuntu 15.04 uses SambaV4 and it looks like Win10 uses V3 I didn't think it would be necessary.

I don't have any allegiance to McAfee & can certainly remove it. I only mentioned Comodo because I used it with the Vista machine & have a firewall profile saved that I know works (or worked) but I can use the Microsoft protection.

Thanks for your suggestions!

---

### Post by Morbius1 on 2016-03-20
> Windows 10 will try to negotiate SMB3_11, which Samba4 doesn't yet support
except in the current 4.3 release candidate. I suspect for now disabling
SMB2/3 on the Windows 10 client is your best, if not ideal, option.

There's a couple of things wrong with that statement.

[1] It's referring to a Windows 10 client accessing a Linux samba server - you are doing the opposite.
[2] It's not accurate.

Well, Win10 will certainly try to access the Samba server first with SMB3.11 but it will auto-negotiate until it settles on SMB3.00 which the samba server will run. Whoever wrote that statement simply didn't know.

Anyway, I can't reproduce your symptom ( I even used your fstab entry with appropriate changes ) so I have nothing valuable to add to this discussion. I also only use Windows Defender as  Weatherman2 suggested so maybe that's the secret here.

---

### Post by oldfred on 2016-03-20
Does the Windows 8 or later, fast start up or always on hibernation also prevent Samba from working?

       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by jdhamric on 2016-03-20
That's correct-the Win10 machine has the shares & is the server. I was able to see & access the Ubuntu computer from Windows, though. So maybe it comes down to the McAfee firewall; I just can't determine where the problem might be there.

---

### Post by Morbius1 on 2016-03-21
I'm "on assignment" at the moment and don't have a Windows system in sight so this is from memory which for me is a dangerous place to start.

If you have Win8 experience you already know this but Windows has many "networks": Private, Public, Domain... depending on where it finds itself. With each "network" there is an associated Windows firewall profile which determines how that network is handled. It could be that you are in the wrong one for your current environment.

I don't know how 3rd party firewall apps handle this but it could further mess things up.

*And don't ask me how to switch from a Public to Private network since I really don't remember off hand.*

---

### Post by jdhamric on 2016-03-21
Morbius1,

It's somewhat reassuring that you can connect using my fstab file. I've been poking around the internet & it appears Ubuntu 15.04 with kernel 3.19 uses SMB3, so it "should" be able to connect to the Win10 box. 

Yes, I know about the different network types & how to get to them; I'd already set mine to "Home", but I think it would only apply to the Windows firewall. McAfee already came installed on my computer & that may be the source of my problems. I'm going to uninstall it at the first opportunity & see what happens (watching the grandkids now & that takes up a LOT of time!). Then I might try it with the Windows firewall or Comodo, which I had used before.

Thanks for the input

Update: Got a chance to uninstall McAfee & use Windows Firewall. Ran "sudo mount -a" on Ubuntu & voilá! I can access my shares! Rebooted the Ubuntu machine just to make sure the shares mounted at boot, which they do. I guess this can be marked as solved.

Thanks to all for you help!

---

### Post by weatherman2 on 2016-03-21
I always thought Mcafee was too aggressive at locking down a PC.  Not totally surprised it blocked your network shares.  Make sure you update Defender if you are going to use that as your primary anti-virus!

---

