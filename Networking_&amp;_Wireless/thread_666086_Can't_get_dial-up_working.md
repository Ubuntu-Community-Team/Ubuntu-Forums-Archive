---
title: "Can't get dial-up working"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by Will Pittenger on 2008-01-13
I am used to Windows doing most of the work.  As such, I find Ubuntu's layout hard to understand and downright obtuse.  The documentation is rather lacking.  It describes what parameters you need, but not what to do after that.  One problem that I have is that the Windows machine that work (this one) uses a DNS lookup rather than a hard coded one.  So I don't know what to tell Ubuntu.

I entered all the other parameters that I saw, but no option to connect appeared until I reboot.  I still don't know that Ubuntu sees the modem (USR 56k External Voice Fax modem).  Options to connect and disconnect are present, but nothing happens when I click the connect menu item.

Until I get it connected to the Internet, I don't really have a good way to transfer files to and from it.  (I am limited to CD/DVD, floppies, and USB keys.  The floppy in that machine is a PATA LS-120 and might not be supported by the default installation of Ubuntu.)

---

### Post by HermanAB on 2008-01-13
Hmm, you are using the wrong distribution.  Ubuntu is not the easiest Linux around, it is sort of intermediate difficult.

Install Mandriva 2008.  It has wizards for everything.

Cheers,

Herman

---

### Post by Nero_Flint on 2008-01-13
> I entered all the other parameters that I saw, but no option to connect appeared until I reboot.

What option did you receive when you rebooted?

---

### Post by Will Pittenger on 2008-01-13
Ubuntu is what someone else downloaded for me.  I have only dial-up here and something that large would take forever to download.

---

### Post by Will Pittenger on 2008-01-13
Just Connect to PPP and Disconnect from PPP.

---

### Post by NJC on 2008-01-14
Will;
 
I also have an External USR modem. For my Gutsy install, I configured the modem in System/Administration/Network, and then enabled it (ensure check mark is selected). 
 
Look for "Gnome PPP" in Synaptic and install.

---

### Post by Will Pittenger on 2008-01-14
I have already done that.  See my posts above.

---

### Post by NJC on 2008-01-14
I just see that you have "entered all the other parameters that I saw" - no mention of Gnome PPP or Network-admin.
 
Also good info: [http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by Jessica's on 2008-01-18
Hi all
Could some one please help i have installed Ubuntu 7.10 for the first time and i cant get dial up to work. I have used scanmodem and it says i have a Modem with Lucent/Agere DSP chipsets (internal). I have downloaded Martian drivers but i have know idea how to install them. Please could some one explain how to get dial up working? 
ohh please explain to me as though im a 5 year old:)

Thanks
Jess

---

### Post by Will Pittenger on 2008-01-18
> **NJC said:**
> I just see that you have "entered all the other parameters that I saw" - no mention of Gnome PPP or Network-admin.
 
Also good info: [http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html)

Network-Admin was what I used.  I also tried another pppconfig and wvdial.  wvdialconfig was the only program to locate the modem at /etc/dev/ttyAMC0.  Nothing else even checked there.  wvdial is what I use at this point, but I have to use a complex command line and I don't know how to disconnect without turning off the modem.  (Try doing that with an internal.)  Because I have Ubuntu set to restore my configuration, wvdial redials (never with success) after a reboot -- and keeps trying until it succeeds which never happens.

I would prefer Windows DUN to wvdial.  It would actually tell me my connection speed which wvdial won't.  DUN also allows for multiple phone numbers for use when the line is busy or the remote machine never picks up.  It would be nice if it demoted numbers when I get a poor connection (28k happens once a day on average).  To me, poor connections should be automaticaly rejected, but even DUN doesn't do that.  DUN also handles multiple locations per connection.  This allows it to take one set of phone numbers and translate them to work where the dialing rules might be different (like home vs. office).

wvdial is the ONLY Linux dial-up option to support multiple connections.  This is important as my provider's definition of "unlimited access" is limited to 40 hours per month.  I go through that in a hurry.  So I have two accounts (they let me have one free).  I use one until the hours run out and then use the other.

The good news is that I may have DSL within 2 weeks.  However, I don't see that as a sure thing.

---

### Post by Will Pittenger on 2008-01-22
I noticed that I could install something called KPPP.  So I tried that.  It could only manage 9600 baud on the attempt I gave it.  When I saw that speed, I quickly when back to wvdial.  Any suggestions?

Also, the attached screen capture shows what I see in network connections.

---

### Post by Will Pittenger on 2008-01-22
It is beginning to look like wvdial is not much faster than KPPP was.  9600 baud is awfully slow.  Sure enough all pages are way slower than anything I have seen under Windows.  If there is one thing to ensure I go back to Windows, slow connection speeds would be a front runner.

---

### Post by Will Pittenger on 2008-01-24
New info: For the past few days I have been running [FONT=Courier New]pppstatus[/FONT] while connected.  It is showing bandwidth used far in excess of what a 9600 baud connection can provide.  I am also seeing modem activity (both on the modem itself and in [FONT=Courier New]pppstatus[/FONT]) while no program should be actively downloading stuff.

So instead of a lousy connection, it looks like something is gobbling up the bandwidth I have.  Any ideas?

---

