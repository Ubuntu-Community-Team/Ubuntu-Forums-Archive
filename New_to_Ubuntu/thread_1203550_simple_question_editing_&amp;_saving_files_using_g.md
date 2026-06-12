---
title: "simple question: editing &amp; saving files using gftp"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by cosmicappuccino on 2009-07-03
Some searches have failed to reveal to me how to do this, although I'm sure the answer must be very simple.

I am using gftp for the first time, have successfully established a connection, and have opened a php file for editing in Scribes. However, when I save the file in Scribes, no change is made to the file in gftp. What else do I have to do in order for gftp to save the edited file?

Thanks a lot :)

---

### Post by cariboo on 2009-07-03
gFtp is just an ftp program, ftp stands for file transfer protocol. You shouldn't be using it to edit files. The way to use gFtp, is to download the file to your computer, then when finished editing, upload the file.

IF the computer that the fie you are editing has a gui you can use Xforwarding to run Scribus remotely. You have to install openssh-server on the remote computer, it is in the repositories. Once you have ssh installed, open an Applications-->Accessories-->Termian and type:

```
ssh -X user@servername
```

enter your password, then at the prompt type:

```
scribus
```

In the above command servername = the name or ip address of the remote computer.

---

### Post by Michael.Godawski on 2009-07-03
Correct me if I get you wrong.

gftp does not have a live mode, the edited and saved files are not updated automatically in the view window, although they are changed indeed. 

Is it this what you mean ?

edit: cariboo has a quicker mind ;)

---

### Post by cosmicappuccino on 2009-07-03
Thanks for the replies!

Please correct me once and for all if I am wrong, but the following section of the gftp website made me think that it was possible to edit files (through an external editor) via gftp:
[http://gftp.seul.org/readme.html#AEN119](http://gftp.seul.org/readme.html#AEN119)

It makes it sound like there is a way to use an external editor where you can make changes that will be updated in gftp. However, I don't understand all that stuff about forking, so what they've said has not told me much.

Thanks again :)

---

### Post by sdlynx on 2009-07-03
all you need to do is download the file locally, edit it with Scribes, refresh the gftp page (F5 probably), and upload it back up.

---

