---
title: "Installing CSA.sh, a authentication program"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by CloFan on 2007-04-01
Hey guys, I'm having a bit of a problem getting online at my University.  We use a program called CSA, which is a client authentication program to make sure that only students are connecting.  Anyways, to get to my problem..

  I was trying to install this earlier, using this command: sh /home/server/Desktop/CSA.sh in the terminal.  I get the following errors:

```
mkdir: cannot create directory '.CSA.TEMP': File exists
awk: cannot open /home/server//home/server/desktop/CSA.sh (No such file of directory)
tail: +: invalid number of lines

gzip: stdin: unexpected end of file
chmod: cannot access './engine': No such file or directory
/home/server/Desktop/CSA.sh: line11: ./engine: No such file or directory
Error running CSA.sh.  Please call the helpdesk.
rm: cannot remove 'engine': No such file or directory
rm: cannot remove 'agent.config': No such file or directory
rm: cannot remove 'tmp.csa': No such file or directory
```

I'm not sure exactly what's going on... I know that the CSA program is set to delete itself once it's ran, so that's probably what's going on with all the rm's at the bottom.

Any help is appreciated!  I'm running Ubuntu 5.10, username is server.

---

### Post by rob4001 on 2007-05-09
Hi 

Sorry to hear about your problems i also have the same problem and my University ICT helpdesk were unable to help! The CSA.sh  is made by bradford campus manager I was told ubuntu was supported but I have had no luck running this software.

---

### Post by NickArgyle on 2007-08-21
I know that this is a pretty old post now, but I was just having this problem with my schools new wireless network, and I did get it to work after a couple of days.

first you have to configure your settings in Firefox to connect through manual proxy. Input the proxy info and select the check box to apply it to all boxes.

then, after you download csa.sh, move it to / while running nautilus as root. chmod +x it and run in terminal. It should work now, the main thing is to have csa.sh in tthe root directory (/) and firefox will only be able to connect through the proxy if you manually configure it. 
I still occasionally get an error in Firefox stating "proxy is refusing connections" but to fix this I usually just restart my wireless connection.
You can configure Thunderbird to work as well if you school or college has email by checking what server they are using, and most likely using the same proxy info as in firefox.

Hope this helps people in the future.

---

### Post by CrashintoDMB on 2007-08-23
so first things first, i have NO idea how to make firefox  a manual proxy, and what proxy info should i be b using?

---

### Post by McSnuffy on 2007-08-23
Same question here. How do I find out what the proxy settings are?

---

### Post by NickArgyle on 2007-08-23
> **CrashintoDMB said:**
> so first things first, i have NO idea how to make firefox  a manual proxy, and what proxy info should i be b using?
To choose manual proxy go to 
edit -> preferences
click the advanced tab, then the network button.
then click settings.

I cant tell you how to find the proxy you need to be using. What I did was look on one of the browsers of someone else using internet explorer in windows and looked at their proxy settings. Basically as someone who has it working to view what they are connected to. You could also just ask you tech office for the ip of the proxy.

Again make sure you install csa.sh in the / directory with root privaliges.

---

### Post by NickArgyle on 2007-10-09
As an update for anyone who encounters trouble with csa.sh, konqueror works much better than firefox with the password system for the network.
With firefox I had to continually enter my network password, but with konqueror the wallet system takes care of it all for me and I have'nt had to re login yet.

---

