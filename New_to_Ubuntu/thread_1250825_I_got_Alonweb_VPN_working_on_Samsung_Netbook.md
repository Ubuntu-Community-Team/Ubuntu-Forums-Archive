---
title: "I got Alonweb VPN working on Samsung Netbook"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by Fungus on 2009-08-27
I just installed Ubuntu 9.04 on a Samsung NC-10, dual boot.  

Here is what I've learned about getting this VPN working:

1.  If you don't have OpenVpn installed, when you right-click the network manager icon, the vpn option will be greyed out.

You have to have VPN connection Manager (OpenVpn)
installed. one way to do this is:

Applications menu, then select /add/remove
Make sure all available applications is set to show and search for openvpn.  When it is found, click the check box to put a check in it, and hit the 'apply changes' button.  

2. you need to remove resolvconf package if it is installed in your system.  See [http://kb.wisc.edu/helpdesk/page.php?id=9834]("http://kb.wisc.edu/helpdesk/page.php?id=9834")

Instructions on the WiscVPN site are pretty clear how to do this.  you can also check the add/remove application applet or synaptic to see if resolvconf is on your machine.

May want to re-boot here. not sure.

3. Set up your user id and password at AlonWeb if you havent already.  Watch out, you need upper and lower case in your password so don't forget where you changed case!!

4. The 'Getting Started!" page on Alonweb has instructions for installing the client info on linux, but their instructions are too sketchy.

It instructs you to download a compressed tar file containing a config file and a cert file.  Click on the link and download the tar file.  then Ubuntu will prompt you to uncompress it. I think it automatically places them in a folder, openvpn, under your home folder.

(At the top of the AlonWeb instruction page it tells you to rename the alonweb.conf to alonweb.opvn, but I didn't do it and it worked for me anyway)

5. Almost done...  Make sure your wireless connection is off, i.e., right-click your network manager icon and have the enable wireless option UNCHECKED, for the moment.  Then left-click the network manager icon and scroll down to VPN Connections.  It should not be greyed out. Select configure VPN.

A network connections window will open up and you select the VPN tab.

Click on the IMPORT button on the right side, and navagate to the folder where you have the two files you extracted in step 4.  Select the alonweb.conf and click the open button.

This will automatically insert all the AlonWeb configuration info into your VPN set up.

(I found if you try this with the wireless connected, the import button is not there, and you GO NUTS trying to figure out what to put in all the configuration boxes!!) 

Then you will have to type in your AlonWeb Username and password.

6. Once you've done this and saved the settings, _now enable_ wireless in your network manager and make your unsecure connection.  After you connect, left click on the network manager again and at the bottom of the list of networks, select VPN Connections, and then click the button for alonweb.

In a minute it will establish the VPN, and the network manager icon will have a steady yellow box on it. (it is actually a tiny padlock, showing your VPN is on).

Also, if you hover your mouse over the icon, it will also say "VPN connection 'alonweb' active"

7. Next time you want to go online, just repeat step 6: make your wireless connection, and then establish the VPN.

Hope this helps folks.  Happy browsing.

As you can tell, I am a new at this and I don't know much more than this!

---

