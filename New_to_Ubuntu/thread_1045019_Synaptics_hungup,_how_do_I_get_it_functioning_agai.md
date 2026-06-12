---
title: "Synaptics hungup, how do I get it functioning again?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Wilbur Kelly on 2009-01-20
Problem with Synaptics, the exact error message below:

"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first."

So I Logged out and logged back in thinking this would shut down any open processes.  I then:
wkelly@wkelly-desktop:~$ sudo apt-get update
And after a lot of lines scrolled past it ended with:
"Fetched 3B in 2s (1B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

I was downloading a package in aptitude when the screen hungup and I had to quit that screen. There was an error message that gave me some instruction to type into a terminal that started with "type dpkg --something -a" I have looked at the help accessed by "dpkg --help" but I don't find the "something" now so cannot replay it now (should have but didn't write it down at the time).  Still, that seems to be where the problem started and where it may need to be fixed since it persists despite logging out and back in.

I can open aptitude and close it without problem now but when I choose "become root" I get virtually the same error message described.  

If this sounds like I have a clue what I am doing, it means I have been trying to solve it by searching on my own but that is not working...

I don't know what to do next.  I would sincerely appreciate any suggestions.

wkelly

---

### Post by glotz on 2009-01-20
Probably **dpkg --configure -a**

---

### Post by Wilbur Kelly on 2009-01-20
> **glotz said:**
> Probably **dpkg --configure -a**

That sounds right.  I'm pretty sure that was it.  The window that hung up had a text window with some instructions and had <OK> at the bottom of it.  I tried to find a way to click on the OK but it was not something I found a way to do.  I closed the window.  Then somehow I triggered the instruction that I think you have "filled in": configure:

dpkg --configure -a

Any idea what I can do to unlock "the administration directory (/var/lib/dpkg/)"?

---

### Post by diablo75 on 2009-01-20
> **Wilbur Kelly said:**
> That sounds right.  I'm pretty sure that was it.  The window that hung up had a text window with some instructions and had <OK> at the bottom of it.  I tried to find a way to click on the OK but it was not something I found a way to do.  I closed the window.  Then somehow I triggered the instruction that I think you have "filled in": configure:

dpkg --configure -a

Any idea what I can do to unlock "the administration directory (/var/lib/dpkg/)"?

Close Synaptic Package Manager first.  You can only have one Update/Install manager program running at a time. and both Synaptic and dpkg fall into that category.

---

### Post by Wilbur Kelly on 2009-01-20
> **diablo75 said:**
> Close Synaptic Package Manager first.  You can only have one Update/Install manager program running at a time. and both Synaptic and dpkg fall into that category.

I've closed synaptics and don't have anything else open but this browser window that I know of...

wkelly

---

### Post by diablo75 on 2009-01-20
> **Wilbur Kelly said:**
> I've closed synaptics and don't have anything else open but this browser window that I know of...

wkelly

Try logging off, then log back in, open a terminal and run that command again.  It should work.

---

### Post by Wilbur Kelly on 2009-01-20
> **diablo75 said:**
> Try logging off, then log back in, open a terminal and run that command again.  It should work.

Sorry to be dense, it's late here... "Run that command again" refer to:
dpkg --configure -a 

Just want to be clear.  Thanks.

---

### Post by diablo75 on 2009-01-20
> **Wilbur Kelly said:**
> Sorry to be dense, it's late here... "Run that command again" refer to:
dpkg --configure -a 

Just want to be clear.  Thanks.

That be it, dude!  :)

---

### Post by Wilbur Kelly on 2009-01-20
> **diablo75 said:**
> That be it, dude!  :)
logging out, loggint in, catch you on the way back, 

thanks
wkelly

---

### Post by Wilbur Kelly on 2009-01-20
> **Wilbur Kelly said:**
> logging out, loggint in, catch you on the way back, 

thanks
wkelly

OK.  I'm back up and have the original problem again.  The program I was originally trying to install by aptitude came back up in the terminal window as if I had never delt with it yet which is probably why it isn't ready to relinquish control.  I did screen captures of the problem terminal window.  I have a terminal window with a box with text that I can scroll the window-within-the-window and at the bottom of the inner window an "<ok>" with no way I know of to tell the program "OK", I have tried highlighting the <ok> and hitting the enter button, but that doesn't work.  

The last time I saw this I gave up and closed the terminal window but that is how I got here.  

