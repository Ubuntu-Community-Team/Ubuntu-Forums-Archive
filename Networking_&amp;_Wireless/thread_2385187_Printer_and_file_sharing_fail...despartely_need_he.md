---
title: "Printer and file sharing fail...despartely need help"
date: 2018-02-17
forum: Networking &amp; Wireless
---

### Post by Stan_Meissner on 2018-02-17
I am attempting to enable file sharing on my network.  Experience level is going on eight years using Ubuntu exclusively and I have never been successful setting up a nextwork with the exception of getting print sharing working one time on my old Dell PC's but that was entirely by accident.  My new computers I'm trying to network now are a Zareason desktop running Ubuntu Studio 16.04 and my wife's laptop is a System76 laptop running Ubuntu 17.10.  

I have attempted to follow several Samba setup pages and followed along with countless videos.  I'm not sure what category I would fall into as far as experience level but to put it in perspective I have been a home computer user for over 20 years and setup networking effortlessly in my "former operating system" using a simple gui.  With Ubuntu I have setup printers and just about everything else but when I get into terminal commands I have to rely on cut & paste as my skills aren't very sophisticated.  

The problem is that I have followed directions in terminal and either get stuck by an error message or in the case of the GUI run into tabs on the video that aren't showing up on my system.  I believe what's happening is that the folks writing the tutorials are leaving out some of the commands or assuming I know what to fill in blank lines.  I tried following a video using the Network settings tab but the window that came up does not have the sharing tab that appeared on the video.  

I love Linux but I'm totally frustrated by the complexity of file sharing and am about to give it up and get my wife a thumb drive for when she wants to print and tell her to use my desktop to view pics of the grandkids.  Are there any SIMPLE tutorials out there that terminal command challenged Linux user can copy and paste terminal commands to activate file sharing.

I'm extremely frustrated with the complexity of something that used to be a "no brainer" with a simple gui interface in my former OS.  Where I live out in the country security isn't an issue, nobody is going to get close enough to pickup my wifi.  Just want to share files and printer and not have to lose what little hair I have left in the process.

---

### Post by Stan_Meissner on 2018-02-17
I can see the name of my computer on my wife's laptop but can't access the public folder or see the printer.  I guess that means I'm moving somewhat in the right direction.

---

### Post by Morbius1 on 2018-02-17
Probably can't help you with the printer issue but may be able to help with the file sharing issue.

From your computer post the output of these commands so we can see how you are set up:
```
testparm -s
```
```
net usershare info --long
```
```
hostname
```

---

### Post by Stan_Meissner on 2018-02-17
Thanks, I will try that.  I got the printer working so I can give myself a pat on the back for that.  Can see the network from her laptop.  Got all setup for recording audio and doing layered graphics on a wine layer and a bunch of other favorite applications but still stuck on file sharing.  I'm a senior citizen 66 y/o and if you listen to the young folks I should still be stuck trying to figure how to turn the thing on.  Not bad for an old guy even if i do end up giving up and buying her a thumb drive for file transfer.  Seriously though, I'm close and will try your suggestions for file sharing.

---

### Post by Stan_Meissner on 2018-02-17
testparm -s

rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
stanley@Limbo-6330a:~$ 


net usershare info --long  (not getting any results for this command)


hostname
Limbo-6330a

---

### Post by Morbius1 on 2018-02-17
You have no shares defined so there is nothing for the other machine to access.

What I would suggest is this:

[1] Make believe you are using WinXP.

[2] Open your file manager, right click your Public folder, select Local Network Share, and fill in all the boxes like this:
[ATTACH=CONFIG]278573[/ATTACH]
You may get a request to install something ... select[B] Install service
[/B]Then it will ask you if you want it to adjust permissions - you do.

You just created a samba share. We may need to make an adjustment but for now:

[3] Go to the other Linux machine, open a terminal, and run this command:
```
nautilus smb://Limbo-6330a.local
```

You should see the Public share listed.

I will be away for a while but I will check up on you - worst case - tomorrow.

---

### Post by Stan_Meissner on 2018-02-18
Thanks, I should get an opportunity to work on it later today after the Daytona 500.  ;)

---

### Post by Stan_Meissner on 2018-02-18
I followed your instructions word for word and when I right click on the public folder there is no sharing tab.  I get a dialog box that says basic, emblems, permissions and notes.  I used the command that you gave on my wife's laptop and it did install some software.  I can see my computer from hers and her computer from mine and the print function works.  This is all the further I have been able to get on networking since switching to Ubuntu in 2010.  The only time I dig down this deep in Ubuntu is when I setup a new computer, after that it basically works problem free until the hardware fails or I decide to buy something new.

