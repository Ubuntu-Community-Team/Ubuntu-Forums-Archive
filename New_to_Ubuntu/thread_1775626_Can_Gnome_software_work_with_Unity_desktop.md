---
title: "Can Gnome software work with Unity desktop?"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by ILoveYorkies on 2011-06-05
[SIZE=2]Hi,
I'm new to Linux, so I have a lot of questions but here's a couple of them.
I've been looking at games and I[/SIZE] t[SIZE=2]hink I found a Bejeweled like game but it says it's for Gnome, I'm  running Natty with the default Unity desktop. Anybody know if it would  work? Also I love playing games on pogo.com but I can't in Natty because I need Java or a Java like  plug-in for Firefox. I don't know how to install plug-ins in general yet nor which version of Java to install for Natty with Unity desktop. This is Pogo's page for Linux download:[/SIZE]Java Plug-in                   In order to play games on Pogo.com, you'll need to install the Java plug-in.                                 
        [IMG]http://java.com/en/inc/cobrand/images/java-logo_80.gif[/IMG]         
        **FREE - Java Plug-in**
**Version 6 Update 25 ** 

To complete the download of the Java Runtime Environment, please select from the list below.         By downloading Java you acknowledge that you have read and accepted the terms of the [end user license agreement]("http://www.oracle.com/technetwork/java/javase/terms/license/")
  
 
            
[SIZE=2]Could someone explain step by step please. Any help will be appreciated.

Using Ubuntu 11.04 with Unity, on an HP Pavilion DV6 model 2157 Win 7 64 bits, also on Acer AOA 150 XP 32 bits.
[/SIZE]

---

### Post by wildmanne39 on 2011-06-05
> **ILoveYorkies said:**
> [SIZE=2]Hi,
I'm new to Linux, so I have a lot of questions but here's a couple of them.
I've been looking at games and I[/SIZE] t[SIZE=2]hink I found a Bejeweled like game but it says it's for Gnome, I'm  running Natty with the default Unity desktop. Anybody know if it would  work? Also I love playing games on pogo.com but I can't in Natty because I need Java or a Java like  plug-in for Firefox. I don't know how to install plug-ins in general yet nor which version of Java to install for Natty with Unity desktop. This is Pogo's page for Linux download:[/SIZE]Java Plug-in                   In order to play games on Pogo.com, you'll need to install the Java plug-in.                                 
        [IMG]http://java.com/en/inc/cobrand/images/java-logo_80.gif[/IMG]         
        **FREE - Java Plug-in**
**Version 6 Update 25 ** 

To complete the download of the Java Runtime Environment, please select from the list below.         By downloading Java you acknowledge that you have read and accepted the terms of the [end user license agreement]("http://www.oracle.com/technetwork/java/javase/terms/license/")
  
 
            
[SIZE=2]Could someone explain step by step please. Any help will be appreciated.

Using Ubuntu 11.04 with Unity, on an HP Pavilion DV6 model 2157 Win 7 64 bits, also on Acer AOA 150 XP 32 bits.
[/SIZE]
Hi, yes you can run things that say for gnome. Go to the software center and install java from there, if it asks for your to accept an agreement do it and it will install.

---

### Post by ILoveYorkies on 2011-06-05
Good Morning,
Thanks for the reply.

---

### Post by Paqman on 2011-06-05
Unity is built on top of Gnome. You should have no problems, especially for a Java app.

---

### Post by oldfred on 2011-06-06
The instructions you have for Pogo are very old and for Redhat as they suggest .RPM files not .DEB. It also mentions the 2.2 kernel which now is very old.

I though the standard install included openjdk and icetea files. Look in synaptic and search if a group of related files with openjdk & icetea are installed.

I used to install the SUN version but changed to the openjdk and have not had issues with anything I do, but I have not tried your games.

I hesitate to suggest the Oracle version if you have the Openjdk installed as whenever I install applications that may conflict I get into more trouble and sometimes have issues uninstalling one or the other.

---

### Post by ILoveYorkies on 2011-06-10
Hi ,
Thanks Old fred, I finally found the Icetea pliugin and openjre that  helped. but it wasn't easy figuring out which java to install.  I still  can't play the games on Pogo, Firefox complains that I'm missing  plugins. I think it might be SWFplugin I'm missing but I can't find any  kind of SWF plugin for Linux not even open source. Adoble's SWF says  it's for Win or Mac, no option for any kind of Linux. Too new or too  dumb to program or compile my own. Any other ideas?

