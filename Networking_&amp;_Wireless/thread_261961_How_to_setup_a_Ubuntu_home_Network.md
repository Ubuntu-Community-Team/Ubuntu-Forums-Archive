---
title: "How to setup a Ubuntu home Network?"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by tuxy on 2006-09-21
Sorry to post this question here. I know there are heaps of postings and webpages on networking but I couldn't find a basic/simple networking procedure through which I can network 2 Ubuntu Dapper pc's.

How many different ways we can network 2 Ubuntu PC's ?
I heard a lot about SAMBA and NFS but what is best way?

My home LAN has 2 Ubuntu Dapper pc's. One of the PC has a HP1210 multifunction printer connected to it. I want the second PC to be able to share the printer through network. 

I have tried through CUPS procedure by typing 127.0.0.1:631 in a web browser in the second pc but it is asking the IPP URI of the printer(which is connected to the first pc) how to get the proper/exact IPP-URI so that I can type in the CUPS setup?

I have tried GNOME's System>Admin>Printing from the second pc so that I can setup network printing it doesn't recognize the printer which is connected to the first pc!!

Any suggestions ?

---

### Post by mssever on 2006-09-21
For file sharing between Linux computers, NFS is definitely the best way to go, as it supports Linux permissions.

For printing using IPP, you want to use the following URL: ```
ipp://<ip address of the computer your printer is attached to>/printers/<printer-name>
```

---

### Post by gwm on 2007-03-18
Hi,
I have two Ubuntu Dapper machines with all the latest updates (6.06.1 I think). I am trying to share a printer. It has been set up on what is to be the server machine, has the name **BJC-250** and is working fine. However, I can't get it to work from the client Ubuntu machine

To network the two boxes, I installed SSH on both. Now I can browse each from the other.

On the box that is to be the print server, I go into **System > Adinistration > Printing**.
There I click on the **Global Settings** menu and make sure that **Detect LAN Printers** is checked. (I don't know if this is supposed to be so. I'm guessing)

On the box that is to print as client I also set **Detect LAN Printers**,
I go into **System>Adinistration>Printing**
Now I double click **New Printer** I get a message saying that Gnome Cups Manager is reading the printer database and after a while that disappears to be replaced by a window headed **Step 1 of 3: Printer Connection**
In this window, I select **Network Printer** and in the option next to it, I lave the option as **Cups Printer (IPP)**.
Now comes the tricky bit. I am asked to enter a URI and the tool tip indicates the format should be as described by **msserver** in his posting. So I consult the box that is to be the printer server and enter the following:

**ipp://192.6.3.16/printers/BJC-250**

and click **Forward**
Now we move to step 2 of 3 and select the manufacturer as **Cannon**, the Model as **BJC 250** (NB there are two models. one is BJC 250, the other is BJC-250. They differ in the drivers offered.) The server is setup to be BJC 250 with the Gutenprint driver, so I make these selections on the client too and click **Forward**.

In step 3 of 3 I Give the printer a name **BJC-250** and click **Apply**.

The setup window disappears and after a few seconds, a new icon for my new printer appears in the **Printers** setup window. Everything seems to be going fine,

I right click on the new icon, select properties and try to print a test page. The job is scheduled and nothing further ever happens. (The server PC is running and the printer is switched on etc.)

**What am I doing wrong? Is it SSH that doesn't support ppi protocols? Should I try the HTTP option suggested in the tool tip? Should I reboot the client?**

I've just tried the HTTP option and the propertis window contains a status message saying:

Ready: Network host '192.6.3.16' is busy: will retry in 30 seconds ...

Yet I can browse the server PC, looking at all it's folders, files and all.

Any help would be much appreciated.
gwm
:confused:

---

### Post by Mr. C. on 2007-03-18
gwm,

Please don't hijack someone's thread.  Post your question in your own thread.

MrC

---

### Post by gwm on 2007-03-19
Sorry,
I figured our problem is identical. Messerver's reply doesn't solve the problem, so I was getting very specific in the hopes of clearing up what was needed.

