---
title: "Best Practices regarding setting up Network Printer"
date: 2014-05-24
forum: Networking &amp; Wireless
---

### Post by Caleb012 on 2014-05-24
Are there any "Best Practices" when it comes to setting up a network printer? I have a desktop running Windows but would like to set up printing on two laptops which I installed Ubuntu 14.04. Thank you very much for any assistance!

---

### Post by deadflowr on 2014-05-25
Magic¿
Jokes aside, though, we would need a little more about the setup.

What's the printer?

And will it be running through a machine(connected to a PC) or as a stand-alone printer(connected only to the local network)?

---

### Post by Caleb012 on 2014-05-25
The printer is a Canon MG2220 Pixma. I am running a Windows XP Desktop connected to the printer. Thanks for your help. I sure could use some "Magic" as Linux is very challenging to novices!

---

### Post by SeijiSensei on 2014-05-25
You must first share the printer in Windows to connect to it from Linux.  

I suggest opening a browser and pointing it at [http://localhost:631/](http://localhost:631/), which will take you to the "CUPS" ("Common Unix Printing System") setup page.  Click the "Add Printers and Classes" entry, then Add Printer. Enter your own username and password when prompted.

Choose the "Windows Printer via Samba" option.  In the box that follows enter "smb://ip.of.your.winxp/printer_share".  Replace "ip.of.your.winxp" with the XP computer's IP address, and "printer_share" with the name of the printer you shared from Windows.  Choose the correct printer driver when prompted.

---

### Post by pdc on 2014-05-25
Canon supply printer drivers for your MG2200 series device; from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100466201.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100466201.html)

you would download [COLOR="#008000"]cnijfilter-mg2200series-3.80-1-deb.tar.gz[/COLOR]

If you plan to install, please come back for commands as to how to do this

---

### Post by Caleb012 on 2014-05-25
Thank you very much for your help in this matter. What password ansd username would I enter when using the "CUPS" System? Once again....thanks for helping others with your knowledge and ability! I enjoy using Linux.........Ubuntu 14.04

---

### Post by SeijiSensei on 2014-05-26
When CUPS prompts for a username and password, use your own, just as if you were logging into Ubuntu.

If you've used the "sudo" command to run programs with administrative ("root") privileges, you're doing the same thing here.  You'll be granted admin privileges so you can install the printer.

---

### Post by pdc on 2014-05-26
SeijiSensei advises you to use your username; and your password; he has many more posts than me

my experience of CUPS on our computer was to enter [COLOR="#0000FF"]root[/COLOR] as the username and our sudo password as the password; so out of interest, see what works for you

---

### Post by Caleb012 on 2014-05-26
Thank you very much for your kindness..........I will give it a try!

---

### Post by Caleb012 on 2014-05-26
Regarding the CUPS username and password......I was unable to enter.........root or Root did not work nor did my username..........thank you very much!

---

### Post by Caleb012 on 2014-05-26
Thank you very much  for your help with this matter! With your help I was able to set up my printer. Thank you for using your knowledge to help others with their Ubuntu questions. Your efforts are greatly appreciated!

---

### Post by SeijiSensei on 2014-05-26
> **pdc said:**
> my experience of CUPS on our computer was to enter [COLOR="#0000FF"]root[/COLOR] as the username and our sudo password as the password; so out of interest, see what works for you
That works on RedHat-flavored systems where root has an actual password.  Ubuntu doesn't assign root a password and uses the sudo mechanism instead.  The user initially created during installation (the one with uid=1000) is granted sudo privileges.

Post count is no guarantee of accuracy, by the way.  I've posted some inaccurate messages in my time here, though I think the proportion is still pretty low!

---

### Post by pdc on 2014-05-26
Caleb: I am not sure what you are aiming to do in CUPS:

have a read at this

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by Caleb012 on 2014-09-17
What are the commands for using the Canon Driver ?

---

### Post by pdc on 2014-09-17
so I am assuming you mean the Canon MG2200 series printer you mentioned on May 25th;

go here: [http://support-asia.canon-asia.com/contents/ASIA/EN/0100466201.html?r=s&q=](http://support-asia.canon-asia.com/contents/ASIA/EN/0100466201.html?r=s&q=) and click to **Download** and **SAVE** what is [COLOR="#008000"]cnijfilter-mg2200series-3.80-1-deb.tar.gz[/COLOR]

_________________

this is the 3.8 version and needs [COLOR="#0000FF"]libtiff4[/COLOR] which ubuntu has stopped supplying; (I understand); 

so get [COLOR="#0000FF"]libtiff4[/COLOR] from the debian repository here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and go down the list about 14 or 18 for the 64bit or 32bit version; according to what you are running;

__________________

to install the Canon drivers, open a terminal; and paste the commands below; **line by line**; and hit** ENTER** after each paste ..............use your mouse and top line of the terminal; 

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mg2200series-3.80-1-deb.tar.gz
cd cnijfilter-mg2200series-3.80-1-deb
./install.sh[/COLOR]

and the install script will run; and ask you for your sudo password

that install the MG2200 series printer driver

________________-

Canon supply ScanGearMP for the scanner if you want to install that;

---

### Post by Caleb012 on 2014-09-18
Thank you very much for your assistance! It is greatly appreciated!

---

### Post by pdc on 2014-09-18
pleased to help: can I assume the Canon MG2220 now prints well for you?

---

### Post by Caleb012 on 2014-09-19
First of all, Thank you very much to all forum members for all the help I have received on Ubuntu forums. I am amazed at the generosity of the members here.........so willing to share their knowledge and help even the most new, inexperienced Ubuntu user. I am thrilled to be part of such a group!


Now....back to the ranch. I currently am unable to print. Background......I am currently running a desktop with Win 7. The Dell Vostro 1500 running Ubuntu 14.04 is my laptop. I was able to print but since that time I had to replace the motherboard. I have the printer showing in the printer window (Canon MG2220) but when trying to print a test page....I get the following error...Unable to connect to the CIFS host......I appreciate any advice.......

---

