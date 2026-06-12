---
title: "Cannot empty trash or delete files from trash"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by bcasanov on 2010-07-17
Hi,

I tried to delete files from the trash at one point and my computer was very busy with another resource-intensive program, and the progress bar that popped up to show how the computer is deleting was stuck on preparing to delete files.  I clicked on the close button to the right to try another time.  Once I closed the other program, I tried again to delete, and I still have a stalled progress bar and a lot of disk activity.  I tried the refresh icon in Nautilus to see if maybe the trash is already emptied, but I get the following message: 

> The folder contents could not be displayed.
Sorry, could not display all the contents of "Trash": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

What could be wrong?  When I logout and log back in, I still have the trash showing the folders and files that I want to delete, but when I click on some of them, they say 0 bytes.

---

### Post by new__buntu on 2010-07-17
My guess is that the files with 0 bytes have been half deleted - there's nothing in them but the machine never got around to realizing that. In order to clear out your trash I would just make a dummy folder on my desktop, drag everything into it, and then via terminal:

$rm -rf dummyFolder

Somebody else on here probably has a better explanation, but that should get rid of the files.

---

### Post by wojox on 2010-07-17
Try a reboot instead of logging in and out.

---

### Post by bumanie on 2010-07-17
If rebooting doesn't fix the issue, > gksudo nautilus in terminal. You should be able to navigate via Places --> Computer --> File System to trash and delete the files. gksudo is the graphical version of sudo, so be careful as what you delete as it will be gone for good. If that doesn't work, go [here]("http://ubuntuguide.net/empty-ubuntu-gnome-trash-in-command-line") and do the command. Again be very sure that you want to get rid of everything in trash before executing the command, because it won't be retrievable once the command has run.

---

### Post by bcasanov on 2010-07-17
Thank you all for your kind suggestions!  With your help, I have fixed the problem at last.

---

