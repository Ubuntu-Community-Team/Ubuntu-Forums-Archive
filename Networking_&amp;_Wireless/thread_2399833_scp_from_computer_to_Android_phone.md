---
title: "scp from computer to Android phone"
date: 2018-08-30
forum: Networking &amp; Wireless
---

### Post by again? on 2018-08-30
Is it possible to scp a file from my pc to my android phone?
I can ssh to my computer and cd to a directory but when I try to 
copy a jpg to my phone I get an error.
I've tried a couple of phone directories.
Is this possible on an unrooted Android?
Am I doing something wrong?
This is a transcript from my phones ssh client.
```
[COLOR="#006400"]**glen@Bionic:~$**[/COLOR] cd Documents/

[COLOR="#006400"]**glen@Bionic:~/Documents$**[/COLOR] ls
bookmarks_25_4_18.html  coffee.jpeg  invoice.pdf

[COLOR="#006400"]**glen@Bionic:~/Documents$**[/COLOR] scp glen@Bionic:124.[COLOR="#696969"]xxx.xx.xxx[/COLOR] coffee.jpeg /mnt/m_internal_storage/Download
/mnt/m_internal_storage/Download: No such file or directory
```

---

### Post by SeijiSensei on 2018-08-30
You can only write to a few locations in Android like your Documents directory.

There are easier options to move files to your phone.  You can connect it to the computer with a USB cable and use the MTP protocol.  If you're looking for network-based solutions, there's Wifi File Transfer Pro an app that turns your phone into a mini webserver that you can connect to with a browser.  Or you can try KDE Connect, a program written for KDE but I'm pretty sure would work on regular Ubuntu as well.  There's an Android app and a corresponding Linux app.  You can do all sorts of things with KDE Connect besides just transferring files.

---

### Post by again? on 2018-09-01
Thanks for the info.
I usually use ssh to copy a file to my computers megasync directory where I can
then access on my phone through the Mega app.
Not having used scp before was just seeing if I could get it to work.
I'll just stick with ssh and mega to access remotely.

---

### Post by edadasiewicz on 2018-09-01
I  use Ghost Commander on both my Android tablet (rooted) and Pixel phone (non-rooted) with the sftp-plugin.

---

### Post by again? on 2018-09-02
I am using [**Amaze**]("https://play.google.com/store/apps/details?id=com.amaze.filemanager&hl=en_AU") file manager in Andriod.
which has an Ftp server plugin.
So I can start that and connect via my PC's browser and copy files off my phone to my PC.

Using sftp how do you copy files from PC to phone?
I have an open-ssh-server running on my PC.
Do I need to also start an ftp server on my PC to connect using sftp from my phone
or do you just need an ssh-server running?
I know little about this.

---

### Post by edadasiewicz on 2018-09-02
I have both openssh-server and openssh-sftp-server installed on my desktop.  With those 2 I am able to access the desktop (thru ssh and sftp) from other desktops, laptops, tablets and smartphones.

---

### Post by again? on 2018-09-18
Found the easiest for my use when on the rare occasion I want a file remotely from my pc 
is to use ssh to copy it to my megasync folder and then use the Mega app on phone to access.

For local transfer over wifi I found my phone has a system app Xender which I didn't know about
that allows to connect via the PC web browser on **local address:port**.
From my PC I can browse my phone files or drag and drop files into the browser.

---

