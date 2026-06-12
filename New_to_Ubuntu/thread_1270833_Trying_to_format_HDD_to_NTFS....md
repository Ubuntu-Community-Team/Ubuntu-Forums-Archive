---
title: "Trying to format HDD to NTFS..."
date: 2009-09-20
forum: New to Ubuntu
---

### Post by YoungTechie on 2009-09-20
Okay so I know there are other threads on this problem but I believe my problem is somewhat unique. Okay so my old HDD of 10 years crapped out on me and no longer spins up... I had a 200 gb Seagate Barrucuda drive collecting dust in my modded xbox that I used to use as an ftp server using Xebian (Linux Distro for xbox) Ok So i wish to eventually install some form of windows.. and windows setup cannot access the HDD... The HDD shows up in the boot loader but nothing seems to be able to actually View the HDD I obtained an ubuntu Live CD which im using to access the internet currently. When I run Gparted No Devices can be detected.... I'm Fairly Technical but my Experience with Linux is limited. Any Help or Suggestions would be appreciated... I've been delaying for too long already and need to get back to business.

---

### Post by Liolikas on 2009-09-20
.. and windows setup cannot access the HDD... 
When I run Gparted No Devices can be detected.
-->
Seems like you have not working at all hdd sorry. Try to find good one.

---

### Post by talsemgeest on 2009-09-20
> **YoungTechie said:**
> Okay so I know there are other threads on this problem but I believe my problem is somewhat unique. Okay so my old HDD of 10 years crapped out on me and no longer spins up... I had a 200 gb Seagate Barrucuda drive collecting dust in my modded xbox that I used to use as an ftp server using Xebian (Linux Distro for xbox) Ok So i wish to eventually install some form of windows.. and windows setup cannot access the HDD... The HDD shows up in the boot loader but nothing seems to be able to actually View the HDD I obtained an ubuntu Live CD which im using to access the internet currently. When I run Gparted No Devices can be detected.... I'm Fairly Technical but my Experience with Linux is limited. Any Help or Suggestions would be appreciated... I've been delaying for too long already and need to get back to business.
Go to Applications>Accessories>Terminal and post the output of ```
sudo fdisk -l
```

---

### Post by YoungTechie on 2009-09-20
No I do not believe this is the case... The HDD was purchased brand new and I hardly used it for 2 months. I can see the drive in the Bios and all.. SO I can't see how the HDD would just be no good.

---

### Post by YoungTechie on 2009-09-20
when I sudo fdisk -l in the terminal nothing happens... just get an identical command line.

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$

---

### Post by Liolikas on 2009-09-20
> **YoungTechie said:**
> when I sudo fdisk -l in the terminal nothing happens... just get an identical command line.

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$
3 signal about bad hdd. Go to shop and ask to replace with other. If they do not give replace ask format to ntfs they fail and give brand new one.

---

### Post by YoungTechie on 2009-09-20
****....Could it really just be a bad HDD??  I'm looking for someone to confirm this... Cause I don't see how it could happen other then manufacturer defect... never had any problems with it before...Just don't know how to format the thing.

---

