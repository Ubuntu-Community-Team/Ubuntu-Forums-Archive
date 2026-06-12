---
title: "Evolution, deleting mail as it retrieves it from the server"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by laidback on 2011-08-17
What is happening, when I press Send/Receive Evolution fetches the mail and then deletes it without giving me a chance to see it or read it AND I cannot find the deleted items either. I have another user on the same PC and that one is working fine. This is the first problem with Evolution in years of use.

The only thing I did yesterday which was different was to Expunge the Deleted Items box.

Any help would be most welcome. 

Ubuntu 9.04 (out of date I Know) Evolution 2.26.1

Update: Can see emails in ~/.evolution/mail/local/Inbox file, tricky to read but they are at least arriving. I've also taken off the Delete from Server option in preferences so I can read them via the web.

Update2: It appears that the emails just aren't being displayed in the Inbox, I seem to be able to send and receive but not view! I've checked the settings etc and can't see anything obvious that's wrong.

---

### Post by Azdour on 2011-08-17
Hi,

Only a wild stab in the dark but could the Evolution index files be the cause of your problem, see:

[http://ubuntuforums.org/showthread.php?t=152980](http://ubuntuforums.org/showthread.php?t=152980)

---

### Post by laidback on 2011-08-17
Wow that's certainly got some things showing up again. I'll test it now.

Many many thanks

There are 2 files, Index.ibex.index.data and Index.ibex.index, I renamed both, evolution recreated them.

---

### Post by laidback on 2011-08-17
Seems as though I may have 2 problems, recreating the index files has helped but I've also discovered that the lost emails were ending up in Junk (and I thought I'd looked in there before) so I've turned off the Junk filter in Preferences, now my Inbox gets populated as normal. But I don't understand what's happened as my other user still has Junk set the way I'd expect it to be and that system is working just fine.

Still don't feel that I've got to the bottom of it all just yet.

---

### Post by Azdour on 2011-08-18
Hi,

I've seen others with the same issue but I have never seen a solution. It sounds as if the configuration of the junk mechanism in evolution has gone haywire a bit like your index files - since I think these are stored locally to that user that's why you are seeing no problems with the other user (i'm guessing it's a separate account on your computer?). Sorry that I cannot be of more help.

---

### Post by laidback on 2011-08-18
Yes the other user has another account and login.
Don't be sorry, you've put me on the track to a solution.
Currently it's working OK with the Junk filter turned off and indexes rebuilt.

Again many thanks, I'm always sure that I will find a solution via the forum.

Kindest Regards

Laidback

---

