---
title: "lost pictures"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by sandy55 on 2009-03-06
When i changed from windows xp to ubuntu 8.10 i seem to have lost all of my photos from my hard drive. These pictures are very important to me. I have tried to get them back using various programs but they all come up with an error 66. (No idea what that is.) I am an absolute beginner with ubuntu so i have and am obviously doing something wrong. I have 3 drives in my system and the photos are on one my slave drives.
Any suggestions would be appreciated. Remember to keep it simple as i am a novice.
Thanks
Sandy

---

### Post by taurus on 2009-03-06
Open a terminal and post the outputs of these commands, running one at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

