---
title: "I would change today if ubuntu had better integration with Active Directory"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by behrendtb on 2007-10-31
I am a tech director for a school, and I have been toying with using edubuntu in my school.  I have used ubuntu on my desktop and i am sold, but I just can't get over the lack of AD integration.

I have read the how-to's and got some of them to work, but it is no where near efficient enough to work.   and I have yet to find a solution for logon scripts.  (I currently use Destop Athority, nice but way to expencive) I am also looking at [http://www.scriptstart.com](http://www.scriptstart.com), but they still don't have linux client support.

This is a plea to the ubuntu Gods.  Please stop working on making ubuntu prittyer and start working on AD integration so all of us use-to-be windows persons can actually start making the switch at our jobs.

What i need:
1. a place where i can type my domain, and an admin account to join to the domain.
2. a way to manage logon scripts.   Something real nice would be an alternative to one of the above programs that can manage windows and linux clients.
    - from the logon scripts i need;  share mappings/mounts and printer management.


This is just a plea to those who would listen.  And wondering when I might see some of the above, 

Bj

P.s. Currently using Gusty Gibbson 7.10

---

### Post by Grey Dog on 2007-12-08
Well spoken, Sir!


I agree.

---

### Post by tact on 2007-12-08
I use my ubuntu desktop in my company's AD domain and have no issues.  I had a look at the login script to see the drive mappings and just chose what I want and have those directories mount (entries in /etc/fstab) via CIFS.

It works like magic.  If i am not on the corporate domain (like at starbucks using free wifi, or at home) no corporate shares mount.  Cool.   When I either go to the office, or fire up the VPN client so that i am logged into the domain, the CIFS system(?) notices the shares are available and mounts them, even without booting!.   Damn cool.

Printers on the AD are no issue either.  Gutsy finds then and I can access them across the LAN/WAN easily.   

About the only thing I have not sorted (and have not even tried yet) is changing my domain password on the AD via ubuntu.

---

### Post by behrendtb on 2007-12-08
I have actually used the /etc/fstab solution on my computer which is ubuntu, and mounted the shares to my folders.  I even got ubuntu to somewhat releayably authenticate to my active directory useing SADMS.   

My problem is that I have 200 computers 400 users, and a different mounting scheam depending on which year a student is (if i didn't mention before I am an IT director for a shcool).

It is just not relyable for me to manage a complicated fstab (requireing if statements and such) on individual computers over the masses.  Even if I did do that then I cannot imagine the amount of work it would take if I needed to change a surver name or add a share.

I would be happy to write something myself but I just don't have the knowlege.

-bj

P.s. Here is my logic for makeing a linux logon script.

1. on the linux box it will mount a temporary share (probably the NetLogon Share)
2. then it will look for a script on that share which will determin the name of the comptuer and the user logged on.
3. That info will be ran against some type of server side db (similar to my original suggestion of scriptlogic).
4. the server side software builds a script that mounts the correct drives and printers on my linux client computer.

note: Idealy the server side db will be a webbased app.
note2: The server side software should be cross platform compatable to linux, windows, and possibly mac.





> **tact said:**
> I use my ubuntu desktop in my company's AD domain and have no issues.  I had a look at the login script to see the drive mappings and just chose what I want and have those directories mount (entries in /etc/fstab) via CIFS.

It works like magic.  If i am not on the corporate domain (like at starbucks using free wifi, or at home) no corporate shares mount.  Cool.   When I either go to the office, or fire up the VPN client so that i am logged into the domain, the CIFS system(?) notices the shares are available and mounts them, even without booting!.   Damn cool.

Printers on the AD are no issue either.  Gutsy finds then and I can access them across the LAN/WAN easily.   

About the only thing I have not sorted (and have not even tried yet) is changing my domain password on the AD via ubuntu.

---

### Post by smadon on 2008-01-28
Hello,

Just Find your message, and it's exactly what I'm looking for : "Integrating Ubuntu Client on  the Active Directory".

I don't know how long it will take for the Ubuntu Guru to Integrate this kind of tools, but I need a solution now :-)

Same as you, I have to manage 200 Pc for a School. 100 Win XP, and the rest with Ubuntu, and the user database on AD on a Windows server 2003, which is file server as well.
Still working on it, but It's going on well (slowly but surely :-l)
One Project nearly finish : the automatic Installation on every PC (ubuntu and XP) with PXE.
WebServer and Mail Server nearly ready as well, DHCP, DNS, ready.
So a fully nice solution going on slowly :-)

Anyway, for the AD in Ubuntu. 
- Integration of Ubuntu PC in the AD, and connection of the user : DONE ([http://ubuntuforums.org/showthread.php?t=288534&page=1](http://ubuntuforums.org/showthread.php?t=288534&page=1))
- Logon Script to start Share Folder : Working on Now.
- Share Printer  : for later.

So Logon Script.
What about a script starting in the beginning when the user log  (emmhh, silly sentence, it's the definition of a logon script)

To start when the user log ([http://ubuntuforums.org/archive/index.php/t-412206.html](http://ubuntuforums.org/archive/index.php/t-412206.html))

The Script 
Script check update, upgrade and mount personnal drive with cifs.

> 
#!/bin/sh 
# Define Variable

# Check System Up to date Source
sudo apt-get update | zenity --progress --title "Selamat datang: Update System" --text "text" --auto-close
# Run a dist-Upgrade
sudo aptitude dist-upgrade | zenity --progress --title "Selamat datang: Upgrade System" --text "text" --auto-close

#Verify access Username

#Ask Password Again 
passwordUser=$(zenity --entry --title "Password" --text "Silahkan menulis passwordnya untuk Network Access: " --hide-text)
logonUser= $LOGNAME

#zenity --warning --title "$pass1" --text " $LOGNAME / $logonUser   /  $USER / $HOME / $OSTYPE /  $passwordUser"
mount -t cifs //MyWindowsServer/$logonuser /media/perso -o username=$logonUser,password=$passwordUser,iocharset=utf8,file_mode=0777,dir_mode=0777



My problem for Now, 
How can I update, upgrade and mount the drive without asking the sudo passowrd ????

or can I give to all my user sudo access only to mount drive?

For sharing drive depending on group, I was thinking to use the command net ads search, and create a list of if with all my drives, it shouldn't change very often.

Thanks for your reply.
And let me know, if this kind of solution could be right.

---

