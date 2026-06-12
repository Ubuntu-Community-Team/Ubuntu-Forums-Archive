---
title: "How to change Computer name"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by bha148 on 2009-03-07
Hi, I have just now installed Ubuntu 8.10. When I open the terminal I am getting like this 

user@user-laptop:~$ 

I want to change "user-laptop" to another name.. How can I do it..

Thanks in advance.

---

### Post by taurus on 2009-03-07
If you want to change the name of your computer, you need to change both in /etc/hostname & /etc/hosts.  Changing one without changing the other (to identical name) will cost sudo not to work anymore.

---

### Post by bha148 on 2009-03-07
> **taurus said:**
> If you want to change the name of your computer, you need to change both in /etc/hostname & /etc/hosts.  Changing one without changing the other (to identical name) will cost sudo not to work anymore.

Hi Thanks a lot for your reply. 
I could not change the name in /etc/hostname & /etc/hosts through GUI, because Permission denied.. 
If possible could you please tell me how can I change it through terminal using "sudo"...
Thanks.

---

### Post by taurus on 2009-03-07
```
gksudo gedit /etc/hostname /etc/hosts
```

---

### Post by bha148 on 2009-03-07
> **taurus said:**
> ```
gksudo gedit /etc/hostname /etc/hosts
```

Done... Ubuntu rocks... Cheers!

---

### Post by rhcm123 on 2009-03-07
> **taurus said:**
> If you want to change the name of your computer, you need to change both in /etc/hostname & /etc/hosts.  Changing one without changing the other (to identical name) will cost sudo not to work anymore.

cant you also change it with the hostname command?

---

### Post by badger_fruit on 2009-09-17
> **rhcm123 said:**
> cant you also change it with the hostname command?

This is something I would like to know myself; what is the command and does it amend it in both files as per the reply earlier from taurus?

---

### Post by wojox on 2009-09-17
What that command doess is opens both files to edit the hostname with gedit.

---

### Post by CatKiller on 2009-09-17
> **rhcm123 said:**
> cant you also change it with the hostname command?

No. The hostname command changes the host name *for that session*. When you reboot, the host name will revert back to the old one. It's just for testing, and to delay a reboot.

If you want a permanent change, you need to edit the files that taurus indicated.

---

### Post by linux.girl on 2010-02-19
> **taurus said:**
> ```
gksudo gedit /etc/hostname /etc/hosts
```

Hello everyone,

I'm quite new with Linux in general, am experimenting with Ubuntu for the first time. I tried to change the Computer name just like taurus indicated, but I get an error that says:

could not find the file /home/mycomputername/etc/hosts

I tried to edit the hosts file via gui and command line, got the same error on both. And I did type it correctly.

Any idea what could be wrong?

Appreciate your help in advance, this is a great community, proud to be around.

---

### Post by argos3016 on 2010-02-19
Eing?!
  Its **/etc/hosts **and **/etc/hostname **not **/home/mycomputername/etc/hosts**

---

### Post by linux.girl on 2010-02-19
Hi there, thanks for your quick reply - but as I said, I typed ***exactly*** what taurus wrote, but I still got that error.

See screenshot attached.

---

### Post by argos3016 on 2010-02-19
> **linux.girl said:**
> Hello everyone,

I'm quite new with Linux in general, am experimenting with Ubuntu for the first time. I tried to change the Computer name just like taurus indicated, but I get an error that says:

could not find the file /home/mycomputername/etc/hosts

I tried to edit the hosts file via gui and command line, got the same error on both. And I did type it correctly.

Any idea what could be wrong?

Appreciate your help in advance, this is a great community, proud to be around.

 [COLOR=Red]**/home/mycomputername/etc/hosts NO**[/COLOR]
[SIZE=5][COLOR=Lime][B]/etc/hosts YES ; gksudo gedit /etc/hosts
[/B][[COLOR=Black]http://www.debianadmin.com/images/ldr.png[/COLOR]]("http://www.debianadmin.com/images/ldr.png")[/COLOR][/SIZE]

---

### Post by linux.girl on 2010-02-19
Again, as I mentioned before, I typed EXACTLY what taurus wrote, meaning, etc/hosts and ********NOT********* home/mycomputer/etc/hosts, but I get that error as if I did type the wrong thing. I get the same error when I go to etc/hosts via the GUI.


Again, thanks for your help.

---

### Post by manoriax on 2010-02-19
I have just read your reply; according to the screenshot you are still in the wrong directory. :o

```
sudo gedit /etc/hosts
``````
sudo gedit /etc/hostname
```

---

### Post by argos3016 on 2010-02-19
OR in a terminal:
sudo nano /etc/hosts

---

### Post by linux.girl on 2010-02-19
I saw the screenshot and I insist I did type exactly as you mention but for some reason instead of going to etc/hosts it goes look for the hosts file at /home/myccomputername/etc/hosts and says it is not found :D

Not only that, when I go to the gui, I find the hosts file at /etc, but when I try to edit it, it gives me the EXACT same error...

I know it sounds I am dumb and don't know where I am in the filesystem, but I believe that via GUI it is pretty clear even a "dumb" person would know...and I still get this error...anyways, I think I might not be explaining myself as well as should - let's forget about it and thanks anyways guys, this is a lot of fun :)

PS: just now saw your answer argos, will try that, thnx!

---

### Post by linux.girl on 2010-02-19
the "nano" worked, thanks!!!

I hope you guys know how grateful I am for your help, was just a little frustrated before, sorry if I sounded harsh.

many many thanks!!!!!!

:D :D :D

---

