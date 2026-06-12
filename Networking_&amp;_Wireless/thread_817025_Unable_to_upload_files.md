---
title: "Unable to upload files"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by Fatfool on 2008-06-03
This is an Issue with the inability to upload files onto any website (tested on Photobucket, imageshack, hotmail, mediafire). it times out instead.

Web browser tested are firefox 3B5 (64 bit) and 2.0.0.14 (32 bit running on 64 bit hardy) and firefox 3B5 (32 bit). all are on hardy. version of firefox has no difference in effect.

No difference between wireless or wired connection. Tested network cards are Marvell Yukon 88E08053 integrated on an ATi RS482 board and Sparklan
WMIA-139AG WLAN 802.11a/b/g Mini PCI Module Atheros (AR5004X) High Power in a laptop with a 855GM chipset. the ATi board based rig has the 64 bit version of Hardy installed on it while the laptop used the 32 bit LiveCD. the 32 bit LiveCD was also used on the ATi board based rig to test for differences; none were found. All produced the same result.

The hardware has been tested under Windows XP and has found to perform in these tasks described above.

Due to mediafire having a flash bar which allows the viewer to see the upload rate and status of the file being upload, a discovery of the reason for the timeouts were made. The upload first bursts at ~50kbps (do note that my connection is declared at ADSL 1500kbps download, 350kbps upload. These rated transfer rates are obtainable as I have tested them in the past under windows.)
subsequently over the next 10 - 15 or so seconds, it constantly drops until it reaches nil. the timeout then occurs. testing with small files of >50kb results in a sucessful upload no matter the file type. larger files result in time outs.

Access point being used is a D-Link DIR-635 (draft N; unknown atheros Xspan chipset) with 1.09W firmware.

Testing different access points with the laptop due to its connection being a wireless one was done as well. It was tested with an ancient Linksys 802.11b access point who's signal was found floating around (aka leeching). This access point's Chipset is probably an ancient Broadcom chipset. This connection to this access point showed no signs of the upload rate dropping and the tester(me) was able to sucessfully upload files of 30+mb.

Early Diagnostics by a forumer were given as 'It's clear now that the problem lies in the Linux client's network, which is perhaps either limiting or not even initialising connection(s) to the upload host.'
[http://forums.hardwarezone.com.sg/showthread.php?t=1964827](http://forums.hardwarezone.com.sg/showthread.php?t=1964827)

posted it here:
[https://bugs.launchpad.net/ubuntu/+bug/235004](https://bugs.launchpad.net/ubuntu/+bug/235004)

though i'm not sure If i did it correctly. also would like to know if there are any work arounds in the meantime. 
I'll provide logs if they're needed. just tell me which :) (newbie here)


P.S. if you're wondering about my third person writing style, sorry, engineering student here :D

---

### Post by Charlie91 on 2008-06-03
Just adding myself in this query; I can't upload files anywhere!  I had no problem until about 2 weeks ago, perhaps coincidental (or caused) with the usual updates (using Hardy Heron), perhaps a bug was introduced in the updates?  I too am looking for a solution...

---

### Post by Fatfool on 2008-06-03
hmm... does the same effect happen when you try to uplaod to mediafire? (look at the progress bar)

and does it only happen under hardy?

would be good if you can post your AP and adapter models here :)

---

### Post by Charlie91 on 2008-06-03
Can't attach with email; can't upload at Yahoogroups; can't upload to Box.net; I guess it won't work with mediafire (without trying it).  It only happened a week or 2 ago; before that it's perfectly working.  I'm not a computer "geek"--can you tell me what to type at the console to get the AP and adapter models?  Yes I've been using Linux but I'm really just a user, and it's been a long time since I last went 'under the hood'.

---

