---
title: "I can't see my shared Windows Vista folders or printer in Ubuntu 8.04"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by hurtstotalktoyou on 2008-05-08
Hi, all.

I have an ethernet crossover cable connecting my Ubuntu and Vista PCs.  I've been able to share the internet connection, and my Vista PC can access files on Ubuntu.  However, Ubuntu can't see anything in Vista.

When I go to Places > Network I can see the Vista PC host name.  But when I double-click on it to explore the shared folders and printer, it acts like there are no shared folders/printers to browse.

Any help would be much appreciated.

Thanks in advance!
--Ben

---

### Post by superprash2003 on 2008-05-08
go to places->computer and in location .. type smb://(ip of windows machine)

---

### Post by desktopj on 2008-05-08
> **hurtstotalktoyou said:**
> Hi, all.

I have an ethernet crossover cable connecting my Ubuntu and Vista PCs.  I've been able to share the internet connection, and my Vista PC can access files on Ubuntu.  However, Ubuntu can't see anything in Vista.

When I go to Places > Network I can see the Vista PC host name.  But when I double-click on it to explore the shared folders and printer, it acts like there are no shared folders/printers to browse.

Any help would be much appreciated.

Thanks in advance!
--Ben


Ben,

I have had problems connecting xp computers to vista. The Vista ones never share well with others (remind you of a particular company?). That said, try the link below to help setup the Vista side. I really don't think it is a problem with Ubuntu. One thing is you have to setup to the same Workgroup in each computer before you can even think of sharing on Vista.

