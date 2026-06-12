---
title: "Mi Ubuntu has gone nuts!!"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by jorge ortega on 2009-02-06
Please, help.

Ubuntu has gone mad, when i try to get into the suitch-off menu it takes me to the logoin scree but before it freezes and complains about my display not being comosed!? (or something like that). When I try to log in after way too long another pop up shows: 
*"an error occurred while loading or saving information for Encryption Key Agent (Seahorse)|*
[I]"After one or two minutes another two windows:
an error occurred while loading or saving configuration information for x-sesion-manager. Somo oif your configuration settings may not work properly."[/I] and also:
[I]
"Some thing, such as themes, sounds, or background settings may not work correcty.
The las error message was:
Failed to connect to socket/tem/dbus-XHYLWbQbp9
Gnome will still try to restart the SettingsDaemon next time you log in."[/I]
After this I am in and everything seems normal!!

---

### Post by jorge ortega on 2009-02-06
I should have said I also lost my wireless connection (although this happens regularly to me)

---

### Post by jorge ortega on 2009-02-06
Uff, that doesn't sound OK to me, I hope someone will know something?

---

### Post by terrery on 2009-02-06
try some of the solutions psted here:

[http://ubuntuforums.org/showthread.php?t=780179](http://ubuntuforums.org/showthread.php?t=780179)

hope it will work for ya

cheers

---

### Post by jorge ortega on 2009-02-07
> **terrery said:**
> try some of the solutions psted here:

[http://ubuntuforums.org/showthread.php?t=780179](http://ubuntuforums.org/showthread.php?t=780179)

hope it will work for ya

cheers

Thanks for that. Following the advice i checked *home/me/.dbus* and it was owned by root. I changed that and lots of things improved. Still when logging in I encounter a note complaining about the gnome-settings-daemon. I found this in */usr/share/doc/* and I checked it: it is for Intrepid bun I'm on Hardy. This obviously happened when I briefly brought in Intrepid repositories to downloads Gtk-gnutella (the one for Hardy doesn't work). Although I changed the repos back to normal it has caused this problem. Synaptic does not give me the option to reinstall the daemon and i can't remove it to install it again because it would take away the whole gnome desktop. It seems that changing this document would solve the problem. Please, anyone know how I could do this? Aside from this document the actual binary has the path */usr/lib/gnome-settings-daemon/gnome-settings-daemon.*

---

### Post by Paqman on 2009-02-07
Can you create a new account and log in to it? Might be useful to see if we can isolate the problem to either settings in your home folder or the system side.

Go to System > Admin > Users & Groups to add a new user.

---

### Post by jorge ortega on 2009-02-07
> **Paqman said:**
> Can you create a new account and log in to it? Might be useful to see if we can isolate the problem to either settings in your home folder or the system side.

Go to System > Admin > Users & Groups to add a new user.

My girlfriend has other account in the computer and she has the same problem. I tried to do as you said and surprise!: It doesn't let me add another user, I put my password but it stays locked!?

---

### Post by jorge ortega on 2009-02-07
Please, anyone has a clue what to do other than reinstalling?

---

### Post by Tomatz on 2009-02-07
I think the problem is network manager hanging. Open a terminal and copy and paste the following text into the terminal:

```
sudo apt-get remove network-manager && sudo apt-get install network-manager
```

---

### Post by jorge ortega on 2009-02-07
> **Tomatz said:**
> I think the problem is network manager hanging. Open a terminal and copy and paste the following text into the terminal:

```
sudo apt-get remove network-manager && sudo apt-get install network-manager
```

Well that I did and it cut off the internet conection, I am writting this from my Windows partition. I can't reinstall the network manager because I need internet for that!! Plese someone to help!!

---

### Post by jorge ortega on 2009-02-07
Still with Windows, anyone there?

---

### Post by Tomatz on 2009-02-07
> **jorge ortega said:**
> Well that I did and it cut off the internet conection, I am writting this from my Windows partition. I can't reinstall the network manager because I need internet for that!! Plese someone to help!!

LOL didn't realise that you didn't have a network connection to start with :/

Sorry ;)

You can download the network manager here:

[http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager/network-manager_0.7~~svn20081018t105859-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager/network-manager_0.7~~svn20081018t105859-0ubuntu1_i386.deb)

Download it in windows put it in the root of **C:**. Then in ubuntu mount your windows partition and **double click** the **network-manager.deb**.

---

### Post by jorge ortega on 2009-02-07
> **Tomatz said:**
> LOL didn't realise that you didn't have a network connection to start with :/

Sorry ;)

