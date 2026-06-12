---
title: "a few setup questions"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by hellomcfly on 2011-02-03
hey all, i'm new to ubuntu, although somewhat familiar with linux from messing around on the moto droid, trying to make the switch from windows 7 on my laptop. there are a few things i'd like to try to set up here and i'm wondering if they are possible.

first off: i have a desktop pc running xp where i store the majority of my music. is there a way to have a media player on the ubuntu machine scan a network folder and automatically add this music to the library? in win7, i have the network folder symbolically linked to a local folder, and winamp is able to scan this and add the files to the library. is there some way to mimic this type of thing in ubuntu?

also, i use the gmail notifier in win7 as sort of a shortcut to my gmail, in that when i click the envelope icon in the taskbar, it will open chrome with my account already logged in.  in ubuntu, i have check gmail set up, and it will open the gmail page in chrome with my username saved, but i have to log in every time.  is there any way to get around this?

any help is greatly appreciated!

---

### Post by dirghrabadia on 2011-02-03
Hi, welcome to the forums :)
 
Yes, you would be able to access your Music on XP through Samba ([http://www.samba.org/samba/](http://www.samba.org/samba/)).
 
And for your Gmail set-up, there is a Gmail Notifier for Linux ([http://gmail-notify.sourceforge.net/index.php](http://gmail-notify.sourceforge.net/index.php)). Hope that helps!

---

### Post by candtalan on 2011-02-03
The default media player in Ubuntu is rhythmbox, but there are others you can use.
I see that rhythmbox has 

Edit>preferences>(Browse music files location)
I guess you will need to arrange for the particular folder/s to allow sharing.

and
The Ubuntu main menu has
Places>Network>(windows network)

good luck

---

### Post by hellomcfly on 2011-02-03
thanks for your responses! i have tried the gmail notifier, and it works, it just will not launch the browser with my account signed in. it forces me to put in my password every time. i'm not sure if this is a chrome setting i have incorrect, but it's odd because if i type gmail.com into the browser or go from a bookmark, i will be signed in. 

i have samba installed in order to share my ubuntu files with my xp pc, which works fine, but should i have samba installed on xp in order to share files the other way around? right now i can see my xp pc on the network, but if i try to access it, i get the error "unable to mount location."

---

### Post by candtalan on 2011-02-03
> **hellomcfly said:**
>  right now i can see my xp pc on the network, but if i try to access it, i get the error "unable to mount location."

My guess is that the XP location is not yet set for sharing. For example
the folder needs to be set  to share
You will probably need to run the network wizard to  arrange sharing in the PC
after that the folder properties will  need to be changed to allow it to be shared on the network (Foldername Properties) 'network sharing and security', share this folder on the network (tick).

Hope that will help, I am not fluent about this, I do not use Windows anymore....

---

### Post by TechWiz2100 on 2011-02-03
How is your XP machine set up to sharing?

Is it SAMBA (shared folder) or
Media share (Windows Media Player/Center)

This is important because neither are not accessed the same way.

---

### Post by candtalan on 2011-02-03
> **candtalan said:**
> My guess is that the XP location is not yet set for sharing. For example
the folder needs to be set  to share
You will probably need to run the network wizard to  arrange sharing in the PC
after that the folder properties will  need to be changed to allow it to be shared on the network (Foldername Properties) 'network sharing and security', share this folder on the network (tick).

Hope that will help, I am not fluent about this, I do not use Windows anymore....

Ah! and not least, your XP machine firewall should be doing its stuff and blocking any sharing activity.... (probably silently), so when you think it *should* be all working but it is not, maybe disable the firewall?

edit:
also istr that the xp machine may need to be set to use a startup password, and not log in automatically. Not sure why, I think it was something to do with the ID and sign on for sharing stuff.

---

### Post by hellomcfly on 2011-02-03
i have the folder set to share through "sharing and security" just as a regular shared folder, not a media share. i know it works with another windows pc because i'd had it set up with win7 previously. i tried disabling the firewall as well and still get the same error.

---

### Post by TechWiz2100 on 2011-02-03
For proper SAMBA connection Places > Connect to Server and select Windows Share from the drop box then enter your XP machine's IP address into the server edit box

To get your IP in XP press Win key + R and type CMD then press enter
in the command prompt type in "ipconfig" and look for the IP address of your network adapter

---

### Post by candtalan on 2011-02-03
> **hellomcfly said:**
> i have the folder set to share through "sharing and security" just as a regular shared folder, not a media share. i know it works with another windows pc because i'd had it set up with win7 previously. i tried disabling the firewall as well and still get the same error.
I just tried a test xp sp2 pc and it connected to Ubuntu 10.04.1 ok, after a lot of xp restarts etc, (btw network stuff does seem to need restarts unless you know exactly which processes to manage and how to) but one thing I seemed to have no choice about was to have to run the xp network wizard when initially viewing the xp folders properties, it just appeared. The workgroup also seemed to be important, and the default name was either WORKGROUP or XPHOME, and I guess it had to be correct. Stopping the XP firewall seemed to finally do the trick, although I think I had to enter the XP password when requested at the ubuntu PC. Not sure it had got a bit confusing by then.

---

### Post by TechWiz2100 on 2011-02-03
Workgroups are generally worthless which is why they were mostly removed in Vista/7 in favor of Bonjour style DNS multicast services. What you really want to do is connect to the server via SAMBA with an IP since XP didn't have service broadcasting yet. On windows 7 it would be located in the network folder because Windows would send a Multicast packet out looking for services and telling the world so to speak that it was hosting services if any. Since Windows XP lacks this feature unless you are running Media Center or iTunes, you have to manually enforce where the connection is to be made by means of IP.

---

### Post by hellomcfly on 2011-02-03
> **TechWiz2100 said:**
> For proper SAMBA connection Places > Connect to Server and select Windows Share from the drop box then enter your XP machine's IP address into the server edit box

To get your IP in XP press Win key + R and type CMD then press enter
in the command prompt type in "ipconfig" and look for the IP address of your network adapter

it was as simple as that! thanks!

---

