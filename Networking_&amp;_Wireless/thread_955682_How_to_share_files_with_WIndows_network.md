---
title: "How to share files with WIndows network"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by YigalB on 2008-10-22
I have Ubuntu computer and several XPs.
SO far I could always see the XP shared files from the Ubuntu, so I could easily copy files between them.
I could never see the Ubuntu from the XP side, but I didn't mind since I could do the tasks from Ubuntu.
Weeks ago, I lost that capability, but it came back after re-setting the network switch.
Now I lost it again - this time resetting didn't help.
The only change I did is adding a password to the administrator of the XP (because VMware required that).
Now I have no way to copy files between the XP and the Ubuntu.
Is there a "how to" simple guide to create home networking with Ubuntu and XP?
I have Samba installed, but I am not sure how to config it.

---

### Post by cariboo on 2008-10-22
Have a look at this howto:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

It should solve your problem.

Jim

---

### Post by YigalB on 2008-10-22
thanks, but .....Wow, are you sure?

It's such a long procedure with many opportunities to make mistakes. I just wanted to copy files between machines, and this procedure is certainly not for the average user. Also, users shouldn't run command lines or change config files - a GUI should do that after the user answers simple questions.

Shouldn't it be as simple as with XP sharing? I mean right click on a folder and share it?

All I need is a one folder to be shared, and use it as bi-directional buffer.

Any idea?

---

### Post by Iowan on 2008-10-22
A couple more for you:
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

### Post by YigalB on 2008-10-23
Thanks - but this is no good.

I was asking for a SIMPLE method for human beings, not a list of endless risky activities. Regular user shouldn't get a list of actions that are even devided intopre-work/manual mount/permanent mount/after word.

"simple" means: a utility with GUI that asks me what worgroup, what folder to share, and R/W permissions. May be passwording. The utility will do the whole work for me.

I can't imagine an OS without such simple capability. Ever tried to make home networking with XP? It's so simple.

---

### Post by Bucky Ball on 2008-10-23
Make a new folder on the desktop, right click on it and go to 'Sharing Options'.

---

### Post by YigalB on 2008-10-23
> **Bucky Ball said:**
> Make a new folder on the desktop, right click on it and go to 'Sharing Options'.

I tried that.
The problem started because I couldn't see any more the windows computers from the Ubuntu side. I do see icon of windows network, but the only computer I can see in that group is the Ubuntu. I can't see any of the 5 XPs I have in the network.

---

### Post by Bucky Ball on 2008-10-23
You need to make sure they are all in the same workgroup/domain. Go System-Administration-Network. Unlock and click the 'General' tab. The host name should be a descriptive title for the machine, the domain should be the same on *all* machines.

---

### Post by YigalB on 2008-10-23
> **Bucky Ball said:**
> You need to make sure they are all in the same workgroup/domain. Go System-Administration-Network. Unlock and click the 'General' tab. The host name should be a descriptive title for the machine, the domain should be the same on *all* machines.

I did that - the domain name is now "MSHOME".
still I don't see the other XP computers.

I see "windows network" icon, but only the Ubutu machine is under.

---

### Post by YigalB on 2008-10-27
Any idea?

---

### Post by porteclefs on 2008-10-27
just run a samba server. samba servers are easy to set up and it should perform the function of "sharing files between windows pc's"

---

### Post by tmansystems on 2008-10-28
Not to threadjack here but what about Vista?  Workgroup is set up and can see shares but not on Vista.

Thanks!

---

### Post by YigalB on 2008-10-28
> **porteclefs said:**
> just run a samba server. samba servers are easy to set up and it should perform the function of "sharing files between windows pc's"

I tried that. Still I can't see the XP computers.
Samba is running. Maybe there is a mistake in the setup, but how can I tell that - there is no simple to use "setting up a home network with XP computers".

---

### Post by Bucky Ball on 2008-10-29
> **YigalB said:**
> there is no simple to use "setting up a home network with XP computers".

No, but there are lots about setting up samba which equates to the same thing:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by dmizer on 2008-10-29
Actually, I sincerely sympathize with you. I was stonewalled by this very problem for months after my first install of Ubuntu. Things have improved a lot since then, but sometimes the quickest and easiest way to solve this SAMBA problem is to work in the command line.

Before it comes to that, I have three questions:
[LIST=1]
[*]Have you installed Firestarter on your Ubuntu machine?
[*]Are both Windows and Ubuntu a part of the same Windows Workgroup?
[*]For testing, have you disabled the Windows (or third-party) firewall?
[/LIST]

---

### Post by YigalB on 2008-10-30
> **dmizer said:**
> actually, i sincerely sympathize with you. I was stonewalled by this very problem for months after my first install of ubuntu. Things have improved a lot since then, but sometimes the quickest and easiest way to solve this samba problem is to work in the command line.

Before it comes to that, i have three questions:
[list=1]
[*]have you installed firestarter on your ubuntu machine?
[*]are both windows and ubuntu a part of the same windows workgroup?
[*]for testing, have you disabled the windows (or third-party) firewall?
[/list]

1- no
2- yes
3-yes

---

### Post by dmizer on 2008-10-30
Lets try configuring you for windows name resolution.

We'll need to make a small edit of a file, and then install a daemon.

Edit /etc/nsswitch.conf like so:
```
gksudo gedit /etc/nsswitch.conf
```
Look for this line (it may be slightly different for you):
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
In front of "dns", add "wins" like so:
```
hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```
Save the file, and exit gedit.

Now install winbind with the following command:
```
sudo aptitude install winbind
```

See if you can view your Windows shares (if unsuccessful, you might try rebooting).

---

