---
title: "How do I do backup to NAS?"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by piergen on 2011-01-04
I run Xubuntu 8.04 hardy. Been running without any hickups for close to 2 years now.
Because it is so stable I have not been learning a whole lot of Linux during this time. Cause it just works. Earlier I have managed backups manually to another pc running windows. I have sambe running and can share files betwen them.

Recently I have got a Stardom NAS. That hw was truly plug n play cause I had it up running within 30 minutes. I can acceess Nas just fine from windows pc, syvio X9 etc.
But no matter what I try for accessing the NAS from Xubuntu I fail. 

I have tried gftp. Would not work. I then tried Gnome Commander. Same there.
Would not work. The strange thing is from windows I can connect to NAS via FTP easy peasy. I also can browse folders in NAS from "My Network Places" in windows. But cant access the NAS at all in Xubuntu. If I type IP adress directly in a browser I get to the Admin login screen for the NAS as excpected. As I am currently without ADSL I have no internet connections to the xubuntu so it is stress to keep adding tools as I can not run sudo apt-get without internet and everything must be compiled, and for that to work I need step by step tutorial. So pls no advice for yet another ftp tool. I also have limited bandwidth now cause windows pc is connected via cellphone.

What I am guessing here it that there is a safety issue that I must find a way around. Like a firewall closing gates or something like that.

All I have running at the moment is a GB switch, router is unplugged as my home network lack internet connections at the moment. I figured removing the router would at least remove one firewall. So I belive this is Xubuntu or Linux firewall that is keeping me from browsing folders or connect FTP to NAS, or some naming issues with WORKGROUP vs workgroup or something.

Is there an easy way to let me connect to NAS from ubuntu? Prefferable I would like to be able to both browse folders on NAS and to connect via FTP.

I have lots of GB data I would like to have copied to NAS, what is most stable method?
Copy files via FTP or manually when browsing folders? Or maybe even via terminal window? Reasson for asking is that I have had issues in the past where files transfer stops for some reasson and that makes me have to start the same job over once more. I really would prefer to use the most stable method here to avoid any hickups.

---

### Post by CharlesA on 2011-01-04
I couldn't find any information about that NAS.

What model is it?

You can try running nmap against it and see what ports are open. That'll tell you how to connect.

I'm guessing it's using Samba, as the Windows boxes are able to connect fine.

---

### Post by piergen on 2011-01-04
The Nas is [Raidon SL3620-2S-LB2]("http://www.raidon.com.tw/content.php?sno=0000096&p_id=25").
Yes you are right about samba, it is samba. But I think it runs a linux firmware of some sort, think I read that somewhere. 

Nmap? Guess I must install that as well and I have no internet connection for the Xubuntu as my adsl is down. Anyhow writing nmap in terminal window didnt do anything so I guess I wil have to look for step by step tutorial on how to compile nmap, cause no way I can find it as .deb file? Well I start looking. Let me know if there is any other methods.

Also even if the NAS is using samba, I should be able to use gftp to connect to port 21 on the NAS. So why is that not working either for me?

---

### Post by CharlesA on 2011-01-04
Try using telnet instead.

```
telnet ipofnas 139
```
```
telnet ipofnas 445
```

EDIT: From the specs sheet, it does use Samba/CIFS. Are you able to connect by using the ip address?

---

### Post by egalvan on 2011-01-04
> **piergen said:**
> But **cant access the NAS at all **in Xubuntu.
If I type IP adress directly in a browser **I get to the Admin login screen for the NAS** as excpected.

These two statements seem to contradict each other

> 
or some naming issues with WORKGROUP vs workgroup or something.


I haven´t stumbled around with uppercase/lowercase stuff in the network arena,
but Linux **IS** case-sensitve with file names...

And what happens if you try to work from the Admin Login screen fro the NAS?

---

### Post by piergen on 2011-01-04
I can connect by using the IP adress in a browser. However browsers use port 80 and that takes me to the admin setup. I did try to connect and added users just to make sure connectivity is not the problem. 
Going back in again to admin GUI from windows pc I can see that the changes I made from xubuntu was correctly stored.

Hmm telenet you say? Well I will start to collect tutorials. Never used telnet before and I am sure it is not all straight forward and smooth sailing.

---

### Post by piergen on 2011-01-05
> **egalvan said:**
> These two statements seem to contradict each other



I haven´t stumbled around with uppercase/lowercase stuff in the network arena,
but Linux **IS** case-sensitve with file names...

And what happens if you try to work from the Admin Login screen fro the NAS?

