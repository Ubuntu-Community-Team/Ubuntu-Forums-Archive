---
title: "Why I'm unable to create a sharing folder?"
date: 2017-10-19
forum: Networking &amp; Wireless
---

### Post by uzumakifahim on 2017-10-19
I have 2 PC's installed Linux Mint 17.X and Ubuntu 16.04  respectively. Now I want to share a folder between these 2 PCs. I've  followed the following steps :
  
[LIST=1]
[*]Right click on the folder I want to share.
[*]Select "Sharing options".
[*]Select "Share this folder" and "Allow others to create and delete files in this folder".
[*]And click "Create share".
[/LIST]
  After this folder icon has also been changed. But unfortunately I'm not getting this folder to other PC to access. 
  How to solve this issue. Please help.

[ATTACH=CONFIG]277166[/ATTACH][ATTACH=CONFIG]277167[/ATTACH]

---

### Post by Morbius1 on 2017-10-19
Why not start with the Mint machine:

From that machine run the following command and post it's output:
```
net usershare info --long
```

In the mean time:
[1] Run this command to find the exact host name of your Mint box:
```
hostname
```
[2] On the Ubuntu machine open a terminal and run:
```
nautilus smb://hostname.local
```
[COLOR=#0000cd]*Change hostname to the Mint host name you found in step 1 - and don't forget to add the .local at the end.*[/COLOR]

---