You can download the network manager here:

[http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager/network-manager_0.7~~svn20081018t105859-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager/network-manager_0.7~~svn20081018t105859-0ubuntu1_i386.deb)

Download it in windows put it in the root of **C:**. Then in ubuntu mount your windows partition and **double click** the **network-manager.deb**.
I donwloaded it, went back to Ubuntu and didn't let me reach the Windows partition becase it doesn't take my password now. Any administrative action that requires a password I can't do (but I still can open Synaptic..)
Unless someone tells me something else to try now I need to know this:

     Can I reinstall Ubunto with the live CD on top of my existing Ubuntu (and if possible keeping files and configurations) and -of course- keeping my Windows partition as It is?
If so: HOW?

---

### Post by Tomatz on 2009-02-07
> **jorge ortega said:**
> I donwloaded it, went back to Ubuntu and didn't let me reach the Windows partition becase it doesn't take my password now. Any administrative action that requires a password I can't do (but I still can open Synaptic..)
Unless someone tells me something else to try now I need to know this:

     Can I reinstall Ubunto with the live CD on top of my existing Ubuntu (and if possible keeping files and configurations) and -of course- keeping my Windows partition as It is?
If so: HOW?

Put the .deb on a flash drive and install it from the flash drive.

---

### Post by Paqman on 2009-02-07
> **jorge ortega said:**
> 
     Can I reinstall Ubunto with the live CD on top of my existing Ubuntu (and if possible keeping files and configurations) and -of course- keeping my Windows partition as It is?
If so: HOW?

Yes, if you have a separate /home partition. Just reinstall opting for manual partitioning. Make sure you specify the right partition for your /home and DO NOT format it, then specify the right partition for / and select it to be formatted.

If you don't have a separate home you should back the entire contents of your /home folders onto removable media and you can reinstall them on the new system.

Either way, you might want to [automate reinstalling all your packages]("http://ubuntuforums.org/showthread.php?t=261366").

---

### Post by jorge ortega on 2009-02-07
> **Tomatz said:**
> Put the .deb on a flash drive and install it from the flash drive.

I did that, tried to install it and was told that it needed *libnm-glib0*which is a unresolvable dependency or something like that. I downloaded the library tried to install it in Ubunty and was told that a later version was already installed. I uninstalled this and installed the one I downloaded and still couldn't install the Network Manager.

[PHP]Yes, if you have a separate /home partition. Just reinstall opting for manual partitioning. Make sure you specify the right partition for your /home and DO NOT format it, then specify the right partition for / and select it to be formatted.

If you don't have a separate home you should back the entire contents of your /home folders onto removable media and you can reinstall them on the new system.

Either way, you might want to automate reinstalling all your package[/PHP]

I don't know if I have a Home partition I supose no because I did the automatic install. Idon't know how to do the manual install (remember on top of existing Ubuntu and respecting Vista). Could someone giveme foolproof instructions on how to do it. As I said I sue Hardy Heron

---

### Post by mkvnmtr on 2009-02-07
See if you can copy your user file to another external disk. Then when you install you can replace the important files in your new home file. Those are the ones you can't see like mozilla, Thunderbird or evolution and such. You should notice others that are important to you. This time when you install make a seperate home partition and you won't have a problem reinstalling in the future. I finally did it yesterday on one of mine and it will make it a lot easier. After the install I just replaced what I needed in my home partition and reinstalled the apps I use and it is just like the same os.

---

### Post by jorge ortega on 2009-02-07
I'm afraid I've finally reinstalled. Windows has survived and not sure how all (for what I can see) my home folder and different configurations too. I'm in the process of updating the 300 plus packages. Still to early to see that everything is OK but thanks to everyone that tried to help. I'll probably have to miss my system a few more times before I learn...

---

### Post by jorge ortega on 2009-02-07
The update is: my girlfriends account has disappeared and *users and groups* doesn't let me open another one for her. It says that *home directory* already exist as it should do. What can I do? I suppose I can't specify a different directory for her, can I?

---

### Post by cariboo on 2009-02-07
Have tried in a Applications-->Accessories-->Terminal:

```
sudo useradd -d /home/girlfriend <username>
```

where girlfriend is her home directory.

Jim

---

### Post by jorge ortega on 2009-02-07
Thanks for answering cariboo.
I have since found out that her folder is there still. If I go to HOME both names are there mine and hers, and I can reach her partition. Some how the connexion has been lost. I have done what you said anyway but no result.

---

