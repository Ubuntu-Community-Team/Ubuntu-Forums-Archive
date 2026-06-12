---
title: "Samba - Client wont find server"
date: 2015-11-26
forum: Networking &amp; Wireless
---

### Post by niklas7 on 2015-11-26
I have two computers with Ubuntu Desktop on both.
  The folder i am trying to share on Computer no.1 can't be found by Computer no.2


  The really frustrating part is that i actually got it to work a  couple of days ago. The thing is, i had to re-install Ubuntu-Desktop on  Computer no.2. After the re-installation i cant find Computer no.1. In  fact, i cant access the Windows Network whatsoever. 
  

When i am trying to access Computer no.1 via the "Connect to Server"  options with smb://workgroup/ or smb://85.226.255.196/ i get error  message :
  **"Unhandled error message: Failed to retrieve share list from server: Connection refused"**

I have been trying to retrace my steps but without luck.


  What i have done so far:
  
[LIST]
[*]Restarted the router 
[*]Changed permissions on the shared folder 
[*]Re-installed Samba 
[*]Updated packages on Computer no.2 
[*]Edited the smb.conf back and forth 
[/LIST]
  [HR][/HR]  Here is my [URL="https://www.dropbox.com/s/niwgmb7szhxr3x0/smb.conf?dl=0"]smb.conf
[/URL]
  The changes i have done:

[INDENT]   name resolve order = lmhosts host wins bcast 
     security = user

      [exempel]
     comment = TEST
     path = /home/holm/Exempel
     guest ok = yes
     browseable = yes
     ready only = no
     create mask = 075    [/INDENT]
[INDENT] 
 [/INDENT]
[HR][/HR]  After that i did this to set the permissions: 
  sudo mkdir -p /path
    sudo chown nobody:nogroup /path




The first time around (when i actually got it to work) i did  exactly the same thing as i have described here. At first i was only  able to see the shared folder but not access it, so i had to fix the  permissions issue. But now i can't even seem to connect to the Windows  Network.

  It may be worth mentioning that i've got dynamic IP:s. I cant change  it to Static IP either because my internetprovider have locked that  option and it would cost me money to get it.  
Also, i have no firewalls

Any ideas would be highly appreciated!

---

### Post by michi1983 on 2015-11-26
Hi,

you say that you have 2 computers with both Ubuntu Desktop on them and then you say you want to connect to a Windows Network?! 
Can you please explain that again a little bit more detailed?

From where to where and to what do you want to connect?
Is everything in your LAN at home? Or do you connect to a different location? If the latter, what hardware and which protocols do you use?

---

### Post by RobertoRecordo on 2015-11-26
I'm not an expert, so I can't tell you if what helped me will help you. I have two Linux machines and two win7 machines. They reliably print to the shared printer which was Ubuntu Studio 12.04, but recently upgraded to  Ubuntu Gnome.

First Issue:

From my notes after installing Ubuntu 15.04 Gnome
> ~~~~ Printer stopped working ~~~~ 12:49:05 PM   Thursday 03 September 2015 ~~~~ 
Installed HP Linux Imaging and Printing   HPLIP
download and ran $ sh hplip-3.15.7.run  
    It is an elaprotate python driven interactive install.
    Tt the end it did a rude reboot of system, I thought it wanted to restart the printer! Lost some notes on debugging, best tips are all here: 
        [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)
    Then I ran $ sudo hp-setup
Back & Working, local and shared
[FONT=arial black]
Second issue: 

Recently the Windows machines stopped working. I deleted the device on windows. It easily found the printer and identified it. I installed a driver. When I attempt to print, the job just sits in the que. I remembered to open a browser window 
```
http://localhost:631/admin
```
and in the "View Acces Log" i noticed repeated attempts and failures
[/FONT]```
localhost - - [26/Nov/2015:13:42:15 -0800] "POST / HTTP/1.1" 200 348 Create-Printer-Subscriptions successful-ok
localhost - - [26/Nov/2015:13:42:15 -0800] "POST / HTTP/1.1" 200 3910706 CUPS-Get-PPDs -
localhost - - [26/Nov/2015:13:50:35 -0800] "POST / HTTP/1.1" 200 187 Renew-Subscription successful-ok
localhost - - [26/Nov/2015:13:50:40 -0800] "POST / HTTP/1.1" 200 156 Cancel-Subscription successful-ok
localhost - - [26/Nov/2015:13:50:40 -0800] "POST / HTTP/1.1" 200 156 Cancel-Subscription client-error-not-found
```

Maybe the errors mean something to someone: I just took it to mean the windows machine was trying to connect to cups and failed.
[FONT=arial black][SIZE=4]
[SIZE=2]I finally found some help here:[/SIZE][/SIZE][/FONT]
[SIZE=4][URL="http://ubuntuforums.org/showthread.php?t=2054048"]Why does CUPS break at EVERY update ?!?
[/URL][/SIZE][FONT=arial black][SIZE=2]
The trick was to run
```
sudo apt-get install --reinstall cups

```[/SIZE][/FONT][SIZE=4][URL="http://ubuntuforums.org/showthread.php?t=2054048"]
[/URL][/SIZE][FONT=arial black][SIZE=2]It seems that the print server is not as robust as we might like it to be, but I hope you can get your printer working, at least until the next upgrade![/SIZE][/FONT][SIZE=4][URL="http://ubuntuforums.org/showthread.php?t=2054048"]
- Rob
[/URL][/SIZE]

---

