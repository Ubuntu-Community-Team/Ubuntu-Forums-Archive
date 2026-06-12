---
title: "Multi-Os printer sharing"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by rehumanize on 2008-02-08
Hey-

I need to share a printer with a bunch of other Windows users I live with (separate comps). The printer is attached to a ubuntu/XP notebook.

I am able to make the printer connected to the ubuntu box visible to windows pcs...but is there anyway to make the printer address similar in both xp and ubuntu? I've just been sharing via windows, and sharing separately via ubuntu. So I have two printers listed in each windows machine. If I'm booted into linux and someone tries to print with the windows printer connection, it won't work and they'll have to try the linux connection (and vice versa).

So what I'm asking is: Can I make the printer connected to my dual-booted notebook have the same sharing address on each OS? That way I won't need two printer entries in the computers i'm sharing with.

I've tried messing with the netbios name in the samba config with no luck...any help appreciated.

It's kinda hard to explain, I hope it came across clear.

Edit:

Actually I found a thread with my exact situation outlined in it:

[http://ubuntuforums.org/showthread.php?t=527965](http://ubuntuforums.org/showthread.php?t=527965)

The problem wasn't answered though, but I thought I'd post the link to help with my explaination

Thanks!

---

### Post by rehumanize on 2008-02-09
bump

---

### Post by rehumanize on 2008-02-11
please help?

---

### Post by swerdna on 2008-02-12
> **rehumanize said:**
> please help?

Hi. Been watching this for the solution. Pity no wisdom yet, interesting problem.

Did this not work for you, just out of interest: [http://forums.suselinuxsupport.de/index.php?showtopic=64708](http://forums.suselinuxsupport.de/index.php?showtopic=64708) ?

Good luck here 

Swerdna

---

### Post by rehumanize on 2008-02-12
Oh hey Swerdna

I tried your suggestions for suse, but I just couldnt get it going. I have another pc with xp/ubuntu so I figured if I could get the ubuntu server running then I could just use the suse as a client. I wasn't sure If there were any OS-specific things so I posted here. Here is my smb.conf that I'm running in ubuntu, if you want to take a look.

```
[global]
        workgroup = MSHOME
        server string = E1505
        password level = 8
        log file = /var/log/samba/log.%m
        max log size = 50
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = lpstat
        dns proxy = No
        hosts allow = 192.168.1.64
        printing = cups
        print command = 
        lpq command = %p
        lprm command = 

[homes]
        comment = Home Directories
        read only = No
        browseable = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        guest ok = Yes
        printable = Yes
        print command = lpr-cups -P %p -o raw %s -r
        browseable = No

[print$]
        path = /var/lib/samba/printers
        write list = @adm, root

[pdf-generator]
        comment = PDF Generator (only valid users)
        path = /var/tmp
        printable = Yes
        print command = /usr/share/samba/scripts/print-pdf %s ~%u \\\\\\\\%L\\\\%u %m %I &

[Agustin]
        comment = Agustin Private Files
        path = /home/agustin/Documents
        valid users = agustin
        read only = No
```

---

### Post by swerdna on 2008-02-12
If you want to print to a netbios name, tweak name resolution thusly:
netbios name = E1505
server string = ""
name resolve order = bcast host lmhosts wins

also the restriction on 192....64 will prevent all other computers, won't it? I'd take it out

There's some more things for printing required in [globa] see my Suse howto (samba doesn't vary across distros)

Anyway, apart from that , I suppose you need an Ubu Guru here

G luck

Swerdna

---

### Post by mike.123850 on 2008-02-12
I have no Ubuntu wisdom, but possibly another option. I got tired of having to turn on my (Ubuntu) machine to act as a print server when my wife needed to print something from her (Windows XP) machine. So, I went to Radioshack and picked up a Linksys PSUS4 usb print server/4 port switch. Works nicely ....  I'm happy and my wife is happy. I even have it plugged into my wifi router so printing is now wireless as well.

Now, the Linksys PSUS4 doesn't work with printer/scanner/copier all-in-one machines but for single use printers I think they do fine. The reason I got mine from our local Radioshack and not Newegg is because the price difference wasn't enough to worry about. And, the guys at Radioshack said if it didn't work they'd take it back. Our printer is a HP Deskjet 960c. It was actually easier to set it up in Ubuntu than Windows XP too.



Good luck though!
Mike

---

### Post by rehumanize on 2008-02-12
Thanks Swerdna, I'll give it another shot.

Mike - I've actually thought of doing that. I'll definitely go that route if I can't get things sorted out.

Thanks to you both :)

---

### Post by jimgeiser on 2008-02-16
> **mike.123850 said:**
> I have no Ubuntu wisdom, but possibly another option. I got tired of having to turn on my (Ubuntu) machine to act as a print server when my wife needed to print something from her (Windows XP) machine. So, I went to Radioshack and picked up a Linksys PSUS4 usb print server/4 port switch. Works nicely ....  I'm happy and my wife is happy. I even have it plugged into my wifi router so printing is now wireless as well.

Now, the Linksys PSUS4 doesn't work with printer/scanner/copier all-in-one machines but for single use printers I think they do fine. The reason I got mine from our local Radioshack and not Newegg is because the price difference wasn't enough to worry about. And, the guys at Radioshack said if it didn't work they'd take it back. Our printer is a HP Deskjet 960c. It was actually easier to set it up in Ubuntu than Windows XP too.



Good luck though!
Mike
Mike, I am in the process of trying to do the same thing as you did with a PSUS4 server. It went just fine until I got to the Ubuntu machine. It won't recognize the HP 1400 printer (all I want to do is use the AIO as a printer). I read Ubuntu instructions for network printing, but seems like I am missing something there. Any suggestions?
jim

---

