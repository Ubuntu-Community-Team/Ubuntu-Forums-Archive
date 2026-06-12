---
title: "Penggy Config"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by TriJump on 2007-05-29
Okay, so sadly I am one of the unlucky ones stuck with AOL as his ISP.  I can't change ISPs as my parents insist on using it.  So I am trying to get penggy to work on Fiesty.  I downloaded it from the repositories and installed it but am now at a loss for how to configure it.  I've looked all over online and I can't seem to find straight forward directions on how to edit the penggy.cfg and aol-secrets files.  

I've played around with the files, trying things like screen-name = XXXX in the aol-secrets file, but to no avail.  Can anyone help me out with setting penggy up so I can finally get online with Ubuntu?  Thanks.

---

### Post by Gerro on 2007-06-13
I think you have to setup the aol secrets similar to how you would with a normal dialup settings such as using ppp. Therefor it would look like "username" "password" -  The dash is very important and has something to do with legacy configuration sort of like how putty uses a . in certain parts.

---

### Post by caratuco on 2007-06-13
I have installed penggy on two computers and had to play with config some. Here is what I did. You will not only need penggy but also it' s dependency packages.  You do can get it and it's dependencies at Debian.
 the package will list all dependencies. Choose the deb packages:
[http://packages.debian.org/stable/net/penggy](http://packages.debian.org/stable/net/penggy)     This page shows and links to dependencies.
  After downloading to a cd, etc., install the dependencies by right clicking on the deb package, scroll down to (k)ubuntu package menu, choose install package. 
  Next install penggy.
  After all the packages and penggy have been installed open Konquerer, select home, then use the up arrow to find the “etc” folder, open it and scroll down to the penggy folder and open it. Inside penggy you will find three files you will need to edit:
 aol-secrets
phonetab
penggy.config
 
  Aol-secrets can be edited by right clicking it , scrolling down to actions, then clicking edit as root.
The only thing that is needed in this file is one line containing your uncommented screen name and  your password. I deleted “Luke”, put in my password, left the two dots in the middle and moved over to(don't use the space bar, use the right arrow) the “f0rce”, deleted it and entered my password. Leave everything else commented out. So:

Your screen name                .                    .                   Your password

  Finally I saved the edited file.
  Phonetab can be edited in the same way- right click it, actions, edit as root. All that is needed here is the uncommented phone number that you use to dial into aol (not your home phone). I didn't use dashes, so 5555555555 not 555-555-5555. leave everything else commented out.
  Penggy.config is edited in the same way, as root. There are quite a few lines in this file but for me uncommenting and using the defaults worked.  For instance, where it says:
auto_reconnect = true 
but the default says it is false, change it to false. Also, I only needed to uncomment initstr1 = ATZ.
Try it first, then initstr2-9 if needed. “Ip_up” and “Ip_down” did nothing so I left them commented out. And finally, enter your screen name on the “screen_name =” line. Save the file.
  Next click on the K menu (applications) , then the run command. Enter penggy (small letters)in the box, then click on options , click on run in terminal window (so you can see what penggy is doing). Click on run as different user, leave the “root” in the first box, enter your password in the second box and click run. Penngy will run and if it is configured correctly when the terminal window says “IP tunnel is working” you are online.
  I could never get konquerer to work as my web browser so I did an “sudo apt-get updates” and “sudo apt-get install firefox”. It works great I am online right now using penggy!
  Hope this helps some aol users.

---

