---
title: "How to create an Ubuntu workgroup"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by evets on 2007-10-23
I need major help in getting my Ubuntu boxes networked with each other.

I already have a windoesn't workgroup, and I can navigate to them, no issues.

Will someone please hold my hand?

Thanks

---

### Post by froy02 on 2007-10-23
If you just want to share and printer, Just right click on any folder you want to share.  If samba or nfts is not installed a dialog box would appear and ask you if you want to install them. Choose samba then click okay.  The samba software would install.  To make sure that it is itstalled open synaptics package manager and see if samba is actually installed.  Right clicked again on the folder you want to share and for share through, choose samba. If you want to be able to read and write uncheck read only. 

On the other computers do the same thing.  If after the setup you change your mind not to share the folder, click sharing and this time choose do not share.
To find out if they are sharing go Menu>Places and click on network.  The computer you're on and the other computers should show up.  

You have to disable firestarter if you installed it. I removed it because when I stop it, it activates itself again after 5 minutes .

---

### Post by evets on 2007-10-23
Thanks, I'll give it a try.

---

### Post by jim_naisium on 2007-10-23
If I understand your question correctly you want to set the Workgroup of your Ubuntu box(es) to the same workgroup that your Windows PCs are on. If this is the case then all you need to do is edit the file /ect/samba/smb.conf/ so that the line:

workgroup =

Is set to the same workgroup that your Windows machines is set on, for instance mine is set to:

workgroup = workgroup1


Hope this helps.

---

### Post by evets on 2007-10-23
> **jim_naisium said:**
> If I understand your question correctly you want to set the Workgroup of your Ubuntu box(es) to the same workgroup that your Windows PCs are on. If this is the case then all you need to do is edit the file /ect/samba/smb.conf/ so that the line:

workgroup =

Is set to the same workgroup that your Windows machines is set on, for instance mine is set to:

workgroup = workgroup1


Hope this helps.

It already is. Now what? LOL


Just to be sure I'm making sense. My Ubuntu boxes (3 of them) can all see and attach to and modify the files on all (4 of them) my windoze boxes.  My wincrap boxes cannot see or attach to the Ubuntu boxes, which isn't a biggie for me anyway, as the winhoser's will be gone in a few months.


The Ubuntu boxes cannot see each other.

---

### Post by evets on 2007-10-23
SOLVED!

Thank you. I was abale to see one of my machines (gutsy), and started fussin' with another (Fiesty) when I got a dialog box asking me to install smb and nfs! ha, what an idiot I am. LOL Now I'm up.

Only a coupla' more hurdles before I send Gates & Co. to the heap. Woot-woot!!!

Thanks for your help.

P.S. How do I mark the title SOLVED?

---

