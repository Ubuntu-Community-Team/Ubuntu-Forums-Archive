---
title: "First attempt at networking: Difficulty level - Vista"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by Cornbreadly on 2007-02-08
Who is ready to invest some time?

I am!

This be my first attempt to set-up a home network.  And I am having problems.

I use the "more experienced" pc downstairs now exclusively, and my wife will now be using a shiny new laptop with vista.  

So far, successfully, everyone has internet access and ubuntu can see the "windows network" in the network servers app.  I have been unsuccessful in the following:

-Getting Vista to see my ubuntu desktop
-Seeing the "windows network" is different from accessing it from ubuntu
-Using my printer, connected to the ubuntu desktop, to be used by vista, through cupsys

When all said and done...
-Being able to share folders on both PCs with each other, and being able to print, using Vista, through, through cupsys
-Hopefully no permission restrictions

Maybe unrelated but something that may point to my troubles...
-getting my DNS settings to use the opendns servers.

I have altered the dhclient.conf and get an error relating to "SIOCSIFADDR: No such device" when I attempt to restart the network.
As for my network problems,[URL="http://ubuntuforums.org/showthread.php?t=351078&highlight=network+xp+ubuntu"]
 this thread looks close [/URL]but when I read the [samba walkthrough]("https://help.ubuntu.com/community/SettingUpSamba"), it seems I don't need it to accomplish my goals.

Now I give up.  I am stressed that it is this hard to network the two together.  If I didn't hate Microsoft that much, it would be easier to just install xp again and get the network running in 10 mins.  Is their a witty, layman way to explain why it is so hard?

---

### Post by chili555 on 2007-02-08
I set up an XP computer just today to use a printer attached to my Fedora Core 6 desktop. I printed off my tax return (eh, by the way, can I borrow a few thousand?). I was greatly helped by this: [http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html](http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html)

The essential elements are to set your linux machine with a *static *IP address; set up printing on the linux machine to share; and amend the hosts file in the Windows machine to reflect the *static* IP address and hostname of the machine with the printer, such as:
```
192.168.1.103    tom-desktop
```

Also, I had instant success with this approach:
> To use a printer queue as a Postscript printer requires a Windows XP Postscript printer driver, such as the built-in MS Publisher Imagesetter

