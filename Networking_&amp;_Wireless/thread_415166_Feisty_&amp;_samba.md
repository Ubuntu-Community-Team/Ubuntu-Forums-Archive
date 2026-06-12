---
title: "Feisty &amp; samba"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by likwid on 2007-04-20
I'm having a terrible time with feisty. I have spent about 5 hours trying to share folders and i'm totally fed up with it. Please, what's changed that i can't make this work? I had everything working well in dapper but this is driving me nuts..

---

### Post by likwid on 2007-04-20
smbtree returns:

HASHBASH
        \\SPARKUS                       Samba 3.0.24
                \\SPARKUS\homes          
                \\SPARKUS\shared         
                \\SPARKUS\IPC$                  IPC Service (Samba 3.0.24)
        \\MEDIAPC                       Samba 3.0.24
cli_start_connection: failed to connect to MEDIAPC<20> (0.0.0.0)


Obviously i wish to access mediapc..

---

### Post by MetalMusicAddict on 2007-04-20
Do you have the user from "SPARKUS" as a user on "MEDIAPC"? Also do you have samba and smbfs installed?

---

### Post by likwid on 2007-04-20
Hi. Thanks for help!

I have the same users on both pc's. I can view sparkus from media but not vice versa.

I thought the message:

Error connecting to 192.168.1.106 (No route to host)
cli_start_connection: failed to connect to MEDIAPC<20> (192.168.1.106)

...  suggests it's being blocked. I mean, the machine MEDIA is fixed a ip different to that one..

---

### Post by likwid on 2007-04-20
Something else which is strange. Sometimes smbtree works, sometimes it doesn't. When it doesn't i think it's because the password isn't accepted, i mean, i can enter anything and it pauses for a few seconds before returning to bash. There's no prompt of incorrect password but the time is consistent no matter what i enter so it seems likely to be password problem. I enter the same password i entered for my user account, which is on both machines, and the same password in 'smbpasswd -a mark'.

Really, i've spent a whole afternoon on this and still nothing. Worth pointing out is that i'm using firestarter, although i've allowed samba and tried stopping the firewall to no avail..

