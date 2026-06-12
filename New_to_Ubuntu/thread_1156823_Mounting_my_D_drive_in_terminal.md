---
title: "Mounting my D drive in terminal?"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by zzzonked on 2009-05-12
Okay I'm a complete noob in this whole CLI thing and I wanna start to use terminal more and more these days after reading up on the benefits of it. Any good resources for me to start from?

Here's the main issue: I wanted to access a file in my D:\ drive. But when I typed ```
cd /media/disk/
```, terminal said there wasn't such a file or directory. But the drive's already been mounted in gnome. May I know why this is happening, and how do I fix this problem? Also, is there anything I can do to get my D:\ drive to be mounted by default everytime I log in? Because all my work and files are in there.

Thanks in advance.

---

### Post by zeroseven0183 on 2009-05-12
Do you have a label for your drive D? You can replace the "disk" by that label.

You can use TAB to complete the CLi entry. For example, if the label is "Data", type cd /media/Da then press tab to auto-complete it.

Check out Chapter 7 of [Keir Thomas' Ubuntu Pocket Guide and Reference]("http://www.ubuntupocketguide.com/download/ubuntupocketguide-v1-1.zip") for basic information on the command line.

Hope that helps. If it's more technical, let us know more about the symptoms.

---

### Post by zeroseven0183 on 2009-05-12
> **zzzonked said:**
> Also, is there anything I can do to get my D:\ drive to be mounted by default everytime I log in? Because all my work and files are in there.

You can use **NTFS Configuration Tool** to automatically mount your drive on startup.

To get it, type the following command:
```
sudo apt-get install ntfs-config
```

---

### Post by zeex on 2009-05-12
> **zzzonked said:**
> Okay I'm a complete noob in this whole CLI thing and I wanna start to use terminal more and more these days after reading up on the benefits of it. Any good resources for me to start from?

Here's the main issue: I wanted to access a file in my D:\ drive. But when I typed ```
cd /media/disk/
```, terminal said there wasn't such a file or directory. But the drive's already been mounted in gnome. May I know why this is happening, and how do I fix this problem? Also, is there anything I can do to get my D:\ drive to be mounted by default everytime I log in? Because all my work and files are in there.

Thanks in advance.

Hi, 

If you want all your windows drives mounted at startup try this.

Install ntfs-3g for NTFS drives

```
$ sudo apt-get install ntfs-3g
```

Label all your drives and try this [script]("http://stringofthoughts.wordpress.com/2009/04/16/auto-mount-window-drives-at-startup-ubuntu-810/").
If you are not sure about running scripts at startup, after booting your system run the script with sudo from terminal.

---

