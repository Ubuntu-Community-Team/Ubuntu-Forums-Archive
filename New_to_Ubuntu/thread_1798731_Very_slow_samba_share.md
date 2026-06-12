---
title: "Very slow samba share"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by Floepsa on 2011-07-06
Hello,

I have installed ubuntu 10.4 on my old computer and put samba on it, but with me windows 7 laptop i have an very slow download speed so i cant even watch an video from the share. I have shared an external harddrive on the computer.

---

### Post by kerry_s on 2011-07-06
usb speed + 5400 speed hd. over wifi?

---

### Post by Floepsa on 2011-07-07
Yes, but it is with my lan network.

---

### Post by kerry_s on 2011-07-07
> **Floepsa said:**
> Yes, but it is with my lan network.

so if you plug the usb drive to your laptop it plays fine?

---

### Post by Floepsa on 2011-07-07
Yes, then i get around 20 mb/s

---

### Post by Floepsa on 2011-07-09
Anyone?

---

### Post by Floepsa on 2011-07-18
Still no solution..

---

### Post by Floepsa on 2011-07-26
Still need help...

---

### Post by androssofer on 2011-07-26
is your lan forwarding all the samba ports:

137 
138						
139
389
445
901

not sure if all are vital. but windows is fussy with things like this. dnt know which tcp which r udp, so i forward all mine as both tcp and udp...

additional:

check smb.conf and make sure the line starting "socket options" looks like this:

```
socket options = SO_KEEPALIVE
```

---

### Post by Floepsa on 2011-07-26
Thanks for your reply, do i need to forward it with the ip adress of my ubuntu computer or my laptop?

---

### Post by androssofer on 2011-07-26
> **Floepsa said:**
> Thanks for your reply, do i need to forward it with the ip adress of my ubuntu computer or my laptop?

forward them to the samba server where the shares are. so the ubuntu computer...

---

### Post by androssofer on 2011-07-26
check ur firewall is letting them though aswell. install "firestarter" and allow incomming connections for ur laptop to those ports.

for more info on doing this: [click here]("http://www.techmetica.com/howto/configure-ubuntu-firewall-using-firestarter/") 

but because you can access your shares already i'd say u might not need this part... but worth a try

---

### Post by Floepsa on 2011-07-26
I did al this, i think its a little quicker now, but now i have an other question about transmission. Because i download all the files to an external harddrive. But when i restart my computer i get the following message:  No data found! Ensure your drives are connected or use "Set Location". To re-download, remove the torrent and re-add it.

Then i have to verify the torrent again and that takes a big amount of time, i guess why transmission does that because it begins to download before the hardrive is mounted.

---

### Post by androssofer on 2011-07-26
> **Floepsa said:**
> I did al this, i think its a little quicker now, but now i have an other question about transmission. Because i download all the files to an external harddrive. But when i restart my computer i get the following message:  No data found! Ensure your drives are connected or use "Set Location". To re-download, remove the torrent and re-add it.

Then i have to verify the torrent again and that takes a big amount of time, i guess why transmission does that because it begins to download before the hardrive is mounted.

i'm assuming tranmission loads on boot? 

if you did it via the "startup programs" program, then open that up, select the 1 for tranmission and edit it. then change the command to be:

```
sleep 10 && transmission
```

that will make it wait 10 seconds before it starts and allow ubuntu to mount your drive...

---

### Post by Floepsa on 2011-07-26
That doesnt work, ive also tried the code: sleep 5s; transmission %F but that doesnt work either. When i type transmission %F then it will start up immediately.

---

### Post by androssofer on 2011-07-28
> **Floepsa said:**
> That doesnt work, ive also tried the code: sleep 5s; transmission %F but that doesnt work either. When i type transmission %F then it will start up immediately.

is it when you launch tranmission on boot? or just in general that it gives you the trouble?

---

### Post by Floepsa on 2011-07-31
It happens when on boot, the code without sleep works just fine..

---

### Post by androssofer on 2011-07-31
> **Floepsa said:**
> It happens when on boot, the code without sleep works just fine..

wierd... could u create a script? "runTranmission.sh":

```
#!/bin/bash  
sleep 5s; transmission %F
```

then run tht on boot?

---

