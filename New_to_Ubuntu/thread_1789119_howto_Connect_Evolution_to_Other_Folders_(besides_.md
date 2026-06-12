---
title: "howto: Connect Evolution to Other Folders (besides inbox)"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by gypsynuke on 2011-06-23
I recently had a disk fail; I used photo rec and some other tools to extract files with limited success.  One of the files that I was unable to retrieve was my Outlook pst file.  What I'd like to do is retrieve my SENT emails from the Yahoo mail server.  

I have a yahoo mail plus account and I have successfully configured and downloaded all of the messages in the inbox.  My question is how can I retrieve emails that are in other folders?  Specifically, sent and then perhaps extending to other folders.  

This will enable me to search and sort locally rather than over the web.

Thanks in advance for you support.  I also apologize if this topic has been covered elsewhere; my searches yielded countless hits on typical send and receive configuration but nothing regarding connecting evolution to other folders.

Keywords: evolution yahoo email download folders sent

---

### Post by _0R10N on 2011-06-23
Well, take a look at 
```
~/.local/share/evolution/mail/local
```
You'll see a plain text file named Sent. Open it, there are your sent e-mails.

As a matter of fact, in 
```
~/.local/share/evolution/mail/
```

there's the root for your old evolution tree.

---

### Post by gypsynuke on 2011-06-23
Thanks _Or1ion, but I should have been more specific - this is a new installation of Evolution.  I am trying to retrieve the sent folder from mail.yahoo.com (not from a sent folder within Evolution that was used in the past).

I used the native web interface to yahoo to send some large files that occasionally would make MS Outlook hang up.  I don't have access to backups that I made earlier (I'm on an extended road trip) but I know they're in the sent folder on the yahoo mail server.  I've checked for some of them, but I think if I can bulk download the sent folder, then I can sort and select more quickly than using the web interface to yahoo mail.

---

### Post by haqking on 2011-06-23
> **gypsynuke said:**
> Thanks _Or1ion, but I should have been more specific - this is a new installation of Evolution.  I am trying to retrieve the sent folder from mail.yahoo.com (not from a sent folder within Evolution that was used in the past).

I used the native web interface to yahoo to send some large files that occasionally would make MS Outlook hang up.  I don't have access to backups that I made earlier (I'm on an extended road trip) but I know they're in the sent folder on the yahoo mail server.  I've checked for some of them, but I think if I can bulk download the sent folder, then I can sort and select more quickly than using the web interface to yahoo mail.

Are you using IMAP ?

---

### Post by gypsynuke on 2011-06-23
NO, but I'm happy to try this evening.

---

### Post by haqking on 2011-06-23
> **gypsynuke said:**
> NO, but I'm happy to try this evening.

make sure IMAP is enabled in your Yahoo mail settings (i dont personally use Yahoo however so you will need to find it ;-)

make sure your mail and folders are all clean and tidy the way you want them.

then set evolution to connect using IMAP or IMAP+ instead of POP, you might to make sure your Yahoo mail is set to push down everything as a one time event whilst your evolution syncs.

Then remove the setting afterwards.

Also make sure your evolution is set to leave messages on server etc (if its what you want)

IMAP handles folders better in my experience.

i personally use Gmail amongst others, but everything is always upto date including all folders and filters between evolution, webmail and my android phone.

Hopefully IMAP will sort things for you, Evolution can do everything pretty much but sometimes takes some messing about to get it all working nicely ;-)

---

### Post by gypsynuke on 2011-06-27
haqking:

Thanks for the suggestion - it worked exactly as I had hoped.  

The only issue that I noticed is that the newly downloaded folders, including the sent folder from the serve, did not appear anywhere within the evolution display.  This puzzled me because I saw the status messages indicating that the folders to which I subscribed were being downloaded.  After some attempts, I decided to exit evolution and restarted it.  Upon restarting the folders that were downloaded using IMAP+ became visible and I was able to open and read the eamil stored in them.

Thanks again, I sincerely appreciate the guidance.

gn

:popcorn:

---

### Post by haqking on 2011-06-27
> **gypsynuke said:**
> haqking:

Thanks for the suggestion - it worked exactly as I had hoped.  

The only issue that I noticed is that the newly downloaded folders, including the sent folder from the serve, did not appear anywhere within the evolution display.  This puzzled me because I saw the status messages indicating that the folders to which I subscribed were being downloaded.  After some attempts, I decided to exit evolution and restarted it.  Upon restarting the folders that were downloaded using IMAP+ became visible and I was able to open and read the eamil stored in them.

Thanks again, I sincerely appreciate the guidance.

gn

:popcorn:


no problem, you are welcome.  It is what the forums are for ;-)

mark the thread as solved from the thread tools option, this allows others to see it as solved and head right to it for same issued etc.

peace

---

