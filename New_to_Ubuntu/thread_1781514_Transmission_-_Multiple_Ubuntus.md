---
title: "Transmission - Multiple Ubuntus"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by avnd on 2011-06-13
Hello there!  I have installed two Ubuntus 11.04 Desktops on two separate partitions. I then started a torrent download with Transmission in one of the 2 Ubuntus. I save the downloaded files in a separate data partition.   My question is that if I were to run the same torrent file in Transmission in the 2nd Ubuntu and point the target folder to the same folder I was using before in the data partition (which now has bits and pieces of the file downloaded in the 1st Ubuntu), will Transmission skip the already downloaded parts or start fresh all over again?  Thank you.

---

### Post by StrayEddy on 2011-06-13
I m pretty sure it would skip the already downloaded parts to continue the download. Just make sure your transmission options are the same.

---

### Post by doas777 on 2011-06-13
if the two clients are sharing a working directory, then the second client should detect the temp files and check them to determine what is there and what is not. 
no guarantees though.

---

### Post by DanneStrat on 2011-06-13
> **avnd said:**
> will Transmission skip the already downloaded parts or start fresh all over again?  Thank you.

Hi! Interesting question.

No, it will not start over.

It should resume the incomplete files.

---

### Post by Joe of loath on 2011-06-13
I have had downloads resume, even when switching clients.

---

### Post by DanneStrat on 2011-06-13
> **Joe of loath said:**
> I have had downloads resume, even when switching clients.

Yes, that is also possible.

BT-clients can append an extension to incomplete files to get exclusive 

rights to those files. Some examples are ".uT", ".bc" and .part. So if 

you had a windows box running a torrent in bitcomet for example, then the incomplete 

files would have the extension ".bc". If you wanted to resume those files 

with transmission under ubuntu, you would first have to remove ".bc" from 

the filename and then transmission would be able to resume that torrent.

Just thought I would leave it here since it's good to know.

---

### Post by avnd on 2011-06-14
(@DanneStrat, Joe of loath, doas777 & StrayEddy) Thank you for your replies and further confirmation, everyone.

---

### Post by DanneStrat on 2011-06-14
> **avnd said:**
> (@DanneStrat, Joe of loath, doas777 & StrayEddy) Thank you for your replies and further confirmation, everyone.

You're welcome.

---

