---
title: "missing /corrupted file command interperter"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by YellowBronco on 2011-07-12
im trying to start umbuntu and im getting a 

"the following file is missing or corrupted: "

then it tells me

"type the name of the command interpeter (e.g,/ C:\WINDOWS\COMMAND.COM)
A>  "

any command i put in tells me missing or corrupted,     im lost

dan

specs

ubuntu 11.04 sometimes
amd athlon 64x2 dual core pro 5000+ 2.59 gh
bios american megatrends v1.6
smbios 2.5
power thermaltake tr2-500pp psf450s
6 g ram crucial
nvidia gforce 7900 gt/gto grapics w/ dual 22 monitors
dr q memorex 16x double layer 5395 cd-r/rw drive
dr r sony optiarc dvd rw ad-7190s ata 1.02
dr A zid citizen tuv
hd B seagate st340810a 40g 
hd C crucial ssd 64g
hd E western digital 1600aajs 160g

---

### Post by Rubi1200 on 2011-07-13
Hi,

Please do the following so we can get a better overview of what is where on the system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by YellowBronco on 2011-07-13
i cant get into  ubuntu at all, on all three computers,,,,,im going to start a new thread 
uninstall ubuntu and install xp,
thanks

---

### Post by Rubi1200 on 2011-07-13
It's your decision of course, but if you were to explain in more detail what is going on that you are unable to boot 3 computers or even run a LiveCD then we might be able to help you find a solution.

In any event, I wish you the best of luck whatever you decide.

---

### Post by YellowBronco on 2011-07-13
im starting to think that i ran an old copy of ubuntu, 6.06 on top of a 11.04 , i found a ubuntu book in the library and wanted to see what was on it, was before i knew the differance in the versions, well, i think i made the system unstable this way , and like a normal windows guy , thought that if i started over it would fix it, on 2 amd64 machines.

then i tried to reformat the disks with amd , that didnt work either, i didnt know about the different file types, windows/linux never the twain shall meet, 
that said i then tried to install windows back on top,,, of corce that didnt work either, ubuntu will not start on any of them, 

i then reformated a external hard drive and tried to boot to that , but there are no driver controls in it, so its not recognized, ???????  

next options are 
1 reformat another hard drive and try it again
2 copy all of a working xp machine to the external hd
3 try to boot to windows 95 and just keep updating operating systems, then reload ubuntu
4 install IEEE-1394 sbp-2 and run off Samba
5 re try bart PE , one disk to run it does not have service pk 2 and the one that does is a dell odm

i get a fedora core screen , dont know what to do with it though

---

### Post by westie457 on 2011-07-14
> **YellowBronco said:**
> im starting to think that i ran an old copy of ubuntu, 6.06 on top of a 11.04 , i found a ubuntu book in the library and wanted to see what was on it, was before i knew the differance in the versions, well, i think i made the system unstable this way , and like a normal windows guy , thought that if i started over it would fix it, on 2 amd64 machines.

then i tried to reformat the disks with amd , that didnt work either, i didnt know about the different file types, windows/linux never the twain shall meet, 
that said i then tried to install windows back on top,,, of corce that didnt work either, ubuntu will not start on any of them, 

i then reformated a external hard drive and tried to boot to that , but there are no driver controls in it, so its not recognized, ???????  

next options are 
1 reformat another hard drive and try it again
2 copy all of a working xp machine to the external hd
3 try to boot to windows 95 and just keep updating operating systems, then reload ubuntu
4 install IEEE-1394 sbp-2 and run off Samba
5 re try bart PE , one disk to run it does not have service pk 2 and the one that does is a dell odm

i get a fedora core screen , dont know what to do with it though

Choices, choices, choices.

What would you like to be doing to your computer?
Are you wanting to dual- (or more)boot with lots of Windows OS's
and Linux OS's all on one hard drive (each with its own partition) or all Windows on one hard drive and Ubuntu/Linux on other hard drives?

Make a decision. Let us know by replying. We cannot advise if you do not know what you want.



Ps nothing to do with helping. In your profile pic nice earrings haha

---

### Post by mcduck on 2011-07-14
> 
"type the name of the command interpreter (e.g,/ C:\WINDOWS\COMMAND.COM)
A> "


This comes when you are trying to boot the Ubuntu CD? How did you burn the disc? That's a Windows/DOS error, not something you'd see during Linux boot.

The disc must be burned as a disc image, not as normal data CD or any "bootable CD" option your burning application might have. This might help: [https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by YellowBronco on 2011-07-22
well, its been almost 2 wks and im finaly to where i can reinstall  11.04, it was my own stupidity, i put a version 6 on top of 11.04. i  thought it was just info from the library , not a whole new install.  like i said^ i like ubuntu, ive been too enamored in the bill gates  world to fully get it all of ubuntu yet, i guess if u are starting out  fresh with it it is easier then having to relearn things 
alot of my problem is i think i know how it works, well it only works that way in windows,, lol
there is probably alot of ways to do this but i nuked the disks all hds ,  re-installed a new os , xp not the vista stuff, had to re-find all  drivers this way and reinstall from bios, in order to do that i had to  take the motherboard out and find the codes on the back side of it
please dont anyone else do what i did
dan

---

### Post by westie457 on 2011-07-22
> **YellowBronco said:**
> well, its been almost 2 wks and im finaly to where i can reinstall  11.04, it was my own stupidity, i put a version 6 on top of 11.04. i  thought it was just info from the library , not a whole new install.  like i said^ i like ubuntu, ive been too enamored in the bill gates  world to fully get it all of ubuntu yet, i guess if u are starting out  fresh with it it is easier then having to relearn things 
alot of my problem is i think i know how it works, well it only works that way in windows,, lol
there is probably alot of ways to do this but i nuked the disks all hds ,  re-installed a new os , xp not the vista stuff, had to re-find all  drivers this way and reinstall from bios, in order to do that i had to  take the motherboard out and find the codes on the back side of it
please dont anyone else do what i did
dan

Hi, thought you had fallen off the planet. lol

Glad you have got it sorted now and for what you have just done 2 weeks would be about right to sort it all out. If that had happened to me the laptop would have resembled half a boomerang. That is throwing a straight stick. No way is it going to return.

Good luck and enjoy your future Ubuntu experiences.

---

