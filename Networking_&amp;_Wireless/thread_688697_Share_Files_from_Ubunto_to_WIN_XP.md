---
title: "Share Files from Ubunto to WIN XP"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by RonRock on 2008-02-05
I have just loaded Ubuntu 7.10 on one computer. I can see shares on my WIN XP computer on my LAN, but unable to open them on the Linux. I can see the Linux- server on the XP computer in View Workgroup Computers/MSHOME but unable to open the computer, keeps asking for Username and Password. I have only created 1 user on the Linux box. How do I open the shares, either way would be a start.
I'm sure this has been beaten to death, but I searched and was unable to find any info that helped.

---

### Post by kirsche on 2008-02-06
How are you trying to mount the share? e.g.
```

[sudo] mount -t [smbfs|cifs] -o username=<user> //<ip/name>/<share> /mnt/<mountpoint> 

```

---

### Post by RonRock on 2008-02-06
Thank You. I must admit I'm a Windows user, and most familiar with a Graphical User Interface. I can use comandline if given precise directions. Maybe I should be called a Windummy. 
What this excersize boils down to is this. I have a home LAN, on the LAN I had a D-Link NAS box. Used for Backups as well as simple storage. Well the NAS quit working, in my efforts to recover data off of it I found out that the NAS disk is formatted to EXT3.
So my solution was to take an old computer and loadup Ubuntu (have wanted to play around with Linux anyway) I have the OS on 1 drive and connected the NAS drive as a slave. I can see files and folders on the NAS drive so my data is safe. Very safe! 
Now to make this work I need to copy those files/folders to my Windows computer. All seems good, if I can get the computers to see each other.

---

### Post by MariusSilverwolf on 2008-02-06
Here's what worked on my systems at home:

Boot Ubuntu Gutsy.
Open System > Administration > Shared Folders
Click the "General Properties" tab
Type in the Windows Workgroup name
Click the Shared Folders tab
Click the Add button
Add the folders you want to share.
Close Shared Folders

Done.

After that, I could access files on the XP boxes from Ubuntu, and vice versa.

It should be noted, I use the same username and password for the main user on all my systems, which probably made the process easier for me.

---

### Post by RonRock on 2008-02-06
Thanks, I'll try that now. I'll be back with the results. I think my biggest obsticle is understanding what password or username I need to input in different places. I also use the same Username and Password on all of my computers. That should make it easier, but unfortunatly it also seems to make it harder to know if I've used the right info at the proper spot.

I'll be back.

---

### Post by RonRock on 2008-02-06
OK, I followed the steps. I can see the RON-LINUX computer from my WIN XP computer in "View Workgroup Computers" I click on it to see shares, A popup opens to "Connect to RON-LINUX" input Username and Password. Then I get the same popup prompt to input Username and Password.
I just loaded Ubuntu on this computer. Computer named Ron. Only 1 user, Ron with 1 Password. Is there something I need to do to Allow Network Users? Any ideas? I can see the Linux computer and get it's IP, so I'm sure it has something to do with Permissions or Uname/Password.

---

### Post by kirsche on 2008-02-06
What shares did you create?

---

### Post by yubu on 2008-02-06
I'm having the same username/password problem. I can see the node in my domain, but I get a prompt asking for authentication. I try using the same user/pass I setup to log on to Ubuntu locally, but no luck. Any idea what I need to do?

---

### Post by RonRock on 2008-02-06
At this point I have several "Shared Folders" showing in Shared Folders on Linux. /home/ron, /media, /home/ron/Desktop/Linux Share, /home/ron/Desktop, /media/disk/Backup from old drive, /media/disk.

The /media/disk  share is the one I just created and it is the drive from the NAS. I first had to Mount it, then can see files and folders on it.

---

### Post by yubu on 2008-02-06
Disregard my post... figured it out... had to edit the smb.conf file

---

### Post by RonRock on 2008-02-06
Good to hear that you got yours figured out. Can you shed a little light on what you did? It seems like we have the same issue.

I'm not crazy about editing conf files, but I would like to look at mine to see if anything pops out at me as wrong. How do I look at mine?

---

### Post by kirsche on 2008-02-06
can you post your share definition from your smb.conf please?
Did you create the smb users? (sudo smbpasswd -a <user>)

---

### Post by raptor222 on 2008-02-06
You shoeld check if the firewall block's you.
in the case you have firestarter open it in the events tab hit clear and try opening (in the places menu ) the network window, it will probably wont show anything but now go back to the firestarter and you should have one entry (with service samba) right click on it and select allow service for everyone try it multiple times until it works.
and for the windows machine try restarting it after you did all the above.

---

### Post by RonRock on 2008-02-06
> **kirsche said:**
> can you post your share definition from your smb.conf please?
Did you create the smb users? (sudo smbpasswd -a <user>)

I would be happy to answer, but need a bit of guidence. As I said I'm a Windows user and not that well versed in commandline input.

In the meantime I'll check for a Firewall on the Linux box. I have disabled the Windows XP firewall and tried to see files with it disabled, but still no joy. I can see the Linux computer through Network connections, so that leads me to beleive that the Firewall is not blocking it. They are both in my LAN on the same side of the Router.