### Post by G.D.C. on 2010-02-19
Just FYI, you said you were typing
```
etc/hosts
```
whereas the command given was
```
/etc/hosts
```
 
It's an easy mistake to make and if you're new to Linux it may not seem important, but it is a significant difference. The former is a *relative* reference, and the latter is an *absolute* reference. So with the first, the command line interpreter would start from whatever directory you are currently in (which, if you were in your home directory would explain why it showed up as /home/myccomputername/etc/hosts). The second (/etc/hosts) is an absolute reference starting at the root directory /.
 
Hopefully this makes sense to you and will help you dealing with the command line in the future.

---

### Post by linux.girl on 2010-02-19
hi there, thanks for the tip!

the etc/hosts was a typo here in the post, was just in a hurry - when i put the command in the command prompt, it was in the correct form, /etc/hosts - I know it because I simply copy pasted what tauros had suggested.

in any event, I did learn a lesson from you - i did copy paste without really understanding all the differences and thanks to your explanation, i do now. 

many many thanks, i really appreciate!!!

---

### Post by Marara on 2010-03-06
hi guys,

I changed the computer name based on the descriptions but when I try to see the ubuntu machine from vista I see 2 which are:

owner-desktop -- which was the previous
jiraya-desktop -- new one

then switched it back to owner-desktop & when I go to the vista machine both are still there. the owner desktop is not accessible & the jiraya one is.... would you guys know why it is like that?

I'm trying to share a printer on ubuntu & access it from vista -- another thing when i access the jiraya-desktop I see a printers folder but the printer connected to ubuntu is not there.... I checked ubuntu & it says it is shared which was by default....

any help will be appreciated.... 

thanks!!!!

---

### Post by patchwork on 2010-03-06
The old name is probably still in the dns server.  Have you selected to publish the shared printer?

System > Administration > Printing > Server > Settings > Publish Shared Printers

---

### Post by Marara on 2010-03-06
> **patchwork said:**
> The old name is probably still in the dns server.  Have you selected to publish the shared printer?

System > Administration > Printing > Server > Settings > Publish Shared Printers
Hi again,

ok I checked & the hostname file was still set to jiraya & the hosts was owner -- I got that fixed now... & for some reason the vista machine kept some computer names on the network even after they were shut off.... so that was just a vista bug....

I did publish the printer but the vista machine still wouldn't see it....

---

### Post by patchwork on 2010-03-06
It will take a few minutes for the DNS to catch up.  You also may need to disable the firewall temporarily (or configure iptables for a more permanent solution).

```
sudo ufw disable
```

This is a process I need to go through whenever I (rarely) access my shared printer...too lazy to change the routing permissions.

To re-enable the firewall, 

```
 sudo ufw enable
```

---

### Post by Marara on 2010-03-06
> **patchwork said:**
> It will take a few minutes for the DNS to catch up.  You also may need to disable the firewall temporarily (or configure iptables for a more permanent solution).

```
sudo ufw disable
```This is a process I need to go through whenever I (rarely) access my shared printer...too lazy to change the routing permissions.

To re-enable the firewall, 

```
 sudo ufw enable
```
ok, thanks....

I'll try that -- so when you mean the dns do you mean the switch/router? because I checked another vista machine & it still has the old names on the network which are not accessible because they no longer exist & also my friends laptop which he shut down & took with him & is no longer on the LAN.....

---

### Post by patchwork on 2010-03-06
One of the computers (probably the VISTA) is acting as the networks Dynamic Name Server.   It periodically checks to see what computers are hooked up to it and fetches their information.  You can probably refresh network on whichever computer is acting as the DNS to remove the computer names that are no longer hooked up.

I have NO experience with Vista, no windows experience post-XP, and limited networking experience in general, so take this with a grain of salt.

---

### Post by Marara on 2010-03-06
> **patchwork said:**
> One of the computers (probably the VISTA) is acting as the networks Dynamic Name Server.   It periodically checks to see what computers are hooked up to it and fetches their information.  You can probably refresh network on whichever computer is acting as the DNS to remove the computer names that are no longer hooked up.

I have NO experience with Vista, no windows experience post-XP, and limited networking experience in general, so take this with a grain of salt.
I disabled the firewall but still nothing......

---

### Post by patchwork on 2010-03-06
> another thing when i access the jiraya-desktop I see a printers folder but the printer connected to ubuntu is not there.... I checked ubuntu & it says it is shared which was by default....

Just a clarification, this folder ( I believe it is the $printer folder) is not where your printer will show up.  This is a folder provided by the system by default to allow you to place printer drivers in it for accessing machines to download.  When the printer is shared and published, the printer should appear in the accessing machine's printer setup screen (again, I'm not familiar with vista).  Also, it may be worth creating a new thread for this since it has drifted from the hostname conversation...you may get more input.

---

### Post by Marara on 2010-03-08
> **patchwork said:**
> Just a clarification, this folder ( I believe it is the $printer folder) is not where your printer will show up.  This is a folder provided by the system by default to allow you to place printer drivers in it for accessing machines to download.  When the printer is shared and published, the printer should appear in the accessing machine's printer setup screen (again, I'm not familiar with vista).  Also, it may be worth creating a new thread for this since it has drifted from the hostname conversation...you may get more input.
ya i was gonna ask about taking this subject to another thread before since like you said its a different issue.... I'll look into it find the right thread, thanks tho......

---

### Post by Francewhoa on 2010-03-12
There is an **easier, safer and faster** way to do this at [http://ubuntuforums.org/showthread.php?p=8955992#post8955992](http://ubuntuforums.org/showthread.php?p=8955992#post8955992)

---

