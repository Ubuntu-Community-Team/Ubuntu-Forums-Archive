---
title: "terminal"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by weezyrider on 2011-02-17
First - whenever I open the terminal i get weezy@computernameadth-0-DMI-table-is-broken-Stop:~$
I can enter commands , but then it wants password. I can't type password in at the cursor. It's like there's no keyboard on the computer!
When I cut and paste the text. I get what looks to be a help file which is no help since I cant type in password. Password works everywhere else.
Now what have I gone and done?
Thanks
PS, I did search the forum - didn't see anything about not being able to type password.

---

### Post by sydbat on 2011-02-17
> **weezyrider said:**
> First - whenever I open the terminal i get weezy@computernameadth-0-DMI-table-is-broken-Stop:~$
I can enter commands , but then it wants password. I can't type password in at the cursor. It's like there's no keyboard on the computer!
When I cut and paste the text. I get what looks to be a help file which is no help since I cant type in password. Password works everywhere else.
Now what have I gone and done?
Thanks
PS, I did search the forum - didn't see anything about not being able to type password.Your password IS being entered, it just does not show up in the terminal. Hit the Enter key after you put your password in.

---

### Post by hansolo4949 on 2011-02-17
Yes, it is being entered, you just cannot see it. This is presumably a security feature, nut is a big pain for people just joining the ubuntu community. Happy typing!

---

### Post by weezyrider on 2011-02-17
Tells me command not found. just typed in dmidecode and got this:
sudo dmidecode
# dmidecode 2.9
SMBIOS 2.2 present.
41 structures occupying 1560 bytes.
Table at 0x000F0000.

Handle 0x0000, DMI type 0, 19 bytes
BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version: 6.00 PG
    Release Date: 11/21/2006
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
    Manufacturer:  
    Product Name:  
    Version:  
    Serial Number:  
    UUID: Not Present
    Wake-up Type: Power Switch

Handle 0x0002, DMI type 188, 255 bytes
OEM-specific Type
    Header and Data:
        BC FF 02 00 4B 38 4E 50 54 44 52 41 4D 30 03 00
        00 00 00 00 9F 00 00 00 00 00 01 00 00 00 00 00
        00 00 02 00 00 00 00 00 00 00 03 00 00 00 00 00
        00 00 04 00 00 00 00 00 00 00 05 00 00 00 00 00
        00 00 06 00 00 00 00 00 00 00 07 00 00 00 00 00
        00 00 40 00 10 0A 00 00 00 00 00 00 03 00 FF 02
        00 5D 01 00 80 00 00 00 00 00 00 00 00 00 00 00
        00 00 01 00 00 00 01 00 40 00 00 00 00 00 00 00
        00 00 E0 3F 18 00 00 00 00 00 E0 3F 38 00 00 00
        00 00 46 00 00 00 00 00 00 00 02 05 00 00 00 00
        00 00 24 C2 6A 5D 20 13 13 08 10 04 01 00 5A 00
        00 67 88 88 FF FE 15 15 15 15 15 15 15 15 15 00
        00 00 16 18 16 18 17 18 17 18 16 00 00 00 30 00
        30 00 18 17 18 18 18 18 18 17 18 16 17 17 17 17
        17 16 17 16 2F 00 2F 00 22 12 11 20 20 22 20 00
        22 12 11 20 20 22 20 00 00 00 00 00 00 00 00
    Strings:
         
         
         
         
         

Handle 0x0000, DMI type 0, 160 bytes
BIOS Information
    Vendor: Not Specified
    Version: Not Specified
    Release Date: Not Specified
    ROM Size: 64 kB
    Characteristics:
    BIOS Revision: 0.0

Invalid entry length (0). DMI table is broken! Stop.

weezy@541t53adth-0-DMI-table-is-broken-Stop:~$ 
I see the zip drive is supported. It shouldn't be. It went south and caused all kinds of junk in XP. It s/h/b/disconnected
What does the bios error mean?
thx

---

### Post by Frogs Hair on 2011-02-17
Other than your post this all I can find at the moment , I will keep looking.
[http://www.cyberciti.biz/faq/check-ram-speed-linux/](http://www.cyberciti.biz/faq/check-ram-speed-linux/)

---

### Post by Frogs Hair on 2011-02-17
Here is a bug report.[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg484674.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg484674.html)

---

### Post by weezyrider on 2011-02-17
> **Frogs Hair said:**
> Here is a bug report.[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg484674.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg484674.html)

 That's mostly what I found when I googled for it. Either the question was never answered, or it was a bug.  So if it's a bug, then what do I do about it? Just limp along and hope the next Ubuntu fixes it? I'm starting to like Ubuntu more and more, but it has to run right. W

---

### Post by weezyrider on 2011-02-18
I just noticed this - why is it different than the first lines?
Handle 0x0000, DMI type 0, 160 bytes
BIOS Information
    Vendor: Not Specified
    Version: Not Specified
    Release Date: Not Specified
    ROM Size: 64 kB
    Characteristics:
    BIOS Revision: 0.0
The first lines are right.
Where is it seeing the last lines? I do have 2 separate hard drives, but the bios controls which one I boot into. 
Thanks

---

### Post by Intruder on 2011-02-18
I have just been installing Ubuntu on my laptop and Im getting this message in the computer name :S

Tosh Tecra M2

---

### Post by ubun2geek on 2011-02-18
type the password, it is automatically hidden!

---

### Post by ubun2geek on 2011-02-18
> **sydbat said:**
> Your password IS being entered, it just does not show up in the terminal. Hit the Enter key after you put your password in.
correct!

---

### Post by ubun2geek on 2011-02-18
your title is not at all descriptive :(

---

### Post by weezyrider on 2011-02-24
> **OpenOffice.org said:**
> type the password, it is automatically hidden!

weezy@541t53adth-0-DMI-table-is-broken-Stop:~$  Found out where it came from. It was picked up off the live CD. I reinstalled Ubuntu, and noticed on the first screen that was already in the computer name box. I deleted it and the terminal looks right now. W

---