Hellp would be very appreciated.  :(

---

### Post by MetalMusicAddict on 2007-04-20
Make sure that are both part of the same workgroup. Is this a all linux network?

---

### Post by likwid on 2007-04-20
Yes. The same workgroup. The two machines are linux but i need samba for flatmates laptop.

---

### Post by Fenix-TX on 2007-04-20
I have problems, i can enter on other computers, but they can't enter to my computer after i upgraded, they have connection refused, please contact to your administrator (they have windowze). It was working perfect before upgrading.

---

### Post by likwid on 2007-04-20
Hmm, i can access network shares from ubuntu1 machine to ubuntu2 however not 2 to 1, however a windows installation on 2 manages 2 to 1..

(that probably isn't the most eloquent description..)

Have to say that apart from this, feisty is very, very good and i love its slickness.

---

### Post by Fenix-TX on 2007-04-21
Solved for me deleting the shared folders and adding them again

---

### Post by Rob_H on 2007-04-23
I had problems with Samba shares after my Feisty upgrade, too. Kept getting errors saying the directory couldn't be found when I tried to access the share. Finally solved it by removing **/etc/samba** and then reinstalling "samba" and "samba-common" packages via Adept. This gave me a fresh **smb.conf** file to work with. Then I reconfigured it using [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") and got it working again.

---

### Post by marx2k on 2007-05-08
I am having the same exact issue:

I would like to access Commodore-64 fro LivingroomBuntu:

```

marx2k@LivingRoomBuntu:~$ smbtree
Password: 
WORKGROUP
        \\LIVINGROOMBUNTU               LivingRoomBuntu server (Samba, Ubuntu)
                \\LIVINGROOMBUNTU\print$                Printer Drivers
                \\LIVINGROOMBUNTU\Music1         
                \\LIVINGROOMBUNTU\Music2         
                \\LIVINGROOMBUNTU\Music3         
                \\LIVINGROOMBUNTU\Music4         
                \\LIVINGROOMBUNTU\Music5         
                \\LIVINGROOMBUNTU\Music6         
                \\LIVINGROOMBUNTU\Documents      
                \\LIVINGROOMBUNTU\Movies         
                \\LIVINGROOMBUNTU\IPC$                  IPC Service (LivingRoomBuntu server (Samba, Ubuntu))
        \\EMAC-800                      Mac OS X
                \\EMAC-800\ADMIN$               IPC Service (Mac OS X)
                \\EMAC-800\IPC$                 IPC Service (Mac OS X)
        \\COMMODORE-64                  Commodore-64 server (Samba, Ubuntu)
cli_start_connection: failed to connect to COMMODORE-64<20> (0.0.0.0)
SIDUX
        \\SIDUXBOX                      Samba 3.0.24
                \\SIDUXBOX\sidux_hda            SIDUXBOX
                \\SIDUXBOX\print$               Printer Drivers
                \\SIDUXBOX\IPC$                 IPC Service (Samba 3.0.24)

```

I have no problem accessing LivingroomBuntu from Commodore-64, but not the other way around!

When I run smbtree on Commodore-64, I see a full listing of everything including Commodore-64

Both are Feisty boxes, both have global read/write access (private network behind a router) with no requesting of passwords

Lil' help?

---

### Post by marx2k on 2007-05-08
Ok, when I drop Firestarter, smbtree works and I am able to see my shares on commodore-64 from LivingRoomBuntu

```

marx2k@LivingRoomBuntu:~$ smbtree
Password: 
WORKGROUP
        \\LIVINGROOMBUNTU               LivingRoomBuntu server (Samba, Ubuntu)
                \\LIVINGROOMBUNTU\print$                Printer Drivers
                \\LIVINGROOMBUNTU\Music1         
                \\LIVINGROOMBUNTU\Music2         
                \\LIVINGROOMBUNTU\Music3         
                \\LIVINGROOMBUNTU\Music4         
                \\LIVINGROOMBUNTU\Music5         
                \\LIVINGROOMBUNTU\Music6         
                \\LIVINGROOMBUNTU\Documents      
                \\LIVINGROOMBUNTU\Movies         
                \\LIVINGROOMBUNTU\IPC$                  IPC Service (LivingRoomBuntu server (Samba, Ubuntu))
        \\EMAC-800                      Mac OS X
                \\EMAC-800\ADMIN$               IPC Service (Mac OS X)
                \\EMAC-800\IPC$                 IPC Service (Mac OS X)
        \\COMMODORE-64                  Commodore-64 server (Samba, Ubuntu)
                \\COMMODORE-64\LaserJet-5       HP_LJ5
                \\COMMODORE-64\LaserJet-4       LaserJet-4
                \\COMMODORE-64\IPC$             IPC Service (Commodore-64 server (Samba, Ubuntu))
                \\COMMODORE-64\Applications     Windows XP Application
                \\COMMODORE-64\ReadWrite      
                \\COMMODORE-64\games            Emulator ROMS
                \\COMMODORE-64\print$           Printer Drivers
SIDUX
        \\SIDUXBOX                      Samba 3.0.24
                \\SIDUXBOX\sidux_hda            SIDUXBOX
                \\SIDUXBOX\print$               Printer Drivers
                \\SIDUXBOX\IPC$                 IPC Service (Samba 3.0.24)

```

But, in Firestarter, I opened up my SMB ports to 'everyone' and explicitly opened all my ports to all private network users (192.168.11.1/24)

Yet, when I bring Firestarter back up, same exact issue 

So obviosuly, it's FireStarter- does anyone have any hints as to why this is happened? From what I can tell, Firestarter should be allowing that traffic to flow!

---

### Post by juangt on 2007-07-15
I am no expert, but it seems to me most of you guys are having problems with your firewalls, namely, iptables by default, and with your router configuration. Samba works with some ports that may or may not be allowed by default by your current working set-up.

As I said, I am no expert, but try reading up on iptables, or install a gui-like firewall and fix your router forwarding (try a switch maybe?) to see if this fixes your issues.

Hope this helps!

---