So to sum it up printing is working on the network and I can see the other computer from each but I can't activate the public folder for sharing.  Hopefully this will make sense to you as I am not seeing a sharing dialog box anywhere.  By the way, I run Ubuntu Studio 16.04 and I use the Mate desktop environment in case that makes a difference.  Thanks.

---

### Post by Morbius1 on 2018-02-19
> By the way, I run Ubuntu Studio 16.04 and I use the Mate desktop environment in case that makes a difference.
Yep. That explains everything and makes all the difference in the world. For reasons unknown MATE's file manager ships without all of it's parts installed. You need to install this package:
```
sudo apt install caja-share
```
Then logoff and log on again - you may have to reboot - to be honest I don;t remember.

Then right click your Public folder and select: **Sharing Options. **You can also select** Properties **and then the** Sharing **Tab if that is the way you want. Either way you will see the same dialogue box as I posted above.

**[COLOR=#0000cd]I can not emphasize this enough[/COLOR]: **When you post a question to the forum always tell people what Desktop Environment ( MATE in this case ) you are using first. Each desktop environment has it's own bugs, design flaws,  and peculiarities.

---

### Post by Morbius1 on 2018-02-21
Just so happens I was helping someone else with Ubuntu Studio and she also claimed her desktop was MATE. None of the things I was telling her to do seemed to work so I downloaded it and ran it live.

I double clicked "Home" on the desktop to open the file manager ... and  ... um ... Thunar opened up. The default desktop environment in Ubuntu Studio is XFCE not MATE. There is no samba usershare implementation in XFCE so if you want to share your public folder you need to go old school:

[COLOR=#0000cd]*Note: I had to install samba first:*[/COLOR]
```
sudo apt install samba
```

Edit /etc/samba/smb.conf:
```
gksu mousepad /etc/samba/smb.conf
```
At the end of the file add your share definition - replacing morbius with your own login user name:
```
[Public]
path = /home/morbius/Public
read only = No
guest ok = yes
force user = morbius
```
Save the file. Then restart smbd:
```
sudo service smbd restart
```
From my current client machine I can see the server and it's share:
[ATTACH=CONFIG]278610[/ATTACH]
Now maybe you installed MATE on top of XFCE but I'm guessing you did not.

---

### Post by Stan_Meissner on 2018-02-21
I just wanted to thank everyone for their assistance.  This all took a turn for the worse after running and setting up Studio for a couple days.  Studio locked up on startup with an (initramfs) error.  I just bough this computer from Zareason a week ago and they don't include a disc so I could boot from disc and get into terminal so I used my wife's System76 laptop to download a copy of Studio and ran to Office Max in a Minnesota snow event to get a spare thumb drive.  After trying to fix the problem in terminal (couldn't get in) and three attempts to install Studio and having it freeze in the middle of install I decided to try Mint.  It worked fine for a couple of days and I didn't do much of anything besides bookmarks and a little organizing but somehow I came up with a broken packages error and then this another error about a critical issue or something to that effect.  I'm not a terminal expert, just good enough to search forums and use posted directions but nothing I found resolved the issues either.  Finally I decided tonight to install the standard Ubuntu 16.4.03 LTS that comes bundled with their computers.  So far so good but just to be safe I unplugged the printer and am taking things slow documenting each thing that I install.  Aside from wine and two windows programs that have worked flawlessly on my former machine and a few of my favorite open source programs from the repository and approving updates I can't see how I could have caused all these problems.  My Dell that just fried the MB was a Optiplex 760 with beefed up memory and two HD's that I added and I NEVER had any issues with Studio, it ran for five years until the hardware failed.  Likewise my wife's System76 laptop, we took it out of the box last fall, set it up, entered her password and haven't had any issues or error messages.  She even updated the firmware that they pushed for the processor using their instructions and she's basically an email, banking, surfing and online shopper.  Anyways I'm going to keep my fingers crossed that this third OS is the charm and I won't come up with any other issues.  I'm still scratching my head because I have never had any problems with Linux that I couldn't solve up to and including laptop wireless work arounds but I'm not above admitting that there could have been some operator error.  I don't think it's a hardware problem and this seems like a nice system but I have wasted a week getting setup over and over and over.  Anyways, thanks for the help and I apologize if I caused anyone extra work.  Hoping since 16.4.03 is the OS Zareason bundles with new builds that we're finally in a good place with Ubuntu.  I'll be back here when I get back to the networking but that could be a week or two.

---