Any suggestions?

There is a line at the top of the main box that says:
"Package configuration" which I suspect is part of apptitude.

---

### Post by diablo75 on 2009-01-20
Try this:

```
sudo apt-get install -f
```

---

### Post by Wilbur Kelly on 2009-01-20
> **diablo75 said:**
> Try this:

```
sudo apt-get install -f
```

Result:

wkelly@wkelly-desktop:~$ sudo apt-get install -f
[sudo] password for wkelly: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

And then I thought, maybe I have to close the other terminal window first, but since I can't tell it "ok", I just have to close it anyway... So I did.

And then got: 
wkelly@wkelly-desktop:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
wkelly@wkelly-desktop:~$ 

And when I did that I got the same problem I had originally closed the first terminal window on, the incomplete install of the first program that I can't tell ok.
************************************

Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring moblock-control &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; WARNING: MoBlock may block your complete network/internet access!         &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; MoBlock starts automatically at system boot per default. Some             &#9618; 
 &#9474; preconfigured blocklists are updated once a day. Be warned, that MoBlock  &#9618; 
 &#9474; will not only block many unwanted IPs, but in most cases running MoBlock  &#9618; 
 &#9474; will result in a limited network availability. This includes your own     &#9618; 
 &#9474; LAN and router, many webpages, services like eMail, instant messaging or  &#9618; 
 &#9474; the "weather applet" and your machine's accessibility from the internet.  &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; There are many configuration options to prevent this. Per default         &#9618; 
 &#9474; traffic to your own LAN will always be allowed (whitelisted). This        &#9618; 
 &#9474; feature is still experimental. If you are on a public LAN, you probably   &#9618; 
 &#9474; want to disable this feature. 
 You can now tweak MoBlock's behaviour.                                    &#9618; 
                                <Ok> &#9474;                                                                           &#9618; 
 &#9474; These settings can later be changed with                                  &#9646; 
 &#9474;  sudo dpkg-reconfigure moblock-control  

**********************
The <ok> above is separate from the rest of the text and stays where it is placed while the last two lines scroll up from below the window.  Still no way I see to tell the program "OK"

---

### Post by diablo75 on 2009-01-20
> **Wilbur Kelly said:**
> Result:

wkelly@wkelly-desktop:~$ sudo apt-get install -f
[sudo] password for wkelly: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

And then I thought, maybe I have to close the other terminal window first, but since I can't tell it "ok", I just have to close it anyway... So I did.

And then got: 
wkelly@wkelly-desktop:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
wkelly@wkelly-desktop:~$ 

And when I did that I got the same problem I had originally closed the first terminal window on, the incomplete install of the first program that I can't tell ok.
************************************

Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring moblock-control &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; WARNING: MoBlock may block your complete network/internet access!         &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; MoBlock starts automatically at system boot per default. Some             &#9618; 
 &#9474; preconfigured blocklists are updated once a day. Be warned, that MoBlock  &#9618; 
 &#9474; will not only block many unwanted IPs, but in most cases running MoBlock  &#9618; 
 &#9474; will result in a limited network availability. This includes your own     &#9618; 
 &#9474; LAN and router, many webpages, services like eMail, instant messaging or  &#9618; 
 &#9474; the "weather applet" and your machine's accessibility from the internet.  &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; There are many configuration options to prevent this. Per default         &#9618; 
 &#9474; traffic to your own LAN will always be allowed (whitelisted). This        &#9618; 
 &#9474; feature is still experimental. If you are on a public LAN, you probably   &#9618; 
 &#9474; want to disable this feature. 
 You can now tweak MoBlock's behaviour.                                    &#9618; 
                                <Ok> &#9474;                                                                           &#9618; 
 &#9474; These settings can later be changed with                                  &#9646; 
 &#9474;  sudo dpkg-reconfigure moblock-control  

**********************
The <ok> above is separate from the rest of the text and stays where it is placed while the last two lines scroll up from below the window.  Still no way I see to tell the program "OK"

Try pressing the Tab key to select the OK "button" and press enter.

---

### Post by Wilbur Kelly on 2009-01-20
> **diablo75 said:**
> Try pressing the Tab key to select the OK "button" and press enter.

Bingo.
There were a lot of screens that followed.
All worked the same way.

It is late here and the alternative was quitting for the night with the machine in limbo.

I really appreciate your help.

wkelly

---

