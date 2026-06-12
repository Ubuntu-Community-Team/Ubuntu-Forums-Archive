---
title: "Evolution stopped working"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by kenmac2 on 2010-10-14
Hi folks,
Today the mains power went of for several hours.
Upon resumption I found that my mail program (Evolution) no longer connects.
When opened, all the command buttons are "greyed" out except the "NEW' one.
All the mail folders are OK and I can compose new mail but cannot send it, and of course I can't receive mail.
The PC is a dual boot running Windows XP Pro and Ubuntu 9.04.
The internet connections are OK when running Windows and also using Firefox in Ubuntu.
The connection is via a an ethernet card to a broadband modem.
Something has happened to the Evolution configuration.
I know nothing about how Evolution/Ubuntu handle mail accounts.
Can anyone suggest what my next move should  be?

kenmac2

---

### Post by El Zoido on 2010-10-14
You can try deleting the Evolution config files.
Open your home directory and set Nautilus to show hidden files.

Then look for the ".evolution" folder and make a backup of it (either move it or compress it).
When you have done so, delete it. When restarting Evolution you have to enter all the account info again, but hopefully it is working.

If anything goes wrong you can still restore the backup.

---

### Post by kenmac2 on 2010-10-14
I renamed the .evolution folder then opened the program.
It re-created the .evolution folder, but there was no initialising activity to enable re-entering the connection details.
I assumed that there would be a requirement to input required setup data, but it didn't happen, just made the new folder.
Maybe the program has been corrupted in some way - I may have to remove it and re-install.

kenmac2

---

### Post by kenmac2 on 2010-10-15
I gave up on Evolution and installed Thunderbird.
It was easy to set up and I now have a working mail connection.
I left Evolution installed because I wasn't sure of uninstalling without affecting the system.

kenmac2

---

### Post by clydesdalefan on 2010-12-02
I have noticed this behavior with Evolution mail also.  It seems anytime Evolution encounters an error or unexpected behavior the program shifts to "work offline".
 
I had this problem during mailbox setup.  I had an incomplete pop3 name and didn't know it right away.  Evolution mail attempted to connect, then failed.  After that, even if I closed the application and restarted it, corrected my pop settings... no connection, and buttons greyed out.  However, I read a 2007 post on this site about mail migration, and it seems that this behavior is expected in Evolution mail.
 
So, the solution is a bit simplistic, but works well.  Go to File --> Work OnLine  
(CTRL-W)
 
All your grey buttons will return and Evolution mail will connect again.
 
Erik

---