No really they do not contradict each other. Because I can not connect to the NAS in a regular fashoin. Meaning browsing folders and drag and drop files, nor can I connect via FTP into the NAS. And mind you those problems excist only on xubuntu pc. However, using firefox or opera I can type in the IP adress to the NAS. But as http goes over port 80 rather then port 21 I end up in Admin GUI for the NAS. I have successfully made some changes to the NAS via admin GUI from xubuntu. So I do know the swich and network adapters are working properly. Also I have tried 2 different FTP clients just to make sure there was not anything wrong with the FTP tool itself. I have also replaced all Cat 5 cables with new cables, (shorter for test purpose) and I changed the switch for the router I use for internet. The router show me the same thing. So I doubt there is any hardware issues here. Must be something within xubuntu, and I am likely to belive it got someting to do with either firwall or some other safety precautions that keeps them bad guys out. Unfortunatly seems I also locked out from doing backups.

I have gone over the naming issues and made sure I use uppercase on all places. Still no home run. 

I must run off to read up on telnet as I was told to try that.

---

### Post by CharlesA on 2011-01-05
If you are able to connect to a web interface, does it allow you to set up access from there?

I'm not quite sure how it's set up, as I just built a "regular" machine to use as a NAS (among other things) instead of getting one of those standalone boxes.

---

### Post by scheuri on 2011-01-05
I have a (different) NAS at home and I am able to connect to it by using gnome-nautilus (and I am sure other gui's work as well) by typing in:
```
smb:\\[IP of NAS]
```
That should work (unless I just made a typo myself here)
However, you surely need to have the smb-client installed for that (and maybe even some samba-plugins for your choice of connecting gui).

Best of luck
scheuri

---

### Post by aytech on 2011-01-05
Hi, 
I had similar trouble connecting to my D-Link NAS. For some reason my ubuntu box connected to NAS for a very long time, like an hour or even more. I made sure both devices were in the same workgroup, but after starting up NAS it appeared in "Network" with a huge delay. I couldnt ping the NAS either. After some time, when it appeared in "Network" it was working fine. 
I'm not sure what caused it, maybe NAS failed to connect immediately, or router needed more time to setup the connection, maybe it was the samba issue, dunno.
I added the NAS shares into fstab and it works ok now. 
 
So I believe you made sure NAS is in the same workgroup as your ubuntu box. If you can see windows machine from ubuntu, and in windows you can see NAS, then you should be able to see NAS from Ubuntu too. I'd suggest waiting for some time if the connection will be established, and then add share to fstab. 
Unless someone will have more tech-savvy suggestion :D

---

### Post by piergen on 2011-01-05
> smb:\\[IP of NAS]

So is that with or without the [ ] ? Cant try it right now cause I am at work but I will sure try as soon as I am home.

---

### Post by piergen on 2011-01-05
I have gotten tips from a guru here at work that I might need to blame the the switch for these problems. He claims the netgear I uses is the worst switch ever made in the whole world. When he bougth one he actually had to return it for a new one three times because the switch dropped speed, lost connections or even blocked connections on some of the ports. Finally store agreed to swap the switch for store credit and he got a more expensive and more profeesional and stable switch.

When he heared about my problems he was very certain they where all caused by the netgear. Even when I explained I had try to change the cables and swapping the switch for the router he explained that most likely xubuntu would be able to connect to the NAS "out of the box" if my home network was consistance. As long as I could connect to other pc's on the network there was no way I should have big issues with xubuntu and a NAS according to him. After all he continued a NAS is "just another pc on your network, which you should reach without any troubles even in linux. He said I had made som many changes to workgroups, namings and so on that i might have changed it too much or been unaware of a typo or something. 

Sure there have been times when I have notcied that the speed was slow, typically when doing backups. First it start out with hi speed then suddenly takes forever. Occasionally the switch has been stucked so I have removed the power chord to get it to restart. I always tougth this was normal and have not reflected over the problems with the netgear switch. The switch is always running so hot. But once again I thought that was to be excpected as it has no fan.

What do other think here? Does _**netgear switch failure/degradation/overheat**_ seems like a plausible explanation? Should I just bite the bullet and order another switch? And if so what kind and what pricerange to avoid future problems?

---

### Post by scheuri on 2011-01-05
> **piergen said:**
> So is that with or without the [ ] ? Cant try it right now cause I am at work but I will sure try as soon as I am home.

Without the brackets []

Sorry for the confusion
cheers
scheuri

---

### Post by scheuri on 2011-01-05
> **piergen said:**
> I have gotten tips [a lot of text about netgear swtiches]

Well, I must admit I can not really comment on that. However, I know that there are switches out there...and switches ;)

Depending on manufacturer and on the type of switch you might indeed face troubles....that I can confirm from personal experience and from what I have seen/read in the internet.

Now, I guess the easiest thing would be getting a new one. They are not that expensive and I personally would recommend Linksys/Cisco to you. 
So far I never had any troubles with those. That is no proof that you will not have problems with them ever. It is just personal experience and personal...

Good luck
cheers
scheuri

---

### Post by CharlesA on 2011-01-05
In my experience a switch, is a switch is a switch - doesn't matter the brand.

Sure, if the switch was dropping connections and whatnot, you could replace it, but it seems to work fine for everything except the NAS.

I doubt it's the switch.

---

