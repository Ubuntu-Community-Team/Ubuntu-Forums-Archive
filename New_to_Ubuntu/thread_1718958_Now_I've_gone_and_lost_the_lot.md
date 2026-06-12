---
title: "Now I've gone and lost the lot"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by Ireallyneedhelp on 2011-04-01
I did an upgrade yesterday on my desk top (posting here from laptop) and I've lost everything. When I boot up I can get neither get windows NOR Ubuntu. In short I was being too clever. I checked for upgrades and saw the Beta version of Ubuntu (11).
At the same time I was tying to stop the machine asking for a password every few minutes. I was getting a bit miffed so I kept saying yes to everything. Result? When I boot up I get nothing except a blank screen. I've tried to get back to windows safe mode but still nothing.

Reading about the upgrade this morning, there is a part saying "not for test machines."
I assumed I didn't have a test machine but just remembered that I have a dual boot (to see if I prefer Ubuntu). I am truly an idiot.

I take it that all is lost? I don't have a start up disc (I'll remember next time). All I have is my original Windows XP disc. Any other suggestions?

I don't mind about losing anything in XP as I have all my files, photos, music etc stored safely on mp4s, pen drives etc. I really just want something to work.

Thanks in advance.

---

### Post by Hedgehog1 on 2011-04-01
The xp install CD is also the emergency boot CD.  You need to do the FIXMBR step to get Windows booting again.

Once you do that, you can delete the Ubuntu 11.04 partitions and install 10.04 or 10.10 instead.

***The Hedge***

:KS

---

### Post by muteXe on 2011-04-01
Can you download a live cd from a mate's machine and use that on yours?  It would be useful to see if your data's still on there before you start deleting partitions.

---

### Post by Ireallyneedhelp on 2011-04-01
My install CD won't install. I get a black screen. Will I bin it?

---

### Post by Ireallyneedhelp on 2011-04-01
Now back in. Did a chkdsk fix and it appears OK. Looked at Ubuntu and it says I have version 10.10 rev197. Is there any way I can find out if version 11 is lurking somewhere? I'm leaving the computer on overnight as I'm not convinced it will start up tomorrow. Thanks again folks. I really appreciate your responses. Assuming all is well, how do I prepare boot discs? My old machine has drive a.

---

### Post by Blasphemist on 2011-04-01
Glad to see you are back up but I can tell your trust still isn't back. 

I too have a laptop with Ubuntu and Win 7 on it. I have a Satellite L505-S6946 with 3GB, Intel Core 2 Duo T6400, Intel 4599MHD graphics, Intel Wi-Fi Link 5100AGN with the laptop display and a Acer monitor. Not a power machine. 

I upgraded to Natty at alpha 3 and that was rocky but since it went to beta it has been very solid. I didn't like unity when it was at alpha but now I'm very pleased.

Just my experience. Upgrades can and do work. Stuff can go wrong but usually attention to detail should help keep such a bad experience as you had from happening.

---

### Post by JKyleOKC on 2011-04-01
> **Ireallyneedhelp said:**
> Now back in. Did a chkdsk fix and it appears OK. Looked at Ubuntu and it says I have version 10.10 rev197. Is there any way I can find out if version 11 is lurking somewhere?Ubuntu doesn't follow the usual customs for revision numbers; instead they use yy.mm (year, month) so 10.10 is from October 2010. The next one out will be 11.04, released toward the end of this month. They do a new one every six months.

The "rev197" sounds like it's coming from the "grub" menu (the boot loading menu) since the boot loader is at revision 1.97. It follows the usual numbering approach, but there's no schedule published for when it might move to 1.98...

---

### Post by matt_symes on 2011-04-01
Hi

Open a terminal and type

```
uname -a
```

Post back results. That will tell your kernel version. Look for a xxxx.35. You're not having much luck.

Kind regards

---

### Post by Ireallyneedhelp on 2011-04-02
> **matt_symes said:**
> Hi

Open a terminal and type

```
uname -a
```Post back results. That will tell your kernel version. Look for a xxxx.35. You're not having much luck.

Kind regards
I'll post back later today. I'm currently going through the XP settings to make sure it's all OK. I'll then prepare a boot disc in case it happens again. 
After I got the beast up and running, I went to "add/Remove programs"in XP. That's where I saw the Ubuntu 10.10 rev197. 

