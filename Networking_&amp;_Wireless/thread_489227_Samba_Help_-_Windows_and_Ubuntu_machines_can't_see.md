---
title: "Samba Help - Windows and Ubuntu machines can't see each other"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by BlueNoteExpress on 2007-07-01
So, I finally took the Linux plunge and installed Ubuntu tonight.  Now, I'm trying to use Samba to share files between my Ubuntu desktop and my Windows XP laptop.  Unfortunately, neither can see the other.  Any help getting this working will be appreciated.

EDIT: My Windows laptop can see an Ubuntu share now, but Ubuntu still can't see the Windows share.  I'm using pyNeighborhood, and when I scan the Windows computer, I get an "Scanning host COMPUTER_NAME... failed".  Any ideas what I'm doing wrong?

---

### Post by BlueNoteExpress on 2007-07-01
Well, I think I managed to get it mostly working.  My user names between my Ubuntu and Windows XP machines are almost identical except my Windows XP user name starts with a capital letter.  Adding and Enabling another samba account with a capital letter seems to have mostly fixed the problems I was having.

I still can't see my Windows XP shares using the pyNeighborhood utility, but I can see them if I just navigate to them by going to Places -> Network -> Windows Network -> WORKGROUP_NAME -> XP_COMPUTER_NAME

After restarting both machines, I got it to prompt me for a user name and password.  I entered my XP username/password combo (the one with the capital letter) and it worked.  Now, if I could just figure out why the pyNeighborhood utility isn't happy...

---

### Post by Spam Banjo on 2007-07-24
> **BlueNoteExpress said:**
> Now, if I could just figure out why the pyNeighborhood utility isn't happy...

I'm now getting the same problem you had originaly.

I can reconnect if I reboot the Ubuntu machine, but only until I logout and back in again. Sometimes it kills off so I get the "... failed" message half way through a session.

From time to time pyNeighborhood forgets my mounts too... and it's so annoying restarting to map them again.

Did you ever fix it?

[COLOR="Red"]EDIT : FIXED!!! YAY!!!
The issue I was having was caused by pyNeighborhood forgetting the network password I had entered when I first set the program up. 

To fix it I went to EDIT>PREFERENCES>GENERAL and selected 'Always use default username and password' and entered my password for the server. Problem solved. :)[/COLOR]

---

### Post by BlueNoteExpress on 2007-07-24
I'm pretty sure I tried the "Always use default user name and password" option at least once.  That seemed to make things worse if I'm remembering correctly, but it's been a while now.  I also have slightly different user names between my XP and Ubuntu installs.  On XP, my user name is Nick and on Ubuntu it's nick.  The passwords are identical.  I'm not sure if the capital letter is messing anything up or not.

I found something even more interesting a few days later.  My desktop is dual booting Ubuntu and XP, but for this discussion, it's running Ubuntu Feisty Fawn 7.04.  My laptop is running XP Pro and my fiance's laptop is running XP Home.  I can connect to my laptop using Places -> Network -> Windows Network -> WORKGROUP_NAME -> MY_LAPTOP_NAME, but cannot connect to it using the pyNeighborhood utility.  On the other hand, I can connect to my fiance's laptop using the pyNeighborhood utility but I cannot connect to it using the Places -> Network -> etc. method.

Since my laptop is running XP Pro, I turned off Simple File Sharing.  Other than one laptop running XP Pro and the other running XP Home, that should be the only difference.  I wouldn't be surprised if this is more of a Windows issue than an Ubuntu issue, but does anyone know why the two XP laptops would behave differently?  This seems really strange to me.

Fortunately, I can connect to either laptop.  I just have to use a different method for each one.  Weird.

---

### Post by Spam Banjo on 2007-07-25
Have you set up your Ubuntu machine as a static IP???

I had to do this first, and enable WINS support on the Ubuntu Box.

You must then add the Ubuntu IP address as WINS servers on the TCP/IP advanced properties on the XP machines.

