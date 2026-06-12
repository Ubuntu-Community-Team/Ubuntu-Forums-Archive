---
title: "Samba Authentication fails! How to configure CUPS for Windows Clients?"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by sieg on 2007-02-27
After finally figuring out how to print from ubuntu (see [http://ubuntuforums.org/showthread.php?p=2215688#post2215688](http://ubuntuforums.org/showthread.php?p=2215688#post2215688)) I now want to expose the printer (and some directory shares) to windows clients. I was surprised to find instructions describing the changes to cups but not samba.
 
I thought sharing printers would be a function of samba and cups! How could this be? Well, regardless, I want samba to work anyway! 

(1) I used the ubuntu interface to share some directories and windows can see it but it prompts for a username and password. I put in the correct username and password but samba won’t swallow it. What is the problem here? I want to use windows explorer to enumerate the directory and printer shares on a remote node and this is not working.

(2) I tried to use [http://127.0.0.1:901](http://127.0.0.1:901) to configure some samba username/passwords using SWAT but it is not up. Why is not SWAT running? How do I start it? 

(3) Why does not the ubuntu GUI for sharing directories correctly configure the smb.conf file so it uses the correct usernames and passwords? 

(4) Can anyone recommend a good URL that describes how to configure CUPS so I can share this printer? I need to know if sharing a printer is a function of CUPS, samba or both. I tried [http://occy.net/printing](http://occy.net/printing) but that did not work.
 

Thanks,
Siegfried

---

### Post by jethro10 on 2007-02-27
You dont need samba to print to a linux printer from windows, you can use "internet printing" which is built into windows for 2000 onwards.

I'm not at an ubuntu box now, but basically in linux printers GUI, there is a sharing menu option or similar. It will say opening up port 631 when you select it anyway. Make sure your firewall has this open too.

Lets say your printer is called Deskjet-940C on ubuntu

On windows when setting up,  select a network printer, then select print to internet where you enter a URL

then put in this :-

[http://UbuntuIPaddress:631/printers/Deskjet-940C](http://UbuntuIPaddress:631/printers/Deskjet-940C)

thats it! It ended up being much simpler than I thought it was going to be

J

---

### Post by sieg on 2007-02-27
Can someone kindly tell me how to open up the fire wall for samba and print sharing? It seems to be different on each linux distro.

Thanks,
Siegfried

---

### Post by sieg on 2007-02-27
I tried following the instructions above. How do I tell if I even have a firewall? After doing some google searches it looks like I don't because apparently you have to manually install a firewall and I don't remember doing that.

So why does windows "add printer" command complain when I enter: 

[http://10.169.0.127/printers/Officejet-G85](http://10.169.0.127/printers/Officejet-G85)

?

I can ping 10.169.0.127. I can print locally on 10.169.0.127.

Windows says:  Windows cannot connect to the printer. Either the printer name was not typed correctly or the specified printer has lost connection to the server. For more information type help.

---

### Post by Floppyjoe on 2007-02-27
You need to enter the port number which is typically for cups:631

[http://10.169.0.127:631/printers/Officejet-G85](http://10.169.0.127:631/printers/Officejet-G85)

like so.

---

### Post by sieg on 2007-02-27
Thanks! That worked!

---

### Post by bcmiller on 2007-02-28
This was the main thing that has been keeping Windows on my computer.  I can't wait to get home and give this a try.

I had tried cups and samba, I even bought a print server to take my computer out of the equation and that didnt' work.

Thanks for this thread

---