> To use the MS Publisher Imagesetter driver, use "Add Printer" to add a new network printer, select "Connect to a printer on the Internet..." and enter the URL for your printer queue (e.g. [http://rock:631/printers/Epson)](http://rock:631/printers/Epson)).  When prompted for a driver select a Manufacturer of "Generic" and the Printer "MS Publisher Imagesetter".


The url you enter will look something like: ```
http://tom-desktop:631/printers/printer
``` 
Play around with it a bit and Windows will only go forward if it likes your entry. Print a test page and you'll know it works!

---

### Post by Cornbreadly on 2007-02-08
That seems like it would make sense.

Is this a static IP between my router and my PC or is it one that I have to pay my SP for?

I could set this up but I still cannot test it because Windows does not "see" my linux machine.

---

### Post by chili555 on 2007-02-08
I assume your Ubuntu machine is the one with the printer attached. It needs to have a static IP address. We might as well use the one it has now. Open a terminal and do ifconfig eth0 (or whatever interface you are using) and you will see a line like this:```
inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
```

We will etch (no pun intended) this into stone. Open up System->Administration->Networking and highlight your interface. Click properties and change DHCP to static. Put in the IP address you found, 192.168.1.113 in my example. The subnet mask will  be the Mask number you found, 255.255.255.0 in my example. The gateway will be the IP address of your router, perhaps 192.168.1.1. You can check by  doing the command route -n. You will see a gateway number, Click OK and you should be all set.

Check your work by issuing the following commands: sudo ifdown eth0, and then, sudo ifup eth0. If the cursor pops back with no complaints or errors, then ping -c3 [www.google.com](www.google.com). You have a static IP now.

---

### Post by Cornbreadly on 2007-02-08
Success!

A few questions...

Now what should I look to do in configuring my router?  
Does it matter that i have a loopback interface (lo) running?
Does the vista box need a static IP?

Thanks.  I am ready for more learning.

---

### Post by chili555 on 2007-02-08
> Now what should I look to do in configuring my router?] Nothing. It connected and it's fine.

> Does it matter that i have a loopback interface (lo) running? Yes, it does. The mysterious lo is used by your computer to ....nobody knows for sure...leave it alone, like the plague.

> Does the vista box need a static IP? Nope.

Get your printer set up now and please print me off a check to IRS.

---

### Post by Cornbreadly on 2007-02-08
I think you overestimated what I consider success.  I was cheering my dominance over the terminal and by applying what you taught me to get a working static IP.

I still cannot "see" linux through the vista box.

I tried to ping the unique IPs they now have under the router from each PC with no success.  what is the next step to get them to play nicely?

---

### Post by Cornbreadly on 2007-02-08
Please bestow more knowledge upon me.

---

### Post by chili555 on 2007-02-08
First, let's see who is alive and who is not. On your Ubuntu box, sudo apt-get install fping. Then sudo fping -g 192.168.x.yyy 192.168.x.zzz where the two IP addresses represent what you estimate are the lowest and highest IP's you think you have in your system. In my network of six computers (might be excessive for just Mrs. Chili and me alone, doncha think?) I check who is naughty or nice with fping -g 192.168.1.98 192.168.1.120. 

If you get back a "192.168.1.116 is alive" for each computer, you know everyone can, hopefully, see everyone. Not necessarily their files, yet, but their existence on the network.

Sharing folders from linux to windows is a tough subject for me since I only use windows about five days a year. Perhaps this will help you get started: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_share_folders_the_easy_way](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_share_folders_the_easy_way)

---

### Post by jml on 2007-02-09
There is another possibility.  I do not have much experience with Windows Vista, (for which I am very grateful,) but it is advertised as being the "most secure Windows" ever shipped.  Is it possible that the reason that your computer running Vista cannot see the Linux box is because its an "untrusted" computer.  Could Vista's security "features" be the problem?  I don't have nay answers, just questions.

Joe

---

### Post by Cornbreadly on 2007-02-09
fping picked up no survivors.  I will be back tomorrow morning to attack this again.  Thanks for all of your help so far.

---

### Post by Cornbreadly on 2007-02-09
Ok.  I have successfully fpinged and found "alive" IPs.  I love that terminology, so full of hope.

Now it seems I need to edit my smb.conf to get my PCs to talk to each other. i am attempting that now.

---

### Post by Cornbreadly on 2007-02-10
Update... still lost and hatred growing for windows.  I wish I good be as happy and content as this [young black man here]("http://www.microsoft.com/windows/products/windowsvista/features/details/networking.mspx").  [This makes me nauseous]("http://www.extremetech.com/article2/0,1697,1931915,00.asp"). 

Anyways, back to trying to entice you to help me.  They can all ping each.  Ubuntu is static, and so is Vista now.  And now Vista can't always find the network through normal means (network sharing center).  But when it does, it can see the printer.  I cannot successfully log into the ubuntu network through vista with the username I specified.

Now my router has a DHCP server setting that is currently turned off.  I just gave everyone static IPs including my wii.  No relevance but the word is fun to use.  My question here is...

1) can I turn the dhcp setting back and keep ubuntu static?
2) will vista use the dhcp setting and still be able to network through samba?


I want to make vista dhcp because every time it reboots, it loses its settings.  Because it is for my PC illiterate wife, this can't happen.  Plus, vista seems to only see ubuntu through normal means, "network sharing center" every once in a while.  Though at all times I can successfully ping but only because I gave everyone static ips.  I wouldnt know how to under other conditions.

When I am at my ubuntu box, I can see the windows network but I am unable to actually browse it.  The folders I choose to share arent showing up.  Do I need to create a login on the windows box for this purpose?  When this does work, can to users be on the pc at once, one at the screen while the other is connected through the network?

