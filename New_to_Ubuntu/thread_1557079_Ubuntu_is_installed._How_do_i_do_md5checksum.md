---
title: "Ubuntu is installed. How do i do md5checksum?"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by Hawhaw1 on 2010-08-20
Hey all. I really need help here as i am completely new to Ubuntu.
I am sorry for a new thread but i am unsure how to delete the old one.

I recently downloaded Ubuntu 10.04 from Torrentz.com.
It installed fine, but when i checked disk for errors it stated that there were 2.
Since i did not download it directly from Ubuntu.com, i would like to know how to run md5checksum to make sure it is safe to use.
HOW do i do this? I have looked on numerous threads but i do not understand.

---

### Post by Robert.Thompson on 2010-08-20
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Hawhaw1 on 2010-08-20
Ive looked at that but it does not help me.I need help from one of you guys/

---

### Post by cascade9 on 2010-08-20
You dont run MD5checksums on an installed system, you are meant to do it against the .iso you d/led. 

Easier to just use the 'recheck' function that most every torrent client I've used has. 

BTW, VERY bad idea to go torrenting any OS from 'torrents.com' (or TPB, mininova, etc etc.). Always get teh torrents from the original source, its much safer- 

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by Sef on 2010-08-20
1) Open the Terminal (Applications > Accessories > Terminal)

2) Copy and paste this command (or type) 

```
cd ~/Downloads
```

3) That will take you to the download directory

4) Then type in 'md5sum' (without quotes)

5) Then start typing in the name of the program exactly how it is e.g.,  

```
md5sum ubuntu-10.04-desktop-amd64.iso
```

Hint: after typing in a word or two, press enter and the rest will appear.

6) After the md5sum comes up, check it against the one on the website; they should be identical.  If not, redownload.

---

### Post by Hawhaw1 on 2010-08-20
> **cascade9 said:**
> You dont run MD5checksums on an installed system, you are meant to do it against the .sio you d/led. 
 
Easier to just use the 'recheck' function that most every torrent client I've used has. 
 
BTW, VERY bad idea to go torrenting any OS from 'torrents.com' (or TPB, mininova, etc etc.). Always get teh torrents from the original source, its much safer- 
 
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)
 
Thanks.
Problem though, i have allready downloaded the version from Ubuntu, but it will not run. It reaches the Ubuntu loading screen and stays there, after i select language and select INSTALL UBUNTU.
I also ran a 'check disk for errors' and it came back with 14 errors.
What do i do?
 
And Sef, i try that but it just says file or directory not found or does not exist, is this maybe because the iso is on the disk not the PC itself?

---

### Post by spec o spec on 2010-08-20
use md5checksun **filename** to find the md5sum

---

### Post by fatality_uk on 2010-08-20
COMPLETELY agree with cascade9. You should NEVER download Ubuntu from ANY other site that ubuntu.com. Are you trying to replace an existing OS such as Windows or are you looking to dual boot?

---

### Post by Hawhaw1 on 2010-08-20
> **fatality_uk said:**
> COMPLETELY agree with cascade9. You should NEVER download Ubuntu from ANY other site that ubuntu.com. Are you trying to replace an existing OS such as Windows or are you looking to dual boot?
 
I know thats why i have downloaded from Ubuntu and burned to a disk, but that will not work and i do not know how to get it to work.
Replace Windows since its broken.

---

### Post by themusicalduck on 2010-08-20
Also, you should always burn the disc at the lowest speed possible. If you burn it at maximum speed then there will almost certainly be errors.

---

### Post by jmfal on 2010-08-20
If your having problems installing from the live cd try the alternate iso

---

### Post by Hawhaw1 on 2010-08-20
Really annoying me now.
Downloaded again, link from ubuntu website, burned to a CD it found 15 errors, and would not install.
Burned again at a lower speed and it found 14 errors, BUT it still will not go past the ubuntu loading screen.
Why is this?? Could it be because i allready have ubuntu installed?

---

### Post by oldos2er on 2010-08-20
Could you please post your hardware specs?

---

### Post by Hawhaw1 on 2010-08-20
> **oldos2er said:**
> Could you please post your hardware specs?
 
How do i get a hold of them?
Also just burned another cd at slowest possible speed: 15 errors.
What do I do to install ubuntu 10.04.1 ?

---

### Post by oldos2er on 2010-08-20
The programs gnome-system-monitor and/or hardinfo will tell you. We mainly need to know CPU, RAM, and video card.

What app are you using to burn ISOs?

---

### Post by Hawhaw1 on 2010-08-20
> **oldos2er said:**
> The programs gnome-system-monitor and/or hardinfo will tell you. We mainly need to know CPU, RAM, and video card.

What app are you using to burn ISOs?


How do I find out that? Used  burncdcc

---

### Post by Hawhaw1 on 2010-08-20
Can someone help me please? I am currently using Ubuntu 10.04, connected to internet and everything but i am worried since i downloaded it from torrentz.
Can someone tell me how i can check to make sure this is safe to use? And what are the risks? PLEASE help! thank you!

---

### Post by ezsit on 2010-08-20
You have already gotten the replies you need. 
1. Re-download the ISO from the official Ubuntu repositories.
2. Verify the md5sum with the command: 
   **md5sum ubuntu-10.04.1-desktop-i386.iso**
3. Burn at a slow speed (4x should be fine). 

It should not be any more difficult than that. If you have already got Ubuntu installed, use that to download and burn. If you have Ubuntu, then burning an ISO file is no harder than right-clicking on the file and selecting "write to disc" as your option.

---

### Post by Hawhaw1 on 2010-08-20
> **ezsit said:**
> You have already gotten the replies you need. 
1. Re-download the ISO from the official Ubuntu repositories.
2. Verify the md5sum with the command: 
   **md5sum ubuntu-10.04.1-desktop-i386.iso**
3. Burn at a slow speed (4x should be fine). 

It should not be any more difficult than that. If you have already got Ubuntu installed, use that to download and burn. If you have Ubuntu, then burning an ISO file is no harder than right-clicking on the file and selecting "write to disc" as your option.

I allready have downloaded it from ubuntu site. I have also burned to numerous disks, but it will not install. It reaches the ubuntu loading screen , after selecting 'install' , and does not go past it.

---

### Post by jtarin on 2010-08-20
> **Hawhaw1 said:**
> I know thats why i have downloaded from Ubuntu and burned to a disk, but that will not work and i do not know how to get it to work.
Replace Windows since its broken.As mentioned...the only way to check the md5 is to go into the directory that contains your downloaded .iso file and run the md5 command as outlined, if it returns errors then you will have to download again. I would suggest using jDownloader as it will check the downloaded .iso for you. It's crossplatform so it will work in Win and Linux. If you want an accurate download this is the download manager I would suggest. Another option is to have the DVD maled to you if your internet speed sucks.

---

### Post by Hawhaw1 on 2010-08-20
> **jtarin said:**
> As mentioned...the only way to check the md5 is to go into the directory that contains your downloaded .iso file and run the md5 command as outlined, if it returns errors then you will have to download again. I would suggest using jDownloader as it will check the downloaded .iso for you. It's crossplatform so it will work in Win and Linux. If you want an accurate download this is the download manager I would suggest. Another option is to have the DVD maled to you if your internet speed sucks.

Thanks. I have tried to run md5sum but it came up 'input/output error'.
Ok I was using utorrent to download but now I'll use jdownloader if I need to download again.

---

