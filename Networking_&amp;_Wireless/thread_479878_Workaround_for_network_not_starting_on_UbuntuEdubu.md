---
title: "Workaround for network not starting on Ubuntu/Edubuntu 7.04 (Feisty)"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by JSpaceCadet on 2007-06-20
Hello all,
I have seen many posts about folks upgrading to or installing Ubuntu/Edubuntu 7.04 and then their network stops working.  I'm sure there are many possible reasons for this, and mine is just one of them.

My symptoms were these:
1) Login, network icon in top-right has an x in it - indicating the network isn't up or connected.
2) From another machine, I couldn't ping the workstation.

There were two ways I found to get the network to work - both were manual.
1) Click on the network icon and then tell it to use the wired network connection (in my case)
2) Go to a command prompt and run:
     sudo dhclient

Doing either of these manually wasn't an option as some of the systems I am working with need to be able to be unattended - workstations or servers.

Here is my workaround in a nutshell:
1) Create a script that simply runs dhclient at startup
2) Configure the script to be run at startup 
3) Reboot

This will get you connected to the network before you log in to the desktop.  The network icon will still show that the network is disconnected.

Here are the steps to take:
1) Go to a terminal window
     Applications->Accessories->Terminal
2) Run the following.  You can use your favorite editor instead of [FONT="Courier New"]vi[/FONT].

[FONT="Courier New"]
cd /etc/init.d
[/FONT]

[My command line to create the script: sudo vi _jcj_start_broken_dhclient]

[---------------]
[FONT="Courier New"]
#!/bin/bash
dhclient
[/FONT]
[---------------]

[FONT="Courier New"]
sudo chmod +x _jcj_start_broken_dhclient
sudo update-rc.d _jcj_start_broken_dhclient defaults
[/FONT]
[You will see the output of result]

Reboot your system and your Ethernet should work (before you log in).  [FONT="Courier New"]sudo shutdown -r now[/FONT]

A few quick things in closing:
1) Yes, I know I tend to be verbose
2) I tend to name strange files _jcj_xyz so I can easily find them later
3) The network icon on your desktop will probably still show the network is disconnected.  In my case the network works consistently despite this oddity.  I can think of some cases where this might not be a robust solution.  I am banking on the development group getting this issue addressed.  I have seen posts as far back as 2004/2005 that appear to be very similar in description.
4) Before I could reliably ping the Edubuntu box I had to install "Shared Folders" (Samba) under System->Administration->Shared Folders
5) See [http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/) for some other ideas about bootup scripts

*****
I hope this helps someone out there!
Joe

---

