---
title: "brother mfc6490cw not printing"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by martyg1 on 2011-03-02
hello all and thanks for having me. after running a dual boot on my systems with xp and linux, decided to switch over totally to Ubuntu 10.10. my only problem is the dang brother printer will not work. I have downed both the ltr and cups deb fm the brother site, installed them and cannot get any action from the printer. The brother site instructions drive me nuts and no solution seems to work. I need a step by step install method if one even exists. The printer shows up as the default printer, yet nothing works, no "print test page", nothing out of openoffice, etc.... Is there a step by step for linux dumbies like me that is new to the terminal and download commands?????

---

### Post by mwray on 2011-03-03
> **martyg1 said:**
> hello all and thanks for having me. after running a dual boot on my systems with xp and linux, decided to switch over totally to Ubuntu 10.10. my only problem is the dang brother printer will not work. I have downed both the ltr and cups deb fm the brother site, installed them and cannot get any action from the printer. The brother site instructions drive me nuts and no solution seems to work. I need a step by step install method if one even exists. The printer shows up as the default printer, yet nothing works, no "print test page", nothing out of openoffice, etc.... Is there a step by step for linux dumbies like me that is new to the terminal and download commands?????

Sorry, don't have a step by step, but I suspect your issues have to do with permissions issues on the filters in /usr/lib/cups/filters/br*

try at a terminal:
cd /usr/lib/cups/filter
sudo chmod 555 br*
sudo restart cups

---

