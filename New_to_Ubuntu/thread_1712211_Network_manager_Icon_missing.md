---
title: "Network manager Icon missing"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by osprey2000 on 2011-03-22
p { margin-bottom: 0.21cm; }  Hi,
 

 I'm a bit of a newbie running 10.04 and have tried to follow advice re security and set up a user account for daily use that has limited rights i.e. it cannot “administer the system”  in order to protect my computer.
 

 However, when logged in as that user  I cannot find the Network Manager Icon in the top right of the screen.
 

 I tried right clicking the area and clicking on “add to panel” but cannot find the icon.
Synaptic says its there, it's on "Startup Apps "

 

 I have “Googled” the problem, searched this forum and tried all the suggestions posted but without any luck....as one user I have the icon , as the other nothing.
 

 I would really appreciate any help please

---

### Post by Rex Bouwense on 2011-03-22
Try this.  Right click an open space on the panel and then select properties.  Increase the size from the default to 27 or 30.  Once the network manager icon shows up on the panel, decrease the size down to 24.

---

### Post by 5149.5 on 2011-03-22
Open startup applications, click network monitor, click edit. Look at the command. It might not be doing what you think.

---

### Post by dineshs on 2011-03-22
Did you try `Right click on the top panel-click add to panel-select notification area -click add'
If there is no luck run ```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```and set ```
managed=true
```then restart

---

### Post by osprey2000 on 2011-03-22
Hi,

The right click and expand bar size didn't work I'm afaid.

"Startup apps" seemd to say it was doing the right thing

I ran the terminal command and got this from it

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


not sure what I'm supposed to do with the other command??

I really am quite a newbie....sorry!

---

### Post by dineshs on 2011-03-22
> I ran the terminal command and got this from it

# This file is installed into /etc/NetworkManager, and is loaded by
# NetworkManager by default. To override, specify: '--config file'
# during NM startup. This can be done by appending to DAEMON_OPTS in
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
[COLOR="Red"]managed=false[/COLOR]
run *gksudo gedit /etc/NetworkManager/nm-system-settings.conf* again, edit the file and make managed=true
save and restart

---

### Post by osprey2000 on 2011-03-22
Dineshs Hi,

I finally got what you meant but no luck, still the same

---

### Post by osprey2000 on 2011-03-22
As that hasn't worked do i leave it set to "true" ????

---

### Post by dineshs on 2011-03-22
[http://ubuntuforums.org/showpost.php?p=9236722&postcount=16](http://ubuntuforums.org/showpost.php?p=9236722&postcount=16)
[http://ubuntuforums.org/showpost.php?p=9882060&postcount=55](http://ubuntuforums.org/showpost.php?p=9882060&postcount=55)

---

### Post by JKyleOKC on 2011-03-22
> **osprey2000 said:**
>  I'm a bit of a newbie running 10.04 and have tried to follow advice re security and set up a user account for daily use that has limited rights i.e. it cannot “administer the system”  in order to protect my computer.
 

 However, when logged in as that user  I cannot find the Network Manager Icon in the top right of the screen.Does the icon show normally if you log in with the original user ID? If it does, then the problem is in the profile of your added user, not in Network Manager itself.

With Linux, unlike in Windows, there's no real need to create a limited account to protect the system. Your original account has no more administrative powers than does the limited one -- the only difference is that the original account has the ability to temporarily gain such powers when needed, but only after you type in your login password. It's much like the "run as" feature of Windows. Thus you're as safe using the original account as you are when using the new one -- and if the original makes things work more to your liking, just use it.

If you still want to use the more limited account, then try comparing every hidden file in the original home directory with its counterpart in the new home directory (hidden files are those whose names start with "." and those in the home directory correspond to Windows registry files for each user). When you find differences, make the new one match the original. That should wind up with both behaving the same way.

---

### Post by osprey2000 on 2011-03-22
Hi,


[http://ubuntuforums.org/showpost.php?p=9882060&postcount=55](http://ubuntuforums.org/showpost.php?p=9882060&postcount=55)

How do I remove this file the other method via the terminal commands doesn't work

---

### Post by 5149.5 on 2011-03-22
> **osprey2000 said:**
> Hi,


[http://ubuntuforums.org/showpost.php?p=9882060&postcount=55](http://ubuntuforums.org/showpost.php?p=9882060&postcount=55)

How do I remove this file the other method via the terminal commands doesn't work

sudo rm-f /home/user/.gconf/apps/panel

---

### Post by QLee on 2011-03-22
osprey2000,

When your admin user made the connection with NetworkManager was the checkbox down in the lower left checked, the one about allowing other users to use the connection?

---

### Post by osprey2000 on 2011-03-22
Hi,
All I get when I run that in terminal is this

test@zeus:~$ sudo rm-f /home/user/.gconf/apps/panel
sudo: rm-f: command not found
test@zeus:~$ ^C
test@zeus:~$

---

### Post by osprey2000 on 2011-03-22
When your admin user made the connection with NetworkManager was the checkbox down in the lower left checked, the one about allowing other users to use the connection?

No it wasn't....I've just gone back in as admin and changed that but still no luck

---

### Post by 5149.5 on 2011-03-22
> **osprey2000 said:**
> Hi,
All I get when I run that in terminal is this

test@zeus:~$ sudo rm-f /home/user/.gconf/apps/panel
sudo: rm-f: command not found
test@zeus:~$ ^C
test@zeus:~$

My mistake, there is supposed to be a space between the m and the f. 
sudo rm -f /home/user/.gconf/apps/panel

---

### Post by osprey2000 on 2011-03-22
Hi,

I should add here that I can go on line via Admin, change users and that new user is on line ok but you can't see the icon for the none admin user

---

### Post by osprey2000 on 2011-03-22
test@zeus:~$ sudo rm -f /home/user/.gconf/apps/panel
[sudo] password for test: 
test@zeus:~$ ^C
test@zeus:~$ 


result of second go...is it me?? am I doing something wrong

---

### Post by 5149.5 on 2011-03-22
> **osprey2000 said:**
> test@zeus:~$ sudo rm -f /home/user/.gconf/apps/panel
[sudo] password for test: 
test@zeus:~$ ^C
test@zeus:~$ 


result of second go...is it me?? am I doing something wrong

Yes. You failed to type in your password.

---

### Post by osprey2000 on 2011-03-22
Hi'

Ran it again....no request for password

---

### Post by Arijit_Kundu on 2011-03-22
[sudo] password for test: 

here you'll give the password and then press enter

---

### Post by osprey2000 on 2011-03-22
Have to go feed kids, back later if you have time....one remoning question is in the suggested solution where I changed a file from "false" to "true"....do I leave that at "true"

---

### Post by osprey2000 on 2011-03-22
Honest! I am doing that but still no request for password but French wife insists I join for dinner....30 mins

---

### Post by QLee on 2011-03-22
[QUOTE=osprey2000]When your admin user made the connection with NetworkManager was the checkbox down in the lower left checked, the one about allowing other users to use the connection?

No it wasn't....I've just gone back in as admin and changed that but still no luck[/QUOTE]

After you made the change to the connection did you restart networking (or reboot)?

[Edit] It also might be worth checking that the limited user is a member of the netdev group.

---

### Post by Arijit_Kundu on 2011-03-22
[sudo] password for test: 

this line is asking you to enter password. neway, have a nice dinner and come back!

---

### Post by osprey2000 on 2011-03-22
Hi,

Tried again this is what I got

test@zeus:~$ sudo rm -f /home/user/.gconf/apps/panel
[sudo] password for test: 
Sorry, try again.
[sudo] password for test: 
test@zeus:~$ [my password]
[my pass woed again ] command not found
test@zeus:~$

---

### Post by osprey2000 on 2011-03-22
Guys, I have to leave to leave this till tomorrow.....homework, dishes...you know what it's like

---

### Post by osprey2000 on 2011-03-23
Hi,

I'm back having tried all of the above without much, well any, luck really.

Are there any more ideas out there??

I have seen lots of solutions on this site and Google links that seem to work for some people but not others is there some chance of Canonical helpinh??

---

### Post by JKyleOKC on 2011-03-23
Did you try this one yet? It just might be your problem...

[http://ubuntuforums.org/showthread.php?t=1711502&highlight=notification](http://ubuntuforums.org/showthread.php?t=1711502&highlight=notification)

Specifically, post #4 in that thread.

---

### Post by osprey2000 on 2011-03-24
Hi,

Thanks for the idea, I tried all those in that thread but none worked it seems a very stubborn problem

---

### Post by QLee on 2011-03-24
osprey2000,

I just looked back over the thread, this is a "limited" user we're discussing isn't it, so what would be the purpose of the applet on this users panel since a limited user doesn't have the permissions to alter connections? Earlier in the thread, after you changed the checkbox for available to all, wasn't the connection available to the user on the next reboot? In other words, didn't the user have access to the Net on the connection setup by the admin user?

---

### Post by osprey2000 on 2011-03-27
Q Lee hi,

Yes you're right this is a limited user we're discussing and that user has access to the internet once I've logged on but even when I give this limited user admin rights, the applet is still unavailable.
Is that right, is that how it's supposed to work...I thought Administrators (which he became when I allowed it t to see if that was the problem) would have the applet available to them

I only did all this to give myself another account without Admin rights for better safety whilst surfing, should I not bother??

---

### Post by linux00 on 2011-03-27
Linux limited users start with the same privileges as administrators - the only difference is that admins can rum a command with *sudo* which allows them to take on full admin privileges for the execution of that command. Thus there is little point in having a second, "limited user" account.

---

### Post by JKyleOKC on 2011-03-27
> **osprey2000 said:**
> Q Lee hi,

Yes you're right this is a limited user we're discussing and that user has access to the internet once I've logged on but even when I give this limited user admin rights, the applet is still unavailable.
Is that right, is that how it's supposed to work...I thought Administrators (which he became when I allowed it t to see if that was the problem) would have the applet available to them

I only did all this to give myself another account without Admin rights for better safety whilst surfing, should I not bother??The applet still has to be installed for each user, to be able to see its icon. This happens automatically at user-creation time, but when the Admin capability is added later by adding the user to the appropriate group, must be done manually. It's possible that all you need to do is check the box for it to start automatically, in your autostart settings dialog. I use Xubuntu rather than Ubuntu, which is the same but uses a different window manager, so I can't give you the exact menu choices to check.

As linux00 has said, the only difference between the limited user and the Admin one created at install time is the ability to use the "sudo" command to make system changes or modify files owned by another user, so there's really no point in having a second limited account if you're the only user. However if others in the family use the box from time to time, it's best to have additional accounts for them if for no other reason than to keep their configuration settings separate.

---

### Post by osprey2000 on 2011-03-28
Hi,

I removed the  "Limited User" account...rebooted..set up from scratch another " Limited User" account and the same thing happened, no Icon !

I tried all the suggested solutions again but still no icon.

I checked the startup apps and it's there ticked and seems ok but I can't find a way to get it onto the panel

What am I doing wrong??

---

### Post by JKyleOKC on 2011-03-28
Sorry, I'm out of ideas! Hopefully some of the others taking part in this thread will have some suggestions.

---

### Post by cheapodonuts on 2011-04-09
> **Rex Bouwense said:**
> Try this.  Right click an open space on the panel and then select properties.  Increase the size from the default to 27 or 30.  Once the network manager icon shows up on the panel, decrease the size down to 24.

Woooo! That worked for me, many thanks Rex! Have a donut.

[IMG]http://i81.photobucket.com/albums/j226/chashugh/donut.gif[/IMG]

---

### Post by Rex Bouwense on 2011-04-09
> **cheapodonuts said:**
> Woooo! That worked for me, many thanks Rex! Have a donut.

[IMG]http://i81.photobucket.com/albums/j226/chashugh/donut.gif[/IMG]

Glad that little trick works for someone other than me.  Every now and then only part of the indicator loads so rather than reboot I just do that.  Enjoy.  Nice lookin' donut.

---

### Post by cheapodonuts on 2011-04-09
> **Rex Bouwense said:**
>   Nice lookin' donut.

You're welcome.
 Sadly, I was jumping the gun quite substantially. I was so eager to get my applet back, that I right clicked on the bar, then looked for the applet. Of course it was there, I was still using my CD to run Ubuntu! Alas, I have no internet at the moment with my 10.04 install. Tried your hint on that without success. Everything else went all stretchy, but I have no applet at all. More annoying for me is that I've lost it before on another install, and got it back, but can't remember how!

Thanx anyway Rex. :D

---

### Post by arvindp3 on 2011-10-14
> **dineshs said:**
> Did you try `Right click on the top panel-click add to panel-select notification area -click add'
If there is no luck run ```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```and set ```
managed=true
```then restart

Dineshs - Thanks a lot.  Worked beautifully. -- Arvind

---

