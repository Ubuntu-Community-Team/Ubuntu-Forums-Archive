---
title: "Networking with Win7"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by AaronJames651 on 2010-10-05
I have an Ubuntu 10.04 laptop and two Win7 desktops in the house. How do I work it up so that I can access files on my Ubuntu box from my Win7 box like I can with the other - my wife's - Win7 box? I'm on a secured Wifi home network

Or for that matter, can I?

I'm not sure how much clearer to put that.

---

### Post by q1_dab on 2010-10-05
> **AaronJames651 said:**
> I have an Ubuntu 10.04 laptop and two Win7 desktops in the house. How do I work it up so that I can access files on my Ubuntu box from my Win7 box like I can with the other - my wife's - Win7 box? I'm on a secured Wifi home network

Or for that matter, can I?

I'm not sure how much clearer to put that.

SSH will do what you require, I'm sure there are some guides/tutorials availible with a little google-fu

---

### Post by gliff159 on 2010-10-05
are you trying to share folder? If so 
System - Administration - Synaptic Package Manager:

Search for system-config-samba and install it. You'll get Samba plus a GUI interface for administering it.

---

### Post by AaronJames651 on 2010-10-05
What I'm looking for, and I'm not sure how to articulate this, is the ability to copy files to and from my Ubuntu laptop the same way I can with my wife's computer.

I installed Samba, but I'm not completely sure what to do with it.

---

### Post by cariboo on 2010-10-05
There is a great resource at [https://help.ubuntu.com]("https://nelp.ubuntu.com").

This [page]("https://help.ubuntu.com/community/Samba/SambaServerGuide") should get you going.

---

### Post by gliff159 on 2010-10-05
> **AaronJames651 said:**
> What I'm looking for, and I'm not sure how to articulate this, is the ability to copy files to and from my Ubuntu laptop the same way I can with my wife's computer.

I installed Samba, but I'm not completely sure what to do with it.

samba allows windows to see drives and files when you set it up use the gui and then type 
```

sudo service smbd restart

```
 
so it will update changes
works like file sharing in wondows

---

### Post by TCHebb on 2010-10-05
Right click on folder you want to share -> Sharing Options. It will ask you to install Samba if you haven't already (sounds like you have) and give you a dialog to configure sharing. After that, your folder should just show up on your windows box under Network.

---

### Post by sandyd on 2010-10-05
> **AaronJames651 said:**
> I have an Ubuntu 10.04 laptop and two Win7 desktops in the house. How do I work it up so that I can access files on my Ubuntu box from my Win7 box like I can with the other - my wife's - Win7 box? I'm on a secured Wifi home network

Or for that matter, can I?

I'm not sure how much clearer to put that.

[http://ubuntuforums.org/showpost.php?p=9924542&postcount=10](http://ubuntuforums.org/showpost.php?p=9924542&postcount=10)

---

### Post by ST3ALTHPSYCH0 on 2010-10-05
Also, if you want to browse your Windows 7 shares, you'll need to uninstall Windows live sign in assistant.

---

