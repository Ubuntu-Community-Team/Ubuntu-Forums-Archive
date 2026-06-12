---
title: "[SOLVED] Zonet Problems--thread change from ndiswrapper"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by Rodney2 on 2008-09-20
PYTHEAS22, per your suggestion, this is  the start of a new thread to continue helping me to solve my problems with getting the Zonet ZEW2500p back on line.  I just copied the last post from the old thread and reprinted it here.

I'm glad to help, although perhaps we should start a new thread for your issue (which doesn't really have to do with ndiswrapper) just to avoid making this one too convoluted.

If you are getting an IP address on your wireless interface and appear to have a decent signal strength yet can't load web pages, then perhaps you are having an issue with DNS. Please unplug your ethernet wire, connect to your wireless network using Rutilt, then run these commands and please post all of the output of each of them:
Code:
ifconfig wlan0
sudo iwconfig wlan0 mode managed channel 11 essid "Rods Wireless"
sudo dhclient wlan0
cat /etc/resolv.conf
wget google.com
wget 64.233.187.99
host google.com
That should help pin down any DNS possibilities. From the standpoint of the driver itself, everything looks like it's working properly.

Also as I said above, we should probably continue this discussion in another thread. So please open up a new one, post the information above in the new thread, and tell us the URL of the new thread so I can respond there.
__________________
         When I disconnected the wired network and tried to get on line with Rutilt I got what I'm showing in the screenshot.  I do not know what I am supposed to type in where it asks for “Key”.
       Now I will go back and plug in the wired connection so that I can get back on line and send you this message which I am writing in OpenOffice.orgWriter while off line.

---

### Post by pytheas22 on 2008-09-20
In the box that says "New Profile," you should enter two things: first, put your WPA passphrase into the box that says "Key"; and second, in the "Name" box, erase "New Profile" and enter a name for this profile, like "home" (since this is your home network, I presume)--Rutilt is asking for this information so that it can save it and connect you automatically next time.  You should also be sure to click on the "IP Settings" tab and make sure that you check the box to enable the use of dhcp.  Then press OK and you should be connected.

If you still can't load web pages thereafter, please let me know what the output of these commands is:
```

iwconfig wlan0
ifconfig wlan0
cat /etc/resolv.conf
host google.com
ping 72.14.207.99
```

---

### Post by Rodney2 on 2008-09-21
Thank you, I just got online with the wireless, your help has been my saviour.  The secret seems to be knowing what to put into the blanks when setting up Rutilt.  I thought it had failed again for a bit as Firefox went "off line" for some reason.  Now, the first time I try to go back on line, I have to reset Firefox (uncheck the work offline box) to keep it from trying to work "off line".  I now get an icon that appears to be an antenna with green waves radiating off it at the upper right hand corner of the screen next to the icon that looks like a monitor.  When I hold the mouse over it it gives me the ESSID, link quality, signal level, noise level and Tx rate.

---

### Post by pytheas22 on 2008-09-21
That's good; I'm glad you're finally online with the wireless, and sorry it took so long to get it straightened out.  Rutilt can be a bit confusing, I agree, but it works well once you figure out how to use it.

If you want to make Rutilt auto-connect to your network when you turn your computer on, let me know and I'll give you the steps to do that (as a disclaimer, it might take a little experimenting before we get a setup that works).  Otherwise, if you're happy enough connecting manually, then we can leave it at that.

---

### Post by Rodney2 on 2008-09-21
Yes, I would like that information on automatically connecting.  I have been asked by some others to demonstrate Ubuntu at a meeting even though I told them I am an absolute novice.  Now, they have a wireless set up at their meeting place which I will have to connect to in order to display all the nice things about Ubuntu I have found.  I think I am the only Linux user (if you can call a novice that) in a group of Windows advocates.  I can not tell you how valuable your help has been, thanks again.Rodney

---

### Post by pytheas22 on 2008-09-21
The auto-connection stuff won't be able to get you connected automatically at your meeting unless you set it up beforehand--it only works for networks for which you've previously created a profile in Rutilt, unfortunately.  But at home, where I think you've already created a profile, you can auto-connect this way:

Go to System>Preferences>Sessions.  Under the "Startup Programs" tab, click "Add."  In the "Command" field of the box that pops up, enter this:
```

gksudo rutilt --profile home --dhcp --hide
```

