---
title: "Download folder of messages in evolution"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by Magnus101 on 2011-04-07
Is there a way in evolution to download all of the messages in a folder?  Without having to click each message.

thanks

---

### Post by Naggobot on 2011-04-07
Sorry but you lost me there?

Is this what you want

1. Click one message in the default view / message list so that it becomes grayed.
2. Press **** key and keep it pressed
3. Click some other message in the list, the gray area expands and now more messages are selected. 
4. Right clic (i.e. press right mouse button) on top of the messages. A pop up menu will open
5. Select "move to folder" from pop up menu. 
6. From the dialogue box select desired folder or create new. 

Note that these are Evolution folders, not file system folders.

---

### Post by Magnus101 on 2011-04-07
no i mean download for offline viewing.
it seems like only if you click the message it will actually be downloaded.
i want to download a whole folder for offline viewing

---

### Post by ebasa on 2011-04-07
Ummm, maybe click on file and select "Download messages for offline viewing" ??

---

### Post by GWBouge on 2011-04-07
You can right-click the folder (on the left side), goto Properties, and check 'Copy folder content locally for offline operation' ... is that what you're looking for?

---

### Post by Naggobot on 2011-04-14
If your e-mail account is POP3 (I admit I do not know what it means. I suspect that there is also IMAP also)

Edit->Preferences->Mail Accounts (selected as default)

Select the mail account so that it becomes grayed and then select edit. 

Select tab Receiving options and unpick Leave Message on server. 

After this all messages are downloaded automatically and they are not left on server at all. So use this with caution only if you want to automatically remove the messages from server. For example my personal mail provider offers only 10 MB of space on server so I want to download all messages and I want to keep the server empty. If you have unlimited space on mail server and you do not take backups from your e-mails then do not use this.

---

