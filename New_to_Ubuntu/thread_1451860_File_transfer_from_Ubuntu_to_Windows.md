---
title: "File transfer from Ubuntu to Windows"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by asharpham on 2010-04-11
I want to enable file transfer from Ubuntu 9.10 to WinXP remotely. I set up SSH according to some instructions I found but I can't work out the method of implementing a transfer using sftp.

I entered sftp into Terminal and got a list of options I just don't understand. For example, it mentions username@host. What on earth does this mean?

Currently I can access the machine remotely through Remote Desktop Viewer as I have its IP address, port number & password. How can I access using ssh? Or can someone point me to a tutorial that's written for newbies?

---

### Post by HermanAB on 2010-04-11
1. Install ssh-server on Ubuntu.  Install Filezilla client on Windows.

2. Install Cygwin with openssh-server on Windows and use Nautilus 'connect to server' on Linux.

3. Install FileZilla Server on Windows and use Nautilus 'connect to server' on Linux.

---

### Post by RudolfMDLT on 2010-04-11
Hi there, 

Your question is a little vague;

Remotely? Via the network, or Via the internet -> from the office?

On the Ubuntu machine make sure you have the open-ssh server installed and configured the correct port.

Then download WinSCP for windows: [http://winscp.net/eng/download.php](http://winscp.net/eng/download.php)

If you now enter the correct information in WinSCP you should be able to access all files on the Ubuntu machine using SCP.

Rudolf

---

### Post by asharpham on 2010-04-11
Hi guys. Thanks for the suggestions. I'll try HermanAB's suggestion first. RudolfMDLT, remote via the internet. And I'm trying to control the Windows machine (host) with the Ubuntu machine, not the other way around. I'll post the result here when I'm done.

---

### Post by daedalas1981 on 2010-04-11
I've been using Samba. By right clicking on a folder and sharing in Ubuntu, I can see the folders I shared on the Network on Windows. There are many forums on Samba and Ubuntu. I prefer it personally.

:guitar:

---

### Post by asharpham on 2010-04-11
I have to admit that after looking at the Cygwin manual, as a newbie I'm quite daunted. Anyway I'll have a look at the options given to me. How do I use Samba? Is there something to download and run in Ubuntu?

---

### Post by daedalas1981 on 2010-04-12
There are two ways to use Samba.

1.
 Try Right Clicking on a Folder. Click Sharing Options. Click Share this Folder. Click Guest Access. If you want to be able to change files in the folder, check the "Allow others to create....", Then click "Create Share".

One of two things will happen. One, it will ask you to install Samba. or Two, It will ask you to change the Samba.conf. If you get the second problem, don't stress. Open Terminal (Applications->Accessories->Terminal) and type "sudo gedit /etc/samba/samba.conf" add this line anywhere on a NEW line "usershare owner only = False" then File, and Save it. Exit Terminal. Your Done, redo the Create Share.

2.
 If you still need to install Samba, use the Synaptic Package Manager. Your source for free programs and other useful stuff. (System->Administration->Synaptic Package Manager) Type your password, then in the search, type "Samba" and press enter. Put a check-mark beside Samba, and press Apply. Wait for it to install, and follow directions. When done, go back to the top where I stated the 1st number :)

Hope this works for you. Also in the Samba.conf you will find many other useful features.

Last but not least, make sure your computers are on the same network/ same router. Things get a little more complicated when you have multiple routers or multiple networks. Like making sure you only have one DNS server, etc etc....

On Windows, click on Start->Networks Then wait for your Ubuntu computer to show up. Click on it, and you should see all your shared folders. Remember that you may only modify,delete,or add files, if you checked that extra option in the create share.

Good Luck!

:guitar:

---

### Post by lswartz on 2010-04-12
> **daedalas1981 said:**
> There are two ways to use Samba.

1.
 Try Right Clicking on a Folder. Click Sharing Options.

While I have done this a lot in Windows I never really needed to share a document from my Ubuntu desktop to a Windows computer. Now I can, Thanks.

I have been using a little program called Dropbox to update & share documents that I am working on. I don't store anything personal-tax forms etc.

---

### Post by Martje_001 on 2010-04-12
I recommend installing Dropbox (see my signature). If you want to continue using ssh, make sure you port forward your router/modem!

---

### Post by asharpham on 2010-04-13
Dropbox isn't really what I'm after. I wish to access my work computer from home using a remote access system.

daedalas1981, I didn't get very far because when I right click a folder, click sharing options and then click "Share this folder", Guest Access is greyed out. Also my samba.conf file is empty.

---

### Post by lswartz on 2010-04-14
> **asharpham said:**
> Dropbox isn't really what I'm after. I wish to access my work computer from home using a remote access system.

daedalas1981, I didn't get very far because when I right click a folder, click sharing options and then click "Share this folder", Guest Access is greyed out. Also my samba.conf file is empty.

Dropbox is nice but it doesn't seem to be exactly what you are asking to do. I'm not really an expert at Ubuntu or even explaining my system, but I'll give it a shot & hope for the best.

I used samba to connect to a shared printer on a windows computer on my LAN. To share folders I had to add a couple of packages & this is what I see installed in Package Manager (9.10 of course) **Samba, Samba-common, Samba-common-bin**. There are about 10 other Samba packages listed in not installed that I can list if you really want to see them. Anyhow, this configuration works for me.

Hopefully this gets you a little closer to your solution.

---

### Post by asharpham on 2010-04-22
I've just discovered TeamViewer for Linux. It works wonderfully well and it's free for non-commercial use. It has answered my file transfer problem fully and is so easy to use.

---

