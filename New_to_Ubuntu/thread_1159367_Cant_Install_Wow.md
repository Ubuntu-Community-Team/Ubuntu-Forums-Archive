---
title: "Cant Install Wow"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Jishen on 2009-05-14
So I Tryed To Install From Blizzards Site And That Wouldnt Work Cause I Couldnt Get My Firewall Config Right, So Then I Got Battlechest And That Didnt Work Either, Saying I Wasnt An Owner So I Couldnt Do Anything With That. So Now Im Trying To Install The Individual Disks (DVD) And When I Run Install It Says No Installer Data Was Found, Or If I Try To Run It From The Terminal It Says:

fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
wine: could not load L"C:\\windows\\system32\\Installer.exe": Module not found
chad@chad-laptop://home/chad/Desktop$ fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:iphlpapi:DeleteIpForwardEntry (pRoute 0x87e978): stub
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x87e908): stub
fixme:service:EnumServicesStatusW 0x127c40 type=30 state=3 (nil) 0 0x87e798 0x87e7a4 0x87e7a0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x87e5a8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x1276b8,(nil)): stub


Any Help?

---

### Post by AndThenWhat on 2009-05-14
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

There's a HowTo if you scroll down on this website.

---

### Post by alexandari on 2009-05-14
solution number 1:

```
sudo mount -o remount,unhide /dev/cdrom
```

solution number 2:

Just copy all the data from the CDs to a folder on your hard drive. Then run the installer

---

### Post by Muffinabus on 2009-05-14
If you have a Windows box handy, installing it on there and copying the World of Warcraft folder over to your Linux box works like a charm.  It's easier to patch on Windows too, heh.

---

### Post by Jishen on 2009-05-14
Ive Tryed The Unhide Mounting But Still Haveing Problems. Is Copying The Files From The Disk To A Folder On My Desktop The Same As Copying To HD? I Tryed The Website 
[http://appdb.winehq.org/objectManage...sion&iId=14154](http://appdb.winehq.org/objectManage...sion&iId=14154)

And It Told Me Others Were Having The Same Problems But Didnt Really Help Me On What Exactly To Do. Im Really At A Loss Here. Im Running Jaunty And The Newest Version Of Wine. Any Other Ideas?

---

### Post by dazman19 on 2009-05-14
bro tis pretty easy, i did it with wine.

The best thing to do it get all the big data files off wow. I copy all of CD1, and just the mpq's (600-700mb data files) for cd's 2,3 and 4 i move to the same folder. then run them. You will need to have your video card set up to use OpenGL. If not I would focus on this first. 
I would put it in /home/uname/.wine/c/wowinstallfiles/

There are 3 dll files (cant remember their names) you need to put into the windows directory, if you read the details on the wine site you can get the names of them and copy to your wine windows\system32 directory. Usually /home/uname/.wine/c/windows/system32/ 

Same for TBC do the same thing this will be cake once you got wow installed. 
Then do the same for WoTLK.

If you got the patches just execute them in the shell. THe only issue I had with installing wow was the HTML fonts and patch notes wouldnt display because i hadnt set up my fonts correctly. 

your error looks like you executing the wrong file 
wine: could not load L"C:\\windows\\system32\\Installer.exe": Module not found

---

### Post by Jishen on 2009-05-14
> **dazman19 said:**
> bro tis pretty easy, i did it with wine.

The best thing to do it get all the big data files off wow. I copy all of CD1, and just the mpq's (600-700mb data files) for cd's 2,3 and 4 i move to the same folder. then run them. You will need to have your video card set up to use OpenGL. If not I would focus on this first. 
I would put it in /home/uname/.wine/c/wowinstallfiles/

There are 3 dll files (cant remember their names) you need to put into the windows directory, if you read the details on the wine site you can get the names of them and copy to your wine windows\system32 directory. Usually /home/uname/.wine/c/windows/system32/ 

Same for TBC do the same thing this will be cake once you got wow installed. 
Then do the same for WoTLK.

If you got the patches just execute them in the shell. THe only issue I had with installing wow was the HTML fonts and patch notes wouldnt display because i hadnt set up my fonts correctly. 

your error looks like you executing the wrong file 
wine: could not load L"C:\\windows\\system32\\Installer.exe": Module not found
Dazman19- 
Is There Anyway I Could Get You To Go More Indepth On This? Im Really Brand New To Everything So Speaking Like Your Talking To An 8 Year Old Would Help Haha. I Also Am Running The DVD version So I Have Only 1 Disk If That Changes Anything.  How Do I Go About Messing With The Opengl?

---

### Post by bacardiandwatermelon on 2009-05-15
I have used winedoors in the past, but not for wow, you could give it a go...

Have you seen this site??
[https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")

---

### Post by Jishen on 2009-05-15
Ya Ive Been There And Followed It To The Letter

---

