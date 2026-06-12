---
title: "How to get back to GNOME desktop?"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by Vladimir Pavic on 2011-07-06
[COLOR=#355e00]**Dear friends, **[/COLOR] 
 [COLOR=#355e00]**Somebody installed yesterday Kubuntu over my Ubuntu 11.04. (just to test it how it works.) As I do not like it I want to go back to my GNOME Ubuntu desktop. I followed instruction which I found on Internet (Get back to pure GNOME Ubuntu), but the command doesn't work. What to do? Do I have to uninstall Linux and reinstall Ubuntu? If so, how to uninstall it? **[/COLOR] 
 

 [COLOR=#355e00]**Thank you. **[/COLOR] 
 

 [COLOR=#355e00]**Vladimir**[/COLOR]

---

### Post by jtarin on 2011-07-06
> I followed instruction which I found on Internet
Link to the instructions you followed.

> If so, how to uninstall it? 
Do you have any other operating systems on that drive?

---

### Post by mastablasta on 2011-07-06
did you follow this guide?: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
 
paste the command in terminal. the whole command. also what version of Ubuntu are you using?

---

### Post by ajgreeny on 2011-07-06
> **Vladimir Pavic said:**
> [COLOR=#355e00]**Dear friends, **[/COLOR] 
 [COLOR=#355e00]**Somebody installed yesterday Kubuntu over my Ubuntu 11.04. (just to test it how it works.) As I do not like it I want to go back to my GNOME Ubuntu desktop. I followed instruction which I found on Internet (Get back to pure GNOME Ubuntu), but the command doesn't work. What to do? Do I have to uninstall Linux and reinstall Ubuntu? If so, how to uninstall it? **[/COLOR] 
 

 [COLOR=#355e00]**Thank you. **[/COLOR] 
 

 [COLOR=#355e00]**Vladimir**[/COLOR]
It will depend on what you mean by [COLOR=#355e00][B]"Somebody installed yesterday Kubuntu over my Ubuntu 11.04".

[/B][COLOR=Black]If they really installed it over 11.04 gnome ubuntu, you will either need to add ubuntu-desktop to your kubuntu install and then remove KDE with the link shown by mastablasta, or you will have to install again from scratch.[/COLOR][COLOR=Black]If all they did was install kubuntu-desktop on top of ubuntu, that link should work without problem.[/COLOR]
[/COLOR]

---

### Post by Perkins on 2011-07-06
There are two possibilities here:

1:  Somebody did a complete install of Kubuntu, wiping out Ubuntu.
2:  Somebody installed the kubuntu-desktop package.

In the latter case, at the login screen, there should be a box somewhere to let you choose your session.  Choose gnome.

In the former case, either reinstall Ubuntu from scratch, or install the ubuntu-desktop package, and then follow the solution for option 2.

---

### Post by stlsaint on 2011-07-06
Did you install the entire OS of kubuntu or just the kde metapackage?? If you installed over ubuntu with full kubuntu then i wuold suggest a complete re-install of ubuntu to get rid of all remnants of kubuntu.

---

### Post by Vladimir Pavic on 2011-07-07
Dear friends. 
You were right. 'Somebody' (my friend) actually did a complete install of Kubuntu, which I didn't know. Now, how to uninstall it? Reinstallation of Ubuntu shouldn't be a problem even for me. I have it on a CD. 
Thank you all for help. Without your suggestions I would have thought that he he only installed KDE metapackage.

---

### Post by nzjethro on 2011-07-07
If it's full Kubuntu, you have two options.

1) Uninstall Kubuntu, and reinstall Ubuntu. To do this, put your CD in the drive and restart your computer. It should boot to the CD, which will give you the option to install Ubuntu. Go through the installation process, and choose "Something Else" for your partition choice. Then, delete you Kubuntu partition, and create a new partition in the "unallocated space" (formatted as ext4) to install Ubuntu to. This method will completely remove Kubuntu, and replace it with a fresh install of Ubuntu, so make sure any files you want saved are backed up first.

2) Run the command
```
sudo apt-get install ubuntu-desktop
```
Then, log out, and on the bottom toolbar select "Ubuntu Session" when you log back in. This method will install Gnome over Kubuntu, so that you can choose between Gnome and KDE on login. The downside is that KDE and Gnome will occasionally not agree on certain config issues, so it may take you a while to get your preferences working how you like them.

---

### Post by mastablasta on 2011-07-07
> **nzjethro said:**
>  
2) Run the command
```
sudo apt-get install ubuntu-desktop
```
Then, log out, and on the bottom toolbar select "Ubuntu Session" when you log back in. 
 
and then you follow the link i gave before - it will remove Kubuntu-desktop and all applications connected wiht it leaving you with pure Gnome (i.e. Ubuntu)

---

