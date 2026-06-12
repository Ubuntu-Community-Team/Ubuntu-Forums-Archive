---
title: "how do i change home dir proftp"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by w0296094 on 2010-02-10
hello, i have a proftpd 1.3.1 on a gproftpd server, running on a Kubuntu 8.10. I am trying to change the default home directory from /var/ftp to the Documents folder outside of root. However, every time i try to change to the Documents folder, the home directory changes back to /var/ftp.
I tried to deactivate the server and inputting the information, but it will revert back to the var dir. 
Are there any ideas?

---

### Post by Temposs on 2010-02-10
Did you know that the Ubuntu file browser can act as your ftp program? I've never use gproftp, and probably most people haven't. If you're willing to use the Ubuntu file browser for your ftp transactions, I can tell you how to set it up how you like.

---

### Post by w0296094 on 2010-02-24
i´m listening

---

### Post by Temposs on 2010-02-24
Open a file browser window, like Places->Home Folder. If the address bar isn't showing, click the pencil icon on the top left. Type in the ftp address that you would like to connect to. It should start with **ftp://**

Then press enter, and it should connect and show you the files and folders. To transfer files, you can just open another file browser window and then drag and drop however you'd like. You can bookmark your ftp connections, too, by clicking Bookmarks->Add Bookmark.

This is the way I recommend to access ftp connections. Actually, moreso, I would recommend for you to use sftp(secure ftp), which can be accessed in the same way I describe above, except your addresses will begin with **sftp://**

To set up your server for sftp, you need to install the openssh-server package on your server, through Synaptic Package Manager. Then you set the sshd program to run on startup with the System->Preferences->Startup Programs app. Then do Alt-F2 and type sshd to start the daemon. Then you should be able to connect to the computer through sftp.

---

### Post by w0296094 on 2010-02-25
ok thanks, now i have a problem in that i want to restrict activity of certain users using ftp. SOme i just want to let upload, others i just want to let download, others i just want to let access certain files but not their peers files. Does the browser ftp work that way also?

---

### Post by Temposs on 2010-02-25
So, for that, you just need to manage the file permissions for the files on the server. If you need help with how file permissions work on Ubuntu, take a look at the doc page on it: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

That tutorial is based on using the terminal, but the concepts are the same even if you use a GUI. If you want to use a GUI, you should right-click on the file or directory whose permissions you want to change, select Properties and then Permissions tab. You can change permissions and owner and group settings through that interface. To add users and groups, you should go to System->Administration->Users and Groups on the server and you can make all those changes there.

---

### Post by w0296094 on 2010-02-26
ok i'll definitely take a look at that and post results

---