---

### Post by MariusSilverwolf on 2008-02-06
RonRock,

In the Linux systems in question, I found one additional step I failed to mention last time.

On the linux syste, launch terminal and type in the following command:

```
sudo smbpasswd -a <username>
```

Use the local username you have on that system in place of <username> in that line of code, e.g. ron
Enter your user password for the sudo prompt
Enter the password you want to use as the Sambe (network) password
Re-enter the password you just used

Once complete, hop back over to the Windows system and try to connect to the Ubuntu box.  Windows will prompt for a username and password.  Enter the user name on the Ubuntu system, and the password you just set for Samba.  Access should be granted.

---

### Post by raptor222 on 2008-02-06
Hi RonRock,
to find if you have a firestarter firewall installed see in the notification area (top right near the clock and shut down button) an red or blue circle with a lightning or a triangle.

---

### Post by RonRock on 2008-02-06
OH YEAH! The Dance of JOY! Thank You Marius. That was the ticket. Now that it works, will it "stick" will it work next time I boot the Linux computer? Did I change something or simply put in some needed info that I was not prompted for?


Now for the next trick. How do I make my WIN XP shares work with Linux? From the Linux box I can see them but when I try to open a file or folder I'm asked  for a Username, Domain, Password. I see a popup titled- "Authentication Required" it says---- You must log in to access guest@dell/Beta File.   The Dell is the WIN XP comp, I do not have the "Guest" account activated on the Dell. The Workgroup is MSHOME but not a part of a Domain. Although the popup has Domain filled in as MSHOME.

Now what do I need to add to go backwards?


I don't think there is a firewall installed. Unless it is part of a default install. I did not install one. And there is no icon.

---

### Post by raptor222 on 2008-02-06
in that case the best advie i can give you is to reboot the win machine.
and then try to enter the username and password you enterd while setting up the share on the linux machine.

---

### Post by MariusSilverwolf on 2008-02-06
> **RonRock said:**
>  Now for the next trick. How do I make my WIN XP shares work with Linux? From the Linux box I can see them but when I try to open a file or folder I'm asked  for a Username, Domain, Password. I see a popup titled- "Authentication Required" it says---- You must log in to access guest@dell/Beta File.   The Dell is the WIN XP comp, I do not have the "Guest" account activated on the Dell. The Workgroup is MSHOME but not a part of a Domain. Although the popup has Domain filled in as MSHOME.

Now what do I need to add to go backwards? 

That depends on your Windows configuration, whether it's XP Home, XP Pro, or one of the Vista versions.

If you're lucky enough to have a XP Pro, you can adjust permissions on the shared folder to allow Network  Users access to the file.

If you're using XP Home, you'll likely need to enable the Guest account.

---

### Post by RonRock on 2008-02-06
My Dell is WIN XP MCE (media center edition, I think) I beleive that XP MCE is based on XP Pro. I have looked at Beta File/ Properties/ Sharing/ Permissions. And found Share Permissions, Everyone Allow. (Read)

I also did reboot the Windows computer, that did not make the Windows Shares work in Linux. But I was still able to see the Linux shares in Windows after a reboot. That's good.

---

### Post by tad1073 on 2008-02-06
I am having the same problem [Here](http://ubuntuforums.org/showthread.php?t=678868) is my thread about it. I still can't access my files on the xp machine.

---

### Post by MariusSilverwolf on 2008-02-06
If Sharing is enabled, and the permissions are set to allow access, the Windows (or third-party) firewall could be denying file sharing access.

We're starting to delve into the realm of Windows configuration and troubleshooting.  Perhaps the KB Article could be helpful: [http://support.microsoft.com/kb/304040](http://support.microsoft.com/kb/304040)

---

### Post by tad1073 on 2008-02-06
Thanks for the information. I have uninstalled Network Magic on the XP machine by the way.  They want you to pay for something that is offered by windows free of charge.

---

### Post by yubu on 2008-02-07
To fix this issue do the following things. Launch the run dialog by pressing Alt+F2. Enter the command gksudo gedit /etc/samba/smb.conf then enter your password when prompted. Find the security section of the configuration file. Change "user" to "share" and remove the semicolon from the start of the line. Find the guest account section. Change "nobody" to your account's username and remove the semi colon from the start of the line. Save the file and restart your computer"

---

### Post by RonRock on 2008-02-07
Thank Everyone for help with this issue. I will not be with my Linux computer today,  will be back to it tomorrow. I will then follow the last advice given and post back. 

I'll be back, Thank You,
Ron

---

### Post by RonRock on 2008-02-11
Thanks Everyone, I got it working. Yee Haa! I can now send files from Linux to Windows, and back. Probably only need to do that once, but now I can.

Now I'll be moving on. Anybody know anything about a "Squid" server? I'll search, but LMK if you have anything. 

Thanks To All Who Helped.
Ron


How do I give Thanks? Up in the corner under "Beans" Now I got sum Beans, I want to shell out sum Thanks. I looked in FAQ but no mention.

---