1 Should the XP prog list show I have Ubuntu? I thought it was on a different partition.
2 I'll try later to see if I still have Ubuntu.
3 Do you suggest I delete it? If so do I do it through Xp Add/Remove programs?

---

### Post by Hedgehog1 on 2011-04-02
> **Ireallyneedhelp said:**
> 
After I got the beast up and running, I went to "add/Remove programs"in XP. That's where I saw the Ubuntu 10.10 rev197. 


You have a WUBI install of Ubuntu.  This changes things a bit; some of the advice you were given was based on an a traditional dual-boot assumption.

So we can avoid confusing you in the future, as long as you are running Ubuntu that shows up in Add/Remove programs in XP, please lets folks know you have a WUBI (**W**indows **UB**untu **I**nstal) when you post.

If you are in doubt, you can remove Ubuntu in Add/Remove programs, and then reinstall it with a clean LiveCD/LiveUSB.  Please save any data you have in Ubuntu before you remove the current install.  **As a note:** 11.04 has a bug in it's current state that does not work with WUBI.  Please re-install 10.10 or 10.04 for now.

***The Hedge***

:KS

**EDIT:** matt_symes - I think I beat your post by a few seconds! We were typing at the same time!

---

### Post by matt_symes on 2011-04-02
Hi

> **Ireallyneedhelp said:**
> I'll post back later today. I'm currently going through the XP settings to make sure it's all OK. I'll then prepare a boot disc in case it happens again. 
After I got the beast up and running, I went to "add/Remove programs"in XP. That's where I saw the Ubuntu 10.10 rev197. 

1 Should the XP prog list show I have Ubuntu? I thought it was on a different partition. 

I think you may have a Wubi install ?

```
sudo fdisk -l
```

(small L) will confirm (From a LiveCD).

> 2 I'll try later to see if I still have Ubuntu.
3 Do you suggest I delete it? If so do I do it through Xp Add/Remove programs?

We need to confirm your installation type first. IIRC, You can migrate a Wubi install to a full partition install so don't delete it just yet.

Kind regards

---

### Post by Ireallyneedhelp on 2011-04-02
Uninstalled Ubuntu. Reinstaled ubuntu. More problems.
1 System requires restart. How do I do this? The restart--help is of little use.
2 I STILL don't have the option of choosing betqeen XP and ubuntu. I have to guess around 12 seconds, press the down arrow, then press enter.

I am losing the will to live.

---

### Post by Hedgehog1 on 2011-04-02
> **Ireallyneedhelp said:**
> I am losing the will to live.

Reality Check - It is only a stupid computer.  You can always get another computer (worst case).  :D

> **Ireallyneedhelp said:**
> Uninstalled Ubuntu. Reinstaled ubuntu. More problems.
1 System requires restart. How do I do this? The restart--help is of little use.

Is this what you are asking about?
[IMG]http://img846.imageshack.us/img846/8349/restartubuntu.png[/IMG]

> **Ireallyneedhelp said:**
> 2 I STILL don't have the option of choosing betqeen XP and ubuntu. I have to guess around 12 seconds, press the down arrow, then press enter.

OK - I just learned this myself yesterday:

Get into Ubuntu (using your guessing method)  and the from the terminal (Menu to: Applications >> Accessories >> Terminal) do this:

```
gksudo gedit /etc/default/grub
```

```
[COLOR="Red"]The change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]To this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]And save and exit the file.[/COLOR]
```

***Removing the '#' turns this from a 'comment' line to a 'real' line.***

Finally, do this:

```
sudo update-grub
```

Now when you reboot, you should see the grub menu, and (hopefully) find windows in the list.

***The Hedge***

:KS

---

### Post by Ireallyneedhelp on 2011-04-02
Thanks hedgehog1. If I had managed to get into Ubuntu I would indeed have clicked "restart." The trouble was that while I was guessing when to press arrows to select Ubuntu, I must have pressed twice as I wasn't taken to the Ubuntu screen but rather a screen that had information scrolling down the screen.

I am now back in (huzzah was the cry) and am re-entering all the info received from Matt and others. 
First I had to change my keyboard to Spanish.

I entered the code you posted. Will this now give me the option between the two systems?

 Now to hunt for Skype. I thought the first time I did this that Skype was there as an installed program. It appears not to be there now.

---

### Post by Ireallyneedhelp on 2011-04-02
Here we go again. I don't have half the stuff in the software centre I had before. Where's Cheese etc? Linphone? Aaargh!
Can't get Skype to download. Windows 7 beckons.

