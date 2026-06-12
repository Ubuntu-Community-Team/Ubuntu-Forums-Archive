---
title: "[SOLVED] Printer may not be connected.....help please!!"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by jeder212 on 2008-12-14
Ok, so things were going great with me and Ubuntu.  I got it installed, got my Epson cx5000 (3 in 1) to print, got my box to show up on network, and then even got the 3 in 1 to scan.  Today, I try to print something, and I get "Printer "CX5000" may not be connected"  It shows up in Localhost:631, but thats about it.  It will not print test page or anything.  My guess is that in messing around with it to get the scanner to scan, I did something to kill the printer.  Any ideas?  I'm pretty much a Ubuntu noob, so try to keep any help kinda simple please.

---

### Post by gettinoriginal on 2008-12-15
System > Preferences > Default Printer   what does it say ?? :p

---

### Post by jeder212 on 2008-12-15
> **gettinoriginal said:**
> System > Preferences > Default Printer   what does it say ?? :p

Stylus CX-5000

---

### Post by ubuntu27 on 2008-12-15
Your [Epson Stylus CX5000]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX5000") works fine in GNU/Linux it seems.

I do not have experience in Printer installation over a network.

So, I will what I can... which is to BUMP!! This thread

---

### Post by gettinoriginal on 2008-12-15
System > Admin > Printer > Server,   check your settings in there :p

---

### Post by jeder212 on 2008-12-15
> **gettinoriginal said:**
> System > Admin > Printer > Server,   check your settings in there :p

This printer isn't on the network, but under "Policies", "Enabled" "Accepting Jobs" and "Shared" are checked.  It also says "Not Published, see server settings"

Also, now under System > Admin > Printing  the icon for the printer has some little red line with a heart in it??  Like I said, complete Ubuntu Noob, but I would like to make it my all the time OS.

---

### Post by cpetercarter on 2008-12-15
I assume that you are trying to communicate with the printer over a network, rather than directly with a USB connection.

I found a lot of difficulties in getting my 2 Ubuntu computers to talk to my HP printer until I added the printer and its IP address to System > Administration > Network > Hosts.

---

### Post by jeder212 on 2008-12-15
> **cpetercarter said:**
> I assume that you are trying to communicate with the printer over a network, rather than directly with a USB connection.

I found a lot of difficulties in getting my 2 Ubuntu computers to talk to my HP printer until I added the printer and its IP address to System > Administration > Network > Hosts.

I'm sorry if i was mis-leading, this is directly with USB.  It was working fine, but the scanner was not working.  I made some changes through the terminal (Because of my nooobness, not sure exactly what changes) and now the scanner works just fine, but it will not print.

---

### Post by jeder212 on 2008-12-15
Bump....

---

### Post by fenian on 2008-12-15
First make certain the printer is connected
Next Go to System>Administration>Printing
If the printer is listed right click the Icon and choose delete
Reinstall the printer by clicking new.

If this is successful you may want to [check out this post]("http://ubuntuforums.org/showpost.php?p=4370600&postcount=7") on getting your scanner working.

---

### Post by starcannon on 2008-12-15
+1 to fenian's idea

delete and reinstall the printer.

---

### Post by jeder212 on 2008-12-15
> **starcannon said:**
> +1 to fenian's idea

delete and reinstall the printer.

Tried delete and re-install a couple of times.  I know it's connected, I can re-boot in xp and print fine.  Like I said, it worked fine before I did whatever it was I did to make scanner part of it work.  In my noobness, I just didn't pay attention to what I was doing so I could undo it.  I will try to find the post I used to make scanner work, and try working backwards from there.

---

### Post by jeder212 on 2008-12-16
I seem to have this all working now.  I had followed this [thread]("http://ubuntuforums.org/showthread.php?t=701943&highlight=cx5000+scan") to get my scanner working.  I followed the same thing that Mark_in_Hollywood did in that post.  After I did that was when my scanner worked, and stopped printing.  I just went back and did the following:
gksugo gedit /etc/udev/rules.d/45-libsane.rules
then removed : SYSFS{idVendor}=="04b8",SYSFS{idProduct}=="082b",M ODE="664",GROUP="scanner"

saved and exited, restarted computer, and it seems to all be working fine now, even the scanner.  Thanks for all the help.

---

