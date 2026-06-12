---
title: "help: windows permisson file over network"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by Dsreaper on 2008-10-10
i have two laptops...one i am running ubuntu 8.04 on and windows vista on the other, the screen broke on the vista laptop and i am currently in the market for another one but i have files on it that i want to get off and copy but obviously i cant see anything...both computers are connected over a network and i can see and access most but there are some files like the my documents folder i cant get into becuase i dont have permission...is there some kind of command or something i can do to change the permissions and pull the files over to ubuntu?

---

### Post by sokopok on 2008-10-10
Why don't you use your ubuntu cd to boot the Windows laptop then file permissions won't be an issue anymore. Or you could connect an external monitor and take it from there...

---

### Post by patrickballeux on 2008-10-10
In nautilus, you can access your shared drive with this URL:

smb://administrator:PASSWORD@192.168.1.XXX/C$

With the samba protocol, you can pass the username/password before the URL.  If you cannot access the C$ drive, at least get to your shared folder.  

Also, is "Terminal Service" activated on this laptop, cause you could simply access the remote destkop and do your stuff from Ubuntu...

Good luck!

---

### Post by Dsreaper on 2008-10-10
> **patrickballeux said:**
> In nautilus, you can access your shared drive with this URL:

smb://administrator:PASSWORD@192.168.1.XXX/C$

With the samba protocol, you can pass the username/password before the URL.  If you cannot access the C$ drive, at least get to your shared folder.  

Also, is "Terminal Service" activated on this laptop, cause you could simply access the remote destkop and do your stuff from Ubuntu...

Good luck!

ty for the replies...i cant seem to get smb://administrator:PASSWORD@192.168.1.XXX/C$ to work and no i cannot remotely connect ive already tried...also the laptop is all types of messed up(dont trip down the stairs while holding your laptop open [-X lol) the whole back of the unit is cracked and i cant connect an external monitor(tried and failed) its amazing it still turns on...idk...im not 100% new to linux and i cant believe you there is no way to change the permissions

---

### Post by patrickballeux on 2008-10-10
Have you tried with other credentials (any local user that there is on this laptop)?

Other thing you could do is to remove the hardisk from that laptop and put it in your Ubuntu laptop.  You should be able at least to boot vista and get your files on a flash disk (or boot with the live CD ubuntu and access the hardisk from there...).

Or maybe boot your Vista laptop (if the cd is working) with a specialized distro that has a bultin openssh server.  Then you could access the local hardrive by mounting manually the driver and accessing it from your Ubuntu laptop (in nautilus): ssh://root@192.168.1.XXX/

Have a look on these distro : [http://www.scriptingbox.com/cfld.php]("http://www.scriptingbox.com/cfld.php")

Another idea would be to put vncserver.exe on a usb stick / cd/ dvd, boot in windows blindly and you could start the vncserver blindly doing: WinKey+R ...  D:\vncserver.exe

Or create an autorun on the cd to start the vncserver automatically when inserting the cd...  If your Vista will let it run automatically...

Here another way by enabling remotly the RDP server:
[URL="http://msgoodies.blogspot.com/2005/02/enable-remote-desktop-connections.html"]http://msgoodies.blogspot.com/2005/02/enable-remote-desktop-connections.html
[/URL]

That's all I could think of...

Good luck!

---

### Post by Dsreaper on 2008-10-10
i wanted to avoid removing the hdd for fear of damaging it...but i really dont think i have a choice...thanks again for your help ill be in touch and let u know how i make out

---

