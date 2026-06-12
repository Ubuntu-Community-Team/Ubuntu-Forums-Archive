---
title: "Java Install problem on Wine"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by Tatariw on 2009-07-13
Hellos everybody!
 I tried Ubuntu about two years ago for some days, but went back to windows for some reason. Now I've come back to the Ubuntu world and using Ubuntu for some ten days, it feels right! See now that the Ubuntu community is growing fast.  
 

 I have question though, some applications at my work place are depend on IE6 and specific Java ver.   
 I need IE6 just for these application to work. After installing IE6 on Wine, IE6 keeps closing ever time I try to open the application. The problem is that j2re-1_4_2_15-windows-i586 was not properly installed. This is the allowed Java ver for this application.  I have been searching around to find a solution with no real result.
 

 Any suggestion will be appreciated.
 Greetings
 Tatariw

---

### Post by HotShotDJ on 2009-07-13
A quick search turned up the following (see comment #10 in the linked thread):  [http://ubuntuforums.org/showthread.php?t=298910](http://ubuntuforums.org/showthread.php?t=298910)

NOTE:  I have not done this myself, so I can't personally vouch for the method.  If you try it, please post back and let us know if it worked or not.

---

### Post by Troll_the_Great on 2009-07-13
Did you install the windows version on IE 6? There is a program called ie4linux, maybe it will work better for you. You can find it here:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
Hope this helps.
Cheers!

---

### Post by Tatariw on 2009-07-13
Hi,

I have installed ies4linux. Am working on the process link HotShotDJ has sent. 
The thing again is that I can not locate the drive_c (it is not there) at home folder to add advpack.dll file.  It is hiding some place?

Thanks again!

---

### Post by IHeequ5i on 2009-07-13
The drive_c folder is in a hidden folder called .wine in your home directory.

EDIT:  Example - mine is in /home/doomspark/.wine

---

### Post by Tatariw on 2009-07-13
Hi,
Every folder under my /home/myuser/ does not contain a folder named .wine (no wine folder here at all). Should I remove and install wine, ie4linux etc from add/remove again? 

Thanks again!

---

### Post by 45acp on 2009-07-13
The .wine folder is a hidden folder. If you are using nautilus hit ctrl h. to show hidden files.

---

### Post by Tatariw on 2009-07-13
Than you, 
The .wine folder is now located and I can paste the advpack.dll file on system32 folder.
The advpack was already there, overwrited. Choosing advpack.dll from wine configuration again and a new install of Java did not give any solution.  Installation of Java is interupted, because there is an error on patchjre.exe file. 

And another thing is that the currupt installation of Java in wine can't be uninstalled.  

Thanks for your follow ups folks!!!

---

### Post by HotShotDJ on 2009-07-13
> **Tatariw said:**
> Installation of Java is interupted, because there is an error on patchjre.exe file. 

And another thing is that the currupt installation of Java in wine can't be uninstalled.The cool thing with Wine is that you can start out fresh simpy by deleting the .wine directory in your home folder (you can even create "wine bottles" for different applications, but lets not get into that right now).  That is what I would do at this point.  I suspect that the initial bad install of Java may be contributing to your problem.

Go ahead and drag the .wine directory to your trash bin, and then start again.  Get IE installed, and then follow the link I gave you above and try to install Java.  If there are any errors, make sure you post them.  There were several packages from Microsoft that I had to install in WINE before I could get some software to run (mostly involving VB 6), and it was the error messages from Wine that helped me track down the issues.

If you continue to have problems, let me know and I'll see if I can replicate them on my system.  What version of Wine do you have installed? (Applications -> Wine -> Configure Wine and click on the "About" tab)

---

### Post by HotShotDJ on 2009-07-13
Ok -- I've successfully installed IE6 + Java 1.4.2_19.  Tested at [http://java.sun.com/products/plugin/1.4/demos/plugin/applets.html](http://java.sun.com/products/plugin/1.4/demos/plugin/applets.html) (many java sites do NOT work, as they require newer version of Java)

1) Deleted my .wine directory (actually, I just moved it out of the way)
2) Used Winetricks```
wget http://www.kegel.com/wine/winetricks
sh winetricks
```
3) Using Winetricks,installed:
[LIST]
[*]ie6
[*]allfonts
[*]d3dx9
[*]wininet
[/LIST]
4) Installed Java 1.4```
wine j2re-1_4_2_19-windows-i586-p.exe
```
5) Simulated a Windows reboot (for good measure)```
wineboot
```
6) Ran IE6 and tested some java 1.4 applets at the above listed website```
wine ~/.wine/drive_c/Program\ Files/Internet\ Explorer/iexplore.exe
```

NOTE:  
[LIST]
[*]Wine Version: 1.0.1 (from standard Jaunty repository)
[*]Winetricks Version 20090705
[*]Java install file: j2re-1_4_2_19-windows-i586-p.exe
[/LIST]

