---
title: "Seeing other people"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by Peter Sommer-Larsen on 2006-11-10
Hi...

I am having problems seeing other people on our network. We are about
40 connected to our network, and I can only see a few. I am the only one
whose using Linux, so I find i pretty weird that I see some and not others..

---

### Post by Peter Sommer-Larsen on 2006-11-10
> **Peter Sommer-Larsen said:**
> Hi...

I am having problems seeing other people on our network. We are about
40 connected to our network, and I can only see a few. I am the only one
whose using Linux, so I find i pretty weird that I see some and not others..

Oh and I use Xfsamba...

I tried using "LinNeighborhood" which i used in Dapper, but I see
no one with this program !!

---

### Post by kidders on 2006-11-10
[COLOR="Silver"]What do you mean by "see" exactly?[/COLOR]

**Edit:** Scratch that ... you're talking about samba.

There could be lots of reasons for this. Perhaps your samba logs might shed some light on your difficulties. They're a bit tricky to follow sometimes, though :-(

---

### Post by dbott67 on 2006-11-10
What's the output of smbtree:
```
dbott@dapper:~$ smbtree
Password:
WORKGROUP
        \\PIII-600
        \\NAS-160GB
                \\NAS-160GB\IPC$
                \\NAS-160GB\Music
                \\NAS-160GB\Archive
                \\NAS-160GB\Data
                \\NAS-160GB\PUBLIC
MSHOME
        \\THEDRAKE                      thedrake server (Samba, Ubuntu)
                \\THEDRAKE\print$               Printer Drivers
                \\THEDRAKE\dbott-P4
                \\THEDRAKE\IPC$                 IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\ADMIN$               IPC Service (thedrake server (Samba, Ubuntu))
        \\PIV3GHZ                       Joyce Laptop
cli_start_connection: failed to connect to PIV3GHZ<20> (0.0.0.0)
        \\DAPPER                        dapper server (Samba, Ubuntu)
                \\DAPPER\print$                 Printer Drivers
                \\DAPPER\ndis
                \\DAPPER\IPC$                   IPC Service (dapper server (Samba, Ubuntu))
                \\DAPPER\ADMIN$                 IPC Service (dapper server (Samba, Ubuntu))

```

Do you have 'winbind' installed?

```
sudo gedit /etc/nsswitch.conf
```

find this line (it may not be exactly that)

```
hosts:          files dns mdns
```

and add wins, so now it looks like

```
hosts:          files dns mdns wins
```

then install winbind
```
sudo apt-get install winbind
```

-Dave

---

### Post by Peter Sommer-Larsen on 2006-11-10
I had installed winbind and added wins to the nsswitch..

I didnt know the smbtree command. When i run this, I can see
all on the network, but still I don't see people
in my programs (Xfsamba and LinNeighborhood)

So weird ..

---

### Post by Peter Sommer-Larsen on 2006-11-10
This is the output of my smbtress:

MSHOME
4MAJ
        \\VESTERGAARD                   vestergaard server (Samba, Ubuntu Linux)
                \\VESTERGAARD\ADMIN$            IPC Service (vestergaard server (Samba, Ubuntu Linux))
                \\VESTERGAARD\IPC$              IPC Service (vestergaard server (Samba, Ubuntu Linux))
                \\VESTERGAARD\musik             mit musik
        \\VESTERBAEK     
                \\VESTERBAEK\C$                 Standardshare
                \\VESTERBAEK\Mere musik         Mere af Anders Guldøls musik
                \\VESTERBAEK\ADMIN$             Fjernadministration
                \\VESTERBAEK\Musik              Anders Guldøls musik
                \\VESTERBAEK\G$                 Standardshare
                \\VESTERBAEK\D              
                \\VESTERBAEK\IPC$               Fjern-IPC
        \\TOROA          
                \\TOROA\Film           
                \\TOROA\C$              Default share
                \\TOROA\ADMIN$          Remote Admin
                \\TOROA\Music          
                \\TOROA\Serier         
                \\TOROA\upload         
                \\TOROA\Z$              Default share
                \\TOROA\Games          
                \\TOROA\IPC$            Remote IPC
                \\TOROA\E$              Default share
        \\SPANDEN                       spanden server (Samba, Ubuntu Linux)
                \\SPANDEN\ADMIN$                IPC Service (spanden server (Samba, Ubuntu Linux))
                \\SPANDEN\IPC$                  IPC Service (spanden server (Samba, Ubuntu Linux))
                \\SPANDEN\_Torrents             Downloads (INCOMPLETES INCLUDED!!!)
                \\SPANDEN\4_Series              Series
                \\SPANDEN\4_Movies              Movies
                \\SPANDEN\4_Cartoons            Cartoons
                \\SPANDEN\4                     Public shared on 400GB Seagate SATA
                \\SPANDEN\3_Manga               Manga (Japanese comics)
                \\SPANDEN\3_Anime               Anime (Japanese cartoons - unsorted!)
                \\SPANDEN\3                     Public shared on 400GB Seagate ATA
                \\SPANDEN\2_Software            Programs, games, drivers, docs and more
                \\SPANDEN\2_Programs            Programs for Windows (primarily XP)
                \\SPANDEN\2_Music               MP3 music
                \\SPANDEN\2_Games               Games for Windows
                \\SPANDEN\2                     Public shares on 160GB Seagate ATA
                \\SPANDEN\1_Video               All video files
                \\SPANDEN\1_Photos              Photos
                \\SPANDEN\1_Books               Books and documents
                \\SPANDEN\1                     Public shares on 200GB Seagate ATA
                \\SPANDEN\restricted            Restricted access!
                \\SPANDEN\kim                   Backup fra Kims bærbare
        \\SMOKED                        Smoked
                \\SMOKED\Film           
                \\SMOKED\C$                     Default share
                \\SMOKED\ADMIN$                 Remote Admin
                \\SMOKED\musik          
                \\SMOKED\D$                     Default share
                \\SMOKED\IPC$                   Remote IPC
                \\SMOKED\E$                     Default share
                \\SMOKED\Billeder       
        \\ROSTAM         
                \\ROSTAM\C$                     Default share
                \\ROSTAM\Interface      
                \\ROSTAM\ADMIN$                 Remote Admin
                \\ROSTAM\WoW film       
                \\ROSTAM\F$                     Default share
                \\ROSTAM\### Music      
                \\ROSTAM\Rollespil      
                \\ROSTAM\D$                     Default share
                \\ROSTAM\IPC$                   Remote IPC
                \\ROSTAM\E$                     Default share
        \\RAMSES         
                \\RAMSES\C$                     Standardshare
                \\RAMSES\ADMIN$                 Fjernadministration
                \\RAMSES\print$                 Printerdrivere
                \\RAMSES\SharedDocs     
                \\RAMSES\IPC$                   Fjern-IPC
        \\OSTEPIKOFDOOM  
                \\OSTEPIKOFDOOM\E$              Default share
                \\OSTEPIKOFDOOM\ADMIN$          Remote Admin
                \\OSTEPIKOFDOOM\Musik          
                \\OSTEPIKOFDOOM\IPC$            Remote IPC
                \\OSTEPIKOFDOOM\Apps           
                \\OSTEPIKOFDOOM\counter        
                \\OSTEPIKOFDOOM\upload         
                \\OSTEPIKOFDOOM\Film           
                \\OSTEPIKOFDOOM\C$              Default share
                \\OSTEPIKOFDOOM\Serier          24 timer, Prison Break, Eureka, My Name Is Earl, Supernatural, Spellbinder, Six Feet Under
        \\MONKEY         
                \\MONKEY\ADMIN$                 IPC Service ("")
                \\MONKEY\IPC$                   IPC Service ("")
                \\MONKEY\Delt           
        \\MADS                          Mads
cli_start_connection: failed to connect to MADS<20> (0.0.0.0)
        \\LABTOPEN                      Lab'en
cli_start_connection: failed to connect to LABTOPEN<20> (0.0.0.0)
        \\INTOXICATED                   Jakob V
        \\HOUMANN        
                \\HOUMANN\C$                    Standardshare
                \\HOUMANN\ADMIN$                Fjernadministration
                \\HOUMANN\print$                Printerdrivere
                \\HOUMANN\D$                    Standardshare
                \\HOUMANN\IPC$                  Fjern-IPC
        \\HALD           
                \\HALD\Film           
                \\HALD\C$               Standardshare
                \\HALD\ADMIN$           Fjernadministration
                \\HALD\Upload         
                \\HALD\Serier         
                \\HALD\Musik          
                \\HALD\D$               Standardshare
                \\HALD\IPC$             Fjern-IPC
                \\HALD\Billeder       
        \\ASKES                         Aske
        \\ANNEMOE                       Anne Ulltveit-Moe
cli_start_connection: failed to connect to ANNEMOE<20> (0.0.0.0)

How

---

