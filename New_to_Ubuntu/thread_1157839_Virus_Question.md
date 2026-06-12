---
title: "Virus Question"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Wormling on 2009-05-13
Hello everyone.  I am new to Ubuntu, and have been using it for about a month now on my laptop.  I have done some research into the topic of viruses on the Unix environment, but I have not been able to find out an answer to my question.  

My problem is that I am trying to save a friends files from his Windows Vista computer.  He had *no* antivirus, antispyware, firewall, etc installed for the past year, and his computer was a mess.  I am surprised it ran at all.  I transfered all of his critical files to a backup harddrive (750gb external) running FAT32.  Can I put these files on to my Ubuntu 8.10 Intrepid laptop without causing harm to my laptop?  Or will the viruses, trojans, etc eat away and make me need to reinstall my operating system as well?  

I *think* I am safe, but I am not entirely sure.  

Part two of my problem is cleaning these files.  Is there an antivirus I can run while on my Ubuntu laptop so that I don't have to put these infected files onto a Windows machine?  I looked at some antivirus programs through Synaptic Package Manager, but they appear to be for email servers.  Would they be able to do a check on an external harddrive, or maybe my /home/user drive and scan for viruses?  Or, should I try to use wine, and with Wine install something like AVG antivirus, Kapersky antivirus, or avast antivirus and use those to try to clean the files?   

Thanks in advance for any help and insight you provide.  
- Wormling, MS Certified on Win2k OS and C++ Programmer

---

### Post by skymera on 2009-05-13
Windows viruses cannot run on Ubuntu.

So yes, you can copy his files over fine :)

Avast and AVG BOTH have Linux clients. These mainly scan for Windows viruses which is great for you :)

You can mount his hard drive (or just scan his files) and the viruses should be picked up.

---