### Post by alastairpjb on 2011-03-17
[FONT=Liberation Serif, serif][SIZE=6]UBUNTU 10.10 – Printer Install MFC6490CW[/SIZE][/FONT]
 

 [FONT=Liberation Serif, serif][SIZE=6]_How to Install Brother MFC-6490CW On a 64bit Ubuntu10.10 Computer System_[/SIZE][/FONT]
 

 [COLOR=#355e00][FONT=Liberation Serif, serif][SIZE=2]Full Install Manual – Every step to make it physically print not just most of it, EVERYTHING[/SIZE][/FONT][/COLOR] :o
 

 [COLOR=#000080][FONT=Liberation Serif, serif][SIZE=3]_**STEP 0**_[/SIZE][/FONT][/COLOR]
  

  [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]_USB Installation_ [/SIZE][/FONT][/COLOR] 
  [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Goto &#8594; Step 1[/SIZE][/FONT][/COLOR]
  

  [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]OR[/SIZE][/FONT][/COLOR]
  

 [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]_Network installation_[/SIZE][/FONT][/COLOR]
  [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Install (Brother Printer MFC-6490CW) Wireless on Windows first with printer disc, (Just so installation is exactly the same as mine - I am not sure if this needs to be done or not). then Goto &#8594; Step 1 [/SIZE][/FONT][/COLOR] 
  

  

 **[COLOR=#000080]_[FONT=Liberation Serif, serif][SIZE=3]STEP 1[/SIZE][/FONT]_[/COLOR]**
 Start Ubuntu10.10>open Firefox or another web-browser
 

 [COLOR=#ff0000][FONT=Liberation Serif, serif][SIZE=3][COLOR=#333333]Open Brother MFC-6490CW [/COLOR][COLOR=#333333]_drivers webpage_[/COLOR][COLOR=#333333] from:[/COLOR] [/SIZE][/FONT][/COLOR] 
 

                                              [COLOR=#008000][FONT=Liberation Serif, serif][SIZE=3]http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-6490CW[/SIZE][/FONT][/COLOR]
                

 

 [COLOR=#000080][FONT=Liberation Serif, serif][SIZE=3]_**STEP 2**_[/SIZE][/FONT][/COLOR]
 

 [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Click “LPR driver deb” to download, agree/disagree to licence: (Will not download if you don't agree)[/SIZE][/FONT][/COLOR]
 

                                                   [COLOR=#008000][FONT=Liberation Serif, serif][SIZE=3]LPR             driver deb [/SIZE][/FONT][/COLOR]             
                                            [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]1.1.2-2             1907 KB 2008.Dec.09 [/SIZE][/FONT][/COLOR]             
                

 [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Downloaded File Name:[/SIZE][/FONT][/COLOR]
                                              [COLOR=#008000][FONT=Liberation Serif, serif][SIZE=3]mfc6490cwlpr-1.1.2-2.i386.deb[/SIZE][/FONT][/COLOR]

                [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Put above file on the Desktop[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000080][FONT=Liberation Serif, serif][SIZE=3]_**STEP 3**_[/SIZE][/FONT][/COLOR]
 

  [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Click “cupswrapper driver” to download, agree/disagree to licence: (Will not download if you don't agree)[/SIZE][/FONT][/COLOR]
                                                   [COLOR=#008000][FONT=Liberation Serif, serif][SIZE=3]cupswrapper             driver[/SIZE][/FONT][/COLOR]
                                            [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]deb             1.1.2-2 14 KB 2008.Dec.09[/SIZE][/FONT][/COLOR]
                

 [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Downloaded File Name: [/SIZE][/FONT][/COLOR] 
                                              [COLOR=#008000][FONT=Liberation Serif, serif][SIZE=3]mfc6490cwcupswrapper-1.1.2-2.i386.deb[/SIZE][/FONT][/COLOR]
                
[COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Put above file on the Desktop[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000080][FONT=Liberation Serif, serif][SIZE=3]_**STEP 4**_[/SIZE][/FONT][/COLOR]
 

 [COLOR=#c0c0c0][FONT=Liberation Serif, serif][SIZE=3]Install 32 bit software on 64bit Ubuntu Computer System[/SIZE][/FONT][/COLOR]
 [FONT=Liberation Serif, serif][SIZE=3]Goto -->Applications>Ubuntu SoftwareCentre>Get Sfotware>-'SEARCH FOR' [/SIZE][/FONT] 
                                              [COLOR=#008000][FONT=Liberation Serif, serif][SIZE=3]ia32-libs[/SIZE][/FONT][/COLOR]
                

 

 [COLOR=#000080][FONT=Liberation Serif, serif][SIZE=3]_**STEP 4**_[/SIZE][/FONT][/COLOR]
 
  [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Goto &#8594; Applications>Accessories>Terminal &#8594; Now type the following into the terminal[/SIZE][/FONT][/COLOR]:
                                              [COLOR=#008000][FONT=Liberation Serif, serif][SIZE=3]sudo             aa-complain cupsd[/SIZE][/FONT][/COLOR]
                [COLOR=#cccccc][FONT=Liberation Serif, serif][SIZE=3]Does Something Important (Brother website says its a prerequisite requirement) [/SIZE][/FONT][/COLOR] 
[COLOR=#008000][FONT=Liberation Serif, serif][SIZE=3]sudo             mkdir /usr/share/cups/model[/SIZE][/FONT][/COLOR]
                [COLOR=#cccccc][FONT=Liberation Serif, serif][SIZE=3]Creates a directory /usr/share/cups/model[/SIZE][/FONT][/COLOR]
 

 

 [COLOR=#000080][FONT=Liberation Serif, serif][SIZE=3]_**STEP 5**_[/SIZE][/FONT][/COLOR]
 

  [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]In Terminal type the below text with your computers username, to check what it is you can: [/SIZE][/FONT][/COLOR] 
  [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]GoTo &#8594; System> Administration>Users and Groups[/SIZE][/FONT][/COLOR][COLOR=#008000][FONT=Liberation Serif, serif][SIZE=3]
cd             /home/YOURUSERNAME/Desktop [/SIZE][/FONT][/COLOR]             
                

 [FONT=Liberation Serif, serif][COLOR=Black][SIZE=3]In Terminal type the following commands in.[/SIZE][/COLOR][/FONT]
 

                                 [COLOR=#008000][FONT=Liberation Serif, serif][SIZE=3]sudo             mkdir[/SIZE][/FONT][/COLOR][COLOR=#008000][FONT=Liberation Serif, serif][SIZE=3]/var/spool/lpd[/SIZE][/FONT][/COLOR]
                [COLOR=#c0c0c0][FONT=Liberation Serif, serif][SIZE=3]Creates folder that .deb package fails to do[/SIZE][/FONT][/COLOR]
 

                                              [COLOR=#008000][FONT=Liberation Serif, serif][SIZE=3]sudo             dpkg -i --force-all --force-architecture             mfc6490cwlpr-1.1.2-2.i386.deb[/SIZE][/FONT][/COLOR]
                [COLOR=#c0c0c0][FONT=Liberation Serif, serif][SIZE=3]Installs driver?[/SIZE][/FONT][/COLOR]
 

                                              [COLOR=#008000][FONT=Liberation Serif, serif][SIZE=3]sudo             dpkg -i --force-all --force-architecture             mfc6490cwcupswrapper-1.1.2-2.i386.deb [/SIZE][/FONT][/COLOR]             
                [COLOR=#c0c0c0][FONT=Liberation Serif, serif][SIZE=3]Installs cups wrapper for driver?[/SIZE][/FONT][/COLOR]
 

 [COLOR=#ff0000][FONT=Liberation Serif, serif][SIZE=3]YOUR PRINTER IS NOW INSTALLED TO USB. TO CHANGE THIS TO NETWORK (LAN WIRELESS) FOLLOW FURTHER STEP BELOW:[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000080][FONT=Liberation Serif, serif][SIZE=3]_**STEP 6**_[/SIZE][/FONT][/COLOR]
 

 [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Goto &#8594;[/SIZE][/FONT][/COLOR]
                                              [COLOR=#355e00][FONT=Liberation Serif, serif][SIZE=3]System>Administration>Printing[/SIZE][/FONT][/COLOR]
                

 [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Right click:[/SIZE][/FONT][/COLOR]
                                              [COLOR=#355e00][FONT=Liberation Serif, serif][SIZE=3]MFC6490CW[/SIZE][/FONT][/COLOR]
                

 [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Select:[/SIZE][/FONT][/COLOR]
                                              [COLOR=#355e00][FONT=Liberation Serif, serif][SIZE=3]Properties             [/SIZE][/FONT][/COLOR]             
                

 Click:
                                 [COLOR=#355e00][FONT=Liberation Serif, serif][SIZE=3]Device             URL: &#8594; Change [/SIZE][/FONT][/COLOR]             
                

 [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Click:[/SIZE][/FONT][/COLOR]
                                 [COLOR=#355e00]&#8594; [FONT=Liberation Serif, serif][SIZE=3]Network             printer [/SIZE][/FONT][/COLOR]             
                

 [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Click: (Click twice and it will slowly find two printers with same name laggy) [/SIZE][/FONT][/COLOR] 
                                 [COLOR=#355e00]&#8594; [FONT=Liberation Serif, serif][SIZE=3]Find             Network printer [/SIZE][/FONT][/COLOR]             
                

 [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Click:[/SIZE][/FONT][/COLOR]
                                 [COLOR=#355e00]&#8594;[FONT=Liberation Serif, serif][SIZE=3]Network             printer &#8594; LPD/LPR Host or Printer [/SIZE][/FONT][/COLOR]             
                

 [COLOR=#333333][SIZE=3][FONT=Liberation Serif, serif]Host &#8594; Type printer IP (The two printers you found, one will have the printer ip address at the end of its name.) e.g [/FONT][/SIZE][/COLOR] 
[COLOR=#355e00][FONT=Liberation Serif, serif][SIZE=3]192.168.1.67             [/SIZE][/FONT][/COLOR]             
                                          
                                                               
                                            
            
                [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Click&#8594; [/SIZE][/FONT][/COLOR] 
                                              [COLOR=#355e00][FONT=Liberation Serif, serif][SIZE=3]Probe[/SIZE][/FONT][/COLOR]
                [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=3]Click &#8594; [/SIZE][/FONT][/COLOR] 
                                              [COLOR=#355e00][FONT=Liberation Serif, serif][SIZE=3]Apply[/SIZE][/FONT][/COLOR]
                

 [COLOR=#333333][FONT=Liberation Serif, serif][SIZE=7]Printing Installation complete[/SIZE][/FONT][/COLOR]

---

### Post by Deguerrilla on 2011-04-23
I am attempting to follow these instructions in order to install my brother mfc 6490

Here is what happens:


MYUSERNAME@studio:~$ sudo aa-complain cupsd
[sudo] password for kingston: 
Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.
MYUSERNAME@studio:~$ sudo mkdir /usr/share/cups/model
mkdir: cannot create directory `/usr/share/cups/model': File exists
MYUSERNAME@studio:~$ sudo mkdir/var/spool/lpd
sudo: mkdir/var/spool/lpd: command not found
MYUSERNAME@studio:~$ sudo mkdir/var/spool/lpd


How do i get passed this problem?

---

### Post by roger_1960 on 2011-04-23
Hi

There is a typo in the previous post;
sudo mkdir/var/spool/lpd should be 
> sudo mkdir /var/spool/lpd
(with a space after mkdir)

---

### Post by sdibaja on 2011-08-04
I followed step by step, this was the result:

peter@peter-P170HMxPinguy:~/Desktop$ sudo dpkg -i --force-all --force-architecture mfc6490cwlpr-1.1.2-2.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: error processing mfc6490cwlpr-1.1.2-2.i386.deb (--install):
 mfc6490cwlpr:i386 1.1.2-2 (Multi-Arch: no) is not co-installable with mfc6490cwlpr:all 1.1.2-2 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 mfc6490cwlpr-1.1.2-2.i386.deb
peter@peter-P170HMxPinguy:~/Desktop$ sudo dpkg -i --force-all --force-architecture mfc6490cwcupswrapper-1.1.2-2.i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: error processing mfc6490cwcupswrapper-1.1.2-2.i386.deb (--install):
 mfc6490cwcupswrapper:i386 1.1.2-2 (Multi-Arch: no) is not co-installable with mfc6490cwcupswrapper:all 1.1.2-2 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 mfc6490cwcupswrapper-1.1.2-2.i386.deb



HELP!
Am I doing something wrong?

---

### Post by Thirt33n on 2011-09-08
Worked perfectly.. thanks..

---

### Post by Shazaam on 2011-09-08
Natty repo's (maybe maverick too) have the Brother drivers already there. Make sure you install the brother "extras" driver packages too (cupswrapper and lpr). Then use the add printer setup in System-Administration-Printing.

---

### Post by sdibaja on 2011-09-09
somebody somewhere said...

Brother MFC6490cw 64bit printer driver installation
-----
Open a console.

Pre-required procedures :

Code:
sudo apt-get install ia32-libs
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model

Download the drivers :
Code:
wget [http://www.brother.com/pub/bsc/linux/dlf/mfc6490cwlpr-1.1.2-2.i386.deb](http://www.brother.com/pub/bsc/linux/dlf/mfc6490cwlpr-1.1.2-2.i386.deb)
wget [http://www.brother.com/pub/bsc/linux/dlf/mfc6490cwcupswrapper-1.1.2-2.i386.deb](http://www.brother.com/pub/bsc/linux/dlf/mfc6490cwcupswrapper-1.1.2-2.i386.deb)

Install the drivers :
Code:
sudo dpkg -i --force-all mfc6490cwlpr-1.1.2-2.i386.deb
sudo dpkg -i --force-all mfc6490cwcupswrapper-1.1.2-2.i386.deb

Open your web browser and go to [http://localhost:631/admin/](http://localhost:631/admin/)
Enter your login and password, click the button "Add printer" and follow instructions.
-----------------------------------
it worked for me!:popcorn:

---

