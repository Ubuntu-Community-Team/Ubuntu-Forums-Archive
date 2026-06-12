---
title: "Slow Browsing Speed Ubuntu 10.10 (Maverick Meerkat)"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by hannodewind on 2011-01-25
Hi all,

I am quite new to Ubuntu (Linux for that matter). 

I recently installed Ubuntu 10.10 (32 bit) in the hopes of learning and experiencing an OS other than Windows, However, I've been experiencing trouble browsing the web in Ubuntu.

I use a DSL connection (which works fine in Windows). It seems to be connected in Ubuntu and the application manager and updater can both connect to the internet. The problem is no other application can access the internet. I have tried browsing with Chromium and Firefox to no avail. Even the "Network Tools" cannot ping google. I can however ping google from terminal. Really strange indeed.

I have tried disabling IPv6 (that seemed to be a solution for some people on the web), but that did not work either.

It's quite hard and laborious to find a solution that actually works since I constantly have to reboot my PC, log into Windows, search the web, reboot and try a solution in Ubuntu.

Anybody got a solution other than IPv6?

Thanks

---

### Post by hannodewind on 2011-01-26
Seems like I cant find a solution...saw another thread with similar problems: [http://ubuntuforums.org/showthread.php?t=1675489](http://ubuntuforums.org/showthread.php?t=1675489)

If anyone maybe cares my internet setup is as follows:
I live in SA and I have an iBurst Wireless internet connection. Currently the modem is connected via an Ethernet cable to my on-board Intel 82567LM-2 Gigabit Network. 
In Windows 7 I set up a DSL connection and everything is perfect.
In Ubuntu 10.10 I do exactly the same, however browsing is horrible. I constantly get "Waiting for..." and then nothing happens.
I have tried the same setup on Kubuntu 10.04 and it worked then..(I uninstalled Kubuntu because it constantly crashed on me).

Anybody got a solution? Otherwise I will be sticking to Windows, have no intention of using an OS that cannot browse the web.

Another thing: Is there any way to apply some change made in the root directory without the need to restart? I have been restarting my system like mad changing the IPv6 setting and stuff. Feels like I'm back in Win ME days...

---

### Post by cipherboy_loc on 2011-01-26
Can you 'wget' a page?

```

wget http://google.com

```

Also, just as a thought, but what type of ethernet adapter are you using? It could be that you need a special set of drivers for it to work...



Cipherboy

---

### Post by cottfcfan on 2011-01-26
If Kubuntu 10.04 worked, try the Ubuntu 10.04-1LTS.
Ive had niggly things go wrong in 10.10 but 10.04 is rock solid for me.
Also have you set up a firewall that may be blocking your browser?

---

### Post by hannodewind on 2011-01-26
> **cipherboy_loc said:**
> Can you 'wget' a page?

```

wget http://google.com

```

Also, just as a thought, but what type of ethernet adapter are you using? It could be that you need a special set of drivers for it to work...



Cipherboy
I tried the wget but all I get is:

hanno@ubuntu:~$ wget [http://google.com](http://google.com)
--2011-01-26 16:20:56--  [http://google.com/](http://google.com/)
Resolving google.com... 64.233.179.104
Connecting to google.com|64.233.179.104|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.google.com/](http://www.google.com/) [following]
--2011-01-26 16:20:57--  [http://www.google.com/](http://www.google.com/)
Resolving [www.google.com](www.google.com)... 64.233.179.104
Reusing existing connection to google.com:80.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://www.google.co.za/](http://www.google.co.za/) [following]
--2011-01-26 16:20:58--  [http://www.google.co.za/](http://www.google.co.za/)
Resolving [www.google.co.za](www.google.co.za)... 64.233.179.104
Reusing existing connection to google.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.1'

    [                       <=>             ] 0           --.-K/s  

and the <=> keeps moving back and forth forever.

As for the ethernet: I use the onboard card of my Intel X58SO MB. I'm rather new to linux, I don't even know exactly where to find the driver details for my card, like in Device Manager in Win.
However, I do not know if it is a problem with the card, since Update Manager and Ubuntu Software Centre can both access the web at full speed...

---

### Post by hannodewind on 2011-01-26
> **cottfcfan said:**
> If Kubuntu 10.04 worked, try the Ubuntu 10.04-1LTS.
Ive had niggly things go wrong in 10.10 but 10.04 is rock solid for me.
Also have you set up a firewall that may be blocking your browser?
I'm not too keen on downloading and reinstalling 10.04...maybe I will try it later if no one has a solution, but I would not like to think 10.10 is that big of a fail.

I have not set up any kind of firewall, I guess the only firewall is the built-in one. I disabled it with "ufw disable" command, it said it was disabled but browsing is still impossible.

---

### Post by hannodewind on 2011-01-26
I may have found a solution :P...but I fear it might not be ideal...

Here is what I did:

1. I backed up the file etc/ppp/peers/dsl-provider
2. Ran "sudo pppoeconf" and enetred the details and answered yes to every question.
3. Tested, still did not work. 
4. Replaced the etc/ppp/peers/dsl-provider file with the backed up one, I figured it pppoeconf did not work anyway.
5. Opened etc/ppp/peers/dsl-provider to check if I cannot manually change the contents.
I changed :
a) #user [email]myusername@myprovider.net[/email] to my username and uncommented it. (line 14)
b) commented pty "/usr/sbin/pppoe -I eth0 -T 80 -m 1452" (line 20)
c) uncommented pty "/usr/sbin/pppoe -I eth0 -T 80" (line 29)

6. Tested using pon dsl-privoder and poff, but poff said multiple connection were active (?). Internet still did not work.
7. Restarted. Did not log on with GUI, but logged on in terminal and used pon dsl-provider. Did a wget [www.google.com](www.google.com) and it work.
8. Returned to GUI and logged on, the networking icon at the top right disappeared, thus network status is invisible, but internet is working perfectly!! :)
9. Restarted again just to be sure...icon is still missing, but I can now control the connection with pon and poff...not ideal, but hey, it's working...

If anybody got an idea how I can manage the connection without terminal (thus with a GUI) that would be awesome.

---

### Post by Splat_NJ on 2011-01-26
I would try Wicd. I had problems, though not DSL, with the built-in net/manager. Once I installed and config'ed Wicd it's been solid since. Good luck.

---

### Post by cipherboy_loc on 2011-01-26
That's what I would suggest, but I tried that a while ago on Ubuntu and it didn't work. What I think you need to do is purge NetworkManager BEFORE you install WICD. Download the WICD and NetworkManager debian packages, so that if WICD fails you can download NetworkManager. I screwed one of my installs this way. Or better yet. Back up your system before installing WICD. 

On a different note, I was having issues with NetworkManager in Gentoo, and WICD installed and works just fine (with a bit of configuration).

EDIT: As for the missing icon, run; nm-applet from the terminal. If it runs without errors, then add it to the gnome startup.

My two or three cents,
Cipherboy

---

### Post by Splat_NJ on 2011-01-27
> **cipherboy_loc said:**
> That's what I would suggest, but I tried that a while ago on Ubuntu and it didn't work. What I think you need to do is purge NetworkManager BEFORE you install WICD.

FWIW, I have installed Wicd with and without Net/Manager already installed and never had a problem. I would, though recommend uninstalling Net/Manager first just to be safe.

---

