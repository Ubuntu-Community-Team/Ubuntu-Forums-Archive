---
title: "Error &quot;mount error: can not change directory into mount target&quot; when directory exists"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by jamespetts on 2008-09-28
I am trying to share a single Thunderbird account (inbox, sent, etc.) seamlessly between four computers. Three of those computers run Ubuntu 8.04, but one of them - the one that I most commonly use - runs Windows XP pro. All of my existing mailbox data is on the XP pro machine. The other three computers are a small backup computer, and computers used by others in the house.

I have previously set Thunderbird to get its inbox file from the Windows machine's hard drive using CIFS/Samba shares in the /mnt directory by changing the settings in Thunderbird itself. However, that technique has not produced the best results, with all messages being marked as unread after I have tried to access them from the Linux machine, and my custom spam filters being reset because it had difficulty finding the subfolders into which I put spam, for some reason.

So, I am trying instead to *mount* my mailbox folder on the Windows machine into the mailbox folder on the Linux machine: I have done that successfully with the users' home directories on the three Linux machines. However, the following fstab line:

```
//study/Blue/Documents\040and\040Settings/James/Application\040Data/Thunderbird/Profiles/fjosvxfm.default/Mail /home/james/.mozilla-thunderbird/sd3k82ko.default/Mail cifs	credentials=/root/.smbcredentials,rw,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

produces the following error:

```
mount error: can not change directory into mount target /home/james/.mozilla-thunderbird/sd3k82ko.default/Mail
```

Oddly, however, I have no problem *manually* changing into the /home/james/.mozilla-thunderbird/sd3k82ko.default/Mail directory, so the error does not make sense. I have tried searching for the text of the error message, but all the results suggest that the error is only generated when the directory specified in the fstab line does not exist, which is not so in my case. Does anyone have any ideas?

(Incidentally, as an aside, I considered at one point switching to Evolution. I tried on my Windows machine the Windows Evolution client, but found it to be very slow, have a poor user interface, and to be quite unstable. When it finally crashed and would not load again without crashing, I went back to Thunderbird, which was a welcome relief. Is that problem confined to the Windows port of Evolution, or is Thunderbird more stable and user-friendly generally? I have a very large mailbox which I had imported from Thunderbird, and Evolution appeared to be having trouble coping with that, although Thunderbird never has a problem with large mailboxes. Any thoughts?)

---

