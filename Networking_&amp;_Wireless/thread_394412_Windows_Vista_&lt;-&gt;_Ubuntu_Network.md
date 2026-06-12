---
title: "Windows Vista &lt;-&gt; Ubuntu Network"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by postalservice14 on 2007-03-26
I have a Windows Vista machine that serves my files and a Ubuntu laptop connected to the same Router.

How can I access each others files?

Thanks,

John

---

### Post by BrianK on 2007-03-26
I don't have Vista, so can't say specifically, but with XP, at least, you had to assign ceratin folders as shared folders (with right-click & then the sharing tab).  You can then access those files via the Ubuntu machine by clicking on "Places > Network Servers" and browsing for your Windows machine (which should have a name assigned to it).

At that point, put whatever files you want to move beween computers in that share folder & you can push or pull from your laptop.

Outside of that, you can setup Ubuntu to connect to your Windows shares via samba & vice versa, but that's a bit more complex.

---

### Post by postalservice14 on 2007-03-26
Thanks Brian for you response,

I recently upgraded to Vista from XP.  When I had XP, you're right and I had to problem sharing.  I believe there is an added level of security on Vista that I have been unable to find?  I have multiple folders shared and accesible from other XP machines.  I even setup a username that is identical to my Ubuntu username and gave it admin privilages, just to test.

I have tried disabling firewalls and all kinds of stuff.  Unfourtunatly none of the XP forum posts that I have found on the forums have worked.  So I thought I would try to create this, more specific to Vista, post.

Anyone out there who has this setup or similar working, please help...

Thanks again Brian,

John

---

### Post by dmizer on 2007-03-27
okay ... i don't have vista, but i think we can plunder through this.  if you bear with me, it may take a bit of effort, but i think this is something that needs to be hammered out.  i'll need some information from your vista machine first though.