---

### Post by Tatariw on 2009-07-15
Thank you for the very detailed how-to-do advice. I am working on it and will be back to let you know the result. Insted of j2re-1_4_2_19-windows-i586-p.exe, the application requires and includes j2re-1_4_2_15-windows-i586-p.exe which I allready have locally. May be there is not much defference but I will try to test both.
   
  Thanks

---

### Post by Tatariw on 2009-07-17
Got several error lines in the process when wineboot and starting IE6. 
[I]ie6 tries to open the remote location application but then stops. (finds the location and then page not found). 

Now, I can not even get into the starting page to that application. Before, I could use ie6 on that application as long as I try not to open the part that requires [/I]j2re-1_4_2_15.....
Am not sure how to fix this. Thanks so far!!

Am using win XP when using this part of job. And then go back to Ubuntu for other and more tasks. Have started to use Ubuntu home as well. Reaaly like Ubuntu! 

Greetings

---

### Post by HotShotDJ on 2009-07-17
> **Tatariw said:**
> Got several error lines in the process when wineboot and starting IE6. 
[I]ie6 tries to open the remote location application but then stops. (finds the location and then page not found).Unfortunately, I'm not able to help you debug this because I don't know what java application you are trying to run, and therefore I can't replicate the issues you are having on my system.  I'm honestly very surprised that you are unable to run that application using more modern versions of Java.  I was under the impression that Java 5 and 6 are backwards compatible with applications written under older versions of Java.  BUT, having said that, I have seen some applications that run nicely under Java 5 but throw fits under Java 6.

Where I work, there are a few things for which I need Windows (although, much to the chagrin of our Microsoft-Only ITS department, most things I can do just fine under Linux!).  For those, I use VirtualBox in which I have an XP Professional virtual machine. That way, I don't have to reboot to get to Windows XP.  It rather impresses my co-workers.  I'll often have a virtualized XP session running full screen on one desktop, and then I use the spinning cube to return to my Gnome desktop.  It can also be run in windowed mode (screen shot) or, if you don't mind giving up the compiz-fusion effects, you can run your XP session in seamless mode (screen shot)

---

### Post by HotShotDJ on 2009-07-17
I almost forgot -- here is a screen shot using full screen (spinning on the cube).

---

### Post by Tatariw on 2009-07-20
That is really impressive HotShotDJ. I appreciate your effort and thank you I must add.
 

 As for my case and as mentioned earlier the application I am having problem is at remote location (across a network). The application with j2re-1_4_2_15-windows-i586-p.exe (works only with this java ver) we are talking about is installed on a PC which runs under MS win Server 2003, used for supervision of devices from different locations. Since am working with other server PCs, I can just plug in anywhere in the network with my Ubuntu laptop and have contact with those servers/applications. Please keep in mind that the other servers run on win, Linux and UNIX. All are fine except the one we talk about. I do not thing it is a firewall thing.
 

 Lately, have tried to solve the problem by using Remote Desktop Viewer from Ubuntu. It works fine but this is not ideal since others are also working on the same server. You will be interrupted or no privacy etc. You will also be depending on how many users the server allows to use the same desktop at the same time. The funny thing is that it is only a tiny but important part of that application that needs j2re-1_4_2_15-windows-i586-p.exe that puzzles me. I feel silly in this regard.  
 

 Can you tell me if VirtualBox is fast enough? Is it secure? Of course I have to read to know more about it. Just need to know your experience about it before jumping.     
 

 Greetings!

---

### Post by HotShotDJ on 2009-07-20
> **Tatariw said:**
>  Can you tell me if VirtualBox is fast enough? Is it secure? Of course I have to read to know more about it. Just need to know your experience about it before jumping.Regarding the speed, it will depend on your system, mostly the amount of physical RAM available.  On my system, I have a total of 2 gig RAM.  When I run VirtualBox, I give the virtual machine 1 gig of that.  My virtualized XP sessions run at near-native speed.  However, Vista is noticeably sluggish (however, I've never run Vista natively on any computer, so I really have no point for comparison).  Also, your CPU may or may not support hardware virtualization.  Mine does not.  If yours does, this could improve performance as well.

As far as security is concerned, running XP in VirtualBox should not be any more or less secure than running it natively.

In any case, I have been using VirtualBox for several years with no issues other than problems that are part of running Windows in general. Virtualization has become a very common practice and is well tested in "the real world."  There really is no need for you to be concerned.

---

### Post by Tatariw on 2009-07-28
I am sorry for late reply, but am using VirtualBox for several days now. The java thing on Wine is still on the back of my head. My problem is lost though. It is nice that VirtualBox is well documented as well.   

I thank you!!!

---

