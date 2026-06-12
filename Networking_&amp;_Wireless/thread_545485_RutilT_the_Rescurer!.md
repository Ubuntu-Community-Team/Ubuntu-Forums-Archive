---
title: "RutilT the Rescurer!"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by sulligogs on 2007-09-07
To Everyone,

I have my Edimax EW-7128g wireless network card running successfully for weeks now with Ubuntu Feisty Fawn.  I am using a static IP network and would like to share how I got my card, which uses the  RT61 chipset, running flawlessly:-

[SIZE=4]1[/SIZE]) Uninstall Network Manager.  It's useless for you.  Go into Synaptic Package Manager and remove the following:-
[INDENT][FONT=Courier New][COLOR=Red]network-manager
network-manager-dev
network-manager-gnome[/COLOR][/FONT][/INDENT]Then, whilst in Synaptic Package Manager, install the following:-
[INDENT][FONT=Courier New][COLOR=Blue]libgtk2.0-dev
g++-4.1[/COLOR][/FONT][/INDENT][SIZE=4]2[/SIZE]) Download and extract the latest version of RutilT from [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/) to your desktop.

[SIZE=4]3[/SIZE]) Open up a terminal and change to the directory to the download on your desktop.  Enter in these commands:-

```
./configure.sh --launcher=nopasswd
make
sudo make install
```Enter your password if asked.

[SIZE=4]4[/SIZE]) Now, within the terminal, enter:-

```
sudo gedit /etc/network/interfaces
```Enter your password if asked.

[SIZE=4]5[/SIZE]) Append the following to the file you just opened (see 4):-[INDENT][FONT=Courier New]# RT61
auto ra0
iface ra0 inet static
address *[COLOR=Gray] your machine's desired ip address[/COLOR]*
netmask *[COLOR=Gray]usually 255.255.255.0[/COLOR]*
gateway *[COLOR=Gray]the ip address of your router[/COLOR]*[/FONT]
[/INDENT]Save the file and close the editor application.

[SIZE=4]6[/SIZE]) At the terminal enter the following:-

```
sudo nameserver *[COLOR=Gray]the ip address of your router[/COLOR]*>>/etc/resolv.conf
sudo route add default gw *[COLOR=Gray]the ip address of your router[/COLOR]*

```Enter your password if asked.  The two characters >> looking to the right actually mean "write to" a file or device.

[SIZE=4]7[/SIZE]) Reboot.  Click on Rutilt WLAN Manager from the Applications->Internet menu.  Up will pop the RutilT application.  Click on the **Profiles** tab then the **New** button.  Fill in the typical details that are required for a wireless network.  Click **Apply** to see if the RutilT icon in the top panel shows that it has connected.  If it has then well done!

[SIZE=4]8[/SIZE]) Now go to System->Preferences->Sessions.  Click **New** and in the box that pops up in the name field enter _RutilT WLAN Manager_ then in the command field enter _rutilt -tp *[COLOR=Gray]the profile you just created[/COLOR]*_.  Click **OK** and then **Close**.  This will ensure that on every boot it will run and automatically select the network profile you had created.

[SIZE=4]9[/SIZE]) Tell me how it goes!

Clicking the RutilT icon from the top panel will show and hide RutilT.  If you click **X** to close the application your network will still run.

[I]If you wish to temporarily change to a DHCP address just bring up the RutilT window, click the **Profiles** tab, then the **Edit** button selected with your profile, then the **IP settings** tab and choose **Automatic (DHCP)** then **OK** and **Apply**.  Click the RutilT icon to hide away.  You're now using DHCP!

If you wish to always use DHCP then go to System->Preferences->Sessions and change the _-tp_ bit to _-dp_.  Reboot and volia!  No severe editing of config files here![/I]

Sulligogs!

---

### Post by kevdog on 2007-09-07
It would be great if you could write this up into just a little bit better formated HOW-TO.  I really like it.  If in the next version, you could confirm all the steps it would be great.  Does rutilt really need the /etc/network/interfaces file?  (I dont know off the top of my head).  And what if you want to use dhcp rather than set a static IP address?  Im not quizzing you, I just think you have done about 80% of the work to make this a great HOW-TO guide.

---

### Post by sulligogs on 2007-09-18
> **kevdog said:**
> Does rutilt really need the /etc/network/interfaces file?
It appears that it does.  By the looks of things, RutilT still uses the network system commands to operate your network, but obviously in a way that doesn't crash things up.  This file would therefore be needed.

> **kevdog said:**
> And what if you want to use dhcp rather than set a static IP address?
Well, I did some testing with this - and then I went away on holiday for a week and now I can't remember quite what was concluded!:)

I think because RutilT at this stage can cater for DHCP better than static IP addressing, why not have your etc/network/interfaces file set up for a static IP system, but then just have RutilT start up with the _-dp_ option to switch things to a DHCP system when it fires up.

Maybe in later versions of RutilT everything can be set directly from it so hardly, if any, manual file editing has to take place at all.

What do you think?

---

### Post by kevdog on 2007-09-18
That how to was great and very thorough.  Id probably repost your how to in a different thread entitled: How To Setup Rutilt 

Few edits

Step #4
It should be:
gksu gedit 
rather than sudo gedit.

Step 5 -- Mention this step is necessary for setting up static IP addresses, for DHCP or dynamic addresses, please see the footer at the bottom

Overall a very nice how to!!!

---

### Post by sulligogs on 2007-09-18
> **kevdog said:**
> That how to was great and very thorough.  Id probably repost your how to in a different thread entitled: How To Setup Rutilt

Will repost in a mo.

> **kevdog said:**
> Few edits

Step #4
It should be:
gksu gedit 
rather than sudo gedit.

I see GKSU fires up a window to run an app as a specified user.  What is the advantage to this rather than just SUDO <app>?

> **kevdog said:**
> Step 5 -- Mention this step is necessary for setting up static IP addresses, for DHCP or dynamic addresses, please see the footer at the bottom

Will it add it in a mo.

> **kevdog said:**
> Overall a very nice how to!!!

Thanks!  Just see if anybody finds it useful!

---

### Post by kevdog on 2007-09-18
Technically the use of sudo is for text based program where as gksu is the equivalent in gnome for your graphical based programs as root.  Ive used both w/o any problem, however Ive read some things breaking for other people

---

### Post by sulligogs on 2007-09-18
Ok, the thread had been reposted.  See [http://ubuntuforums.org/showthread.php?t=554089](http://ubuntuforums.org/showthread.php?t=554089)

Erm, how would I go about making it into a sticky?  Or is that for a moderator to do?

Would really like to know the feedback on my idea.

---

### Post by kevdog on 2007-09-19
Although its a good howto, I dont think they are going to make it a sticky.  You could also try posting it to the tutorial and tips section.

---

