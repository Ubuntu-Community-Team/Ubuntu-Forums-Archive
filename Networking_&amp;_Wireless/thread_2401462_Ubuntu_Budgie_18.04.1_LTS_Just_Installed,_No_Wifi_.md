---
title: "Ubuntu Budgie 18.04.1 LTS Just Installed, No Wifi Adapter found"
date: 2018-09-18
forum: Networking &amp; Wireless
---

### Post by emmbego on 2018-09-18
Hello people from the forum.
I´m just starting to know about ubuntu, and i decided to dual boot my windows 10 laptop with ubuntu budgie, i installed it perfectly, and everthing seems correct except the wifi. I can connect perfectly through ethernet. In the settings it says that there is no wifi adapter or something like that. I know i have a broadcom adapter. 

At the moment of writing this i dont have acces to my pc, so if you ask for more info about the system or the adapter, ill post it in an update when i get home :)

UPDATE: So, i got the wireless-info.txt, made it executable, ran it, and i got a txt file with the same name that only says : 

########## wireless info START ##########

Literally there is nothing more in the file, and i didnt get one with the contents of the examples in the other forum pages, neither i got a tar.gz.
(made it with the offline method. The online method that uses the code with  "wget" throwed me this (btw im still connected through ethernet):  

Resolving github.com (github.com)... failed: Connection timed out.
wget: unable to resolve host address &#8216;github.com&#8217;

What can i do now?

---

### Post by jeremy31 on 2018-09-18
When you get home see the wireless script link in my signature and post the results

---

### Post by emmbego on 2018-09-18
I remembered i tried some command that gave me information about some hardware, before this i followed some other tutorials with no luck. One of the things i got was a number of the broadcom adapter, : [14e4:4365] (rev01). I have no idea what does that number refer to, but maybe is usefull to solve my issue, idk.

---

### Post by jeremy31 on 2018-09-18
That one needs either broadcom-sta-dkms or bcmwl-kernel-source to be installed and you will need to have secure boot disabled if Ubuntu was installed in EFI mode

---

### Post by emmbego on 2018-09-22
UPDATE: I decided to change Budgie for Ubuntu studio, installed it, wifi still doesnt work, but the command you gave me worked this time, there it is i think so... [ATTACH]281136[/ATTACH]

---

### Post by jeremy31 on 2018-09-22
What happens with ```
sudo modprobe -v wl
```

---

### Post by emmbego on 2018-09-22
UPDATE: DUDE, i did that and followed the steps on the page of your wireless script, with broadcom drivers, made something with the secure boot on the bios, and now is fixed!  Thank you very much, you saved my life man.

---