[http://technet.microsoft.com/en-us/library/bb727037.aspx]("http://technet.microsoft.com/en-us/library/bb727037.aspx")


Jeff

---

### Post by hurtstotalktoyou on 2008-05-08
> **superprash2003 said:**
> go to places->computer and in location .. type smb://(ip of windows machine)

I'll be glad to try that, but how do I determine the IP address of my Vista PC?

---

### Post by superprash2003 on 2008-05-08
i think it would work for machine name also .. but if you want to find out the ip.. go to the vista pc and type ipconfig and you should see the ip there.. if you are not sure post the output here

---

### Post by M3D on 2008-05-10
> **hurtstotalktoyou said:**
> Hi, all.

I have an ethernet crossover cable connecting my Ubuntu and Vista PCs.  I've been able to share the internet connection, and my Vista PC can access files on Ubuntu.  However, Ubuntu can't see anything in Vista.

When I go to Places > Network I can see the Vista PC host name.  But when I double-click on it to explore the shared folders and printer, it acts like there are no shared folders/printers to browse.

Any help would be much appreciated.

Thanks in advance!
--Ben
I have the same problem. Worked fine with 7.10. Now with 8.04 cannot see Vista shares.

My workaround: I go to places/network/windows_network/"my_machine_name"/ and the type the shared drive like C$ or U$ in my case.

Example: places/network/windows_network/"my_machine_name"/U$

Hope it helps till someone finds a better solution.

---

### Post by hurtstotalktoyou on 2008-05-13
> **M3D said:**
> I have the same problem. Worked fine with 7.10. Now with 8.04 cannot see Vista shares.

My workaround: I go to places/network/windows_network/"my_machine_name"/ and the type the shared drive like C$ or U$ in my case.

Example: places/network/windows_network/"my_machine_name"/U$

Hope it helps till someone finds a better solution.

Thanks for the idea, but it doesn't work, I'm sorry to say.  "places.../U$" isn't found.  If I try "smb://vista_name/C$" it prompts me for a password, but my password does not work, and so it doesn't connect.

---

### Post by hurtstotalktoyou on 2008-05-13
> **superprash2003 said:**
> go to places->computer and in location .. type smb://(ip of windows machine)

Okay, I figured out the Vista IP address and typed it in, as instructed.  Unfortunately, the same thing happens when I click on the Vista network in the places menu:  I get a blank folder.

...

Ubuntu DOES detect my Vista PC.  It just does not read any shared folders *on* the Vista PC.  This is unacceptable, yet nothing I do seems to help.  Initially thought this might be a problem on Vista's end, but my Windows XP partition (on the same box as Ubuntu) detects the shared folders just fine.  So, it must be Ubuntu.

I'm at the mercy of the community support base, here.

---

### Post by tazmannusa on 2008-05-13
I use Kubuntu 8.04 and in remote places/samba shares vista shows up and works ok.
 double check your network and sharing center in control panel of visa, in mine the network is private network. 
Network discovery     on
File sharing          on
public folder sharing on
Printer               off
Password protect      off
Media sharing         off
 
  I allso renamed the workgroup to MSHOME on all pc's 
 
 Question When using cross over cable do you have to manualy configure IP's ?
  Tom

---

### Post by tazmannusa on 2008-05-13
My mistake skipped the part about you sharing internet, Thats where your IP's come from
 assuming the vista pc is the one you are using as host the settings are a bit different. the settings above are for vista client.
 I dual boot Vista and Kubuntu and eather one share files, printer,and internet as host-server
 I haven't had any issues with ubuntu accessing Vista's share's. When I get home this evening I will boot up vista and post the settings that seem to work on mine.
 Tom

---

### Post by hurtstotalktoyou on 2008-05-13
> **tazmannusa said:**
> I use Kubuntu 8.04 and in remote places/samba shares vista shows up and works ok.
 double check your network and sharing center in control panel of visa, in mine the network is private network. 
Network discovery     on
File sharing          on
public folder sharing on
Printer               off
Password protect      off
Media sharing         off

I did all that, but I am sad to report that nothing has changed.
 
>   I allso renamed the workgroup to MSHOME on all pc's 

This I cannot seem to do.  The network name seems stuck on "Unidentified network".  If I try to type in a new name, nothing happens--the characters won't even appear.

> Question When using cross over cable do you have to manualy configure IP's ?

No.  Vista<->XP works just fine without any config.  The internet on Vista-->Ubuntu works fine, too.  Before I upgraded to Vista, XP<->Ubuntu file sharing was automatic.  It's Vista<->Ubuntu file sharing that's giving me a problem.

Thanks for all the help so far.  Here's hoping I can get this thing to work.

---

### Post by hurtstotalktoyou on 2008-05-13
Okay, I may have had a breakthrough.  I can access my files for the moment, after changing some settings in Vista.  I think I can use this to further access my other folders and printer.

Thanks for the help!

---

### Post by tazmannusa on 2008-05-13
Ok mabee this will help 
 Booted up Vista thats configured with file,print, and internet sharing But it turned out I didnt have Ubuntu 8.04 installed anywhere so what I did was boot live cd of it on different pc hard wired to network, when booted I went directly to places/network and it showed windows network,cicked that and it showed MSHOME, clicked that and it showed all pc's on net,clicked P6600 whitch is the Vista pc and it shows all shared files, now when I click to open a shared file Ubuntu ask for username, domain, and password, this seems to be where the trick is because I have vista shares setup with no passwords  in the username box put user and leave the domain and password boxes blank click connect and your in. now this only works on the files you have shared in vista, it shows the drives as C$ D$ ect but you cant mount them, Windows vista will not share the root drive like xp will only files you create on those drives that you share.
 In vista I use the sierra 875 card and share it for the internet connection. In the network and sharing center both network conections are setup as private network
Network discovery     on.
File sharing          on.
Public folder sharing on.  (read only)
Printer sharing       on.
Password protect sharing  off.
Media sharing    off.

 every once in while when I boot vista and no other pc's are on it shuts off network discovery for whatever reason I have to turn it on.
 Anyway hope this helps
 Vista is a little more streamlined for using a router or wireless and not a modem you cant use the setup a network wizard using a modem as internet. XP was a little better in that regard 
 Tom

---

### Post by tazmannusa on 2008-05-13
Yes mine shows unidentified network allso, cant change it but it does work.
 To change workgroup to MSHOME its in the Control panel/ system then in the colum Computer name, domain, and workgroup setting  click on the right side that says change settings.
 Vista and Ubuntu both use workgroup: workgroup by default Xp uses workgroup: MSHOME by default
 Tom

---