I followed [this guide to sort out basic shares]("http://ubuntuforums.org/showthread.php?t=202605"), and It works 100% at home... With the server at work it's a slightly different story as the server is a Windows 2003 machine and required a password to access shares. This is one of the reasons I *need* to use pyNeighborhood.

I also need the shares to be accessible through WINE, so I have to mount them to be able to use the /mnt/lan/SERVER/FOLDER path to map them as drive in wine.

I am still getting the problem of pyNeighborhood forgetting my mounts. I have to go back and mount the shares each time I reboot, although logout>logon stores them fine. They are also forgotten when I logout and log in to an XGL session.

I feel I should start a separate post regarding my issue.

---

### Post by BlueNoteExpress on 2007-07-26
No, I haven't set this up as a static IP, although I could easily do that.  I haven't enabled WINS support either.

I'm concerned about making Ubuntu a WINS server because I dual boot this PC.  If I were to set up this Ubuntu box as a WINS server, what would happen when I boot it to XP?  Would that cause problems?  If it won't, I can try setting a static IP and setting this box up as a WINS server.

The other thing is that I can access the shares on each laptop.  I just have to go about it one way form the XP Pro laptop and another way for the XP Home laptop.  That seems strange to me, and I was wondering if anyone might know what was up with that.  I wouldn't be surprised if it's more of a Windows problem than a Ubuntu/Linux problem, but I'm still curious why I have to access each version of XP using a different method.

---

### Post by ugm6hr on 2007-07-27
> **BlueNoteExpress said:**
> No, I haven't set this up as a static IP, although I could easily do that.  I haven't enabled WINS support either.

I'm concerned about making Ubuntu a WINS server because I dual boot this PC.  If I were to set up this Ubuntu box as a WINS server, what would happen when I boot it to XP?  Would that cause problems?  If it won't, I can try setting a static IP and setting this box up as a WINS server.

The other thing is that I can access the shares on each laptop.  I just have to go about it one way form the XP Pro laptop and another way for the XP Home laptop.  That seems strange to me, and I was wondering if anyone might know what was up with that.  I wouldn't be surprised if it's more of a Windows problem than a Ubuntu/Linux problem, but I'm still curious why I have to access each version of XP using a different method.

I dual-boot, and have Xubuntu set as a WINS server.  Doesn't seem to cause any problems for me.

As for the pyNeighborhood / GNOME networks issue - it's not because XP Home uses MSHOME and Pro uses something else (is it MSOFFICE) as Workgroup is it?

In case you want to see how I got PyNeighborhood to work:
[http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

---

### Post by BlueNoteExpress on 2007-07-28
> **ugm6hr said:**
> I dual-boot, and have Xubuntu set as a WINS server.  Doesn't seem to cause any problems for me.

As for the pyNeighborhood / GNOME networks issue - it's not because XP Home uses MSHOME and Pro uses something else (is it MSOFFICE) as Workgroup is it?

In case you want to see how I got PyNeighborhood to work:
[http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

Alright, I might give the WINS server thing a whirl even though I don't think it will make much difference.  My old PC is suffering from some kind of hardware problem.  If I can figure out how to get it running again, I'm going to try turning it into a Ubuntu-only file server.  If I can get that PC running again, I'll just make it the WINS server.

All of my PCs are set to the same workgroup so mismatched workgroups shouldn't be causing any of these problems.  That's one of the first things I change every time I install Windows.

The pyNeighborhood browsing method works for one laptop but not the other.  The Places -> Network  -> etc. method works for the other laptop but not the one that works with the pyNeighborhood method.  I'm thinking there has to be some kind of difference between XP Pro and XP Home, and I'm betting that it might be that I turned Simple File Sharing off on the XP Pro laptop.  I might try turning Simple File Sharing back on for the XP Pro laptop and see if that makes any difference.  The difference seems strange to me so I thought I'd see if there were any Windows/Linux networking gurus out there that knew what might be going on.

If anyone has any additional ideas, I'd love to hear them.  Otherwise, I'll post again with the results of anything else I try.

---

