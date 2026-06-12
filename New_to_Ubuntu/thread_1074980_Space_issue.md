---
title: "Space issue"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by metzy85 on 2009-02-19
Ok so i have a dual boot with xp and ubuntu 8.07 and the partitionis fat32 which i think is the problem. The partition size is about 50gb and it wont let me move 3gb on to it what is wrong you think?

---

### Post by bumanie on 2009-02-19
FAT32 has an inherent limit of 4gb files, so I am not sure why it won't accept the transfer of 3gb. There is no need to use FAT32 as linux now has very good and stable support for reading/writing to ntfs. I would change the data drive to ntfs filesystem. I assume you are using 8.04 (there is no 8.07). Go to terminal > sudo apt-get install ntfs-configThen find the configuration tool under Applications --> System Tools --> NTFS configuration tool. You should not have any hassles after this. Back the music you already have on that drive first as formatting to ntfs will wipe what is on the drive.

---

### Post by metzy85 on 2009-02-19
I had no idea linux could handle ntfs thanks sso much i will take care of the resst thank you

---