---

### Post by Hedgehog1 on 2011-04-02
Dave,

On the serious side - you need to select the OS that is right for you and your hardware.  Given your situation, I wonder if operating in Windows 7 would perhaps be the best choice for you right now.  Ubuntu is great fun when it works for you.  But if it is really not working for you right now, Windows 7 will keep you operational.  Win7 is the best Windows OS so far.

I prefer Ubuntu myself, but I am a realist.  You can always try Ubuntu again on your next PC.

Just a thought....


***The Hedge***

:KS

---

### Post by Ireallyneedhelp on 2011-04-02
You're probably correct Hedge. After a successful download of Ubuntu and another test to see if I get the choice between the 2 systems ( I do, so thanks), I find it somewhat annoying to find that the "successful" download didn't include what I had a few days back. Ekiga? Skype? There's also no sign of Canonical Partners. Perhaps they too have given up on me.

I downloaded the static version of Skype ... extracted it .. but it won't load. I'll give it another bash tomorrow and if I have no joy, I'll bid you all a fond farewell.

If I do go, I'd like to thank the posters - especially Matt - for his kind and helpful advice. He got me up and running until I mucked the system up. I blame the power cut we had while doing an upgrade.

Maybe later ...

---

### Post by Ireallyneedhelp on 2011-04-03
Hallelujah! Instead of annoying you guys I decided to read all about Ubuntu. It makes for sore reading at night, but in case anyone cares ... it's all back. You name it - I've got it. Skype works a treat - with video. All files from XP moved across;
Docs, spreadsheets etc. I WILL NOT BE BEATEN BY A MACHINE!

---

### Post by matt_symes on 2011-04-03
That's the spirit :D :D :D

---

### Post by Ireallyneedhelp on 2011-04-03
> **matt_symes said:**
> That's the spirit :D :D :D
Still not got Voipcheap tho'
I tried iy with Linphone - no joy.
I tried it with Ekiga - no joy.

(I am getting weird sybold as I type ... eh? My letter "y" is weird. )

---

### Post by matt_symes on 2011-04-03
Hi

> **Ireallyneedhelp said:**
> Still not got Voipcheap tho'
I tried iy with Linphone - no joy.
I tried it with Ekiga - no joy.


