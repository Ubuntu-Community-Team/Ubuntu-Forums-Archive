---
title: "a problem with samba"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by saneone on 2007-03-06
I`ve got a problem with samba and /etc/fstab.
I have a second computer running Windows XP SP2 with Western Digital MyBook USB2 external hard disk attached. The Disk is shared over windows network with a label "My Book (J)".
I can manually mount this samba resource by typing "sudo mount -t smbfs -o fmask=777,dmask=777,guest '//win/My Book (J)' /media/MyBook", but I can't figure out how to mount it by using fstab...
The problem is with the disk label, as it contains three strings: "My", "Book" and "(J)".

I tried:
//win/My Book (J) /media/MyBook smbfs guest,dmask=777,fmask=777  0    0
and
'//win/My Book (J)' /media/MyBook smbfs guest,dmask=777,fmask=777  0    0

I also tried replacing ' with " but nothing has changed.

PS. Windows doesn't allow me to share the disk with one-word label... the ... (J) is always there.

Plz someone help me.

---

### Post by LotsOfPhil on 2007-03-06
I wonder if escaping the ( would do it. Try

//win/"My Book \(J\)"/media/MyBook smbfs guest,dmask=777,fmask=777 0 0

or

//win/"My Book (J)"/media/MyBook smbfs guest,dmask=777,fmask=777 0 0

Also, there is a space between (J) and the next /    was that on purpose?

---

### Post by saneone on 2007-03-06
> **LotsOfPhil said:**
> I wonder if escaping the ( would do it. Try

//win/"My Book \(J\)"/media/MyBook smbfs guest,dmask=777,fmask=777 0 0

doesn't work

> 
or

//win/"My Book (J)"/media/MyBook smbfs guest,dmask=777,fmask=777 0 0

doesn't work too :/

> 
Also, there is a space between (J) and the next /    was that on purpose?
yep... the (J) is a drive letter in Windows and is added automatically by MS product. It's a part of the share`s name.
And the space is always there. Check other lines in fstab file.

---

### Post by LotsOfPhil on 2007-03-06
Hmm. I guess you can escape the spaces...

/win/My\ Book\ (J)\ /media/MyBook smbfs guest,dmask=777,fmask=777 0 0

And then try escaping the ( and the spaces...

/win/My\ Book\ \(J\)\ /media/MyBook smbfs guest,dmask=777,fmask=777 0 0

Other than this I am stumped.

---

### Post by saneone on 2007-03-06
neither first, nor second solution works, but thx for your help

---

### Post by saneone on 2007-03-06
is there someone who could help me?

---

### Post by dmizer on 2007-03-06
you won't be able to mount network share names with the "(" and ")" characters using smbfs.

you MIGHT be able to make this work with cifs using the "mapchars" option like so:
```
//win/"My Book (J)" /media/MyBook cifs guest,rw,mapchars,dir_mode=0777,file_mode=0777 0 0
```

otherwise you'll have to edit the share name to remove the "(J)" portion of the share name.

if that doesn't work, post the output of this command:
smbtree

---

### Post by saneone on 2007-03-07
> **dmizer said:**
> you won't be able to mount network share names with the "(" and ")" characters using smbfs.

you MIGHT be able to make this work with cifs using the "mapchars" option like so:
```
//win/"My Book (J)" /media/MyBook cifs guest,rw,mapchars,dir_mode=0777,file_mode=0777 0 0
```

otherwise you'll have to edit the share name to remove the "(J)" portion of the share name.

after editing /etc/fstab and adding the line you suggested i get:

saneone@biggie:~$ sudo mount -a
[mntent]: warning: no final newline at the end of /etc/fstab
[mntent]: line 31 in /etc/fstab is bad


> 
if that doesn't work, post the output of this command:
smbtree

smbtree
debug_parse_params: unrecognized debug class name or format [#]
ERROR: Badly formed boolean in configuration file: "yes                     # Default".
ERROR: Badly formed boolean in configuration file: "yes                    # Default".
ERROR: Badly formed boolean in configuration file: "yes                      # Default".
Unknown parameter encountered: "lpq cache"
Ignoring unknown parameter "lpq cache"
Password:
DOM
        \\SANE                          Samba 3.0.22
                \\SANE\ADMIN$           IPC Service (Samba 3.0.22)
                \\SANE\IPC$             IPC Service (Samba 3.0.22)
                \\SANE\Torrenty
                \\SANE\Music
        \\PATRYK                        PATRYK
                \\PATRYK\NEI                    NEI]
                \\PATRYK\C$                     
                \\PATRYK\ADMIN$                 
                \\PATRYK\mat                    NES
                \\PATRYK\SharedDocs
                \\PATRYK\print$                
                \\PATRYK\D$                    
                \\PATRYK\IPC$                   
        \\MALY                          Przemek
                \\WIN\J$
                \\WIN\Incoming
                \\WIN\C$
                \\WIN\ADMIN$
                \\WIN\POUND (E)
                \\WIN\THA (C)
                \\WIN\SharedDocs
                \\WIN\print$
                \\WIN\D$              
                \\WIN\IPC$
                \\WIN\My Book (J)
                \\WIN\E$

---

### Post by saneone on 2007-03-07
okay... i finally forced my windows to change the sharename
moreover, i fixed my smb.conf file, so now it doesn't generate any errors
Thx for replies.

---

### Post by dmizer on 2007-03-07
edit:
never mind ... it appears you already have it solved.

---

