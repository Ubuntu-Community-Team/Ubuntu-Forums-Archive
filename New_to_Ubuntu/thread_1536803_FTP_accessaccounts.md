---
title: "FTP access/accounts"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by ash369 on 2010-07-22
I want to be able to upload files from my windows PC to my linux server.

What do i need to install, and how do i make new accounts?

---

### Post by ubunterooster on 2010-07-22
See: [SIZE=1] [mount windows/samba shares with CIFS + unicode]("http://www.ubuntuforums.org/showthread.php?t=288534")[/SIZE]

---

### Post by natex on 2010-07-22
FTP server is very simple to set up. There is a good guide at [https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html)

If you plan to upload files via FTP from *outside your network*, make sure that your firewall won't be blocking port 21 (or whichever port you choose).

---

### Post by ubunterooster on 2010-07-22
> **natex said:**
> FTP server is very simple to set up. There is a good guide at [https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html)

If you plan to upload files via FTP from *outside your network*, make sure that your firewall won't be blocking port 21 (or whichever port you choose).
I find [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588) simpler, but take your pick

---

### Post by ash369 on 2010-07-23
Thanks for the links. I used natex's guide, i have installed the ftp server and its working. But how do i make a new user so i can login?

---

### Post by ubunterooster on 2010-07-23
Replace **userftp** with whatever you want [quote=Dmizer]Create a user named **userftp** which will be used only for ftp access. This user don't need a valid shell (more secure) therefore select /bin/false shell for **userftp** and /home/FTP-shared as home directory (property button in user and group window).
To make this section clearer, i give you the equivalent command line to  create the user,  but it would be better to use the GUI (System >  Administration > User & Group) to create the user since users  here often got problems with the user creation and the password (530  error) with the command line, so i really advice to use the GUI :      ```

     sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false
sudo passwd userftp 
``` In FTP-shared directory create a **download** and an **upload** directory :      ```

     cd /home/FTP-shared/
sudo mkdir download
sudo mkdir upload 
```Now we have to set the good permissions for these directories :     ```

     cd /home
sudo chmod 755 FTP-shared
cd FTP-shared
sudo chmod 755 download
sudo chmod 777 upload
```[/quote]

---

### Post by ash369 on 2010-07-25
Thanks for that, got it working now.

---

