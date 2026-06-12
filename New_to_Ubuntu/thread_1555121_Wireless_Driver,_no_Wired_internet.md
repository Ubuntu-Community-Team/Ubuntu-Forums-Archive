---
title: "Wireless Driver, no Wired internet"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-08-17
I have a Dell Mini 10v netbook.  Just installed Ubuntu.  Wireless does not work.  I have no access to wired, wireless is my only available internet at the moment.  I downloaded the Driver to transfer to my USB stick, but in order to compile it in Ubuntu I need some program that's not pre-installed.  Can someone please help me?  I would like to be able to get full use out of my netbook...

---

### Post by earthpigg on 2010-08-17
hi,

there is a long thread on this, [here]("http://ubuntuforums.org/showthread.php?t=1390979"). 

post 53 has a list of all the possible solutions.

on my dell mini 9 (almost the exact same hardware as the 10v), [this]("http://ubuntuforums.org/showpost.php?p=9223467&postcount=21") is what worked for me. post 21 in that thread.


in short: its a 10.04 bug. ubuntu supports that hardware with software that is on the install cd/usb, but doesn't seem to know it.

edit: please let us know what worked on your dell mini 10v, so others can benefit.

---

### Post by sandyd on 2010-08-17
> **TriBlox6432 said:**
> I have a Dell Mini 10v netbook.  Just installed Ubuntu.  Wireless does not work.  I have no access to wired, wireless is my only available internet at the moment.  I downloaded the Driver to transfer to my USB stick, but in order to compile it in Ubuntu I need some program that's not pre-installed.  Can someone please help me?  I would like to be able to get full use out of my netbook...
try this
[http://linux.dell.com/files/ubuntu/lucid/iso-images/](http://linux.dell.com/files/ubuntu/lucid/iso-images/)

---

### Post by TriBlox6432 on 2010-08-18
> **earthpigg said:**
> in case anyone using a **Dell Mini 9** comes across this:

i was able to get **wifi working on 10.04 without ever plugging into wired internet after installing from thumb drive**.

1) install ubuntu 10.04 from thumb drive.
2) boot normally.
3) insert the thumb drive you just installed from.
4) open the file manager, go to the thumb drive, and navigate to  pool/restricted/b/bcmwl, and double click on the .deb in there. it will  tell you it needs 3 dependancies - make a mental note of which three.
5) navigate back to pool/main, find those deps and install them.
6) install the .deb in pool/restricted/b/bcmwl
7) reboot

Thanks for that.  But now when I click on the network icon, under wireless networks instead of saying disconnected, it says "device not ready".  Any ideas?

---

### Post by earthpigg on 2010-08-18
> **TriBlox6432 said:**
> Thanks for that.  But now when I click on the network icon, under wireless networks instead of saying disconnected, it says "device not ready".  Any ideas?

I'm afraid not, sorry. I've never had the method I outlined fail, and so have never had to troubleshoot it.

---

### Post by lg5productions on 2010-08-19
I have a method that has worked for me various times. Hope it helps. If you need all the screenshots, just email me at [email]lg5productions@gmail.com[/email]
The document is just at 1.0 MB in PDF format

Here is another thing that works. :)

While you are connected via a wired connection, open your applications option on the left hand side and look for ADD/REMOVE or something relevant to that depending on your version of Ubuntu.

Now select ALL in the left hand column (or again something relevant), and conduct a search for "Windows Wireless Drivers”. 

Place a check next to it and select APPLY OR click the INSTALL option.  Wait until the package states its completed.

Next conduct a search via Google for your wireless card's drivers (My Case a Linksys Wireless Card) and save to your DESKTOP or DOCUMENTS folder. You can use the Windows versions. I recommend XP compliant but of course you can try the Vista or 7 versions. Mine worked with XP drivers since I had and knew it worked with my XP Pro installation on that same laptop before.

Now comes the slightly tricky parts. Look for your download and right click like you would in Windows. Select OPEN WITH ARCHIVE MANAGER and then select the same location for extraction. 

Almost done. Click on SYSTEMS and select ADMINISTRATION then WINDOWS WIRELESS DRIVERS.

Find your extracted files by clicking on INSTALL NEW DRIVER. It will ask for an INF file. It's there, you probably have to drill down some menus.

Your typical wired connection will turn into 4 bars after the install. Click on the bars and find your secured or unsecured connection. Remember to have your password handy for those secured connections. I got mine. :P

Test out your connection after the icon of the two balls/two arrows stops rotating and you are good to go. Enjoy your wireless roaming on your new Ubuntu powered laptop!! 

Regards, 

LG5Productions

---

### Post by TriBlox6432 on 2010-08-19
Erm, thanks.  But if you check the title and original post, you see that I cannot access wired internet.

---

### Post by lg5productions on 2010-08-19
> **TriBlox6432 said:**
> Erm, thanks.  But if you check the title and original post, you see that I cannot access wired internet.

My apologies, I must have read to quickly. I'll have to research. Will see what I can do. ](*,):-#

---

### Post by TriBlox6432 on 2010-08-20
Thanks, and bump.

---

### Post by TriBlox6432 on 2010-08-20
One thing that might be involved in it not working is that there was only one dependancy when I did it.  DKMS.  That was it.  Could you tell me what the others were, and I'll try again?

---

### Post by TriBlox6432 on 2010-08-20
Carlee's iso worked.  Thank you.

---

