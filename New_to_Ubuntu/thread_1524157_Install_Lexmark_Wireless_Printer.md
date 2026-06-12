---
title: "Install Lexmark Wireless Printer"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by hoosier1104 on 2010-07-04
I have a Lexmark X6675 wireless printer.  I have already downloaded the driver for it but need to know how to install it.  Any help will be greatly appreciated.

Justin

---

### Post by hoosier1104 on 2010-07-04
Back to the top.  Please advise on this matter.

---

### Post by sgosnell on 2010-07-04
What form is the driver in?  .deb?   *.gz?  It's impossible to say exactly how to install it without more information.  Lexmark is one of the least compatible printers sold, but it might work.

---

### Post by mprice on 2010-07-05
Here is the link for the drivers for your printer, you just have to untar the file then install the .deb file.

[http://support.lexmark.com/index?page=content&productCode=LEXMARK_X6675&actp=PRODUCT&id=DR20523&segment=DOWNLOAD&userlocale=EN_US&locale=en](http://support.lexmark.com/index?page=content&productCode=LEXMARK_X6675&actp=PRODUCT&id=DR20523&segment=DOWNLOAD&userlocale=EN_US&locale=en)

---

### Post by Jakiejake on 2010-07-05
> **hoosier1104 said:**
> Back to the top.  Please advise on this matter.

I assume that's a Bump
Please do not bump posts until they are around 24 Hours Old

---

### Post by Jakiejake on 2010-07-05
Are you accessing it via a cable or wireless?
If wireless is it Bluetooth or Wifi

---

### Post by hoosier1104 on 2010-07-05
> **sgosnell said:**
> What form is the driver in?  .deb?   *.gz?  It's impossible to say exactly how to install it without more information.  Lexmark is one of the least compatible printers sold, but it might work.

It is the .gz that I downloaded from their site.


> **Jakiejake said:**
> Are you accessing it via a cable or wireless?
If wireless is it Bluetooth or Wifi

It is via Wifi.  Sorry for bumping it prematurely.  I have a paper to print off for class that is due tomorrow and really need to get it install.

---

### Post by VraiChevalier on 2010-07-05
I have the same or a very similar Lexmark printer. I believe you will need to attach the printer with a cable (usb) in order to install. The installer will tell you when to plug it in.

---

### Post by sgosnell on 2010-07-05
If you still need instructions, open the .gz file with Archive Manager, by right-clicking on the file in Nautilus and selecting that.  Then extract the files to somewhere in your home directory, where you have proper permissions.  If the extracted file is a .deb, right-click on it and open it with gdebi, the package installer.  Gdebi will install it after you enter your password.  If there is no .deb file, you'll have to compile and install it manually.  If that's the case, let us know, and provide a file list so we can better advise you.

---

### Post by hoosier1104 on 2011-02-12
Well I finally got around to installing the software.  I put in my admin  password, which is the same as my login (I know that is not very safe  but no ever messes with my stuff) and it is telling me that it is  incorrect.

[IMG]http://i567.photobucket.com/albums/ss119/hoosier1104/Screenshot-1.png[/IMG]

[IMG]http://i567.photobucket.com/albums/ss119/hoosier1104/Screenshot-2.png[/IMG]

Is there a way to recover the admin password w/o wiping my machine?

---

### Post by bcamm60 on 2011-03-15
> **hoosier1104 said:**
> Well I finally got around to installing the software.  I put in my admin  password, which is the same as my login (I know that is not very safe  but no ever messes with my stuff) and it is telling me that it is  incorrect.

[IMG]http://i567.photobucket.com/albums/ss119/hoosier1104/Screenshot-1.png[/IMG]

[IMG]http://i567.photobucket.com/albums/ss119/hoosier1104/Screenshot-2.png[/IMG]

Is there a way to recover the admin password w/o wiping my machine?

Hey I was having the same problem. The reason its not recognizing your password as the root password is because Ubuntu does not allow the use of root. To get it to work properly open up the console and run gksudo <filename>  it will then ask u for ur password enter it and it should work alright.

---