On a more helpful note, I found this reference in another thread. The problem seems to be fixed in Ubuntu 6.10. In the other thread, they solved their problem by setting up the Ubuntu 6.06 cups.conf file the way that the article says you should set up Ubuntu 5.10. The reference is:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

The thread ithat I took it from is:

[http://www.ubuntuforums.org/showthread.php?t=208187&highlight=lan+printer+setup](http://www.ubuntuforums.org/showthread.php?t=208187&highlight=lan+printer+setup)

Another good thread seems to be:

[http://www.ubuntuforums.org/showthread.php?t=222134&highlight=lan+printer+setup](http://www.ubuntuforums.org/showthread.php?t=222134&highlight=lan+printer+setup)

gwm
:popcorn:

---

### Post by tuxy on 2007-03-19
Did you try networking configuring through [http://127.0.0.1:631](http://127.0.0.1:631) ?

---

### Post by gwm on 2007-03-19
Yes - no go.
From what I have read in the two threads given above, the problem seems to be with the way the file /etc/cups/cupsd.conf is updated by the GUI. Even Ubuntu 6.10 hasn't quite got it right yet.

The first reference given, presents a sample version of the file for the server and then one for the client. Comparing that with what 6.10 does, I feel confident that Feisty will have it right.

In the mean time I'm going to try the manual edit route as described. It seems to be quite straight forward. The CUPS server must know who is allowed to send print jobs, admin requests etc. and the client must know where to look. One simply needs to add the relevant IP addresses in the right places, using the samples as a guide.

gwm
:)

---

### Post by chili555 on 2007-03-19
The system that works for me very well is this:

1. On machine with printer: Set it with a static IP address, so we can find it on the network. Under System -> Administration -> Printing -> Global Settings, check Share Printers. Make note of this computer's name, such as chili-desktop, etc.

2. On all the machines on the network that wish to use the network printer: sudo gedit /etc/hosts to add a line associating the IP address of the printer machine with its name. Here is mine, for example, abbreviated: ```
127.0.0.1       localhost
127.0.1.1       LAPTOP

192.168.1.116   MBR2.linux
``` The name of the machine on my network with the printer is MBR2.linux. Yours will vary, of course.

Open System -> Administration -> Printing and add a new printer. Select Network Printer and CUPS(ipp). Put in the address ipp://MBR2.linux:631/printers/printer (in my case), use the same driver, obviously, that you selected when you installed the printer on the host, save and print a test page.

It is a little unnerving to be sitting at your desktop and the printer starts, seemingly on its own, and prints a recipe.

---

### Post by gwm on 2007-03-19
Hi,
tuxy said he was using Dapper.

I believe that Dapper has only one Global Setting for Detect LAN Printers. There isn't one for Share Printers. Either my Dapper is missing something you've got or you're on a later version.

gwm

---

### Post by chili555 on 2007-03-19
Sorry, I missed Dapper. I apologize. I am a bit Edgy!

If you have it in Dapper, you might try:```
sh /usr/share/cups/enable_sharing 1
```on the machine with the printer.

---

### Post by gwm on 2007-04-04
Hi,
I've finally managed to get back to this problem. I undid all of my changes to /etc/cups/confd.conf and ran the command as suggested above by chili555 on all the PCs in my network. Suddenly they all could see each other's printers and could print to them too. I didn't need to add any new printers via the manager or anything as suggested in chili555's previous post. They simply found each other's printers and made them all available to their applications. In summary, what I did was:

1. Change **/etc/cups/cups.d/browse.conf** to read **Browsing On**

2. Submit the command **sudo sh /usr/share/cups/enable_sharing 1**

Thats all!

Thanks a million chili555
:popcorn:

---

### Post by H.E. Pennypacker on 2007-04-22
> **mssever said:**
> For file sharing between Linux computers, NFS is definitely the best way to go, as it supports Linux permissions.

For printing using IPP, you want to use the following URL: ```
ipp://<ip address of the computer your printer is attached to>/printers/<printer-name>
```

That's exactly what I needed.  Thanks.

---

