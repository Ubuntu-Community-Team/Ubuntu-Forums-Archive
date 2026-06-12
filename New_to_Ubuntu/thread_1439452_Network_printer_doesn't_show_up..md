---
title: "Network printer doesn't show up."
date: 2010-03-26
forum: New to Ubuntu
---

### Post by Silvertones on 2010-03-26
I know this is a hot topic but didn't quite find the answer. Using Karmic 9.1 all up to date. My HP printer is attached to my Ubuntu machine. I have a wireless adhoc network to my Windows XP machine via Samba.It works flawlessly. I did the add printer in windows and let it search and it was fine. One day I went to print and it wouldn't. I had to do the add printer again. Now I can't even do that.If I go to "my network places I see "my files" on Ubuntu and all printers and faxes. Double click on my files and I can see my files on Ubuntu. Double click on the "printers and faxes and it goes to Ubuntu but the page is blank. The printer is not showing up. That's what happens now if I try to add a printer. It goes as far as dell-ubuntu but no printers show up.
If there's something I need to do please be detailed in the explanation.

---

### Post by cogier on 2010-03-26
You don't say which HP printer it is but the best bet with HP is to go **Application>Ubuntu Software Centre** and put **HPLIP** in the search field and install it. Follow the instructions when you run it. 

HPLIP software is written by HP for Linux.

---

### Post by Silvertones on 2010-03-26
HPLIP is installed however I've got to DL the GUI. I typed HPLIP into the terminal but it said command not found.

---

### Post by philinux on 2010-03-26
```
sudo apt-get install hplip-gui
```

Or just type

apt:hplip-gui

in the address bar of firefox.

---

### Post by Silvertones on 2010-03-26
It's listed in synaptic however I need towait a bit until I'm ready to take a break. With dial up you can't DL and surf very well.

---

### Post by Silvertones on 2010-03-27
OK I'm not getting much here. I think a lot of folks are having this issue. I've got more data that may help. As I said I have Samba shares happening. The first thing I do once my computers are up and running each day is to make sure my network is working and that I can share files. Never an issue. Next I try the printer and it's a no go. I discovered the if I go into terminal and restart Samba the printer will now work.
```
sudo /etc/init.d/samba start
```
Any thoughts?

---

### Post by Silvertones on 2010-03-28
Well this works consistently. It's kind of queer though don't you think?
I still try to run the hp tool box program and have it search and it says no devices detected when in fact I have a functioning printer hooked up to the parrellel printer port.

---

### Post by Silvertones on 2010-03-31
I solved the issue. I re-installed the printer with the HPLIP  Toolbox. I also discovered that once the network is established each day even though files will share immediatly it takes about 5 minutes before CUPS makes connection.

---

