---
title: "Cant see linux shares, only windows"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by jeepintx on 2007-12-10
My problem is i cant get samba to work reliably, sometimes it works and all my computers talk to each other just fine. I have a laptop running ubuntu 7.10 a desktop running XP and my xbox running xbmc. Most of the time my linux shares wont show up on the network and i can only see the windows xp shares. Any ideas as to what could be causing this?

---

### Post by tyggna1 on 2007-12-10
This isn't a good answer, but it is an answer:

From windows 98 to Vista, Microsoft's file-sharing transfer protocols have been crap.  I believe that is putting it nicely.  Let me share with you my experience of using MS file-transfers:

98 -  Had a hub and two computers,  both with static IP addresses, and after 4 hours of tinkering with every setting, I got a ping to work sucessfully.
NT -  Two computers, wanted to transfer a single file using a cross-over cable. . .ended up spending $20 on two floppy drives.
XP -  Could get wired shares to work and sometimes transfer over a linksys router--wireless shares unavailable always.  After about two weeks of working properly, decided to give out, had to reinstall windows before it would work again.  Problem persisted--and needed a full OS reinstall every two weeks.
Vista - If the TCP/IP stack doesn't have an absolutely immaculate birth, then it will just give you dumb looks and messages when you ask for network shares.

Now, for my experiences with NFS:
Gui has never worked for browsing files--but if I mount the share, then it works flawlessly, and has never given me any problems.  Adding it to my fstab made it so I could have my music/pictures/movies available anywhere in the house.

My recommendation--[set up XP to use an NFS client]("http://support.microsoft.com/kb/324055")
[You might need this too]("http://www.microsoft.com/downloads/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en")

---

### Post by jeepintx on 2007-12-10
Thanks for the quick reply, Im not sure if i made myself completely clear on my first post. Im trying to make my share show up for my xp machine and XBMC on my xbox it works about 15% of the time then the rest of the time no linux shares are visible.


ok new problem lol, after messing with it the only share that i can show is MyFiles which isnt even a share that i have. I checked the samba config and there is no listing of that anywhere. I have posted my smb.conf file and it has no mention of the myfiles share only the correct one that does not show up called Videos. Thanks in advance :)


[global]
    ; General server settings
    netbios name = brandon
    
    workgroup = Workgroup
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/brandon/videos
    
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = brandon
    force group = brandon
available = yes
browsable = yes
public = yes
writable = no

---

### Post by jeepintx on 2007-12-10
ok guys thanks for the help, i figured out the problem "i think" i set everything to static ips and am having no problems now

---

### Post by tact on 2007-12-10
*chuckle*  Good luck.  Static IP will take one variable out of the equation.  :)

I think a good point to take from tygnna1's post is that even peer networking of windows machines to windows machines has its challenges.  Windows peer networking is problematic at best and depending on how long it takes for browsemaster elections and other overheads to do their bit (this is all microsoft - nothing to do with samba or linux) it can take a LONG time for shares to show up when browsing networks.

All that said.  You can work around microsoft, and microsoft peer networking,  limitations to a degree.

Before your any share on an ubuntu machine will have a chance to show up at all in the browse lists of windows machines you gotta be sure that you have truly shared the folder.  :)  Yes its too obvious I know but I am starting at the beginning.

Clicking on System>Administration>Shared folders ....  there is at least one folder shared right?  Check properties ...  it is shared as "Windows Networks - SMB", right?

Now go to the actual folder you have shared....  Places>Home Folder....navigate til u can see the folder thats shared....   Right click on that folder and check its properties>Permissions tab.

Make sure that the permissions for "Others" will allow them to access the folder (read only or read/write).

Now if all that is good - on any of the windows machines browse the network and see if you can see the ubuntu machine and its share(s).   If its not visible then use the "Find a computer" function in windows network browser..  type in the ubuntu machine name.  Even if it is not (yet) showing in browse lists it is likely able to be found in a search.

If it can be found in a search it will eventually show up in windows network browser.  One fine day...  and if it is there some days and not others... call Bill and ask.  Its a windows networking feature.  :)

---

### Post by rechick on 2007-12-10
Just a couple of  things to check:
When Ubuntu turns on SMB shares it does not create a password for SMB for the current users. That must be done manually:
sudo smbpasswd -r username

Second: WIndows relies on WINS for peer to peer networking and a standard windows XP box will try to negotiate for the master list but not always compatible with other systems. Thus it is usually helpful to turn on the checkmark to make your linux (ubunbtu) box a WINS server.

Finally: Be sure the workgroup name in the smb.conf file matches the workgroup used in your network. By default setting the workgroup in networking does not make the equivacal change in smb.conf. That must be done manually.

Just some hints.

---

