---
title: "Really Really Weird Problem"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by twistie on 2006-09-30
Okay, this may not be a local hardware issue. It may be a router issue or even a software issue. So I have just installed 6.06 over an old SUSE install. Anyway, None of my programs can receive data from the internet yet they can send it fine. I can ping google fine and request pages in firefox. But they won't load anything unless (now here comes the weird part!) it is ubuntu.com. Ubuntu.com loads fine! ubuntuforums.org won't load and google won't load. What the hell is up! I would copy and paste all the *route* and ping data from terminal in except I have no way of transferring it to the windows system I am using now. Is there anything I can look for in there which may sugeest the cause of the problem?

Can anyone help?

Thanx in advnace to anyone who can.
:KS

---

### Post by PaganHippie on 2006-09-30
Sounds like some sort of bizarre DNS issue, but that's just a guess.

You say you installed Ubuntu over a previous SUSE install.  Did you preserve the partitions you were using with SUSE or did you reformat the disc(s) and install clean?  If you tried to install right over an existing installation, conceivably something left over from before could be munging your networking setup.  In that case, it might be worth backing up your irreplaceable data and re-installing Ubuntu 'clean' with a complete re-format of your HDD(s).

Just a thought....

---

### Post by mips on 2006-09-30
> **twistie said:**
> I would copy and paste all the *route* and ping data from terminal in except I have no way of transferring it to the windows system I am using now.
:KS

If it is a dual-boot system and you formatted the linux partitions as ext2/3 then you can install the ext2ifs driver in windows to read the linux partitions.

If it is not dual-boot then save the data to a flash key or stiffy.

---

### Post by JGuru on 2006-09-30
If you are able to **ping** & get the data transfer then your Net connection
 is working fine!!
 Is it a standalone PC or one connected to the LAN? This sounds weird indeed
 since you should be able to connect to the Net & browse the Web, unless 
 some firewall or something is blocking!! 
 Try this mate, open the Terminal Window & type:
 
 $ **net lookup [www.yahoo.com](www.yahoo.com)**
  
  This will display the IP address of Yahoo.
  Now open the **Network Settings**, you can open it from another Terminal 
 Window or from the Menu.

 $ **gksu network-admin**

  Here click on the 'Host' tab , now click on the 'Add' button.
  A dialog by name 'Host alias settings' will popup.
  You must enter the IP address & the website address, like this one:

 [b]IP address : 209.73.186.238
  Aliases : [www.yahoo.com](www.yahoo.com)[/b]

 Now click on the 'OK' button. Similarly add the other websites that you
 browse. This should solve your DNS resolving problems.

---

### Post by darth_vader_ca on 2006-09-30
Hi there,

have you tried to statically set your gateway IP, its worth a shot.

cheers

---

