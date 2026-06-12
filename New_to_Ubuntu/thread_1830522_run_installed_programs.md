---
title: "run installed programs"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by eslam elbyaly on 2011-08-21
hi folks , 
i just installed the ftp client program , but i can not find how i can run it , i do not see 
an icon on the desktop to run it , and it is not in the applications tab on the desktop too , 


i do not know how can i run it 
please , help 

regards

---

### Post by lmarmisa on 2011-08-21
What package have you installed?.

Are you referring to the FTP client?. If so, you have to open a terminal and type the command:

```

ftp ftpserver

```

---

### Post by mike555 on 2011-08-21
sometimes logging out and back in helps, if not try typing the programs name in terminal.......

---

### Post by 3rdalbum on 2011-08-21
I'll just point out that Ubuntu already contains the ability to connect to FTP. Go to your home directory and find the File menu at the top of the screen. Come down to Connect To Server...

You can select FTP, put in your FTP server's details, and then a new file browser window will open that's actually the remote FTP folder. You can use it in much the same way as a normal local file browser, including copying files.

As for the program you downloaded, you probably downloaded a command-line program. It doesn't contain a graphical user interface, so it doesn't appear in the menus. Be sure that what you download in the future contains a graphical user interface, or that you don't mind using a terminal-based command-line program.

---

### Post by eslam elbyaly on 2011-08-21
i wanna publish a web site , so i want a ftp software for this mission like in windows , 

if u can guide me , how can i do that on linux , 
can i do it with the file menu manner mentioned ?

regards

---

### Post by the.phantom on 2011-08-21
just go to the "ubuntu software center"
and install "filezilla"
will show up under the "Internet" part of programs

easy to use and set up
been using it for about 11 years now on all my systems and works great, free, and good documentation

i even used it on windows systems back in 2k till i "saw the light" and then used it on ubuntu

---

### Post by eslam elbyaly on 2011-08-22
hi all , hi phantom 
but if u could help me , i designed a web site with ms front page , 
and i wanna publish the pages of the site i designed ,

does filezilla can do that for me , or i need something else ?

notice , i can not publish it with ms front page , forget it .

regards

---

### Post by eslam elbyaly on 2011-08-22
can you guide me please

---

### Post by smurphy_it on 2011-08-22
MS Front page uses "Front Page extensions".  In order to use the frontpage extensions, the web host you are using has to have this ability enabled, otherwise it won't work.

What web host/service are you using ?  Does it state it supports Front Page extension ?  Lastly, some websites that offer Web hosting claim to support "Front Page Extensions" but only with a membership option, free ones don't have that support.

---

### Post by 3rdalbum on 2011-08-22
> **eslam elbyaly said:**
> i wanna publish a web site , so i want a ftp software for this mission like in windows , 

if u can guide me , how can i do that on linux , 
can i do it with the file menu manner mentioned ?

regards

Click on the Home Folder icon in the launcher on the left, or open a file browser window in some other manner.

Go to the top panel and choose File and "Connect To Server..."

Change the Service Type to "FTP (with login)". Type in the server address in the Server field. Type your FTP username in the User Name field. If you also need to specify the Port or the Folder, then put those in as well. Click Connect. You'll be asked for a password, and for how long you want Ubuntu to remember the password. When you've typed the password and made your selection, click Ok and the file browser window will open after a short wait.

Open another file browser window, find the files you want to upload, and drag them to the window you opened for the FTP site.

---

