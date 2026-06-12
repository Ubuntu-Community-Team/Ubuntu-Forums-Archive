---
title: "Evolution with Hotmail destroyed my wireless network"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by Salomonis on 2008-07-13
Ok guys I  NEEEEED help please.  I followed instructions  to put Hotmail on evolution. This is what I did :
HOWTO: Send and Receive Hotmail through Evolution
Okay everyone, after digging around in these forums and googling like I've never googled before, I figured out how to send and receive e-mail through hotmail using Evolution. I'm throwing together a rough HOWTO for others. If things need more clarification, let me know and I'll update it.

First, make sure your system is up to date. Open up a terminal and type:

Code:

sudo apt-get update

Now, install the inet daemon

Code:

sudo apt-get install inetutils-inetd

This takes care of all of our dependencies. Now on to the good stuff...

Code:

sudo apt-get install hotway hotsmtp

This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtpd, which allows you to send e-mail through hotmail using SMTP. By default, however, only hotway gets installed properly to your inet daemon, so let's fix this.

Code:

sudo gedit /etc/inetd.conf

Look for a line like this:

Code:

pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd

By default, hotway leaves a copy of each message it downloads on the server. I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:

Code:

pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r

And we also need to add a line to get hotsmtpd working, just paste this at the bottom:

Code:

2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotsmtpd

This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon. Now, save your file, exit gedit, and restart your inetd server:

Code:

sudo /etc/init.d/inetutils-inetd restart

If everything is working properly, you'll see this pop up on your screen:

Code:

* Restarting internet superserver inetd                            [ ok ]

Now, close out of your terminal and start up Evolution. It may pop up the first-time use wizard, you can use that if you like. Or, you may have to go to Edit->Preferences and hit the Mail Accounts button on the left. However you choose to do it, here's your information:

Email Address: [email]xxx@hotmail.com[/email] (fill in your normal e-mail address that you use to login to hotmail)

Receive Server type: POP
Server: 127.0.0.1
Username: [email]xxx@hotmail.com[/email] (same as above)
Security: No encryption
Authentication type: Password
(Remember password checkbox is up to you)

Send Server type: SMTP
Server: 127.0.0.1:2500
[X] Server requires authentication (check this box)
Use Secure Connection: No encryption
Authentication Type: PLAIN
Username: [email]xxx@hotmail.com[/email] (same as above)
(Optional Remember password checkbox)
Last edited by Indras; July 7th, 2006 at 10:43 PM. :
It ended up not working because of WebDAV so I got a gmail account and it works fine with Evolution.  That's not the problem. 
 After turning my computer off my roomate noticed that the wireless was extremely slow during the morning.  When I turned my computer back on I didn't have any wireless (no signal strength), however I did have a little signal strength to a different wn, but I couldn't retrieve the ip  using WiFi Radar.  I read on another forum that wifi radar could be the source of the problem.  I uninstalled it and restarted my computer after receiving updates.  No change for me, however no one else can use the wireless network now.  Did making my computer a pop server for hotmail cause this?  I don't understand how I set up servers on my personal machine could affect everyones connection to the wireless routers. Another mystery is why would the name for the wireless network change?  Most of this is over my head.

---

### Post by cariboo on 2008-07-13
You probably changed something else. To check and see if inetd was the problem. Shut down the service, In a terminal type:

```
sudo /etc/init.d/inetd stop
```

and just in case restart the network service.

```
sudo /etc/init.d/networking restart
```

Jim

---

### Post by Salomonis on 2008-07-13
Thank you for responding.  I tried the first option and it said the command not found,  I went ahead and restarted the network and strangely it said ignoring eth0,eth1,eth2,wlan then said ok.  I thought the ignoring part was unusual.

---

### Post by Salomonis on 2008-07-13
I'm going to search my files to see what is in init.d/inetd

---

### Post by Salomonis on 2008-07-13
There is no inetd in that folder however there is an inetutils-inetd there.  should I type sudo /etc/init.d/inetutils-inetd stop?

---

### Post by TreeFinger on 2008-07-13
you should have just gotten a g-mail account. All I had to do to set up gmail in evolution was plug in the info..

---

### Post by Salomonis on 2008-07-13
Yea I should have done that first.  I don't know what I was thinking.  I usually avoid Microsoft.  I guess I gave them too much credit thinking hotmail and linux could mix.  Or simply Microsoft could mix with anything non Microsoft.  Won't make that mistake again.

---

### Post by Salomonis on 2008-07-14
Does anyone have any ideas what could be the problem?  The only thing I can think of is that Deluge killed our wireless router.

---

### Post by Salomonis on 2008-07-15
It was probably the electrical storm.  I upgraded my router firmware and it's working now.  Thanks to all who tried to help.

---