### Post by dmizer on 2008-10-30
Lets try configuring you for windows name resolution.

We'll need to make a small edit of a file, and then install a daemon.

Edit /etc/nsswitch.conf like so:
```
gksudo gedit /etc/nsswitch.conf
```
Look for this line (it may be slightly different for you):
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
In front of "dns", add "wins" like so (the order is important):
```
hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
```
Save the file, and exit gedit.

Now install winbind with the following command:
```
sudo aptitude install winbind
```

If you are still not successful:
Try rebooting.
Please post the output of this command:
```
smbtree
```

---

### Post by YigalB on 2008-10-31
Thank you very much fr the effort and answer, but I am afraid I will not try that, because I will not be able to change back and maintain it ver time.
I decided to use only GUI because this way I will not be able to damage system files with typos, and also it's the only way to guide regular users.

Again - I appreciate your help.

---

### Post by dmizer on 2008-10-31
Actually, I did the above just once ... on my server. The configuration has remained untouched through every update, and distribution update for the past 4 years.

Your Ubuntu computer needs a way of reading Windows host names. There are two ways you can do that. First, you can do what I suggested above, or you can configure a local DNS server.

The only other option I know of (or can think of) would be to install a non-supported and depreciated GTK samba browser called smb2k.

Edit:
People using KDE (Kubuntu) report a much more seamless Windows network integration.

---

### Post by YigalB on 2008-10-31
It's a matter of expectations from the OS. 
I expect user friendly interface, and unfortunately Ubuntu is way behind. 
Whenever the solutions to such simple tasks requires so many bypasses, my conculsion is that Ubuntu is just not ready yet for the people.
I am using Ubuntu with one of my computers for more than two years. I see great progress, but the GUI level is very poor, and the fact that it's not easy to inteface Ubuntu to home networking requiers engineering skills, brings me slowly to the decision that I just can't afford spending time on that task. It's such a basic need: same like browsing the web.

---

### Post by dmizer on 2008-10-31
Of course it's your decision. But when I set up my first Window's network, it took me a couple of months to get everything working correctly. It actually took me less time to learn how to make Ubuntu do the same thing, and I had very little experience with Linux before I started using Ubuntu.

I sincerely believe that Ubuntu is neither more difficult nor more backwards than Windows. It's just different.

I do understand your desire for a GUI, but you're asking Ubuntu to automatically talk to a system (Windows) which doesn't even talk to itself, let alone Linux or OSX, well on many occasions. SAMBA is a closed source Windows specific file sharing protocol. It only works in Ubuntu because it has been reverse engineered. It really does work quite well, but it does take some patience.

---

### Post by dmizer on 2008-10-31
Of course it's your decision. But when I set up my first Window's network, it took me a couple of months to get everything working correctly. It actually took me less time to learn how to make Ubuntu do the same thing, and I had zero experience with Linux before I started using Ubuntu.

I sincerely believe that Ubuntu is neither more difficult nor more backwards than Windows. It's just different.

I do understand your desire for a GUI, but you're asking Ubuntu to automatically talk to a system (Windows) which doesn't even talk to itself, let alone Linux or OSX, well on many occasions. SAMBA is a closed source Windows specific file sharing protocol. It only works in Ubuntu because it has been reverse engineered. It really does work quite well, but it does take some patience.

---

### Post by YigalB on 2008-10-31
As for XP installation: it's very easy. Few clicks and you have a working network. Sharing a folder is just right click away. I did it many times, never failed. With Ubuntu there is no guide, no wizard - I never suceeded to do a full networking.

As for the market position - keep in mind that most of the market is XP. It doesn't matter if this is right or wrong - it's the situation.
In order to push Ubuntu there must be easy way to integrate Ubuntu into the standard home networking. This is a must, not nice to have. People will never listen if your answer starts with "sudo". It should be few clicks for the default and that's it. Until Ubuntu will be there - it will not be alternative for the people.

This is what I don't understand: Ubuntu is so good, and in many ways easy to use. There are enough applications. Someone should give an attention to the daily tasks, such as: home networking, adding another hard disk, using DiskOnKey - all of these are undoable with Ubuntu and peice of cake with XP.

---

### Post by lisati on 2008-10-31
The germ of an idea here: would the development of a GUI-based equivalent of XP's "Setup network wizard" be something to pencil in for the future?

I've used the guide at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) without any hassle, even though some of it requires using the terminal and editing text files.

---

### Post by YigalB on 2008-10-31
> **lisati said:**
> The germ of an idea here: would the development of a GUI-based equivalent of XP's "Setup network wizard" be something to pencil in for the future?

I've used the guide at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) without any hassle, even though some of it requires using the terminal and editing text files.

Again - this is not doable for 98% of the population. I didn't say it wont work - I am just saying that wizard is something people can live with. Very few will bother going to forums, read tips and most of all use commands. Even wizard is too much for many - right click should be the answer for most standard issues. 

It will just not work.

---

### Post by two4two on 2008-11-26
Actually, when I used the GUI it was very easy except I still couldn't see my Linux box from my WinXP box. So I entered the sudo /etc/init.d/samba start command and voila: visible from WinXP (although I didn't try to browse or update any files yet). Also I didn't see what happens if I reboot if the SAMBA START is automatically performed during boot. Also in the Ubuntu community documentation Setting Up SAMBA they have a reference to:

[COLOR="Blue"][B]Configuring your computer
Start the network configurator using the following menu: 


(see attached image)


System -> Administration -> Network 



You will need the General tab, in the middle.[/B][/COLOR]

I am running 8.10 with current updates installed and I don't have a panel like that one.  Where do I get one?  It would be a nice addition to my Ubuntu.

---