### Post by Fatfool on 2008-06-04
> **Charlie91 said:**
> Can't attach with email; can't upload at Yahoogroups; can't upload to Box.net; I guess it won't work with mediafire (without trying it).  It only happened a week or 2 ago; before that it's perfectly working.  I'm not a computer "geek"--can you tell me what to type at the console to get the AP and adapter models?  Yes I've been using Linux but I'm really just a user, and it's been a long time since I last went 'under the hood'.
well I only started on Ubuntu bout a month ago. but as for your access point/router and adapter, well, check your box which you use to connect to the internet. if its a wired connection, you're probably using your motherboard's ethernet port and if so list down your motherboard's model.

if its a wireless connection, you could open up your case to check the card or if its a USB adapter, just list it down. ubuntu doesn't list the exact card model, just its chipset.

---

### Post by Charlie91 on 2008-06-04
It's ethernet, eth0: RealTek RTL8139 at 0xc400, 00:11:d8:4d:c3:44, IRQ 20.  I don't know if that's the info needed.

Anyway, I guess I sidetracked the thread: I'm just wondering why I can't upload files (I had no problems since 2006, and I guess it started after an 'update' a few days ago).

---

### Post by Fatfool on 2008-06-04
> **Charlie91 said:**
> It's ethernet, eth0: RealTek RTL8139 at 0xc400, 00:11:d8:4d:c3:44, IRQ 20.  I don't know if that's the info needed.

Anyway, I guess I sidetracked the thread: I'm just wondering why I can't upload files (I had no problems since 2006, and I guess it started after an 'update' a few days ago).
i see. ok and what is your router/gateway model? (the box it connects to)

it could have been that update screwing up the connection to your router model as in my case... you're on 8.04 right?

---

### Post by Charlie91 on 2008-06-04
Yes, I'm using Ubuntu 8.04.  I can't get a hold of my router model (sorry).  How come it's only the uploading; I can use the internet though (surf, email, etc.).  Maybe there are just some config files to change?

---

### Post by Fatfool on 2008-06-04
> **Charlie91 said:**
> Yes, I'm using Ubuntu 8.04.  I can't get a hold of my router model (sorry).  How come it's only the uploading; I can use the internet though (surf, email, etc.).  Maybe there are just some config files to change?
o.O shouldn't that box be around somewhere?

or you can go into firefox and type '192.168.0.0' or '192.168.0.1' in the address bar.

at least i know these 2 are for Linksys and D-link models.
and well, I can't upload files either so....... downloading works though as in your case.

---