### Post by Liolikas on 2009-09-20
[http://maketecheasier.com/how-to-reformat-an-external-hard-drive-to-ntfs-format-in-ubuntu-hardy/2008/09/29](http://maketecheasier.com/how-to-reformat-an-external-hard-drive-to-ntfs-format-in-ubuntu-hardy/2008/09/29)

---

### Post by YoungTechie on 2009-09-20
It's an Internal IDE Drive though....Nothing in that tutorial seems to apply...

---

### Post by YoungTechie on 2009-09-20
I read something somewhere about a bios setting that might keep Gparted from being able to detect the drive.. although that was for an sata Drive....Could it be a similar problem?

---

### Post by JHan816 on 2009-09-20
Go into your computer's Bios setup and see if ithe HD appears on the list of devices. 
 
If it is not there then you either have a problem with the HD itself or the IDE controller. Check/swap out ribbon cable and check/re-seat power cable to the drive.

---

### Post by YoungTechie on 2009-09-20
I did originally say that the HDD Does infact show up in the Bios setup... 

As ST3(some combo of numbers) 
with 2098765 bytes of data.... 200gb

I'll recheck the connections right now.

---

### Post by YoungTechie on 2009-09-20
Ok So I went ahead and just clicked the install button on this live CD and when it asks me where to put ubuntu it shows the drive as the following.

SCSI5 (0,0,0) (sda) 200.0 gb ATA ST3200822A

---

### Post by Spiffworks on 2009-09-20
Is the Xebian install still working on the Xbox? If it is, then the drive is fine. If not, sorry.

---

### Post by YoungTechie on 2009-09-20
Okay So I went further and it actually lets me create partition tables and gives me options to format it and such... but no option for NTFS...The reason being obvious....do you think if I go ahead and format the drive in ext3 I can go back afterwards with Gparted and reformat it into NTFS?

---

### Post by YoungTechie on 2009-09-20
I fried that Xbox in a soldering mishap few years ago... the drive hasn't been used since then...So I assume everything should still be in working order

---

### Post by JHan816 on 2009-09-20
> **YoungTechie said:**
> I did originally say that the HDD Does infact show up in the Bios setup... 

 
Sorry. I missed that. I am surprised that Gparted and fdisk can't see it. I would also suggest doing a full shutdown/poweroff let it sit 1 minute then turn on.
 
This is a second IDE drive? Also check jumper on the new drive, some can be set to master, slave or cable select (CS). Could be some confusion if both were set to master.
 
Just some ideas, I hope this helps.

---

### Post by YoungTechie on 2009-09-20
The Drive is set to CS and placed on the black..(end) connector... I Built this rig myself and every pc i had before it.....Mom was a PC Specialist so I was kinda raised around em....I think I'm making progress on it though.... since ubuntu's install is letting me manipulate the drive at least in some manner

---

### Post by YoungTechie on 2009-09-20
Okay I attempted to go through an install and get an input/output read error at 15%
Gee I'm Stumped...

---

### Post by Liolikas on 2009-09-20
Return to first answar. Oki if you borred to walk download hdd check program from hdd manufacturer site and use it. Check will wipe all data but you already interested in that and give all answers.

---

### Post by YoungTechie on 2009-09-20
> **Liolikas said:**
> Return to first answar. Oki if you borred to walk download hdd check program from hdd manufacturer site and use it. Check will wipe all data but you already interested in that and give all answers.

Surprised I didn't think of that before...Oh well I'm willing to try anything at this point.

---

### Post by YoungTechie on 2009-09-20
Ok I got a Diagnostic tool from Seagate but how do I open it in ubuntu? Says it's a command line type of program....I have it on the desktop

---

### Post by Liolikas on 2009-09-20
It is program for DOS?
So use FreeDOS.

---

### Post by YoungTechie on 2009-09-20
No I downloaded the one for linux... but it doesn't seem to just run when I click it....came in a tar file.... I assume some sort of archive? I extracted it to desktop and try to click the executable but nada....

---

### Post by Liolikas on 2009-09-20
Yes tar is folder "glued" into one file.
You can:
```

tar -xvvf balbla.tar
(extract)
ls
(you see now folder)
cd (that_folder)
ls -l
(you see file with -rwx means program)
./(that program)

```

---

### Post by YoungTechie on 2009-09-20
Sorry I'm fairly new to using commands in Linux can you explain what to do in abit more detail?

---

### Post by YoungTechie on 2009-09-20
Something is incorrect with the code?

---

### Post by Liolikas on 2009-09-20
Move downloaded file to your desktop and enter:
cd Desktop
ls
Post output here I will tell exact commands then.

---

### Post by YoungTechie on 2009-09-20
I think it might be necessary to tell you I am running off the live cd atm.... but cd desktop yield no results

---

### Post by YoungTechie on 2009-09-20
ubuntu@ubuntu:~$ cd desktop
bash: cd: desktop: No such file or directory
ubuntu@ubuntu:~$ cd
ubuntu@ubuntu:~$ desktop
bash: desktop: command not found
ubuntu@ubuntu:~$ ls
Desktop  Documents  Music  Pictures  Public  Templates  Videos

---

### Post by Liolikas on 2009-09-20
So first lesson:
Linux is not DOS D is not same as d.
Keep it up.

---

### Post by YoungTechie on 2009-09-20
hmm? Oh yes I know capitalization is very important... but I didn't capitalize did I?

---

### Post by Liolikas on 2009-09-20
Yes.

---

### Post by YoungTechie on 2009-09-20
So whats the code... I have the executable extracted to my desktop... but If I click it nothing occurs... it's named st  So what do I need to do...please help I'm getting sleepy

---

### Post by YoungTechie on 2009-09-20
haha I feel so dumb... So thats what you meant...

ubuntu@ubuntu:~$ cd Desktop
ubuntu@ubuntu:~/Desktop$ ls
examples.desktop  seatools_cli.tar  st  ubiquity-gtkui.desktop

ahh i see... I used sudo ./st afterwards and I got right in... took me awhile but I feel good for figuring it out myself.

---

### Post by YoungTechie on 2009-09-20
Ok after tinkering around with the SeaTools Diagnostic I came up with this info on the HDD in question.

```
ubuntu@ubuntu:~/Desktop$ sudo ./st -i /dev/sg0
    /dev/sg0
    Vendor = ATA      
    Product = ST3200822A       
    Version = 3.01
    Serial Number = 
    Copyright = 
    SCSI Firmware = 
    Servo RAM Release = 
    Servo ROM Release = 
    Servo RAM Date = 
    Servo ROM Date = 

    Blocksize = 512, Highblock = 390721967, Capacity = 195361 MB
    -this is a Seagate drive
    -this drive does not support DST
    -Mode Page Settings [current value (default)]:
        -WCE bit = 1 (0)
        -RCD bit = 0 (0)
        -AWRE bit = 1 (0)
        -ARRE bit = 0 (0)
        -DExcpt bit = 0 (0)
        -Number of cache segments = 0 (0)
        -JIT bit 0 = 0 (1)
        -JIT bit 1 = 0 (1)
        -JIT bit 2 = 0 (1)
        -JIT bit 3 = 0 (1)

```

K So still think it's a bad Disk?

---

### Post by Sidewinder1 on 2009-09-20
I believe that you're missing the "/" (slash), immediately preceding Desktop.
Try this:
```
cd /Desktop
``` 
Hope that helps.

---

### Post by YoungTechie on 2009-09-20
well i've gotten into the program now but all drive tests fail... im gonna see if i need some sort of firmware update..

---

### Post by Spiffworks on 2009-09-20
Didn't your Ubuntu install on the disk work?

Edit:I just saw the previous posts. Seems to be a bad sector for sure now

---

### Post by talsemgeest on 2009-09-20
> **Sidewinder1 said:**
> I believe that you're missing the "/" (slash), immediately preceding Desktop.
Try this:
```
cd /Desktop
``` 
Hope that helps.
That is a bad suggestion, as that tells it to go into the root directory, then into the Desktop folder in the root directory. ~/Desktop maybe, but not /Desktop.

---