Also, in Vista, I found a setting that turned on its use of a wins server.  Might be useful.  And here is some other [reference material that is a little out of my safety zone]("http://www.linux-watch.com/news/NS4434907782.html").  That "secpol" command isnt included in my one of thirteen vista release.  So I am at a loss there.

Im going to post some code now, to see if anyone can help.  Here is my "smbclient -L localhost -U%" showing that I am ready to share two linux folders but the vista laptop isnt showing up.

```
        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      
        fat_files       Disk      
        oldxp           Disk      
        IPC$            IPC       IPC Service (Samba 3.0.22)
        ADMIN$          IPC       IPC Service (Samba 3.0.22)
        DeskJet-5550    Printer   home
Domain=[HOME] OS=[Unix] Server=[Samba 3.0.22]

        Server               Comment
        ---------            -------
        ERIC                 Samba 3.0.22

        Workgroup            Master
        ---------            -------
        HOME                 ERIC

```

Here is my smb.conf  I think the problem might lie in here somewhere.

```

[global]
; General server settings
netbios name = eric

workgroup = HOME
announce version = 5.0
socket options = SO_KEEPALIVE TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192 
interfaces = lo, eth0
bind interfaces only = yes

passdb backend = tdbsam
null passwords = yes
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = yes

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes
security = share
restrict anonymous = yes
domain master = no
preferred master = no
max protocol = NT
ldap ssl = No
server signing = Auto

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
guest ok = yes
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


[fat_files]
path = /media/fat_files
guest ok = yes
read only = no

[oldxp]
path = /media/windows
guest ok = yes
read only = no

```

Thanks in advance for any help.  Please try to keep in mind my request for making Vista DHCP so that my wife doesnt kill me.

---

### Post by Cornbreadly on 2007-02-10
I switched my router to dhcp and kept ubuntu static.  So that worked.

Any ideas on why vista or my smb.conf arent allowing my pcs to talk to each other?

---

### Post by Cornbreadly on 2007-02-10
Almost Success!!!

I have now been able to gain access to my ubuntu shared files thru vista.  For those who want to know...

In network control center, there is a "view status" link for your connection.

view status->ip4 properties-> advanced->wins tab

Once there, input your linux box static ip if you enabled wins server and make sure netbios default is on.

Now, just a few more wrinkles.

I can now from ubuntu successfully get to the login screen in order to access the vista box.  But the login and passwords dont work.  I am going to try making a new user for vista and use those setting to login.

Next is more like an annoyance.  When I got to system-> network servers to access windows from ubuntu, the first icons that pop up are useless.  They are named correctly, but clicking on them brings an error.  After about two of three "reload" clicks, they are replaced by network location icons, and clicking on them brings me to the next step be it a login screen or files shared on the network. 

Will these be fixed if I mount those network connections somewhere?

---

### Post by Cornbreadly on 2007-02-10
I think I found out why the user didn't work when logging into windows.  [This explains it]("http://forums.techarena.in/showthread.php?t=670498").

Vista is forcing a new security level between networks called NTLMv2 and samba uses NTLM.

I applied the fix but I still cannot access Vista thru Ubuntu.  I dont think it was set-up correctly in the first place.

---

### Post by Cornbreadly on 2007-02-10
I know I have been talking to myself but I could use some help besides the voices in my head.

I can't log into vista from ubuntu and I am pretty sure I have it setup the way its been explained in the howto.

---

### Post by meng on 2007-02-10
Hey there, I'm keen to help if I can, but can you help me out and confirm the following for me:
1) Both machines have consistent local IP addresses.
2) You have already tried using these IP addresses to allow the machines to connect to one another
(from Ubuntu/Nautilus, this means smb://192.168.0.4, from Windows, this means \\192.168.0.4)

because this is the easiest way to see files on network machines.

If I've misunderstood how far you've progressed, or the nature of the difficulty, then let me know!

---

