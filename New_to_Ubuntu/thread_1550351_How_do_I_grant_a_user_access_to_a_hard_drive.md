---
title: "How do I grant a user access to a hard drive?"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by memoria on 2010-08-10
I have 2 users on my box. My original admin username i created for my self and another one for my girlfriend. On her username she cant open her external hardrive thats plugged into thru the usb and she cant access my internal hard drive either. (We have two internal hard drives. one with the OS and the other is storage for audio/video).

So I know absolutely nothing about linux. So if you got some nifty terminal commands please make it copy/paste friendly without too much editting.

Its a fairly clean install of Lucid Lynx so things should be pretty default.

her external usb drive name is "SimpleDrive"
for "type" it says "folder (inode/directory)"
Location: /media
volume: SimpleDrive

I understand there is something called fstab out there. To be honest with you right now I am studying Insurance for a career and its too much trouble for me to bother leaning a how new knowledgebase of information. So please help me out here. 

For my intenral hard drive tihngs get complicated. I only want to about 2 folders on the hard drive. the rest i want to remain restricted to my access only. In Windows all you would have to do is right click the folder and check mark a box or two...With ubuntu you have to study for an exam....Hopefully it wont be the case for this issue (As it has been for every other minor problem ive run into with ubuntu)


Thank you for your help. And please forgive my love of windows. One day I will be a ubuntu wiz im sure! (not really)

---

### Post by Peter09 on 2010-08-11
Are these drives formated as NTFS? (windows)

---

### Post by memoria on 2010-08-11
I believe they where both designed for Windows. The SimpleDrive has the default settings that CostCo sold us...Plugs into any Windows based computer and loads up right away through USB.

The internal drive is also "The way it came"...Its a Western Digital Caviar Black 1tb.

They both worked on default settings with WindowsXP. So I think its safe to assume they are formatted using the default Windows format.

How would I double check that?

---

### Post by frenchn00b on 2010-08-11
depending on your needs and type partition here is an example 

```
echo "/dev/hda1       /mnt/hda1       vfat    user,rw,auto,umask=0000,uid=1000,gid=1000  0    2" >> /etc/fstab
echo "/dev/hda5 /mnt/hda5 ntfs-3g auto,user,defaults,force 0 0" >> /etc/fstab
echo "/dev/hda6 /mnt/hda6 ntfs-3g auto,user,defaults,force 0 0" >> /etc/fstab


```

---

