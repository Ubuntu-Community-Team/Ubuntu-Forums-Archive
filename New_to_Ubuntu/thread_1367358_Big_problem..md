---
title: "Big problem."
date: 2009-12-29
forum: New to Ubuntu
---

### Post by e.jejcic on 2009-12-29
Good morning to everybody:Well. I have a big problem. A couple of days ago came to my house a SOB (happends to be a member of the family!!). Anyway. in a minute I left the computer running alone somehow he inserted a memory card (he have a support of a informatic expert) and screwed my rythmbox (I can·t listen to any music at all (even on Internet.I can·t remove and re.install rythmbox, because it ask me to remove the flashplayer, that I cannot. I can·t update either.I would need a big assistance from you. I don·t know what to do!!!.Please help.Thanking in advance from Eduardo. I am running Ubuntu 9.10.

---

### Post by HarrisonNapper on 2009-12-29
Why can you not remove flash player? I don't think an external storage device in and of itself would mess up rythmbox. Have you tried playing media in other players? Does sound work in general?

Most importantly, run rythmbox from terminal, recreate the problem, and post the terminal output here. (To run it in terminal, just open a terminal and type "rythmbox")

Cheers.

---

### Post by e.jejcic on 2009-12-29
Thanks for the reply. I ty6ped rythmbox in a termina and the response was  command not found.When I go to installed programs I find the flashplayer . Then Ihightligted it and then I pressed to remove and nothing happened.Then I go to update and it tell me that can make a partial update I say OK and tell me that I have the flashplayer corrupted (??).Then I removed it and the update stops saying I need to remove ti manually.So I don·t know what to do (Ihope t5hey are dead now9 Sorry my english. Hope you understand. Thanks from Eduardo. (argentina). Good holidays.

---

### Post by e.jejcic on 2009-12-29
eduardo@eduardo-desktop:~$ rythmbox
No command 'rythmbox' found, did you mean:
 Command 'rhythmbox' from package 'rhythmbox' (main)
rythmbox: command not found
eduardo@eduardo-desktop:~$ 







































eduardo@eduardo-desktop:~$ rythmbox
No command 'rythmbox' found, did you mean:
 Command 'rhythmbox' from package 'rhythmbox' (main)
rythmbox: command not found
eduardo@eduardo-desktop:~$ 

I forgot to tell no sound at all, Not even from the cd plyer no frm internet radio. Regards from Eduardo. Thanks a lot.

---

### Post by nerdy_kid on 2009-12-29
rhythmbox not rythmbox

btw, <TAB> == autocomplete; so if you type rhyt the hit <tab> it should finish it for you.

---

### Post by ezsit on 2009-12-29
> he inserted a memory card (he have a support of a informatic expert) and screwed my rythmbox (I can·t listen to any music at all

The sequence of events does not make any sense whatsoever. Reading a memory card and sound working supposedly have nothing to do with each other. There must be something else to explain the coincidence. Worst case, have the SOB that messed it up come and fix the problem.

---

### Post by FinalCoyote on 2009-12-29
yeah, first of all rhythmbox (make sure the spelling is right or it won't work)

i had a similar problem, in respect to sound not working, but i simply went
System->Preferences->Sound

opened the hardware tab and changed [B]Settings for the selected device:
[/B]to Digital Stereo Duplex

Now i dunno if your hardware will have that option, but play about

---

### Post by thatguruguy on 2009-12-29
Can you hear other sounds?

Also, have you checked to make sure that he didn't change the default music directory within Rhythmbox?  Are your songs showing up in your Rhythmbox library?

---

### Post by e.jejcic on 2009-12-29
A big sorry. Itold you sorry my english.eduardo@eduardo-desktop:~$ rhythmbox

** (rhythmbox:1933): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:1933): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:1933): Rhythmbox-WARNING **: Could not open device /dev/radio0

---

### Post by HarrisonNapper on 2009-12-30
post the output of these commands here:

```

lspci
ls /dev
cat /dev/radio0

```

---

### Post by e.jejcic on 2009-12-30
Good afternoon to everybody(now in here is 14.40Hrs. local time).
First lspci:
eduardo@eduardo-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
eduardo@eduardo-desktop:~$ 
 

eduardo@eduardo-desktop:~$ ls/dev
bash: ls/dev: No such file or directory
eduardo@eduardo-desktop:~$ 


eduardo@eduardo-desktop:~$ cat/dev/radio0
bash: cat/dev/radio0: No such file or directory
eduardo@eduardo-desktop:~$ 

The change to ..digital stuff doesn·t do any change.Good idea to make SOB come and repair it(no food till repaired).Thanks from Eduardo.

---

### Post by skierkyles on 2009-12-30
You need a space in between ls and /dev, and between cat and /dev/radio0 
```
ls /dev
```

and 

```
cat /dev/radio0
```

---

### Post by e.jejcic on 2009-12-30
I am sorry I am not a very good peduardo@eduardo-desktop:~$ ls /dev
adsp             loop5               ram7        stdout  tty37  ttyS0
agpgart          loop6               ram8        tty     tty38  ttyS1
audio            loop7               ram9        tty0    tty39  ttyS2
binder           lp0                 random      tty1    tty4   ttyS3
block            mapper              rfkill      tty10   tty40  urandom
bus              mcelog              rtc         tty11   tty41  usbmon0
cdrom            mem                 rtc0        tty12   tty42  usbmon1
cdrw             mixer               scd0        tty13   tty43  usbmon2
char             net                 sda         tty14   tty44  usbmon3
console          network_latency     sda1        tty15   tty45  usbmon4
core             network_throughput  sda2        tty16   tty46  usbmon5
cpu_dma_latency  null                sda3        tty17   tty47  v4l
disk             oldmem              sda5        tty18   tty48  vcs
dri              parport0            sda6        tty19   tty49  vcs1
dsp              pktcdvd             sdb         tty2    tty5   vcs2
dvd              port                sdc         tty20   tty50  vcs3
dvdrw            ppp                 sdd         tty21   tty51  vcs4
ecryptfs         psaux               sde         tty22   tty52  vcs5
fb0              ptmx                sequencer   tty23   tty53  vcs6
fd               pts                 sequencer2  tty24   tty54  vcs7
fd0              ram0                sg0         tty25   tty55  vcs8
full             ram1                sg1         tty26   tty56  vcsa
fuse             ram10               sg2         tty27   tty57  vcsa1
hidraw0          ram11               sg3         tty28   tty58  vcsa2
hpet             ram12               sg4         tty29   tty59  vcsa3
input            ram13               sg5         tty3    tty6   vcsa4
kmsg             ram14               shm         tty30   tty60  vcsa5
log              ram15               snapshot    tty31   tty61  vcsa6
loop0            ram2                snd         tty32   tty62  vcsa7
loop1            ram3                sndstat     tty33   tty63  vcsa8
loop2            ram4                sr0         tty34   tty7   video0
loop3            ram5                stderr      tty35   tty8   zero
loop4            ram6                stdin       tty36   tty9
eduardo@eduardo-desktop:~$

---

### Post by e.jejcic on 2009-12-30
ubuntu.com - launchpad.net - ubuntu help 
Search  go   

	 	Ubuntu Forums > The Ubuntu Forum Community > Absolute Beginner Talk > [ubuntu] Big problem. 
 Reply to Thread 
	Welcome, e.jejcic.
You last visited: 18 Hours Ago at 09:10 PM 
Private Messages: Unread 0, Total 0.
User CP	Forum Help 	Forum Council 	New Posts	Search 	Quick Links 	Log Out

Absolute Beginner Talk
The perfect starting place to find out more about computers, Linux and Ubuntu. 

Thread: [ubuntu] Big problem.
Reply to Thread 
Logged in as e.jejcic Title:
	  	

Message:			Fonts	
		Sizes	
			
	
				
			
				 	

																						
	Smilies







[More]



Post IconsYou may choose an icon for your message from the following list:
No icon    														
 														

  


Additional Options 
Miscellaneous Options
Automatically parse links in text
Disable smilies in text
Attach Files
Valid file extensions: bmp bz2 doc gif gp3 gp4 gp5 gpl gz jpe jpeg jpg odg odp ods odt pdf png psd py sh svg tar tg txt xcf zip
 
Thread SubscriptionNotification Type:


  


Topic Review (Newest First) 
1 Minute Ago 03:22 PM
e.jejcic	Re: Big problem.
I am sorry I am not a very good peduardo@eduardo-desktop:~$ ls /dev
adsp loop5 ram7 stdout tty37 ttyS0
agpgart loop6 ram8 tty tty38 ttyS1
audio loop7 ram9 tty0 tty39 ttyS2
binder lp0 random tty1 tty4 ttyS3
block mapper rfkill tty10 tty40 urandom
bus mcelog rtc tty11 tty41 usbmon0
cdrom mem rtc0 tty12 tty42 usbmon1
cdrw mixer scd0 tty13 tty43 usbmon2
char net sda tty14 tty44 usbmon3
console network_latency sda1 tty15 tty45 usbmon4
core network_throughput sda2 tty16 tty46 usbmon5
cpu_dma_latency null sda3 tty17 tty47 v4l
disk oldmem sda5 tty18 tty48 vcs
dri parport0 sda6 tty19 tty49 vcs1
dsp pktcdvd sdb tty2 tty5 vcs2
dvd port sdc tty20 tty50 vcs3
dvdrw ppp sdd tty21 tty51 vcs4
ecryptfs psaux sde tty22 tty52 vcs5
fb0 ptmx sequencer tty23 tty53 vcs6
fd pts sequencer2 tty24 tty54 vcs7
fd0 ram0 sg0 tty25 tty55 vcs8
full ram1 sg1 tty26 tty56 vcsa
fuse ram10 sg2 tty27 tty57 vcsa1
hidraw0 ram11 sg3 tty28 tty58 vcsa2
hpet ram12 sg4 tty29 tty59 vcsa3
input ram13 sg5 tty3 tty6 vcsa4
kmsg ram14 shm tty30 tty60 vcsa5
log ram15 snapshot tty31 tty61 vcsa6
loop0 ram2 snd tty32 tty62 vcsa7
loop1 ram3 sndstat tty33 tty63 vcsa8
loop2 ram4 sr0 tty34 tty7 video0
loop3 ram5 stderr tty35 tty8 zero
loop4 ram6 stdin tty36 tty9
eduardo@eduardo-desktop:~$ 
12 Minutes Ago 03:09 PM
skierkyles	Re: Big problem.
You need a space in between ls and /dev, and between cat and /dev/radio0 
Code:
ls /dev
and 

Code:
cat /dev/radio0
17 Minutes Ago 03:05 PM
e.jejcic	Re: Big problem.
Good afternoon to everybody(now in here is 14.40Hrs. local time).
First lspci:
eduardo@eduardo-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
eduardo@eduardo-desktop:~$ 


eduardo@eduardo-desktop:~$ ls/dev
bash: ls/dev: No such file or directory
eduardo@eduardo-desktop:~$ 


eduardo@eduardo-desktop:~$ cat/dev/radio0
bash: cat/dev/radio0: No such file or directory
eduardo@eduardo-desktop:~$ 

The change to ..digital stuff doesn·t do any change.Good idea to make SOB come and repair it(no food till repaired).Thanks from Eduardo. 
3 Hours Ago 12:09 PM
HarrisonNapper	Re: Big problem.
post the output of these commands here:

Code:
lspci
ls /dev
cat /dev/radio0
18 Hours Ago 08:56 PM
e.jejcic	Re: Big problem.
A big sorry. Itold you sorry my english.eduardo@eduardo-desktop:~$ rhythmbox

** (rhythmbox:1933): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:1933): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:1933): Rhythmbox-WARNING **: Could not open device /dev/radio0 
18 Hours Ago 08:51 PM
thatguruguy	Re: Big problem.
Can you hear other sounds?

Also, have you checked to make sure that he didn't change the default music directory within Rhythmbox? Are your songs showing up in your Rhythmbox library? 
18 Hours Ago 08:49 PM
FinalCoyote	Re: Big problem.
yeah, first of all rhythmbox (make sure the spelling is right or it won't work)

i had a similar problem, in respect to sound not working, but i simply went
System->Preferences->Sound

opened the hardware tab and changed Settings for the selected device:
to Digital Stereo Duplex

Now i dunno if your hardware will have that option, but play about 
18 Hours Ago 08:43 PM
ezsit	Re: Big problem.
Quote:he inserted a memory card (he have a support of a informatic expert) and screwed my rythmbox (I can·t listen to any music at all 

The sequence of events does not make any sense whatsoever. Reading a memory card and sound working supposedly have nothing to do with each other. There must be something else to explain the coincidence. Worst case, have the SOB that messed it up come and fix the problem. 
18 Hours Ago 08:42 PM
nerdy_kid	Re: Big problem.
rhythmbox not rythmbox

btw, <TAB> == autocomplete; so if you type rhyt the hit <tab> it should finish it for you. 
18 Hours Ago 08:35 PM
e.jejcic	Re: Big problem.
eduardo@eduardo-desktop:~$ rythmbox
No command 'rythmbox' found, did you mean:
Command 'rhythmbox' from package 'rhythmbox' (main)
rythmbox: command not found
eduardo@eduardo-desktop:~$ 

This is what appears when I paste terminal output.(rare not???).





































eduardo@eduardo-desktop:~$ rythmbox
No command 'rythmbox' found, did you mean:
Command 'rhythmbox' from package 'rhythmbox' (main)
rythmbox: command not found
eduardo@eduardo-desktop:~$ 

I forgot to tell no sound at all, Not even from the cd plyer no frm internet radio. Regards from Eduardo. Thanks a lot. 
This thread has more than 10 replies. Click here to review the whole thread. 


Posting Rules 
You may post new threads
You may post replies
You may post attachments
You may edit your posts
BB code is On
Smilies are On
[IMG] code is On
HTML code is Off
Forum Rules


All times are GMT -3. The time now is 03:22 PM.
Contact Us - Ubuntu Forums - Archive - Top 


vBulletin ©2000 - 2009, Jelsoft Enterprises Ltd. Ubuntu Logo, Ubuntu and Canonical © Canonical Ltd. Tango Icons © Tango Desktop Project. bilberry

---

### Post by e.jejcic on 2009-12-30
Sorry, I can·t post cat /dev/radio0 output from terminal. Shows the thing that is in the last post. Weird no?.Eduardo.

---

### Post by HarrisonNapper on 2009-12-30
Well, one problem is that rhythmbox is trying to play from a radio receiver that you do not have. As far as your sound issues, I know that there have been issues with karmic and sound as well as issues from some of the more recent kernels. My suggestion would be to forget rhythmbox for the time being and try googling "karmic no sound" or something similar to that. I would be remiss to point you in a single direction, as afaik there is no single solution that has worked.

Probably, with sound, it's best to start with the mixer and make sure nothing is muted. Right-click the audio icon in the notification area and open the mixer from there. If you don't see anything there, run "alsamixer" in terminal and, again, make sure nothing is muted. Some have reported that turning the volume up and then down again helps. Another one I've seen if it's a kernel problem is disabling the software modem in BIOS. Probably search for the problem before resorting to anything in the BIOS, though :)

Good luck and let us know how you fixed it when you do.

Cheers.

---

### Post by e.jejcic on 2009-12-30
good evening to everybody:I really want to give the tanks to everybodu who answer the post I made. You people are really helpfull.The answers were fast and helpfull. I know now that Ihave to learn english and a lot of Ubuntu.Thankyou very much for your time. Eduardo.

---

### Post by Don1500 on 2009-12-30
> **e.jejcic said:**
> good evening to everybody:I really want to give the tanks to everybody who answer the post I made. You people are really helpful.The answers were fast and helpful. I know now that I have to learn English and a lot of Ubuntu.Thank you very much for your time. Eduardo.

Have you fixed the problem?
If not, try this page, follow everything closely  and you will have sound => [[COLOR="Red"]Sound from Ubuntu[/COLOR]]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html") (Don't worry that it says 9.04, it will work)

---

### Post by theozzlives on 2009-12-30
I can't help you with the sound, but from a security perspective, lock your screen when you leave your machine. I live alone and make a habit of doing that.

---

### Post by e.jejcic on 2010-01-01
Good new year to all of you.I·ll try to resume all problems I have:
1) sound: not solved yet.
2) can·t update.Only partial, stops and ask to remove adobe flashplayer mannualy, cannot do it.
3) Sreensaver does·nt work. So lock screen.
QUESTONS:
1) ¿Is in here any program to stop autorun in USB sticks?.( like in windows with "vaccinate". Or with mounting it is enough.
2) ¿Is any possibility to inject malware into the system whit a USB stick with autorun in it?.
4) Do you think if I reinstall Ubuntu 8.10 all the problems will be gone?. Itried, but partitions look weird to me. Looks that I going to wip out my windows partition. I dont know how to format Ubuntu partition only.
Well, I think is enough for this year.Thanks for all the help. Regards from Eduardo.