### Post by binbash on 2009-05-13
I suggest this one : [http://www.ubuntu-inside.me/2009/04/new-free-antivirus-for-nix-platforms.html](http://www.ubuntu-inside.me/2009/04/new-free-antivirus-for-nix-platforms.html)

---

### Post by lovinglinux on 2009-05-13
> **binbash said:**
> I suggest this one : [http://www.ubuntu-inside.me/2009/04/new-free-antivirus-for-nix-platforms.html](http://www.ubuntu-inside.me/2009/04/new-free-antivirus-for-nix-platforms.html)

+1 for Bitdefender

---

### Post by billgoldberg on 2009-05-13
[B]Can I put these files on to my Ubuntu 8.10 Intrepid laptop without causing harm to my laptop?  Or will the viruses, trojans, etc eat away and make me need to reinstall my operating system as well?  

I *think* I am safe, but I am not entirely sure.  [/B]

You are safe.

**Part two of my problem is cleaning these files.  Is there an antivirus I can run while on my Ubuntu laptop so that I don't have to put these infected files onto a Windows machine? **

Clam AV comes to mind. There are others like AVG, ...

These apps don't help against potential Linux viruses, so only run the when you need to get rid of Windows viruses.

---

### Post by Wormling on 2009-05-13
Thank you all very much for the quick replies.  I am now installing BitDefender to try to remove the virii.

---

### Post by bigboy_pdb on 2009-05-13
> **Wormling said:**
> Can I put these files on to my Ubuntu 8.10 Intrepid laptop without causing harm to my laptop?  Or will the viruses, trojans, etc eat away and make me need to reinstall my operating system as well?

A virus can only run on the OS series it was programmed for. So a Windows virus wouldn't affect a Linux system. If you were to run it with wine, it might infect some of your wine programs, but I wouldn't recommend trying that because I don't know how well wine integrates itself with the system it is running on.

Even if you were using a Windows operating system to copy the files directly from the hard drive you wouldn't get infected unless you ran an infected program or opened an infected document (such as an infected word document) on the system that you're using to copy the files.

It's also worth mentioning that only files that are executable (exe), scripts (js, bat, vbs), or that can contain programs (such as office documents) (doc, xls, ppt, mdb) can have viruses. Other files such as image formats (png, gif, jpg, bmp), media files that don't contain scripts (mp3, wav), and non-executable plain text files (txt) don't contain viruses.

Although, you should still be weary of any file from an unknown or untrusted source since extensions are hidden on the newer Windows OSes (meaning 'readme.txt' could be 'readme.txt.exe') and since it isn't the extension alone that determines the file type (for some files the first few bytes also indicate the file type). If you uncheck the option for hiding extensions, you can see which files are more likely to be problematic.

---

### Post by Wormling on 2009-05-13
Hello everyone.  Another quick question.  I am trying to install the BitDefender, but can't seem to figure out how.  I have downloaded these files:
BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run.md5
BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.rpm.run
BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.rpm.run.md5

I originally downloaded the deb files, and tried to run them with  
sudo BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run

but that did not work.  So then I tried
sudo ./BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run

Still nada.  Nothing I try to do with any of these files actually starts an install of any kind.  I got them from:
[http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/](http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/)

Do I by chance have the wrong install files for BitDefender?  I tried following the main website install areas, but that just kept giving me the exe for Windows.  I finally got this website through their Unices (I think that was the link) page.  If anyone knows how to install BitDefender, I would appreciate it.  

P.S.  I am also trying to install clamav through Synaptic Package Manager... After nearly 2 hours... I am still trying to install ClamAv...  Guess I still have lots to learn about Linux/Unix environment.

---

### Post by perlluver on 2009-05-13
The bitdefender.deb, just double click on it, and it should install, if not, then you may have the wrong architecture, and you will have to get the 32bit deb file.

---

### Post by LoGinthebest on 2009-05-13
I don't worry about this, because I tink my sudo password safe me=)))

---

### Post by Inaia on 2009-05-13
> **bigboy_pdb said:**
>  ...It's also worth mentioning that only files that are executable (exe), scripts (js, bat, vbs), or that can contain programs (such as office documents) (doc, xls, ppt, mdb) can have viruses. Other files such as image formats (png, gif, jpg, bmp), media files that don't contain scripts (mp3, wav), and non-executable plain text files (txt) don't contain viruses....

A special type of image with the ending of .GIFAR contains script, it's a combination GIF / JAR file which can be used to transmit malicious code online. Some image hosting sites don't properly check the file and assume it's a .GIF, however, the browser often runs it as a JAR, meaning that the code within gets activated, leading to infection.

[http://hackaday.com/2008/08/04/the-gifar-image-vulnerability/](http://hackaday.com/2008/08/04/the-gifar-image-vulnerability/)

Not sure how well an attack like this could be used against a Linux machine though.

---

### Post by iswear on 2009-05-13
> Hello everyone. Another quick question. I am trying to install the BitDefender, but can't seem to figure out how. I have downloaded these files:
BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run.md5
BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.rpm.run
BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.rpm.run.md5

I originally downloaded the deb files, and tried to run them with
sudo BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run

but that did not work. So then I tried
sudo ./BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run

Still nada. Nothing I try to do with any of these files actually starts an install of any kind. I got them from:
[http://download.bitdefender.com/SMB/...R_BR_RO/Linux/](http://download.bitdefender.com/SMB/...R_BR_RO/Linux/)

Do I by chance have the wrong install files for BitDefender? I tried following the main website install areas, but that just kept giving me the exe for Windows. I finally got this website through their Unices (I think that was the link) page. If anyone knows how to install BitDefender, I would appreciate it.

P.S. I am also trying to install clamav through Synaptic Package Manager... After nearly 2 hours... I am still trying to install ClamAv... Guess I still have lots to learn about Linux/Unix environment.

Yea i had problem with getting Bit defender to work to but i just figured out what i was doing wrong, i had it on the Desktop and never changed the derectoy.

So if you have on the file on the Desktop type [cd ~/Desktop],without the brakets, then type this:

chmod +x BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
sudo ./BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run

When your done typing those it will tell you about there licens agrement, jsut keep pressing enter untill you get to the bottom of the page and type 'accept'. Once its done installing it should be in accesorys or something like that, i dont know because im not using ubuntu right now. Also make sure you downloaded the right deb file, if you have an intel prosessor it wont work cause the files you have are for an amd64 prosessor.

---

### Post by Jazzy_Jeff on 2009-05-13
If you right click on the icon and go to properties just check the box to make it executable. Worked for me.

---

### Post by gn2 on 2009-05-13
> **Wormling said:**
> ~ virii ~

Nope, plural is *viruses*.

---

### Post by Sir Jasper on 2009-05-13
Hi,

I think your chance of solving this problem using Linux is so remote that I would suggest visiting:
[http://forum.emsisoft.com/](http://forum.emsisoft.com/)
becoming a forum member and copying your post into the "Offtopic" section.

Lynx, a Moderator there, will probably be the person who responds and he has huge expertise on viruses and Windows and he is no slouch with Linux.

There may also be other advantages, firstly a-squared Free is second to none in detecting all windows infections and the free help in the Malware Removal section has to be seen or experienced to be believed. Just have a look at some of the threads.

My regards

PS Even if I am mistaken, there is nothing to lose (and it says nothing detrimental about either Linux or this forum and its members).

---

### Post by bigboy_pdb on 2009-05-13
> **Inaia said:**
> 
A special type of image with the ending of .GIFAR contains script, it's a combination GIF / JAR file which can be used to transmit malicious code online.


Technically it's not a valid image format, but you're right that the file is malicious. What you mentioned is a good example of why a person should be careful either way.

---

