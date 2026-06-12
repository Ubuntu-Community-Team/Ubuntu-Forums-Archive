---
title: "Help Ubuntu access to windows files"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by raspercacho on 2011-02-13
I had windows and i installed ubuntu... then windows gave me an error and now all my C:\ Drive files are lost... And now for some reason the C:\ drive is in ext4 for some weird reason... could anyone help me? i really need one specific folder that remained in my desktop

PS: Does anyone know how to configure the Empathy chatting? doesnt work for me

PSS: Thanks for any help you can bring for me

---

### Post by Eternal_Light on 2011-02-13
Since the C drive is in ext4 you can access it from your ubuntu installation but there is a good chance it got erased. For it to be ext4 you must have mistakenly formatted it during the installation of ubuntu and in that case I don't know what can be done for your lost data. :(


To access it from ubuntu you just have to open your nautilus. In the "places" section you will see the partition you are looking for and you can browse its contents directly from there.

---

### Post by Guilden_NL on 2011-02-13
I agree with Eternal Light.  Unfortunately, given that it was reformatted and to EXT4 format, the tools that I could suggest for file recovery will not work.  Everything I am familiar with only works with NTFS and FAT native files being quick formatted.

However.....can you open Windows and see any drives?  There may be an outside chance that your drive naming was changed.  Not enough info to tell us whether you're talking about from within Ubuntu or Windows.  A little more information will help us help you.

---

### Post by CaptainMark on 2011-02-13
Go to applications> accessories> terminal and give us the output from ```
sudo fdisk -l
```(thats a lower case L) your windows partition if it still exists will have NTFS under the system column, its ifs not there, its probably lost im afraid, i cant offer much recovery advice

---