I would try to run this through wine (it's a windows installer, yes ?). Have you tried that ? Do you know how to ?

> (I am getting weird sybold as I type ... eh? My letter "y" is weird. )

Not quite with you. Is your keyboard set up correctly ?

System->Preferences->Keyboard. Go to the Layout tab and make sure it's set up for your keyboard.

Kind regards

---

### Post by Ireallyneedhelp on 2011-04-03
Thanks Matt. Keyboard set up correctly. This only happened as I was typing. After I sent the post it read OK.

---

### Post by Ireallyneedhelp on 2011-04-03
Matt said, "I would try to run this through wine (it's a windows installer, yes ?). Have you tried that ? Do you know how to ?"

In short ... no.

In longer! I am now pretty confident about adding programs. I have now got wine installed and it's showing in the list "Applications>Wine. I'll stop for lunch then browse around to see how it works.
Please don't give yourself any hassle on a glorious sunny Sunday afternoon.

---

### Post by Ireallyneedhelp on 2011-04-03
Wine in but no sign of Voipcheap. I'm trying to configure "wine" but when I click the control panel the message says, "Launching audio control panel not implemented yet". Eh?

---

### Post by matt_symes on 2011-04-03
Hi

Where did you install wine from ? Was it the repositories ?

Have you configured wine yet ? Open a terminal and type 

```
winecfg
```

You should be able to configure wine from there.

Try these values

Application tab: winodw version -> window XP
Audio tab: tick alsa driver and oss driver.
Graphics: Vertex shader support-> Hardware; tick allow pixel shading if supported.

That is what i use and that works for me.

Here is a link

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Kind regards

---

### Post by Ireallyneedhelp on 2011-04-03
Thanks. I found that link earlier and ran of a few pages. Wine now configured. I take it I have to download Voipcheap again in Wine.
EDIT  Ignore above. I went to Voipcheap and tried to download the .exe file. When I went to install it I got the message** "The file '/home/nerja/Downloads/setupvoipcheapCOM.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."**

I read through "executable bit" and I think I'll give it a miss for the moment. I'll read through it again slowly.
If I did what I **thought** it was saying and I was wrong, I'm worried I'd mess up the settings again. As it is, every time I boot up I still have to **guess** when I would get the option between XP and Ubuntu as the change I made yesterday (taking out a $) hasn't been recognised. I also have to keep telling the computer I have a Spanish keyboard. Ah the joys.

Update. Managed to download Voipcheap. It's in Wine. I started the program but it has now frozen. I can't kill the process. I've tried some suggestions I saw on other forums but to no avail. Running processes below

 1587 ?        00:00:00 indicator-sound
 1590 ?        00:00:00 indicator-messa
 1592 ?        00:00:00 gvfsd-burn
 1593 ?        00:00:00 gdu-notificatio
 1595 ?        00:00:00 firefox
 1599 ?        00:00:00 run-mozilla.sh
 1603 ?        00:05:46 firefox-bin
 1621 ?        00:01:03 plugin-containe
 1623 ?        00:00:00 applet.py
 1648 ?        00:00:00 update-notifier
 1835 ?        00:00:01 notify-osd
 1842 ?        00:00:00 gvfsd-http
 2397 ?        00:00:02 wineserver
 2401 ?        00:00:00 services.exe
 2403 ?        00:00:00 winedevice.exe
 2412 ?        00:00:00 explorer.exe
 2418 ?        00:00:11 VoipCheapCom.ex
 2536 ?        00:00:00 dhclient
 2605 ?        00:00:00 gvfsd-computer
 2855 ?        00:00:00 gnome-terminal
 2858 ?        00:00:00 gnome-pty-helpe
 2859 pts/0    00:00:00 bash
 2878 pts/0    00:00:00 ps

---

### Post by matt_symes on 2011-04-04
Hi

> 
As it is, every time I boot up I still have to **guess** when I would get the option between XP and Ubuntu as the change I made yesterday (taking out a $) hasn't been recognised. 

Not quite with you here. What change did you make ?

> I also have to keep telling the computer I have a Spanish keyboard. Ah the joys.

Is it not storing your keyboard settings after reboot ?

Please post the output of

```
cat /etc/default/locale
```

when you have rebooted and changed the layout and then after you have rebooted but before you change the layout.

> Update. Managed to download Voipcheap. It's in Wine. I started the program but it has now frozen. I can't kill the process. I've tried some suggestions I saw on other forums but to no avail. 

If you get a process that freezes and can't kill it the easiest way is to press ALT + F2 to bring up the run application dialog.

Type in the dialog

```
xkill
``` 

You cursor will change to an X. Move the cursor to the application that has frozen and hit the left mouse button. Problem solved :). There is an applet you can put on the panel called Force Quit and it will do the same thing.

> I started the program but it has now frozen.

How far did you get before it froze. Did the program start up and then freeze. Did it freeze when making a call ?

If you start the program fro the terminal it will give extra information in the terminal. That can help diagnose some issues. From the terminal

```
wine VoipCheapCom.exe
```

You may have to change the name VoipCheapCom.exe if that is the wrong file name. When it crashes post the last messages from the terminal here.

Kind regards

---

### Post by Ireallyneedhelp on 2011-04-04
Regarding changes to get Windows to show, Hedge suggested this:-
Get into Ubuntu (using your guessing method)  and the from the terminal  (Menu to: Applications >> Accessories >> Terminal) do this:

     Code:
     gksudo gedit /etc/default/grub 
     Code:
     [COLOR=Red]The change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR=red]To this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR=red]And save and exit the file.[/COLOR] 
***Removing the '#' turns this from a 'comment' line to a 'real' line.***

Finally, do this:

     Code:
     sudo update-grub 
Now when you reboot, you should see the grub menu, and (hopefully) find windows in the list.
****************************************************************************
It didn't work.

Keyboard defaults to English as you can see from the output:-
LANG="en_GB.UTF-8"

Regarding Voipcheap, I've now deleted it but it still appears in Wine so obviously it's NOT deleted!
I got as far as the Voipcheap sign in screen. I keyed in my details then it locked. I can't remember the message of-hand but it was something along the lines of a windows "an error has occurred."

---

### Post by Ireallyneedhelp on 2011-04-04
Voipcheap now totally deleted. It didn't delete before as I got a message saying the process was still running. Process killed(thanks)  and Voipcheap now somewhere in the ether.

---