in vista, i'll need the computer name and work group.  to find this, you'll need to do the following ([microsoft tech net](http://www.microsoft.com/technet/network/evaluate/vista_fp.mspx)):
> To find out the existing workgroup name for a computer running Windows Vista, click Start, right-click Computer, and then click Properties.

In the System window, the workgroup name is listed in the Computer name, domain, and workgroup settings section.

---

### Post by postalservice14 on 2007-03-27
Great!  Thanks for being willing to help me through this.  Here is my computer information:

VISTA DESKTOP
My workgroup is the default: MSHOME
My computer name is: john-desktop

UBUNTU 6.10 Edgy Eft LAPTOP
Host name: john-laptop
Domain name: {blank}

Also note, my laptop does have internet access through the wireless.  Just FYI.

John

---

### Post by dmizer on 2007-03-28
okay ... lets prep the ubuntu box for domain name resolution in a windows network environment (please run these commands even if you have already done it in the past).  all commands that follow can be simply copy/pasted into your terminal and executed.

we'll need samba file system:
```
sudo aptitude install smbfs
```

edit your nsswitch file:
```
gksudo gedit /etc/nsswitch.conf
```
search through the file and look for the line that looks something like so:
> 
hosts: files dns
[COLOR="Red"]note:[/COLOR] (it might have other hosts listed like "mdns" or such, but there will only be one "hosts:" line)

and add "wins" to the end of the line so it looks something like this:
> 
hosts: files wins dns

save and exit the file.

install winbind:
```
sudo aptitude install winbind
```

now lets set you up to join the same workgroup.

install samba server:
```
sudo aptitude install samba
```

backup your samba template.  this will save any previous samba settings you may have already implimented so we can start from scratch:
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.template
```
(if you need to restore this file, just rename smb.template to smb.conf)

make a new smb configure file:
```
sudo touch /etc/samba/smb.conf$$gksudo gedit /etc/samba/smb.conf
```

past this in the file:
```
[global]
    ; General server settings
    netbios name = john-laptop
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    name resolve order = hosts wins bcast

    wins support = no
    syslog = 1
    syslog only = yes
```

save and reboot ubuntu.  then open firefox and enter this in your address bar:
> smb://mshome/john-desktop

if you get results from this, post them (screen shot, or list is fine) ... if not, let me know.

---

### Post by postalservice14 on 2007-03-28
Ok, a few things.  First off, I upgraded to Ubuntu 7.04 today.  I figure what we are doing needs to work with the latest version, and it is about to get released.

I did everything you said and at the last step I put the smb:// url into firefox and it sent me a text file download with the following in it:

[Desktop Entry]
Encoding=UTF-8
Name=john-desktop
Type=Link
URL=smb://john-desktop/
Icon=gnome-fs-server

I took the liberty to jump ahead (hope you don't mind :-) ).....I saved it to my desktop to create a link.  Double clicked the link and it asked me for my username and password, so I logged in and was able to access my shared folder on my Vista machine....woohoo!  thanks a million.

One thing about it though, is I am unable to read or write to that folder.  I tested it with a text file on the Vista machine and I can't open it on the Ubuntu laptop.  Any ideas?

Let me know if you need screenshots of anything.

Thanks again,

John

---

### Post by dmizer on 2007-03-28
yeah ... we're not done yet.  lol

post the output of:
```
smbtree
```
it will ask for a password.  don't enter one, just hit the enter key

if you don't get any results this way, try this instead:
```
smbtree --user=winlogin[winpassword]
```
of course ... replacing winlogin and winpassword with your respective equivalents.

ps. delete the link you created on your desktop, it won't be of much use to you.
pps. it wouldn't have mattered if you upgraded or not.

---

### Post by brennydoogles on 2007-03-28
> **postalservice14 said:**
> Thanks Brian for you response,

I recently upgraded to Vista from XP.  When I had XP, you're right and I had to problem sharing.  I believe there is an added level of security on Vista that I have been unable to find?  I have multiple folders shared and accesible from other XP machines.  I even setup a username that is identical to my Ubuntu username and gave it admin privilages, just to test.

I have tried disabling firewalls and all kinds of stuff.  Unfourtunatly none of the XP forum posts that I have found on the forums have worked.  So I thought I would try to create this, more specific to Vista, post.

Anyone out there who has this setup or similar working, please help...

Thanks again Brian,

John

The short time I used Vista I couldn't get it to communicate with other Windows Machines... let alone Linux. It is still quite buggy.

---

### Post by postalservice14 on 2007-03-28
> **brennydoogles said:**
> The short time I used Vista I couldn't get it to communicate with other Windows Machines... let alone Linux. It is still quite buggy.

I was beta testing Vista throughout Beta 1, Beta 2, RC-1 and RC-2 and all of those were extremely buggy.

I purchased Vista a few days after it came out and was very impressed at how it was much more stable.

Did you purchase Vista and it wasn't able to communicate with any other machines?  Or are you referring to the BETA products.  Cause, yes, those were very very buggy.

dmizer, I'm at work right now, I'll try what you suggested when I get home.

John

---

### Post by Armagedon225 on 2007-03-28
Im also a noob to networking on ubuntu and am following this thread. Anyway this is what I get when I input "smbtree" into the terminal.

        \\WINDWAKER      
                \\WINDWAKER\ADMIN$              IPC Service ()
                \\WINDWAKER\IPC$                IPC Service ()
        \\FAMILYCOMPUTER                Family Computer
                \\FAMILYCOMPUTER\SharedDocs     
                \\FAMILYCOMPUTER\print$                 Printer Drivers
                \\FAMILYCOMPUTER\IPC$                   Remote IPC

Oh and I also get my work group name to but I left that out.
And just to mention my desktop (Familycomputer) is running windows xp.

EDIT:
I forgot to mention that I trying to make my desktop be able to get stuff of my ubuntu laptop. I already have it setup to get stuff off the desktop onto my laptop.

---

### Post by dmizer on 2007-03-28
@Armagedon225:
well all the directions up to this point have been related to getting ubuntu to see vista.  getting vista to see ubuntu is next in line, but should be significantly easier.  if you care to jump ahead, take a look at the first link in my sig for the howto.

---

### Post by postalservice14 on 2007-03-29
Ok,

I had to try a lot of different things to get it to display anything.  I think samba wasn't started or something?  cause I tried smbtree and nothing happened at first.  So I connected to smb://john-desktop then tried it and it display the following using just "smbtree":

MSHOME
        \\JOHN-LAPTOP    
                \\JOHN-LAPTOP\IPC$              IPC Service ()
        \\JOHN-DESKTOP                  John's Desktop Computer
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine JOHN-DESKTOP.  Error was NT_STATUS_ACCESS_DENIED

Thanks,

John

---

### Post by dmizer on 2007-03-29
okay ... we're still getting blocked by vista.  lets look a bit deeper at vista.  change and/or double check all of the following settings.

make sure that your location type is set to "private"

click Start, right-click Network, and then click Properties.

The Network and Sharing Center window displays the network location type in parentheses after the network name.

If your network type is Public, do the following:

1. To the right of the network name and location type, click Customize.

2. In the Set Network Location dialog box, click Private, and then click Next.

3. In the Successfully set network settings dialog box, click Close.

Then make sure that File and printer sharing is enabled:

1. In the Sharing and Discovery section of the Network and Sharing Center window, click the down arrow next to File sharing.

2. Within the File sharing settings, click Turn on file sharing, and then click Apply.

now, you've said that you've already added your ubuntu username and pass to your vista machine, so let's see if you can get results from smbtree after these changes.

---

### Post by postalservice14 on 2007-03-29
Hi,

After going through your suggestions the only thing that needed to be changed was file sharing.  I changed it from "Turn on sharing so anyone with network access can open files" to "Turn on sharing so anyone with network access can open, change, and create files"

After running smbtree again, I got the same text.

John

---

### Post by dmizer on 2007-04-01
okay.  let's see if vista actually sees that your shares exist.

1. Click Start, right-click Network, and then click Properties.

2. Under the "Sharing and Discovery" section of the Network and Sharing Center window, click "Show me all the shared network folders on this computer".

let me know if your share is listed there, and if so, what is the share name?

---

### Post by pudgewack on 2007-04-02
Sorry to steal the post, but I have the same probem with my laptop (running kubuntu) and my desktop running Vista Busniess.  I would like to be able to access all shared files, but the main thing I need to do is be able to print on the printer hookep up to my Vista PC.  Here is the info about my computer:

Vista Desktop
Computer Name: Office-PC
Workgroup: WORKGROUP

I followed all of the steps earlier in the post.  When I run "smbtree" in konsole, I get this output:

WORKGROUP
        \\OFFICE-PC
        \\BIGELOW-LAPTOP
                \\BIGELOW-LAPTOP\ADMIN$                 IPC Service ()
                \\BIGELOW-LAPTOP\IPC$                   IPC Service ()


When I run smb://WORKGROUP/Office-PC or smb://Office-PC, I get a pop up error message saying:
"Firefox doesn't know how to open this address, because the protocol (smb) isn't associated with any program."

Any help would be greatly appretiated.  As you can probabaly tell, I am a newbie to linux.

Thanks in advance,
Matt


Edit:  Forgot to mention..... when I look at what is shared in Vista, it shows my printer and the drive containing most of my multimedia (which is all that I want to share).

---

### Post by dmizer on 2007-04-02
@pudgewack:

okay ... postalservice14 has already done this, but we need to take another step in vista here:

take a look at the following settings ...

1. In the Sharing and Discovery section of the Network and Sharing Center window, click the down arrow next to Public folder sharing.

2. Within the Public folder sharing settings, click one of the following according to your needs:

[LIST]
[*]([COLOR="Red"]readonly[/COLOR]) If you want to share the public folder so that other computers on the network can access the Public share to open files, but not create or change files, click Turn on sharing so anyone with network access can open files. This is the default setting.

[*]([COLOR="Red"]read/write[/COLOR]) If you want to share the public folder so that other computers on the network can access the Public share to open files and also create or change files, click Turn on sharing so anyone with network access can open, change, and create files.
[/LIST]

3. Click Apply.

this should enable non-password protected file sharing.  if you need more secure, password protected sharing, it will require more configuration.  try smbtree again and see if you get better results.

---

### Post by dmizer on 2007-04-02
let's add one more thing here that i don't think has been covered:

1. In the Sharing and Discovery section of the Network and Sharing Center window, click the down arrow next to Password protected sharing.

2. Within the Password protected sharing settings, click Turn off password protected sharing, and then click Apply.

---

### Post by pudgewack on 2007-04-02
dmizer,
thanks for the help.  I have already enabled file sharing and selected the option to read/write.  But I still not get get my linux let me access the windows network. I am able to access my laptop from my Vista PC, I just can not access my PC from the laptop.

A couple more optons have been added when I run smbtree.  Here is the output:

WORKGROUP
        \\OFFICE-PC
        \\BIGELOW-LAPTOP
                \\BIGELOW-LAPTOP\ADMIN$                 IPC Service ()
                \\BIGELOW-LAPTOP\IPC$                   IPC Service ()
                \\BIGELOW-LAPTOP\MyFiles
                \\BIGELOW-LAPTOP\print$

Anymore ideas?

Matt


edit:   I also have already turned off password protected sharing in the network and sharing center,  However, when I try to acess anything on windows machine or add a printer, I am still promted for a username/password

---

### Post by dmizer on 2007-04-03
@pudgewack:

1) what is the share name of your shared folder?

2) can you access the vista shared folder from another windows computer?

---

### Post by postalservice14 on 2007-04-04
> **dmizer said:**
> let's add one more thing here that i don't think has been covered:

1. In the Sharing and Discovery section of the Network and Sharing Center window, click the down arrow next to Password protected sharing.

2. Within the Password protected sharing settings, click Turn off password protected sharing, and then click Apply.

I have done this and get the following result with smbtree:

MSHOME
        \\JOHN-LAPTOP    
                \\JOHN-LAPTOP\ADMIN$            IPC Service ()
                \\JOHN-LAPTOP\IPC$              IPC Service ()
        \\JOHN-DESKTOP                  John's Desktop Computer


Is that good?  Looks like there is no more error.

John

---

### Post by dmizer on 2007-04-04
yes ... that looks better.  it's still not listing the share name, but we may be able to connect you now.  what is the network name of your shared directory (ie: what did you name it when you created it?)

---

### Post by postalservice14 on 2007-04-04
> **dmizer said:**
> yes ... that looks better.  it's still not listing the share name, but we may be able to connect you now.  what is the network name of your shared directory (ie: what did you name it when you created it?)

I have a few shares.  But one we can work with is Recorded_TV.

John

---

### Post by jsully1 on 2007-04-04
This doesn't work for me unfortunately - Nautilus keeps asking for my username and password, and just won't accept them.

Doing a sudo mount -t smbfs with the same credentials works mounts it read/write just fine though.  The Vista PC doesn't show up in smbtree's output, but I can ping it by IP and name (entry in host file)

Any ideas?

---

### Post by pudgewack on 2007-04-04
> **dmizer said:**
> @pudgewack:

1) what is the share name of your shared folder?

2) can you access the vista shared folder from another windows computer?


1.  One of my shared folders is called \\Office-pc\I\Music

2.  Yes, I can access my Vista machine when I boot into XP on my laptop.  One thing that is strange is that I have disabled password protect sharing, but when I connect with my laptop (using XP), it still asks for a password.  I type the username/password and it takes me to the shared files and everything works fine (still in XP).

When I try to connect to Vista in linux, it still asks for a username/password (just like in XP), but will not accept it.

---

### Post by jsully1 on 2007-04-04
I have the same issue you do - try this...
Say your Vista PC is Vista1, and you're trying to get the Music share with your user Eric, password 12345:
First make sure you can ping your Vista machine by name:
```
ping Vista1
```
if you can, then make a directory to mount the share in locally:
```
sudo mkdir /mnt/Vista1
```
and then mount the music share there:
```
sudo mount -t smbfs //Vista1/Music /mnt/Vista1/ -o username=Eric,password=12345
```

That should mount the Music share on Vista1 in /mnt/Vista1 - take a look to see if it worked.

You can do a 
```
sudo umount /mnt/Vista1
```
to unmount the share.

---

### Post by adriantry on 2007-04-04
Hi John - you're having a Vista specific problem!

> **postalservice14 said:**
> I have a Windows Vista machine that serves my files and a Ubuntu laptop connected to the same Router.

How can I access each others files?

I was recently trying to help a Mac user access shared files on her new Vista machine. It seems that MS have changed their networking so that it only works with Windows by default. I think that's called MS security! I read several forums about this at the time (most talking about changing settings in the Vista group policy editor), but couldn't get it working - the Dell she bought didn't seem to come with the group policy editor. Perhaps that's only available in the Ultimate edition?!?

I had been assuming that the same problem would effect Ubuntu, but haven't had the opportunity to check.

Here are couple of Mac sites that talk about the same problem, with some suggestions that may work. (One day I'll go back and try to get this Mac working again!)

[http://www.marialanger.com/2006/12/05/file-sharing-mac-vista/](http://www.marialanger.com/2006/12/05/file-sharing-mac-vista/)
[http://forums.mactalk.com.au/showthread.php?t=25292](http://forums.mactalk.com.au/showthread.php?t=25292)

And here is a helpful(?) Microsoft page on the changes they made to networking in Vista:
[http://www.microsoft.com/technet/network/evaluate/vista_fp.mspx](http://www.microsoft.com/technet/network/evaluate/vista_fp.mspx)

Adrian

---

### Post by imminentwill on 2007-04-04
> **adriantry said:**
> 
[http://forums.mactalk.com.au/showthread.php?t=25292](http://forums.mactalk.com.au/showthread.php?t=25292)


Hi Adrian, thanks for the tip. Following the instructions in your link worked for me. I'm running a Vista Ultimate and Ubuntu Feisty box on a local network and I could never get the share mapped properly. I'm finally getting somewhere now.

I can finally browse to my Vista box from Firefox but only after I've logged onto my machine for a few minutes. It's almost as if Ubuntu has to warm up before I can access any SMB shares.

Thanks again, hopefully I can get my network share mapped and ready to go.

EDIT: My Vista share is now fully accessible from Ubuntu Feisty. I had to remove Portmap from my Ubuntu box before it would work, however, and my system would hang on shutdown if I used CIFS, so I switched to SMBFS. Now all's right with my network. Thanks to dmizer and Adrian for their help and advice.

Colin

---

### Post by dmizer on 2007-04-04
> **postalservice14 said:**
> I have a few shares.  But one we can work with is Recorded_TV.

John

let's try mounting this thing.  first, we need a place to mount it.  create a folder in /media so that later, the folder will show up on your desktop.  also, we will need to change the permissions of this folder so it's writeable.  you can call it what you like, but you should use something that distinguishes it from the other folders, like so:
```
sudo mkdir /media/desktop-tv
sudo chmod 777 /media/desktop-tv
```
once that's done, now we can try mounting the folder:
```
sudo mount -t cifs //john-desktop/recorded_tv /media/desktop-tv -o guest,rw,file_mode=0777,dir_mode=0777
```

now open up your file browser (nautilus) and browse to /media/desktop-tv and see if you can save to the folder.  if you can, then we'll need to make a similar mount command to add to your fstab so the folder will appear on your desktop when mounted.

if it doesn't work, let me know and we'll try to come up with something else.

---

### Post by bobbob1016 on 2007-04-05
Not sure if this helps, but I have the same problem, I can't connect to Vista through the GUI.  I can however when I type:

sudo mount //192.168.0.***/***** /media/point/ -o username=winlogin,password=winpassword,dmask=777,fmask=777

In the terminal, it shows up as a mounted drive.

---

### Post by dmizer on 2007-04-05
@bobbob1016:
the problem you describe is a shortcoming of nautilus, not of vista, or ubuntu and is not the same problem experienced by the original poster.

connecting to samba shares via gui has been a fairly typical issue when trying to connect to shares hosted from any os (xp, vista, linux or otherwise).  your best bet is to add a line into /etc/fstab and let your computer mount automatically, or add the "noauto" option, and mount with the following command:
```
sudo mount /media/point
```

this allows for the following conditional improvements over nautilus:
1) much higher file transfer speeds
2) less packet/data loss during transfer
3) file transfers of over 2gb (when using cifs)
4) more stable file transfers
5) better connection to the server
6) less network traffic
7) better support for non-latin characters

there are other options available for you to mount with a gui interface, but i'm not sure if they work any better than gnome's native nautilus.

---

### Post by bobbob1016 on 2007-04-06
I wasn't saying that it was a problem, I was offering help.  Since it worked for me, I thought it might work for others.

---

### Post by jsully1 on 2007-04-06
> **dmizer said:**
> @bobbob1016:
the problem you describe is a shortcoming of nautilus, not of vista, or ubuntu and is not the same problem experienced by the original poster.

connecting to samba shares via gui has been a fairly typical issue when trying to connect to shares hosted from any os (xp, vista, linux or otherwise).  your best bet is to add a line into /etc/fstab and let your computer mount automatically, or add the "noauto" option, and mount with the following command:
```
sudo mount /media/point
```

I like the idea of being able to quickly and easilly mount shares without the whole long command I mentioned work for me.  Can you elaborate on what I'd want to do with fstab?  I like the no auto option too, since this is a laptop and I take it between work and home.

---

### Post by dmizer on 2007-04-06
sorry for misunderstanding bobbob1016.

@jsully1
okay ... you said you were manually mounting using this line :
```
sudo mount -t smbfs //Vista1/Music /mnt/Vista1/ -o username=Eric,password=12345
```
but noauto is not a valid option for smbfs, so we'll have to switch you to cifs.  first, edit fstab:
```
gksudo gedit /etc/fstab
```
and add this line to the end:
```
//Vista1/Music /mnt/vista1 cifs [COLOR="Red"]noauto[/COLOR],username=Eric,password=12345,file_mode=0777,dir_mode=0777 0 0
```
now you can mount your share by typing:
```
sudo mount /mnt/vista1
```

just a note of security, you might browse through my howto in the second link in my sig and look for the section about creating a credentials file.  your username and password will be much more secure when using a credentials file.

---

### Post by fettuohi on 2007-04-14
This might be a bit of topic for this thread but has anybody been able to get Vista to your samba shares?

Regards

André

---

### Post by dmizer on 2007-04-15
getting vista to see your samba share shouldn't be any different than getting win xp to see your samba share.  try the first link in my sig.

---

### Post by carusoswi on 2007-04-15
> **dmizer said:**
> okay 

past this in the file:
```
[global]
    ; General server settings
    netbios name = john-laptop
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    name resolve order = hosts wins bcast

    wins support = no
    syslog = 1
    syslog only = yes
```

save and reboot ubuntu.  then open firefox and enter this in your address bar:

.

When I open this file to paste in the above, I find that it is read only.  If I try to change permission settings, I am told that I am not the owner.

What am I doing wrong?

Caruso

---

### Post by carusoswi on 2007-04-15
managed to change the file.  Before I did all this, my new installation of Samba was detecting and showing the other machines on my network. Afterwards, it sees nothing, so I did something wrong.

I tried uninstalling Samba and then installing it again, but that didn't work, as, somehow, the reinstalled ap remembers the configuration from before.

I could use some help at this point.

Thanks!

Caruso

---

### Post by dmizer on 2007-04-15
middle of the night for me when you posted.  sorry i'm a bit late.

in the post i explained that you should back up your old smb.conf file with this command: ```
sudo mv /etc/samba/smb.conf /etc/samba/smb.template
```

to restore your old settings, simply reverse the command:
```
sudo mv /etc/samba/smb.template /etc/samba/smb.conf
```

restart samba:
```
sudo /etc/init.d/samba restart
```
and you should be able to view your ubuntu shares from vista again.

---

### Post by MiD-AwE on 2007-04-16
I have a similar problem; I believe. Only, I dual boot Ubuntu7.04beta with Vista. 64bit dual core AMD64 4600+. I can connect to WAN in Ubuntu by switching my modem from USB to Ethernet and vise versa if I loose connection. But, If I boot to vista I have no connection. So to remedy, I have to shutdown and sever my modem from the physical computer. Wait about 30 seconds and reconnect everything. Then, I boot into vista and all is well. 

Do you think that this information can help me as well?

Thanks for any reply.:D

---

### Post by dmizer on 2007-04-16
> **MiD-AwE said:**
> I have a similar problem; I believe. Only, I dual boot Ubuntu7.04beta with Vista. 64bit dual core AMD64 4600+. I can connect to WAN in Ubuntu by switching my modem from USB to Ethernet and vise versa if I loose connection. But, If I boot to vista I have no connection. So to remedy, I have to shutdown and sever my modem from the physical computer. Wait about 30 seconds and reconnect everything. Then, I boot into vista and all is well. 

Do you think that this information can help me as well?

Thanks for any reply.:D

no ... this information is about file sharing, not connecting to your wan.  your best bet for a fix on this is to purchase a hub (if your modem can to NAT), or a router (if your modem cannot do NAT)

you can tell if your router can do NAT by checking the following:
browse to [www.whatismyip.com](www.whatismyip.com) and make a note of the ip address shown.

then, in terminal, type: *ifconfig*
and look at the ip address reported there.  if these are different, your modem is probably doing NAT and you can fix the problem by purchasing a hub (cheap).  if they are the same, your modem is not doing NAT and you will need to purchase a router (still cheap if you do not purchase a wireless router).

---

### Post by MiD-AwE on 2007-04-16
Thank you. The ip addresses match so it looks like I've got to find a router. Thanks again for your advice.

---

### Post by apsalyers on 2007-04-20
Having the same issue, networking Ubuntu to vista.

---

