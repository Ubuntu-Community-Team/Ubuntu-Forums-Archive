---
title: "[SOLVED] Gutsy can't connect to CUPS Server"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by inyoka on 2007-11-01
Gutsy cannot print through a CUPS server (in this case remote not local), _[COLOR="Blue"][ I have already got a post open]("http://ubuntuforums.org/showthread.php?p=3683511#post3683511")[/COLOR]_ but is not getting any replies (perhaps because it shows as already having received replies).  

Fault exists on multiple Gutsy clients, Fedora and 7.04 clients can print fine.  Gutsy can ping.  No errors in the log files that I can see.  OpenOffice crashes when changing page format of trying to print. When opening sytem-config-printer get error "unable to contact server" (however it shows the names of the printers on the server.)
[COLOR="Blue"][U]
[Might be a similar problem to this post (with no replies yet either).]("http://ubuntuforums.org/showthread.php?t=306028") [/COLOR][/U]I tried to revert to the Gnome printer manager TNA.  The users are starting to get fed up and so am I.  I tried re-installing (even cleared cache and downloaded from different repo) TNA.  **Can someone please confirm that there is at least one Gutsy system somewhere in the world printing to a CUPS server, and if so how they got it to work**. I tried using the GUI and manually writing the client.conf file both TNA.

All available patches have been applied. Please, please help.

---

### Post by sav2005 on 2007-11-08
My experience is similar but odd. I cannot connect to the shared printer from my remote machines via OpenOffice or gnome-printer-config tool. BUT I can print a test page by pointing my web browser at [http://serverIP:631/](http://serverIP:631/). My clients receive "cannot connect to cups server" if I select the printer in the Gnome-printer-config thingy.

My print server has a static IP, my clients DHCP on a wireless network. All machines are running Gutsy or Feisty and can ping one another.The server is running Gutsy.

---

### Post by sav2005 on 2007-11-08
I solved my own problem by including the following line in the **/etc/hosts** file on each of my clients

    **xx.yy.zz.aa  serverName**

where xx.yy.zz.aa is the server's local network address.

---

### Post by inyoka on 2007-11-08
Okay I'll try pointing a test page at my server, one of my computers can still print despite system-config-printer hanging.  Also I just downloaded some updates to the CUPS software which I have yet to apply to the afflicted machine.  I'll do that tonight and post an update tomorrow morning, its already 5pm here.

I'll check if the same fix helps my machines, although I will not edit all my hosts files perhaps I could reconfigure my DNS Server.  I'm sure some of these problems are due to developers wanting software deployed early to ensure Hardy is a solid release.

I'll post tomorrow with my results and hopefully a reproducible fix. 

Thanks sav2005.

---

### Post by inyoka on 2007-11-09
I had a reply on another post from v.cecchetto who said to try changing the system theme to Human.  This appears to work and anyone interested should check out [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/153173") for the bug reports (there are quite a few).  [Or this launchpad bug report.]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526")

I have yet to connect to the CUPS server so I'll try tomorrow morning and close the post if it works.  However I am 95% certain this is fixed.  I just wish I didn't have to use the Human theme all the time.  Hopefully a fix is in the works.

FYI - If you don't mind loosing OpenOffice Gnome integration try removing OpenOffice-Gtk, this fix was suggested by Innovator on launchpad.
[CENTER]:):KS:)[/CENTER]

---

### Post by sav2005 on 2007-11-10
Actually the probelm is more complex. The server's CUPD Daemon doesn't seem to be starting with the system even though it is the list of services. If I start it by hand it works. 

Not Happy!

---

### Post by inyoka on 2007-11-10
Hi sav2005,

Sounds very strange but if you definitely have cupsys starting with your other services, have you tried reinstalling cups?  Alternatively if you use 'CTRL'+'ALT'+'F1' while booting you might get an error or some other clue of whats happening.

As a temporary fix though have you just tried running your cups start command through System>Preferences>Sessions.  You can add extra startup programs and although it doesn't fix the problem it might prevent you having to start the server every time you boot.

Hope this helps.

---

### Post by inyoka on 2007-11-10
Okay its official, however strange it may sound by changing my theme back to Human all my problems went away.  It appears that some themes cause Ubuntu Gutsy to become incredibly unstable.  This has been posted in Launchpad and should be fixed.

For anyone interested the Launchpad reference number is : [#131526]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526")

FYI - If you don't mind loosing OpenOffice Gnome integration try removing OpenOffice-Gtk, this fix was suggested by Innovator on launchpad.

:) Thanks to everyone who tried to help on this. :KS

---

### Post by inyoka on 2007-11-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Launchpad Bug Report

---

### Post by sav2005 on 2007-11-11
That is not a satisfactory solution because my sever is not a desktop machine. No users are accessing it directly - **[COLOR="Red"]it's a server[/COLOR]**! 

I _downgraded_ it to Feisty and it works!

---

### Post by inyoka on 2007-11-11
Hi sav2005,

Sorry this thread was closed because the fault it was opened to solve has been solved.  It sounds as though you have a very different problem and it should be posted under a new thread.

With regards to your fault can you confirm if you are running Ubuntu-Server or Ubuntu-Desktop?  I need to clarify this because a lot of people (myself included) run the desktop edition for CUPS servers so people can log in locally to work and print.

Also have you tried the following :

```
sudo apt-get remove cupsys cupsys-client
sudo apt-get remove --purge cupsys cupsys-client
sudo apt-get install cupsys cupsys-client
```

Also try checking your logs : /var/log/cups 
 
This might give some clue but definitely make sure you've tried purging and re-installing.  If you decide to open up a new thread please post a link to it here.

---

### Post by sav2005 on 2007-11-12
Thanks. Yes I reinstalled cupsys and cupsys-client. I didn't think about the purge option, but I had installed a clean, new system rather than upgrading. 

I initially installed ubuntu-server (LAMP), then installed ubuntu-desktop on top of that, partly to make CUPS configuration simpler!

I have downgraded and Feisty works well so I won't bother with an upgrade until later. Gutsy has too many annoying bugs at the moment - (I lost remote printing, wireless WEP-enterprise authentication and OOo-gtk is buggy). Not very good for a production environment.

Cheers,

Laurie

---

### Post by inyoka on 2007-11-12
I know what you mean, it feels like they are experimenting a lot with Gutsy perhaps so they can get a good reliable Hardy Heron LTS release.  I wish they could have warned us though, Hardy Heron better be awesome!  

Really wish I had stuck with Feisty, I cant really think of Gutsy's advantages anymore.  The OOo-Gtk problems are major deal-breakers, and I just can't get ubuntu-server to run as well as my fedora 4 server box.

Anyway hope things go better for you now,
Simon

---

### Post by sav2005 on 2007-11-12
Thanks, I hope you can fix your issues too.

I'm playing with SUSE 10.3 on a couple of spare machines! I hope I don't have to move - I'd convinced my organisation to use Ubuntu for its servers. (Debian was our first choice, but it didn't like our hardware, Ubuntu didn't complain)

---

### Post by tednyc on 2007-11-15
I just handled a similar problem with a Gutsy desktop not being able to print to a printer on a Gutsy server. OOO had problems. Found out that it appears to  be the controls that cause the problem. Most appear to not affect printing from OOO.

---

