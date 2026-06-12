---
title: "Connect to other computers"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by Hydrohs on 2008-11-29
On Windows it's easy to network multiple computers, as long as they're all in the same work group. But I'm not sure how to do this in Ubuntu, I need to be able to so I can access my printer, which is connected to my laptop downstairs. Can someone tell me what I need to do?

I do have wireless configured for Ubuntu, and I'm using Intrepid Ibex.

---

### Post by cmnorton on 2008-11-29
You do this in Network Manager (if you have that running).

Else, you make the change in /etc/hosts

---

### Post by cariboo on 2008-11-29
You're not very clear on your setup, is the printer connected to a windows computer or one running Ubuntu? If the printer is connected to a windows computer and you have sharing setup, all you have to do is go to System-->Administration-->Printing and select New-->Windows Printer via SAMBA. CLick the browse button and select your printer then click forward and follow the prompts.

Ubuntu defaults to WORKGROUP for the work group name. There two ways to change the work group name.

Method 1: Install samba, then edit /etc/samba/smb.conf to reflect your workgroup name:

```
gksu gedit /etc/samba/smb.conf
```

Will open the file for editing. Change the workgroup to your's then save the file and restart samba. To restart samba, in a terminal type:

```
sudo /etc/init.d/samba restart
```

Method 2: Press Alt-F2 and type:

```
gconf-editor
```

then select system-->smb then right-click on workgroup and select New Key, then add you workgroup name and exit. You will have to log out then back in a again for the changes to take effect

Jim

---

### Post by Hydrohs on 2008-11-30
Yes, my other computer is running Windows. Now I got Samba installed and I can see my printer, but I can't complete the set up because it insists on needing drivers, there are no drivers on my CD and when I search online is knows my printer but no drivers are on the list.

My printer is an HP PSC 1100. Any idea what I do to get these PDD drivers or something?

---

### Post by Nikmaster0 on 2008-11-30
is there an exe file on the cd, if so, you could run cabextract and extract the driver files from the exe.

---

### Post by Hydrohs on 2008-12-01
I was able to get drivers using Samba, turns out I just ahd to pick a different option. Although now I'm having a weird problem, I have the printer all set up, but I can't print to it. It know it's there, it's set as my default printer, when I print the print icon comes up and everything, but it doesn't print O_o

Is this some problem with my printer? Or Ubuntu?

---

### Post by spcwingo on 2008-12-01
Try logging on to the windows computer hosting the printer.  If it's running XP go to control panel and open up printers and faxes, right click the shared printer, choose properties, choose the ports tab, and untick enable bidirectional suport.  If that alone doesn't work try installing smbfs to the Ubuntu computer.  If the hosting computer is running Vista...I don't know how to disable bidirectional support.  Vista is the reason I'm using Ubuntu.:)

---