(I'm assuming that the profile name for your home network is 'home'; if it's something else, substitute that name into the command.  If you don't know what the name is, look under the "Profiles" tab in the Rutilt window.)

You can give the command whichever name you like, then close the window.

Then log out of Gnome and log back in.  When Gnome starts, you should be prompted for your password (unfortunately there's no way to connect without entering your password first).  After you enter it, Rutilt should start running in the background (if you want it to run in the foreground with the window open, remove the '--hide' option from the command above) and connect you to your home network--if it's successful, you should see the tray icon indicating a connection.

As I said, it may take a bit of trial and error to get this right, so let me know if the steps above don't seem to work for you.

---

### Post by Rodney2 on 2008-09-24
I tried the procedure you outlined in the above post and I'm afraid I really screwed something up.  It does not appear to work and now I can not get on line with the wireless at all (I'm back on wired interface).
Now, when I type rutilt in the terminal, it comes up and I can find my wireless.  I created a new profile called "home" and tried to use it.  When I am in the "Site Profile" section and highlight my SSID and click connect, the Connection window pops up and I click "OK" with "home" as the name.  The Connection window dissappears, the Sit Profile shows the info on my SSID greyed out.  I highlight it and then hit the Connect button.  It appears to work for about 3 to 5 seconds as the little antenna icon in the upper right part of the screen shows up with the radiating lines.  It dissappears in about 3 to 5 seconds.  The following is a copy of what shows up on the terminal when I try to use rutilt along with some output after some terminal commands.
[1]+  Stopped                 rutilt
rodney@rodney-desktop:~$ rutilt
There is already a pid file /var/run/dhclient.pid with pid 6247777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777777
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

77777777777777777777777777777777777777777777777777777777777777
[1]   Killed                  rutilt

[2]+  Stopped                 rutilt
rodney@rodney-desktop:~$ rutilt
There is already a pid file /var/run/dhclient.pid with pid 6278removed stale PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

 
[3]+  Stopped                 rutilt
rodney@rodney-desktop:~$ ifconfig wlan0
wlan0: error fetching interface information: Device not found
rodney@rodney-desktop:~$ ifconfig wlan1
wlan1     Link encap:Ethernet  HWaddr 00:fd:07:91:aa:38  
          inet6 addr: fe80::2fd:7ff:fe91:aa38/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:15058 errors:0 dropped:10 overruns:10 frame:10
          TX packets:9440 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1585170 (1.5 MB)  TX bytes:786108 (767.6 KB)

rodney@rodney-desktop:~$ cat /etc/resolv.conf
search Belkin
nameserver 192.168.2.1
nameserver 207.69.188.186
nameserver 207.69.188.187
rodney@rodney-desktop:~$ 
rodney@rodney-desktop:~$ 

Any suggestions as to what I have done wrong or what I need to do to correct things?  Thanks again Rodney
PS should I remove the "Solved" flag from this post?  If so, how?

---

### Post by pytheas22 on 2008-09-24
Sorry for the regression.  You can remove the SOLVED tag from the thread under the "Thread Tools" menu, I believe (not sure though).

First of all, I guess we should try reversing the last step that we took in the attempt to get Rutilt to auto-connect.  So go to System>Preferences>Sessions, and uncheck the box that enables the command for Rutilt that you entered a couple of days ago.

Then please try rebooting.  Run Rutilt from the command line by opening a terminal and typing 'sudo rutilt' and try to connect there.  If it doesn't work the first time, try once or twice more.  Please post the terminal output here.

I don't think that the Sessions startup command would have broken Rutilt--I think it's probably a coincidence with something else--but it's possible.  Sorry that again that things broke after you thought they were finally solved.

---

### Post by Rodney2 on 2008-09-24
I removed the entry in the start up menu and now it works as before.  I'm going to let this problem rest a few days since I am now back on line with wireless then try to set up for automatically going on line later.  Again thanks for your expert help.  Rodney

---

### Post by pytheas22 on 2008-09-24
Alright, I guess that command did trigger the problem then.  Strange.  But I think that the next thing to do (when you're ready to go at this again; take your time), would be to reboot, and then, before doing anything else (i.e. before starting Rutilt manually), run this command:
```

gksudo rutilt --profile home --dhcp --hide
```

(replace 'home' in the command with the name of the profile for your home network).

You'll be prompted for your password, and after that, in principle, you should be connected.  If you're not, what is the terminal output?  What happens if you try to connect manually in Rutilt after running that command?

---

### Post by Rodney2 on 2008-09-25
Here is the terminal output I got when I put in the suggested code:
rodney@rodney-desktop:~$ gksudo rutilt --profile home  --dhcp --hide
gksudo: unrecognized option `--profile'
GKsu version 2.0.0

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.
rodney@rodney-desktop:~$

---

### Post by pytheas22 on 2008-09-25
That's weird...it looks like the command is not being passed to 'gksudo' at all.  What happens if you type:
```

gksudo 'rutilt --profile home --dhcp --hide'
```

Maybe the quotes would make a difference.

---

### Post by Rodney2 on 2008-10-01
Again, I want to thank you so much for your patient help in getting my wireless working.  I just posted another thread "RutiltProbSolution" itemizing what I think was my problems with Rutilt in hopes that it may help someone else.  I just hope I do not misslead someone in what I said, it is just that it workes for me right now.  I do not know quite why or how but maybe, as I learn more about Ubuntu linux I will eventually understand.  Anyway, I'll drop this thread and, when my next problem crops up will create a new one.  Thanks again, Rodney

---