### Post by piergen on 2011-01-05
I am home from work but after spending the entire last night trying to make things work I am just too tired and to beat to bother with backup, switches, firewalls and telnet. So I am actually going to bed after dinner. If I do wake up before alarmclock buzzez @6am I will have some strong coffee and try out telnet among other tips gotten here. 

Btw, when I do get things running will copying files/backup from terminal window be more stable method then using drag and drop or FTP or even telnet?

---

### Post by gandaran on 2011-01-05
> **piergen said:**
> So is that with or without the [ ] ? Cant try it right now cause I am at work but I will sure try as soon as I am home.
something like this, this is how I connect my NAS drive from nautilus or using connect to server 
> smb://192.168.0.1/usb1-c/
the ip should be the same one you use in the browser to login the NAS administration page and you have to add the drive name too, check in windows which drive name if you are not exactly sure.
I'm sure with the correct ip and drive name you will connect.

---

### Post by CharlesA on 2011-01-05
> **piergen said:**
> I am home from work but after spending the entire last night trying to make things work I am just too tired and to beat to bother with backup, switches, firewalls and telnet. So I am actually going to bed after dinner. If I do wake up before alarmclock buzzez @6am I will have some strong coffee and try out telnet among other tips gotten here. 

Btw, when I do get things running will copying files/backup from terminal window be more stable method then using drag and drop or FTP or even telnet?
Any method should be equally easy/stable.

---

### Post by piergen on 2011-01-05
Well still not getting this matter solved.
I am close on giving up now, and to ba safe I will use a way of getting the backup without struggling with the connections problems. 

What I will do know is start up a vm of windows xp. Using VMplayer I will be able to connect from within winxp to the NAS. Also the virtual winxp can browse files and folders in the shared folder so moving all folders I need backup of to my shared folder takes care of this for now.

Trying the telnet tricks I got this response: (same for the 139 as well

> telnet: could not resolve ipofnas/445: Name or service not known

---

### Post by CharlesA on 2011-01-05
You need to put in the ip address for the NAS:

```
telnet 192.168.1.100 139
```

---

### Post by piergen on 2011-01-05
Ohh thx. See that is often the problem. What other take for granted we newbies manage to mess up.

Ok so here is where I am now. I have removed gftp and made a new install.
Now I am able to connect to nas. I did not change anything else. But now it seems when 
I try to transfer a folder from ubuntu to NAS I only transfer the singel files inside that folder. Subfolders and their content is not transferred. 

Am I doing something wrong here? I mean I can not handle backup this way. It will be too much work. There must be possible to transfer one folder and alle subfolder and thir folders into NAS?
After all creating the file structure and using this structure rather then scatter files all over have been importent to me. So there must be a way to keep the structure?

Regarding Gnome Commander I still can not connect using that one. And that is a shame cause that is a brilliant tool to work with files and folders. I know it should be possible but everytime I try to connect Commander shuts down. Any ideas?

---

### Post by dBuster on 2011-01-05
With Nautilus you can not see the drive?  I mean if Samba is working right you should be able to see the drive when you use nautilus...

---

### Post by piergen on 2011-01-05
Nope cant see them in Nautilus. This is second night in a row I struggle with this problem. And as I am without ADSL as well I will not be able to do more apt-get either cause of quota on mobile connection.


Now I can connect via ftp. But still there are some problems as I cant transfer one folder and all subfolder. 

What I would like to do is to transfer HOME folder to NAS. But when I try to do that via gftp I only get HOME and the few individual files inside HOME. Not subfolders and content of subfolders. Can someone help me with that pls?

---

### Post by CharlesA on 2011-01-05
I'd say use filezilla for now, but with no access to the repos, that would make it difficult to install.

---

### Post by piergen on 2011-01-06
Yeah see lack of adsl is a problem, so I will have to stick to gftp for now. Otherwise I will be financial ruined if I continue to download via cell phones 3G.

I am sure I am doing something wrong when it comes to the process of transferring files and folders with gftp. Cause in my mind one should be able to transfer one folder with all subfolders and even subfolders content in one go, right? Easy operation like that can not only excist in my dreams?

No one can be excpected to do to labor intensive back breaking excersice of copying files one folder at a time? In real world that would be a crazy and meaningless approach.

So any skilled gftp users whom migth give me some pointers on how I can transfer Home folder with all subfolders AND the subfolders content in one operation?

[U][B]Edit
[/B][/U]Well what do you know. Turns out I am able to get folders and subfolders transferred. All I do is to make sure I select more then one folder and things works like a charm. Have no idea why just happy this is possible.

---

### Post by piergen on 2011-01-06
So backup is running smooth now. Why it is that I must tranfer more then one folders in order to get subfolders included I dont know. 

When I get dsl line connected again I will update xubuntu box and reinstall samba. Guess that will solve this mystery once and for all.

---

### Post by CharlesA on 2011-01-06
Good luck. I think it might have to do with the way FTP is set up, but I'm not sure. I can transfer one folder at a time with filezilla with no problems.

---