---

### Post by e.jejcic on 2010-01-07
Weell everything looks OK for now.What I did??. I reinstal Ubuntu 8.04 and upgraded gradually to 9.04.Install flash playerand everything works OK now.The thing with sound was terrible (what a dummy) the plugs from headphones were reversed. The screen locks now, updates work. So now I am working with Ubuntu 9.04. I am affraid to upgrade to 9.10.I·have asked for a live CD from Cannonical. Everything is working for now. I shall thanks to everybody·s time and help. I really appreciated it.Regards from Eduardo.
I want to put this thread as SOLVED.

---

### Post by HarrisonNapper on 2010-01-08
To mark the thread solved, edit the first post and edit it from advanced mode. A reinstall is sometimes all that is required to fix some problems, glad to hear you got it working. If you're going to upgrade to 9.10, I would recommend doing a fresh install from the LiveCD or a LiveUSB.

>  I know now that Ihave to learn english and a lot of Ubuntu. 

Actually, with Ubuntu, this may not be necessary. Search around and you should be able to find forums in your native language. Of course, if you want to learn another language, I personally find the process is a fun and engaging way to spend time and it will enhance the set of skills you have to give to the community. But I shouldn't think English is a requirement for running Ubuntu or looking for support therefrom. I realize this may be wishful thinking for some languages, but for those where support is inadequate, we would definitely appreciate any help on translating help documents, man pages, and forum questions and answers.

Cheers.

---

### Post by 3rdalbum on 2010-01-08
Removing Rhythmbox and reinstalling it would have done nothing anyway, because there's no way this person could have modified the Rhythmbox program itself. What you should have tried is removing the Rhythmbox settings from the .gnome2 and .config directories in your home directory - this causes Rhythmbox to start afresh as though you've never used it.

Removing the settings file fixes problems.

---

