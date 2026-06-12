---
title: "Brother HL-2040 Printer Driver"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by csevolution on 2009-07-02
I have a network printer connected via SAMBA on a windows laptop, but when I add it it says Choose Driver, and when I go into Select Printer from database the closest I can get is HL-2060, HL-2040 isn't in the list!!!

Please help.

---

### Post by csevolution on 2009-07-02
I found this [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html) but I'm not sure what to do there.[]("http://solutions.brother.com/linux/en_us/index.html")

---

### Post by csevolution on 2009-07-02
This might be more relevant:
[http://solutions.brother.com/linux/en_us/download_prn.html#HL-2040](http://solutions.brother.com/linux/en_us/download_prn.html#HL-2040)

---

### Post by synapsys on 2009-07-02
So.... I'm guessing you solved your own problem then?

Nice picture by the way...

Nice but not necessary...

---

### Post by csevolution on 2009-07-02
Not quite, I don't know what to do on that page
[http://solutions.brother.com/linux/en_us/download_prn.html#HL-2040]("http://http//solutions.brother.com/linux/en_us/download_prn.html#HL-2040")

---

### Post by csevolution on 2009-07-02
Do I install the LPR driver or the cupswrapper driver?

---

### Post by starcraft.man on 2009-07-02
I've a 4040CN pretty much same thing. I assume you weren't sure how to install in Linux.

1) Download the lpr and cups driver from the last link. Make sure their in home directory.

2) open a terminal (applications > Accessories > terminal) then type in the following. Each entry in the code tags should be typed and then push enter.

3)```
sudo dpkg -i --force-all --force-architecture brhl2040lpr-2.0.1-1.i386.deb

```
4 )```
sudo dpkg -i --force-all --force-architecture cupswrapperHL2040-2.0.1-2.i386
```

5) ```
sudo aa-complain cupsd
```

After that, their installed and will run properly. The printer can be found in the System > Admin > printing menu.

However, needs the IP address so open a browser (firefox) and paste into the url localhost:631/printers/ . Once there, go to the administration tab and modify the printer, go through the screens most self explanatory. Eventually you get to the connection screen, use the appsocket type and just add the IP at the end. Should work flawlessly.

And if you didn't need the tutorial, well, it's there in case I need to help another networking brother person.

Edit: You need both the lpr and cupswrapper cs. You do the above, shall work without much trouble.

---

### Post by csevolution on 2009-07-02
user@Ubuntu:~$ sudo dpkg -i --force-all --force-architecture cupswrapperHL2040-2.0.1-2.i386.deb 
Selecting previously deselected package cupswrapperhl2040.
(Reading database ... 129055 files and directories currently installed.)
Unpacking cupswrapperhl2040 (from cupswrapperHL2040-2.0.1-2.i386.deb) ...
Setting up cupswrapperhl2040 (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperHL2040-2.0.1: 64: cannot create /usr/share/cups/model/HL2040.ppd: Directory nonexistent
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
cp: cannot stat `/usr/share/cups/model/HL2040.ppd': No such file or directory
dpkg: error processing cupswrapperhl2040 (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupswrapperhl2040
user@Ubuntu:~$ lpadmin: No such file or directory

Help!

---

### Post by csevolution on 2009-07-02
The lpr one installed, though

---

### Post by csevolution on 2009-07-02
I managed to get it working after reading a bit on the Brother site, thanks people.

---

### Post by synapsys on 2009-07-02
Try

```
cd /usr/share/cups
sudo mkdir model
```
Then try installing the cupswrapper again.

---

### Post by csevolution on 2009-07-02
Yes, I did that. :)

---

### Post by synapsys on 2009-07-02
Have you tried without all the bs?

```
 sudo dpkg -i cupswrapperHL2040-2.0.1-2.i386.deb 
```

---

### Post by csevolution on 2009-07-02
It's working now, thanks synapsys.

---

### Post by SlappyPappy on 2009-09-27
Requirement
    1. "sudo aa-complain cupsd" command is required before the installation.
    2. "sudo mkdir /usr/share/cups/model" command (as it is) is required before the installation.

Do this gibberish first and then the rest is easy peasy.

BTW the printing is really sharp and clean. Man, I remember some of the problems you had in the early days of Linux. It's getting so easy to setup printers now, it's nuts.

Rock on with your bad Brother printing self. :guitar::guitar::guitar::guitar::guitar:

---

