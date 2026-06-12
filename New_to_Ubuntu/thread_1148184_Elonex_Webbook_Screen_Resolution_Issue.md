---
title: "Elonex Webbook Screen Resolution Issue"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by webbooknovice on 2009-05-04
(SOLVED) Elonex Webbook Screen Resolution Issue.  Dear all, yesterday I upgraded my Elonex Webbook to Ubuntu 9.04 and now have an issue with the screen resolution and the 3G connection.  The Wader? broadband connector seems to be missing too.  As regards the screen resolution, it is currently too big, and means I can't scroll down to the bottom of some of the panels.  Any ideas, I so wish I'd just left things be!!

Thanks in advance.

Andy

---

### Post by Didius Falco on 2009-05-04
Hi Andy,

I think I've found a solution to the screen resolution problem:

[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

That's halfway home...

I hope it helps...

---

### Post by Didius Falco on 2009-05-04
Here is a link to the Wader PPA, where you can download the deb file and sneakernet it to your webbook for installation and then add the Repository to your **Software Sources** for any future updates.

[https://edge.launchpad.net/~wader/+archive/ppa]("https://edge.launchpad.net/%7Ewader/+archive/ppa")

I hope this resolves your issues...

Regards,

Didius

---

### Post by KJH on 2009-05-04
Yes I had the same problem and it drove me nuts.  The lovely people at Elonex were very friendly, but completely useless, the best they could offer was to rebuild the hard disk at my own expense with 8.04, as it was my fault for trying to upgrade to unsupported software - I politely declined.  I am no expert in Linux, but like an intellectual challenge, though this one taxed my patience to the limit!  

The work around I found was to put in a line explicitly defining the PanelSize in the xorg.conf file.  Search around on google for how to edit that file if you haven't done it before.  I think this is probably all you need to do, but I spent some time trying to find a work around so I also am using the OpenChrome drivers, (the Via chip in the Elonex is a CX700) and have put in the monitor size in the conf file too, neither of these worked, but I have not dared remove them yet as I wasted so much work time already on this :), and now the system is working fine I daren't waste more time on it.

So what i have added into my default xorg.conf is this (below), but as I say I suspect all you need is the line defining the PanelSize, so try that line first then add the other lines if this doesn't work, and download the drivers from the OpenChrome site if necessary but I think they are already included with Jaunty:

"Device"
Indetinfier "Configured Video Device"
Driver "openchrome"
Option "PanelSize" "1024x600"
EndSection

Section "Monitor"
Indentifier "Configured Monitor"
DisplaySize 221 129 # 117 DPI @ 1024x600
Opiton "noDDC"
EndSection


Please let me know how all you poor unsupported Elonex customers get on, and if you find any other mods that work, but I am finding this works just fine and really like Jaunty, especially the fast load time.

---

### Post by KJH on 2009-05-04
PS can't help with the 3G bit, as I don't use that so hope the solution above works

---

### Post by webbooknovice on 2009-05-06
SOLVED - Many thanks. Andy

---

### Post by webbooknovice on 2009-05-06
> **KJH said:**
> Yes I had the same problem and it drove me nuts.  The lovely people at Elonex were very friendly, but completely useless, the best they could offer was to rebuild the hard disk at my own expense with 8.04, as it was my fault for trying to upgrade to unsupported software - I politely declined.  I am no expert in Linux, but like an intellectual challenge, though this one taxed my patience to the limit!  

The work around I found was to put in a line explicitly defining the PanelSize in the xorg.conf file.  Search around on google for how to edit that file if you haven't done it before.  I think this is probably all you need to do, but I spent some time trying to find a work around so I also am using the OpenChrome drivers, (the Via chip in the Elonex is a CX700) and have put in the monitor size in the conf file too, neither of these worked, but I have not dared remove them yet as I wasted so much work time already on this :), and now the system is working fine I daren't waste more time on it.

So what i have added into my default xorg.conf is this (below), but as I say I suspect all you need is the line defining the PanelSize, so try that line first then add the other lines if this doesn't work, and download the drivers from the OpenChrome site if necessary but I think they are already included with Jaunty:

"Device"
Indetinfier "Configured Video Device"
Driver "openchrome"
Option "PanelSize" "1024x600"
EndSection

Section "Monitor"
Indentifier "Configured Monitor"
DisplaySize 221 129 # 117 DPI @ 1024x600
Opiton "noDDC"
EndSection


Please let me know how all you poor unsupported Elonex customers get on, and if you find any other mods that work, but I am finding this works just fine and really like Jaunty, especially the fast load time.

________________________________________________________________

Many thanks, it worked a treat. Andy

---

### Post by maxcelpc on 2009-06-04
Thank you KJH.

As you suspected, I only required the Options "PanelSize" "1024x600" line to get my display correct.

---

### Post by grinaldi on 2009-10-31
I have just updated my Elonex webbook with Ubuntu 9.10 and found my screen is unreadable - help! - please. :oops:

---

### Post by Hygaphunkik on 2009-11-01
> **grinaldi said:**
> I have just updated my Elonex webbook with Ubuntu 9.10 and found my screen is unreadable - help! - please. :oops:

Have just finished upgrading this afternoon and found this page which helped a huge amount [http://webbookblog.com/]("http://webbookblog.com/")

Just one thing though where he writes the line 

Section Device

right at the beginning he should have put 

Section "Device"

The quotes are important, without them it will not work.

Hope this helps, and let me know how it goes.

---

### Post by grinaldi on 2009-11-01
Looked at your suggestion, but do not have the equipment mention in webbookblog.

I have started my Elonex webbook in safe mode and gone to the comand-line. But, when I type "sudo gedit /etc/X11/xorg.conf" I get the following error message "Gtk-WARNING **: cannot open display"

Any suggestions welcome - Thanks in anticipation. ](*,)

I have used a relative's windows laptop to write this message.

---

### Post by Hygaphunkik on 2009-11-02
> **grinaldi said:**
> Looked at your suggestion, but do not have the equipment mention in webbookblog.

I have started my Elonex webbook in safe mode and gone to the comand-line. But, when I type "sudo gedit /etc/X11/xorg.conf" I get the following error message "Gtk-WARNING **: cannot open display"

Any suggestions welcome - Thanks in anticipation. ](*,)

I have used a relative's windows laptop to write this message.


If you can get to the prompt try writing in 
"sudo nano /etc/X11/xorg.conf" 

That should bring you up a command line text editor, but to be honest I am just guessing about this, I am no expert but it has got to be worth a try.

Let me know how you get on, and if anyone else has any better ideas please help.

---

### Post by grinaldi on 2009-11-02
> **Hygaphunkik said:**
> If you can get to the prompt try writing in 
"sudo nano /etc/X11/xorg.conf" 

That should bring you up a command line text editor, but to be honest I am just guessing about this, I am no expert but it has got to be worth a try.

Let me know how you get on, and if anyone else has any better ideas please help.

Thanks for your help - it worked.

I guess we have both learnt something and you appear to be one step nearer to being an expert.

Thanks again :D

---

### Post by Nad42 on 2010-07-22
Hi dunno if this thread is a bit dead but... ive just put ubuntu netbook remix onto my webbook and ive done what was said above and got the resolution working but the main desktop screen is unreadable and the mouse cant click on anything... just wondering if anyone knew what is up with it?

---