### Post by Charlie91 on 2008-06-05
The long RJ-45 cable goes straight to the box at the antenna on the roof (can't access); I don't have documentation.  Meridiantelekoms is the company.  I tried those numbers on the browser and nothing happens.  I'll look at other threads and see what things they say.  In one they suggested removing IPv6, but it didn't work...

---

### Post by Fatfool on 2008-06-05
> **Charlie91 said:**
> The long RJ-45 cable goes straight to the box at the antenna on the roof (can't access); I don't have documentation.  Meridiantelekoms is the company.  I tried those numbers on the browser and nothing happens.  I'll look at other threads and see what things they say.  In one they suggested removing IPv6, but it didn't work...
o.O that sounds like a satallite connection to me. darn.....

---

### Post by Charlie91 on 2008-06-05
Sorry for the piecemeal approach.  There is a Wi-Fi tower 1-2 miles from my house, and my antenna is oriented towards that tower (line-of-sight).  Perhaps the thing is that it's perfectly working since the beginning.  Just the uploading (now).  I still am searching for possible solutions in other threads.

Maybe I'll test it in Windows XP just to be sure it's not the connection...

I'm intrigued by your name (Fatfool).  I hope one of the million other Ubuntu users give us solutions.

---

### Post by Fatfool on 2008-06-05
> **Charlie91 said:**
> Sorry for the piecemeal approach.  There is a Wi-Fi tower 1-2 miles from my house, and my antenna is oriented towards that tower (line-of-sight).  Perhaps the thing is that it's perfectly working since the beginning.  Just the uploading (now).  I still am searching for possible solutions in other threads.

Maybe I'll test it in Windows XP just to be sure it's not the connection...

I'm intrigued by your name (Fatfool).  I hope one of the million other Ubuntu users give us solutions.
oh. i see. a wireless connection. usually the ISP will either sell or lease a special adapter for that; not one you can purchase in retail.

and yeah do test it with XP to see if it works. Also, you could add a comment to the bug report to detail your experiences. I use a DSL connection btw.

as for my name/nick well I believe that everyone is born with a nickname subconciously hidden within them which they will find out sooner or later. this is mine :). (Oh btw i'm not fat nor am I a fool)

oh and correction, its not 'one of the million other Ubuntu users' its 'one of the 8 million other ubuntu users' :D

---

### Post by Charlie91 on 2008-06-05
I'm in XP now... It's working here--I can upload!  It is therefore a problem in my Linux box...  I have yet to file a bug report.  8 million already!  With the inflation going on, I guess Linux should overtake Windows in 5 years time.

---

### Post by Fatfool on 2008-06-05
> **Charlie91 said:**
> I'm in XP now... It's working here--I can upload!  It is therefore a problem in my Linux box...  I have yet to file a bug report.  8 million already!  With the inflation going on, I guess Linux should overtake Windows in 5 years time.
err. i think you should file it in my report since it looks pretty much the same...... no point having multiple entries... gotta say i don't know what the actual procedure is though.

oh and It seems that now i CAN upload!!! i can upload to any site. weird. maybe its one of the recent updates which fixed it? i could try the LiveCD again to test if an older version of hardy still has this problem.

---

### Post by Charlie91 on 2008-06-06
**I can upload now!**  I didn't do anything (maybe the updates yesterday had something to do here); I have to thank you for your time...

---

### Post by darab77 on 2008-06-19
Hi there!

I have the same problem, ubuntu, hardy heron, cant upload files (and i downloaded all the updates, no help). Its not a router problem, i use a notebook (HP Compaq nc6220), and i tried it in my workplace, at home, at my friends place, same results. 
I tried to capture network traffic with wireshark, but i cant use that either. When i try to start a packet cpature, the window turns into grey, and nothing happens.

Can anyone help me, or at least can suggest a distribution wich is not has annoying problems like this?

---

### Post by LinuxNooBee on 2008-07-27
Im having the same problems too. Can't upload photos to any photofinishing services, can't upload to yahoo, can't email photos. I have a similar high-speed internet connection as described earlier, a radio transmitting to a tower nearby. I'd appreciate any help, this is very frustrating. I am using ubuntu 8.04.

---

### Post by LinuxNooBee on 2008-07-28
Upon further investigation, I found I am able to upload large photos from a Mac machine on the same internet connection. That rules out my connection, isp, and router in my opinion, so the problem has to be a setting within ubuntu. I read somewhere numerous posts about a "Max file size" value in a PHP.ini file. However it seems to me that is only for Linux servers. Regardless I havent a clue how to access that file to edit it. 

Im hoping someone out there might be able to assist me in figuring this out. 

Thanks

---

### Post by Fatfool on 2008-07-30
> **LinuxNooBee said:**
> Upon further investigation, I found I am able to upload large photos from a Mac machine on the same internet connection. That rules out my connection, isp, and router in my opinion, so the problem has to be a setting within ubuntu. I read somewhere numerous posts about a "Max file size" value in a PHP.ini file. However it seems to me that is only for Linux servers. Regardless I havent a clue how to access that file to edit it. 

Im hoping someone out there might be able to assist me in figuring this out. 

Thanks
hmmm..... i'm no expert at this... but it seems like no other experience guy has experienced this?

---

### Post by kdorf on 2008-07-30
I have a Realtek wireless card in my box at home, and I found that the Linux implemenation of Realtek wireless drivers is faulty. I didn't have the upload problem you described, but I would just get dropped regularly, particularly when downloading a large amount of data, but sometimes just every so often, even if there wasn't much traffic.

The fix for me was to use ndiswrapper with the latest Windows drivers. Try this, and see if it helps.

Note that you might see some fixes around concerning the use of Aircrack drivers. These DID NOT work for me.

---

### Post by Fatfool on 2008-07-30
> **kdorf said:**
> I have a Realtek wireless card in my box at home, and I found that the Linux implemenation of Realtek wireless drivers is faulty. I didn't have the upload problem you described, but I would just get dropped regularly, particularly when downloading a large amount of data, but sometimes just every so often, even if there wasn't much traffic.

The fix for me was to use ndiswrapper with the latest Windows drivers. Try this, and see if it helps.

Note that you might see some fixes around concerning the use of Aircrack drivers. These DID NOT work for me.
um, mine isn't a wireless problem actually. my starting post described it happening on wireless and on wired.

and it suddenly resolved itself after a period of time. weird eh.

---

### Post by agrobuntu on 2008-08-09
Hi everybody!

I'm having a similar problem with 8.04 server. I can't upload large email attachments (postfix) to my SMTP relay. I can't tell if it happened suddenly, but it's happening all the time now. I think it's been from the beginning, just never noticed it until the queue started to fill up. I haven't tried uploading files as stated in previous posts to some webserver, but I guess it's the same situation. I could try, if you think it'd help to find the real problem.

The server is connected through wired connection, and all other PCs connected to the router work perfectly (XP, Vista, some other Linux distro I'm using (2.4 kernel)). DSL here. Everything else internet or local network works on the server, except big uploads .

I tried with the sysctl (window size, etc.) modifications, no change. I turned off ipv6 no change. Any ideas?

Fatfool: any ideas how it got solved by itself? ;-)

Thanks.

---

### Post by marce34 on 2008-08-16
It's happening to me too with Ubuntu 8.04 and openSUSE 11.0 (firewall disabled).

---

### Post by noobuntu_86 on 2008-09-10
This is my first post in the Ubuntu forums... so hi! I've been using Ubuntu for 2 years now, and all of my problems have been solved using these forums... amazing how I got through 2 years without needing to post!

Anyway, I have uploading dramas as well. So I thought I would add some comments here about my situation, and what I suspect is the problem.

** I have set up a home network, XP on my desktop and Ubuntu 8.04 on my laptop... don't ask why :p XP works absolutely fine. I'm on dualboot with Vista on my laptop which also works fine.
** Download -> full speed on Ubuntu.
** Upload -> peaks to start with, and gradually declines.
** when I sftp to my university workstation, I can "put" at full download speed, but when I "get," the upload speed peaks to begin with at full speed and declines slowly (within about 10-20 secs). However, the upload does finish... eventually.
**I have changed the /etc/modprobe.d/aliases file:

#alias net-pf-10 ipv6
alias net-pf-10 off

This tells me that it's not an issue relating to browser, connection, ethernet port/wireless etc. However, interestingly, changing the aliases file corrected my webcam dropping out in the new version of Skype, which essentially is a download/upload program... this is wierd...

Personally, I think it's a driver issue.
see [this post (click here!)]("http://www.dslreports.com/forum/r21030423-Please-help-with-slow-upload-in-Ubuntu")

However details are not clear how to fix this problem. I will look into it and get back to you all ASAP...

This is *definately* a problem with an Ubuntu driver.

I suspect FatTool updated a driver without realising perhaps?

---

### Post by noobuntu_86 on 2008-09-10
It's possible that there's a problem with the drivers. There was a problem with the realtek drivers which has now been resolved:

[CLICK HERE]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/114171")
(if you have a Realtek driver)

Unfortunately.. I don't...

go to a terminal and type:

gedit /var/log/dmesg

and do a search for: eth0

I get:

Intel(R) PRO/1000

I will look for new drivers. anyone else have the same? perhaps this is the problem?

Alternatively just type in terminal:
lspci

---

### Post by noobuntu_86 on 2008-09-11
Advance in the problem:

I've updated my drivers (although it didn't work properly, so that is still a possible solution.) I also followed this link:

[LINK]("http://ubuntuforums.org/showthread.php?t=826020&highlight=slow+upload")

and did what they said. I noted that uploads are *definately* going faster with this fix, but still not full speed. By sftp to my institution workstation, I found that instead of gradually declining down to a pathetic 0.1kb/s (no typo there), it stalled temporarily -> decreased, then spiked and slowly decreased again, stalling, and repeating, but nevertheless, this is definately faster.

PROBLEM NOT SOLVED, but getting closer. I hope this helps someone though...

---

### Post by agrobuntu on 2008-09-18
> **noobuntu_86 said:**
> It's possible that there's a problem with the drivers. There was a problem with the realtek drivers which has now been resolved:
----SNIP---


Well, I can't exactly say why, but this is how I fixed it:

Noobuntu was right, I guess, in that it had to do with the driver.

My lappy is running with a Realtek 8101e which was correctly detected and loaded, but showed the symptoms described by the other posters, that is, I had a timeout sending my emails, everything else seemed to work.

Anyway, I went a bit more radical, I compiled my own kernel, then used the driver you can download from Realtek and now everything's fine. Except for the fact that it takes AGES for the system to boot (Loading linux ..... etc, like 5 minutes or more), but it's not supposed to boot often anyway, so I can live with that. So if you ask me, it's either a Ubuntu-kernel issue or something about the drivers or both. And yes, I still have IPv6 disabled and some of the sysctl tuning mentioned elsewhere in this post also. But again, it didn't work until the kernel compilation. I did change the driver before re-compiling but doing both is what really fixed it for me.

I hope this helps anyone.

---

### Post by Sniqs on 2008-10-04
I have a similar problem. I can only send attachments/upload files that are <200kB. With larger files, the speed stalls and eventually it times out. I'm using Hardy on a desktop that also serves as a router for a laptop (two NICs in it: an onboard Marvell Yukon using the sky2 driver and a PCI RTL-8139). The interesting things I've found:

- Everything works well under Windows XP
- Everything works well from a LiveCD 
- Once installed on the disk (even before any updates) it doesn't work well anymore (timeout)
- Everything works decently (it's not lightning but it does work ok) when I **physically take the Realtek out of the computer**. Ifdown doesn't help, the card has to be taken out of the slot. 

Atm I'm looking for a router so that should solve my problems, but it is rather interesting IMO. Seems like there is some kind of a conflict between the two cards. However, the laptop has no problems sending large attachments... Also the desktop has no problems with torrents (smaller chunks?). If anyone is interested I can provide more info, just tell me what you need.

---

### Post by marce34 on 2009-02-05
It seems to be related to the TCP Window Scaling problem ([http://en.wikipedia.org/wiki/Window_scaling ](http://en.wikipedia.org/wiki/Window_scaling )) as I have changed that value and the problem's gone for me (I have Intrepid 32bit). I just edited /etc/sysctl.conf, added this at the end of the file:

net.ipv4.tcp_window_scaling = 0

and typed sudo sysctl -p at a terminal (this prevents a restart of the system).

Try it and tell me what happened.

---

### Post by balkie99 on 2009-04-08
Hi there!

No connection, no speed problem, but the same problem: cannot upload anything to anywhere. It opens the window where I should be able to browse files, but nothing happens, this window is "dead", I can only close it.
Firefox is ok, no NoScript, I have Java, everything ok, I can browse, etc. 

What to do?
Or at least
What to try?

Thanks for help.

---

### Post by marce34 on 2009-04-08
> **balkie99 said:**
> Hi there!
No connection, no speed problem, but the same problem: cannot upload anything to anywhere. It opens the window where I should be able to browse files, but nothing happens, this window is "dead", I can only close it.
Firefox is ok, no NoScript, I have Java, everything ok, I can browse, etc. 


Have you tried other browser? (just to isolate the problem)

Greetings,
//.arce

---

### Post by balkie99 on 2009-04-09
hi!

Yes, I did try Opera, same problem.

Is there any test or terminal command I should run to test what is the cause?

Thanks
b

---

### Post by Spider7 on 2009-04-09
> **balkie99 said:**
> hi!

Yes, I did try Opera, same problem.

Is there any test or terminal command I should run to test what is the cause?

Thanks
b

if can find a server, try upload through ftp.

---

### Post by Spider7 on 2009-04-09
packet capture that includes a slowdown will be very helpful.

---

### Post by balkie99 on 2009-04-09
Hi,
To make it clearer: I am not an intensive uploader, I do not use any ftp, my problem is, I can not add attachments to my mails, neither hotmail, nor gmail, nor my sun messenger mail, and even cannot upload anything to my googlegroups pages. Nothing. No slow upload - I can not upload.
Maybe some general settings in intrepid, or I installed something (amsn, or else) what causes the problem.
I dont know if that matters, but I CAN chat using amsn or pidgin.
And tested my speed test and the download and upload speed is OK.
I am confused, I like ubuntu, but this problem makes me a bit "halfhanded".

---

### Post by balkie99 on 2009-04-09
A solution, but what is this???

Check this out.
What I did today, was to download the latest updates for Ibex.

Then, just to see, I tried attaching files- and it works, BUT somehow strangely:

Lets say I have a folder Documents, and in it a folder ABC, and it that some files, from which I would like to upload.

I click the Browse button in the mail window (for example my work mail). A windiw opens: Open file. Now, I can click on the left to Documents. On the right, my folders appear, including ABC. BUT! If i click on ABC, nothing happens, even the active "orange" line does not skip to it from the first row.

but If after clicking Browse, it opens Open file window, and THEN i click to maximize this window, I click on folder ABC and it opens and I can choose my file.

AND! If I do not maximize the Open file window, and click on ABC, it does not show any activity, but after this maximizing - it shows files in ABC. 

I can not understand it, maybe some programmers might, but I tried it several times and it works this way. 
Let me know, if you find out why, now I am happy that it works. (but it would be useful to know why, so next time i could deal with it better...)

---

### Post by balkie99 on 2009-04-11
I got a hint that it might be nautilus problem...So I did, what i had been said and reinstalled nautilus...the things started to NOT work again.

Since then I have reinstalled the wholu ibex, but have the same problem. 
Now, my comp freeze every time I click upload or attach and browse in any website. 

A changed nautilus to thunar, but nothing happened, freezing.
I have installed the Gnome Do, but think that does not do anything.

What to do? There must be a command or test I could run to see where is the problem, not?

---

### Post by marce34 on 2009-04-11
> **balkie99 said:**
> What to do? There must be a command or test I could run to see where is the problem, not?

Have you tried, as I said, changing tcp window scaling?. Type this on a terminal:

sudo -s
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

---

### Post by balkie99 on 2009-04-11
Hi marce34!

Yes, I have already tried it and it does not seem to be the problem.

It makes me feel sick...

---

### Post by balkie99 on 2009-04-12
So...

I have a 64bit system. I have put on the 64x version of ibex.
Intentionally, did not download any updates.

Attaching, uploading works. From Openoffice and on hotmail only when I maximize the window, but it works.
Is there any problem with updates? How could I check what not to download to avoid my previos problems?
Or should I stay without all those updates?

I am afraid it will happen again, no uploading, and I cannot understand, why, even on a freshly installed system it works sometimes only when maximizing window. But it works...

---

### Post by balkie99 on 2009-04-13
Last?

Hi, so.... A difference: when I click visaul effects to normal or extra, the above things happen. When leaving it on "none", so no fancy visual effects, then everything works. I do not know, what the cause is, but surely will not change this...
As anyone gets an idea, what had caused my problems, please, let me know.
Thanks.

---