Oh, by the way I did download Gweled and it's just like Bejeweled. Great  game, maybe too addictive though. I'm having a hard time quitting it,  it's like eating one bite of chocolate. LOL!

Anybody here play on  GGZ Gaming Zone? If you do, do you recommend it?
Thanks for any more help you guys can offer

---

### Post by wildmanne39 on 2011-06-10
> **ILoveYorkies said:**
> Hi ,
Thanks Old fred, I finally found the Icetea pliugin and openjre that  helped. but it wasn't easy figuring out which java to install.  I still  can't play the games on Pogo, Firefox complains that I'm missing  plugins. I think it might be SWFplugin I'm missing but I can't find any  kind of SWF plugin for Linux not even open source. Adoble's SWF says  it's for Win or Mac, no option for any kind of Linux. Too new or too  dumb to program or compile my own. Any other ideas?

Oh, by the way I did download Gweled and it's just like Bejeweled. Great  game, maybe too addictive though. I'm having a hard time quitting it,  it's like eating one bite of chocolate. LOL!

Anybody here play on  GGZ Gaming Zone? If you do, do you recommend it?
Thanks for any more help you guys can offer
HI, to get all your media needs taken care of you can go here and follow the directions, go all the way to the bottom becasue there a things to install all through out the page. I am sure that the swf you talked about is included in the packages you will install on that page, at least they were before natty.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) I just checked out pogo and I can play the games with fire fox, I use that page that I gave you to set up my system, also open fire fox and click on tools and add ons then search for and install flashaid it will fix flash problems for you just follow the instructions. Do this first then you might not have to do what i mentioned first with the links.

---

### Post by ILoveYorkies on 2011-06-12
> **wildmanne39 said:**
> HI, to get all your media needs taken care of you can go here and follow the directions, go all the way to the bottom becasue there a things to install all through out the page. I am sure that the swf you talked about is included in the packages you will install on that page, at least they were before natty.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) I just checked out pogo and I can play the games with fire fox, I use that page that I gave you to set up my system, also open fire fox and click on tools and add ons then search for and install flashaid it will fix flash problems for you just follow the instructions. Do this first then you might not have to do what i mentioned first with the links.

Hi everyone,
This is an update. I have installed Icetea6-plugin, Icetea-plugin, Icetea-netx, etc. Openjre such as openjdk-6-ire, openjdk-6-jre-lib, flashplugin-installer according to Synaptic Manager (see attachments for full list).  With these I can play most games on Yahoo but I still can't play games on Pogo. I can choose a game, pick a room and it says game loading while showing an ad which is clickable. But it never gets past the game loading screen. Also at the bottom of the loading screen it says applet started, within a few minutes firefox then crashes.

I have installed Flash-Aid too. What about my installing this one named Moonlight-plugin-mozilla? Should I try it? Or should I try what Wildmanne39 suggests?
Thanks for the help so far and anymore that anyone can offer.

---

### Post by oldfred on 2011-06-12
Do not know about the issues with games. It seems like it just needs the basics. Moonlight is much newer. 

Have you installed the complete ubuntu-restricted-extras? I think that is a meta-package that is what the check during install includes and then it should have installed all the other packages you were missing.

---

### Post by wildmanne39 on 2011-06-12
> **ILoveYorkies said:**
> Hi everyone,
This is an update. I have installed Icetea6-plugin, Icetea-plugin, Icetea-netx, etc. Openjre such as openjdk-6-ire, openjdk-6-jre-lib, flashplugin-installer according to Synaptic Manager (see attachments for full list).  With these I can play most games on Yahoo but I still can't play games on Pogo. I can choose a game, pick a room and it says game loading while showing an ad which is clickable. But it never gets past the game loading screen. Also at the bottom of the loading screen it says applet started, within a few minutes firefox then crashes.

I have installed Flash-Aid too. What about my installing this one named Moonlight-plugin-mozilla? Should I try it? Or should I try what Wildmanne39 suggests?
Thanks for the help so far and anymore that anyone can offer.
Hi, one thing I forgot to mention if you have noscript enabled in firefox you need to set it to allow Pogo or it will block it from playing games.

---

