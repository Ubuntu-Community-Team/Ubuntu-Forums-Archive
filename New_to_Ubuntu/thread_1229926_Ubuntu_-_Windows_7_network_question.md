---
title: "Ubuntu - Windows 7 network question"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by serbforce on 2009-08-02
Hello
I have 2 PCs one running Ubuntu 9.04 other Windows 7 beta.
My question is how can i access files from Ubuntu ext3 partitions from Windows 7.
Other way around was very easy to setup with Samba.

Tyvm in advance

---

### Post by alphacrucis2 on 2009-08-02
> **serbforce said:**
> Hello
I have 2 PCs one running Ubuntu 9.04 other Windows 7 beta.
My question is how can i access files from Ubuntu ext3 partitions from Windows 7.
Other way around was very easy to setup with Samba.

Tyvm in advance

Samba has both client and server components. In Ubuntu just right click on the folder you want to share in Nautilus and select sharing options. Windows 7 will be able to see the shared folder.

---

### Post by Revolutionary101 on 2009-08-02
No I don't think you will be able to read the Ubuntu files from Windows 7 because Windows can not read ext3 formatted hard drives.

---

### Post by alphacrucis2 on 2009-08-02
> **Revolutionary101 said:**
> No I don't think you will be able to read the Ubuntu files from Windows 7 because Windows can not read ext3 formatted hard drives.

Well it can actually using available utilities you can download. However he appears to be running Ubuntu and Windows on different machines so the file system isn't relevant. Samba makes whatever file system Linux is using look like a normal Windows file share to the Windows client.

---

### Post by serbforce on 2009-08-02
Yes i am using Ubuntu and Windows on different machines.
Could someone please clarify how can i use samba to view Ubuntu files from Windows?

---

### Post by alphacrucis2 on 2009-08-02
> **serbforce said:**
> Yes i am using Ubuntu and Windows on different machines.
Could someone please clarify how can i use samba to view Ubuntu files from Windows?

I already told you. Start Nautilus by clicking on Places - Home from the Ubuntu menu. Select the folder you want to share and right click on it and select sharing options. You can specify whether you want to allow guest access or require the Windows side to have to enter a valid Ubuntu usercode and password to connect. You can also specify read only or read/write access etc.

---

### Post by serbforce on 2009-08-02
Ok thanks guys , i just had to access Ubuntu's ip in windows explorer and map.

---

### Post by powel212 on 2009-08-02
1.) install system-config-samba
```
sudo apt-get install system-config-samba
```
2.) configure system-config-samba
```
sudo system-config-samba
```
click add folder - make it writable and visable and under access make it accessible to all users to let the windows box access this new share folder.

3. under preferences\security change auth mode to "share"
then change the guest account to your ubuntu user name and you are done.

Don't need to logout or reboot.

I use this configuration to share files between linux - windows 7 - vista - xp - OSX

ps - when you right click a folder in nautilus as mentioned above you are using the "share folder" control structure and it is not as comprehensive as system-config-samba so you may find it a little troublesome sometimes. system-config-samba is best but a little more difficult to get set-up initially. If you follow the steps above it will work perfectly though.

I hope that helps

Powel

---

### Post by Volume on 2009-08-04
Thanks for the info Powell.  How do I get Windows to "see" the share?  I am using Vista, and trying to move some files from Vista to Ubuntu.

---

### Post by powel212 on 2009-08-05
Sorry for the late reply. I am in Taiwan so our time is a bit different.

Once system config samba is installed you can configure it by going to "system\administration\samba"

Then check the attached photos to see how I have mine configured. note: where you see "drock" in my setup please substitute your own user name.

also attached is my vista network config setup. Vista is a bit pesky to get set up initially but it is designed to run as a server so it works quite well once it is setup correctly.

Let me know if you have any other questions or something doesn't work.

Powel

---

### Post by Volume on 2009-08-05
> **powel212 said:**
> Sorry for the late reply. I am in Taiwan so our time is a bit different.

Once system config samba is installed you can configure it by going to "system\administration\samba"

Then check the attached photos to see how I have mine configured. note: where you see "drock" in my setup please substitute your own user name.

also attached is my vista network config setup. Vista is a bit pesky to get set up initially but it is designed to run as a server so it works quite well once it is setup correctly.

Let me know if you have any other questions or something doesn't work.

Powel

Thanks!  Everything looks the same on the lLinux side, but the problem I have is in Vista.  My network map does not say "Multiple Networks", just a single network.

Any suggestions on how to fix that?

Steve

---

### Post by powel212 on 2009-08-05
Ubuntu Linux does not auto announce itself on the network so you first need to access the windows share from Ubuntu then the router will give the Ubuntu box an address that the windows machine can then see. Does that make sense? Let me know if it doesn't show up.

Powel

---

### Post by Volume on 2009-08-05
> **powel212 said:**
> Ubuntu Linux does not auto announce itself on the network so you first need to access the windows share from Ubuntu then the router will give the Ubuntu box an address that the windows machine can then see. Does that make sense? Let me know if it doesn't show up.

Powel

I was able to add all of my machines on the router (netgear, via routerlogin.net) but I still cannot see the Linux machine on the Windows machine. I have setup the Samba config as I was suggested, but I still get errors even on the linux box trying to access the windows machine...

Whadya think?

Steve

---

### Post by powel212 on 2009-08-06
Okay that is odd.

Can you give me some details on your network setup?

Should be something like this.

win-->router-->
................................-->Router-->dsl,broadband,dialup box-->internet
Linux-->router-->

attached is a diagram.

as a note you can have more than one switch or hub but you can only have one router per network and you must have at least one router. a switch or a hub will not work, (using DHCP), without a router.

does this make sense?

---

### Post by powel212 on 2009-08-06
Another note.

Most home setups include the DSL box provided by your isp and a router you bought yourself. But you don't need a switch or a hub unless you have many machines. I have a 20 port switch because I have 5 computers and i build them so I often have a lot more than that running at the same time.

If you only have the DSL box provided by your isp and not your own router that could be the problem because many isp provided boxes act as AP and not router. 

Let me know some more specifics of your network setup and actual hardware and I can narrow down the problem.

I hope that helps

powel

---

### Post by Volume on 2009-08-06
> **powel212 said:**
> Okay that is odd.

Can you give me some details on your network setup?

Should be something like this.

win-->router-->
................................-->Router-->dsl,broadband,dialup box-->internet
Linux-->router-->

attached is a diagram.

as a note you can have more than one switch or hub but you can only have one router per network and you must have at least one router. a switch or a hub will not work, (using DHCP), without a router.

does this make sense?

Makes perfect sense.  Where you have "router" I have a Netgear wireless router with 4 hardwire ports on them.  My setup is essentially how you have laid it out in the diagram, but I have 2 linux boxes, and one windows system.  I am using the hardwire, not the wireless.

Does this help?

---

### Post by powel212 on 2009-08-06
I am sorry you have got me beat. Based on the info it looks to me like it should be working. I don't know what to tell you at this point. 

Powel

---

### Post by Volume on 2009-08-06
> **powel212 said:**
> I am sorry you have got me beat. Based on the info it looks to me like it should be working. I don't know what to tell you at this point. 

Powel

No worries, thank you for sticking it out for this long!  I'll make sure and post if I hear anything else

Steve

---

### Post by awarre on 2009-11-15
had to register just to say  Thank You powel21!!
just got win7 to replace OS X{ hardware failure}and was tearing my hair out trying to remember how I got Kubuntu, XP, 98,  and OS X to play nice previously.Mostly stumbled on kludges that sorta worked but this worked immediatly and completely didn't have to re boot Win boxes even !! Why is such important info hidden ??Thank You again kind sir .

---

